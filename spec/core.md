# OLTS Core

This file captures the release-candidate OLTS Core model. It remains launch-gated until maintainers explicitly approve public visibility, the `v1.0.0` tag, and the GitHub Release.

OLTS Core defines the minimum shared language needed to make lifecycle traceability explicit, repo-native, reviewable, and automatable.

The candidate `v1.0.0` core terminology review is recorded in [../docs/core-terminology.md](../docs/core-terminology.md).

## Normative Language

The key words `MUST`, `MUST NOT`, `SHOULD`, `SHOULD NOT`, and `MAY` in OLTS specification files are to be interpreted as described in RFC 2119 and RFC 8174 when, and only when, they appear in all capitals.

Lowercase words such as "should", "may", and "recommended" are ordinary explanatory language unless this standard explicitly says otherwise.

Before an explicit public launch and certification policy, normative keywords describe intended stable semantics. They do not create a public certification program, public release guarantee, or third-party compliance claim.

## Core Principles

1. Product repositories remain the source of truth.
2. Stable identifiers name lifecycle entities, not status or priority.
3. Important lifecycle relationships are explicit records, not inferred guesses.
4. Generated views, diagrams, indexes, and reports are derived artifacts.
5. Automation MAY diagnose and propose; humans MUST approve canonical lifecycle truth.
6. Missing lifecycle data produces diagnostics, not false confidence.
7. OLTS MUST NOT require a specific ALM tool, database, UI, AI agent, MBSE framework, or change-governance method.

## Lifecycle Identifier Shape

The candidate identifier shape is:

```text
<DOMAIN>-<TYPE>-<NNNNN>
```

Where:

- `DOMAIN` is a short uppercase prefix owned by the adopting product, platform, project, or organization.
- `TYPE` is the lifecycle entity type.
- `NNNNN` is a five-digit counter scoped by `(DOMAIN, TYPE)`.

Examples:

```text
APP-UC-00003
APP-SR-00014
APP-VT-00221
APP-EVD-00098
```

Stable IDs name lifecycle entities. They SHOULD NOT encode status, priority, maturity, owner, release, branch, or implementation state. Those are attributes that may change.

## Candidate Entity Types

| Type | Entity | Meaning |
| --- | --- | --- |
| `CAP` | Capability | Product or platform capability grouping. |
| `TRK` | Work item | Tracker row, issue, ticket, or planned implementation item. |
| `UC` | Use case | User, operator, system, or stakeholder scenario. |
| `SR` | System requirement | Functional, quality, security, safety, compliance, or system requirement. |
| `VT` | Verification test | Test that verifies one or more requirements. |
| `VAL` | Validation scenario | Scenario that validates user or stakeholder need. |
| `EVD` | Evidence | Test result, audit record, report, log, or release evidence. |
| `ART` | Artifact | Design doc, diagram, interface spec, generated artifact, or other lifecycle artifact. |
| `ADR` | Decision | Architecture decision, design decision, or accepted rationale record. |

Adopters MAY add local entity types during experimentation, but public conformance claims SHOULD identify which types are core OLTS types and which are local extensions.

## Minimal Record Shape

A lifecycle record MUST include at least:

```yaml
id: APP-SR-00014
type: SR
title: Operator can revoke an API token
```

The `type` value uses the entity-type code from the Candidate Entity Types table, such as `UC`, `SR`, `VT`, or `EVD`. The `type` value MUST match the `<TYPE>` segment in `id`; for example, `APP-SR-00014` uses `type: SR`.

A more useful record includes explicit relationships:

```yaml
id: APP-SR-00014
type: SR
title: Operator can revoke an API token
verified_by:
  - APP-VT-00221
explained_by:
  - APP-ADR-00007
```

## Source Formats

OLTS SHOULD be format-tolerant. The same concepts MAY be represented in Markdown with YAML frontmatter, CSV, YAML, JSON, existing ALM exports, issue tracker metadata, OpenSpec changes, ADR folders, and release or evidence records.

For early adoption, Markdown, CSV, YAML, and JSON are preferred because they are easy to review in pull requests. Candidate v1 JSON Schemas under [../schemas/](../schemas/) describe the shared validation contracts for records, parsed relationship rows, diagnostics, conformance reports, and generated artifact metadata.

## Source-of-Truth Boundaries

OLTS does not replace repository or system source truth. It makes lifecycle facts explicit enough for review, validation, reporting, and automation.

Product repositories, reviewed files, or reviewed external systems own lifecycle truth. OLTS records and relationship rows are source truth only when the adopting repository accepts them through normal review.

Generated diagrams, dashboards, indexes, reports, traceability matrices, and review packets are derived unless explicitly accepted as source truth through reviewed source-truth policy.

Automation MAY diagnose, summarize, visualize, and propose updates. Humans MUST approve canonical lifecycle truth through normal review.

Missing or unreadable sources MUST produce diagnostics instead of healthy zero states.

## Generated Artifacts

Generated artifacts SHOULD preserve the source files, records, relationship rows, external systems, commits, timestamps, hashes, omitted facts, diagnostics, and generator metadata needed for reviewers to understand how the artifact was produced.

If a repository wants a generated artifact to become source truth, it MUST define and follow a reviewed acceptance process. Without that acceptance, generated artifacts remain derived and rebuildable.

## Provenance

A conforming reader or validator SHOULD preserve enough provenance for each lifecycle fact to answer:

1. Which repository or source owns this fact?
2. Which file or external system record provided it?
3. Which row, heading, key, or section identified it?
4. Which version, commit, timestamp, or source hash was inspected when practical?

Provenance is essential because OLTS is designed to support review, CI checks, generated diagrams, and AI-assisted recommendations without replacing source truth.

## Diagnostics

OLTS diagnostics SHOULD be explicit and reviewable. Candidate diagnostic categories include:

- invalid identifier shape;
- duplicate identifier;
- missing referenced entity;
- unknown relationship type;
- missing required relationship file;
- missing verification coverage;
- missing validation coverage;
- missing evidence coverage;
- malformed source record;
- ambiguous external reference;
- generated artifact missing provenance.

A missing source MUST NOT be treated as a healthy zero state. It SHOULD produce a diagnostic.

## Conformance Summary

The OLTS conformance ladder is defined in [conformance.md](conformance.md). In summary:

| Level | Meaning |
| --- | --- |
| `L1` | Lifecycle entities have durable identifiers. |
| `L2` | Key relationships are recorded in reviewable files or fields. |
| `L3` | Requirements and use cases in scope link to tests or validation scenarios. |
| `L4` | Tests, validation scenarios, and release claims in scope link to evidence. |
| `L5` | Automated checks validate identifiers, relationships, provenance, and diagnostics. |

These labels remain launch-gated until maintainers approve the public `v1.0.0` release.
