# OLTS Schemas

This directory contains machine-readable schema contracts for OLTS `v1.0.0` readiness. They are candidate stable contracts for early adopters and tooling authors, but they do not create a public `v1.0.0` release or compatibility guarantee until maintainers explicitly approve the public release.

## Schema Files

| File | Purpose |
| --- | --- |
| [olts-record.schema.json](olts-record.schema.json) | Validates one lifecycle record with a stable ID, entity type, title, optional provenance, and inline relationship fields. |
| [olts-relationship.schema.json](olts-relationship.schema.json) | Validates one parsed relationship row using the draft relationship vocabulary. |
| [olts-diagnostic.schema.json](olts-diagnostic.schema.json) | Validates one diagnostic emitted by review, local scripts, CI, or future reference tooling. |
| [olts-conformance-report.schema.json](olts-conformance-report.schema.json) | Validates one conformance report for a stated level and scope. |
| [olts-generated-artifact.schema.json](olts-generated-artifact.schema.json) | Validates metadata for generated diagrams, dashboards, RTMs, reports, indexes, or review packets. |

## Schema Identifiers

Schema `$id` values use stable, versioned, vendor-neutral URNs:

| File | `$id` |
| --- | --- |
| [olts-record.schema.json](olts-record.schema.json) | `urn:olts:schema:v1:record` |
| [olts-relationship.schema.json](olts-relationship.schema.json) | `urn:olts:schema:v1:relationship` |
| [olts-diagnostic.schema.json](olts-diagnostic.schema.json) | `urn:olts:schema:v1:diagnostic` |
| [olts-conformance-report.schema.json](olts-conformance-report.schema.json) | `urn:olts:schema:v1:conformance-report` |
| [olts-generated-artifact.schema.json](olts-generated-artifact.schema.json) | `urn:olts:schema:v1:generated-artifact` |

Cross-schema references use those same `urn:olts:schema:v1:*` identifiers. Future incompatible schema generations should use a new version segment rather than changing the meaning of existing v1 identifiers.

## Scope

The schemas intentionally stay small and readable. They cover the shared shape of OLTS facts while leaving room for repository-specific extensions during the `v0.x` draft period.

They are designed around the current draft specs:

- [../spec/core.md](../spec/core.md)
- [../spec/relationships.md](../spec/relationships.md)
- [../spec/conformance.md](../spec/conformance.md)

Core entity types, identifier shape, source-of-truth boundaries, and generated artifact semantics are reviewed in [../docs/core-terminology.md](../docs/core-terminology.md).

Relationship verb direction and naming are reviewed in [../docs/relationship-semantics.md](../docs/relationship-semantics.md). The relationship schema enum matches the core vocabulary documented there.

Schema-to-prose alignment is reviewed in [../docs/schema-contract-review.md](../docs/schema-contract-review.md). That review records which expectations are expressed directly in portable JSON Schema and which remain semantic checks for validators or reviewers.

## Record Type Invariant

The record schema validates the shape of `id` and `type`, but plain JSON Schema cannot portably compare the `type` value with the type segment embedded in `id`.

OLTS validators MUST apply this semantic check in addition to JSON Schema validation:

```text
record.type == the <TYPE> segment of record.id
```

For example, `APP-SR-00014` must use `type: SR`. The same rule applies to documented local entity types.

## CSV Relationship Files

OLTS examples use CSV because CSV is easy to review in pull requests. JSON Schema does not validate raw CSV text directly. A validator can parse each CSV row into an object with these keys and then validate each object with [olts-relationship.schema.json](olts-relationship.schema.json):

```json
{
  "Source_Key": "APP-UC-00003",
  "Target_Key": "APP-SR-00014",
  "Relationship": "requires",
  "Notes": "Use case depends on requirement"
}
```

See [../docs/schema-validation.md](../docs/schema-validation.md) for a repeatable validation path that covers schema parsing, record validation, CSV row mapping, and semantic checks that plain JSON Schema cannot express.

## Extension Guidance

Local extensions are allowed during the draft period, but they should be documented. A repository that adds local entity types, relationship verbs, diagnostic codes, or metadata fields should state whether those extensions are local-only or proposed for future OLTS standardization.

The core relationship schema accepts only the draft OLTS relationship vocabulary. Repositories that intentionally use local relationship verbs should layer their own schema overlay on top of the core schema rather than presenting local verbs as core OLTS vocabulary.

See [../docs/extensions.md](../docs/extensions.md) for extension behavior across records, relationship rows, diagnostics, conformance reports, generated artifact metadata, and local schema overlays.

## Stability

These schemas are candidate v1 contracts. They may still change before `v1.0.0` if review finds a blocking issue, but changes to identifiers, required fields, relationship vocabulary, or cross-schema references should be treated as v1 readiness decisions and reviewed intentionally.
