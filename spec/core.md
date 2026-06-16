# OLTS Core Draft

This file captures the initial public direction for OLTS Core. It is draft material for `v0.1.0`, not a stable `v1.0.0` standard.

OLTS Core defines the minimum shared language needed to make lifecycle traceability explicit, repo-native, reviewable, and automatable.

## Core Principles

1. Product repositories remain the source of truth.
2. Stable identifiers name lifecycle entities, not status or priority.
3. Important lifecycle relationships are explicit records, not inferred guesses.
4. Generated views, diagrams, indexes, and reports are derived artifacts.
5. Automation may diagnose and propose; humans approve canonical truth.
6. Missing lifecycle data produces diagnostics, not false confidence.
7. OLTS must not require a specific ALM tool, database, UI, AI agent, MBSE framework, or change-governance method.

## Lifecycle Identifier Shape

The draft identifier shape is:

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

Stable IDs should not encode status, priority, maturity, owner, release, branch, or implementation state. Those are attributes that may change.

## Draft Entity Types

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

Adopters may add local entity types during experimentation, but public conformance claims should identify which types are draft OLTS types and which are local extensions.

## Minimal Record Shape

A lifecycle record should include at least:

```yaml
id: APP-SR-00014
type: SR
title: Operator can revoke an API token
```

The `type` value uses the entity-type code from the Draft Entity Types table, such as `UC`, `SR`, `VT`, or `EVD`.

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

OLTS should be format-tolerant. The same concepts may be represented in Markdown with YAML frontmatter, CSV, YAML, JSON, existing ALM exports, issue tracker metadata, OpenSpec changes, ADR folders, and release or evidence records.

For early adoption, Markdown, CSV, YAML, and JSON are preferred because they are easy to review in pull requests.

## Provenance

A conforming reader or validator should preserve enough provenance for each lifecycle fact to answer:

1. Which repository or source owns this fact?
2. Which file or external system record provided it?
3. Which row, heading, key, or section identified it?
4. Which version, commit, timestamp, or source hash was inspected when practical?

Provenance is essential because OLTS is designed to support review, CI checks, generated diagrams, and AI-assisted recommendations without replacing source truth.

## Diagnostics

OLTS diagnostics should be explicit and reviewable. Draft diagnostic categories include:

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

A missing source should not be treated as a healthy zero state. It should produce a diagnostic.

## Draft Conformance Levels

| Level | Meaning |
| --- | --- |
| L1: Stable IDs | Lifecycle entities have durable identifiers. |
| L2: Explicit Relationships | Key relationships are recorded in reviewable files. |
| L3: Verification Coverage | Requirements and use cases link to tests or validation scenarios. |
| L4: Evidence Coverage | Tests, validation scenarios, and release claims link to evidence. |
| L5: Automated Conformance | CI checks validate identifiers, links, provenance, and diagnostics. |

These labels are provisional during the `v0.x` draft series.
