# OLTS Schema Validation Path

This guide describes one repeatable way to validate OLTS candidate v1 records, relationship rows, and examples against the candidate v1 schema contracts.

It is validation guidance, not required reference tooling. OLTS adopters MAY use any JSON Schema validator, CI system, local script, review checklist, or external tool that preserves the same semantics and produces reviewable diagnostics.

## Validation Goals

A useful OLTS validation path should answer:

1. Do schema files parse as JSON?
2. Do lifecycle records match the candidate record schema?
3. Do relationship CSV rows map cleanly into relationship-row objects?
4. Do relationship rows use known verbs and resolvable targets?
5. Do semantic rules that JSON Schema cannot express pass or produce diagnostics?
6. Does the report identify its scope, inputs, diagnostics, and advisory or blocking posture?

Passing these checks does not create an OLTS certification claim. It only gives reviewers evidence for the stated scope.

## Inputs

A validator normally needs:

- one or more lifecycle record files, such as YAML, JSON, Markdown frontmatter, or an exported tracker format;
- one or more relationship files, usually CSV during early adoption;
- the candidate schemas under [../schemas/](../schemas/);
- any documented local extensions for entity types, relationship verbs, metadata fields, or diagnostic codes;
- the claimed OLTS level and scope, if the output is used as conformance evidence.

## Recommended Sequence

### 1. Parse Schema Files

All schema files under [../schemas/](../schemas/) SHOULD parse as JSON before they are used by a validator.

Example:

```text
parse schemas/*.schema.json as JSON
fail or diagnose malformed schema files
```

### 2. Validate Record Shape

Each parsed lifecycle record SHOULD validate against [../schemas/olts-record.schema.json](../schemas/olts-record.schema.json).

At minimum, the validator SHOULD check:

- `id` exists and follows `<DOMAIN>-<TYPE>-<NNNNN>`;
- `type` exists;
- `title` exists and is not empty;
- inline relationship fields, such as `verified_by` or `explained_by`, contain OLTS IDs or external references;
- extension fields remain reviewable and documented.

### 3. Map CSV Rows Before Schema Validation

JSON Schema does not validate raw CSV text. A relationship CSV file SHOULD first be parsed into one object per row.

For this CSV row:

```csv
Source_Key,Target_Key,Relationship,Notes
APP-UC-00003,APP-SR-00014,requires,Use case depends on requirement
```

The parsed object is:

```json
{
  "Source_Key": "APP-UC-00003",
  "Target_Key": "APP-SR-00014",
  "Relationship": "requires",
  "Notes": "Use case depends on requirement"
}
```

Each parsed object SHOULD validate against [../schemas/olts-relationship.schema.json](../schemas/olts-relationship.schema.json).

CSV parsers SHOULD preserve source row numbers when practical so diagnostics can point back to the reviewed file.

### 4. Apply Semantic Checks

Some OLTS rules are intentionally semantic and cannot be expressed portably in JSON Schema alone.

Validators SHOULD apply these checks in addition to schema validation:

- `record.type` MUST match the `<TYPE>` segment in `record.id`;
- lifecycle IDs MUST NOT be reused for different entities in the checked scope;
- relationship verbs MUST use the draft OLTS vocabulary or documented local extensions;
- relationship direction SHOULD match [../spec/relationships.md](../spec/relationships.md);
- OLTS relationship targets SHOULD resolve to known records unless they are documented external references;
- inline relationship fields SHOULD align with relationship-file rows when both are present;
- missing files, parser failures, or disabled sources MUST NOT be treated as healthy zero-result scans.

When a semantic check cannot be completed, the validator SHOULD emit a diagnostic rather than silently passing.

## Example Validation Scope

The minimal example can be checked as a small shape and relationship-row validation case:

- parse every record in [../examples/minimal/records.yaml](../examples/minimal/records.yaml);
- validate each record shape;
- confirm each `type` matches the ID type segment;
- parse [../examples/minimal/relationships.csv](../examples/minimal/relationships.csv);
- validate each parsed relationship row;
- confirm all relationship verbs are in the draft vocabulary;
- confirm each OLTS relationship source and target resolves to a record in the example.

The realistic example exercises a broader scoped L4 traceability chain:

- parse every record in [../examples/realistic/records.yaml](../examples/realistic/records.yaml);
- validate each record shape;
- confirm each `type` matches the ID type segment;
- parse [../examples/realistic/relationships.csv](../examples/realistic/relationships.csv);
- validate each parsed relationship row;
- confirm each OLTS target resolves to a record in the example, unless it is an external reference such as `openspec:passwordless-sign-in`;
- confirm evidence attaches to validation, verification, or artifact records rather than acting as unexplained direct proof for a requirement.

## Diagnostics and Reports

Validation output SHOULD be reviewable even when it is generated by a local script, CI job, or external tool.

A useful report SHOULD identify:

- claimed level and checked scope;
- source files inspected;
- schema identifiers used;
- local extensions allowed;
- diagnostics found;
- reviewed exceptions;
- whether the result is advisory or blocking;
- if blocking, which severities, diagnostic codes, or source-read failures can block the stated scope.

Conformance reports can use [../schemas/olts-conformance-report.schema.json](../schemas/olts-conformance-report.schema.json), and individual diagnostics can use [../schemas/olts-diagnostic.schema.json](../schemas/olts-diagnostic.schema.json).

## CI Guidance

Early CI jobs SHOULD start as advisory checks. They can become blocking only after maintainers trust the parser, schema mapping, semantic checks, and diagnostic quality for the claimed scope.

A CI job SHOULD NOT report an unscoped `OLTS L3`, `OLTS L4`, or `OLTS L5` result when it inspected only selected paths, entity types, or releases.

Manual checklists, local scripts, CI jobs, external validators, and platform-native checks can all produce validation evidence. The chosen validation path SHOULD preserve OLTS semantics and report the same scope, sources, diagnostics, exceptions, and advisory or blocking posture.

L5 does not require OLTS reference tooling. A repository can make a scoped draft L5 claim with its own automation if the checks preserve OLTS semantics and produce reviewable diagnostics.

## Extension Handling

Local extensions SHOULD be declared before validation runs. See [extensions.md](extensions.md) for the full extension model.

A validator SHOULD distinguish:

- core OLTS entity types and relationship verbs;
- local entity types and relationship verbs that are allowed for this repository;
- unknown values that should produce diagnostics;
- proposed extensions that are not yet accepted into the core standard.

Local extensions MUST NOT be presented as core OLTS vocabulary unless accepted into the standard.
