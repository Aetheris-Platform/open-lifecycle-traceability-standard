# OLTS Core Terminology Review

This review records the candidate `v1.0.0` core terminology decisions for entity types, identifier shape, source-of-truth boundaries, generated artifacts, and launch-gated language.

It is launch-readiness evidence, not a release announcement. OLTS remains a private `v1.0.0` release candidate until maintainers explicitly approve public visibility, the `v1.0.0` tag, and the GitHub Release.

## Entity Types

The candidate core entity types are:

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

These types are intentionally broad enough to cover common software and systems-development pipelines without requiring a specific ALM, issue tracker, MBSE platform, OpenSpec workflow, or AI tool.

Repositories MAY define local entity types, but local types remain extensions unless accepted into OLTS. Conformance claims SHOULD distinguish core OLTS entity types from documented local extensions.

## Identifier Shape

The candidate identifier shape is:

```text
<DOMAIN>-<TYPE>-<NNNNN>
```

Where:

- `DOMAIN` is a short uppercase prefix owned by the adopting product, platform, project, or organization;
- `TYPE` is a core OLTS entity type or documented local entity type;
- `NNNNN` is a five-digit counter scoped by `(DOMAIN, TYPE)`.

Stable IDs name lifecycle entities. They SHOULD NOT encode status, priority, maturity, owner, release, branch, or implementation state because those values can change while the lifecycle entity remains the same.

The `type` field in a record MUST match the `<TYPE>` segment in `id`. For example, `APP-SR-00014` uses `type: SR`.

## Source-of-Truth Boundaries

OLTS does not replace repository or system source truth. It makes lifecycle facts explicit enough for review, validation, reporting, and automation.

Core boundaries:

- Product repositories, reviewed files, or reviewed external systems own lifecycle truth.
- OLTS records and relationship rows are source truth only when the adopting repository accepts them through normal review.
- Generated diagrams, dashboards, indexes, reports, traceability matrices, and review packets are derived unless explicitly accepted as source truth through reviewed source-truth policy.
- Automation MAY diagnose, summarize, visualize, and propose updates.
- Humans MUST approve canonical lifecycle truth through normal review.
- Missing or unreadable sources MUST produce diagnostics instead of healthy zero states.

These boundaries apply whether the repository uses Markdown, CSV, YAML, JSON, OpenSpec, GitHub Issues, Jira, Azure Boards, ADRs, ALM exports, MBSE tools, local scripts, CI jobs, or AI agents.

## Generated Artifacts

Generated artifacts are useful because they make traceability easier to inspect, but they are not automatically canonical.

Generated artifacts SHOULD preserve:

- source files, records, or external systems inspected;
- source commits, timestamps, or hashes when practical;
- relationship rows or lifecycle facts included;
- omitted facts and reasons when the artifact is partial;
- diagnostics that affected the artifact;
- generator name, version, or configuration when practical.

If a repository wants a generated artifact to become source truth, it MUST define and follow a reviewed acceptance process. Without that acceptance, generated artifacts remain derived and rebuildable.

## Launch-Gated Language

During the private release-candidate period, OLTS documents still use launch-gated framing because the stable public release has not been approved.

For `v1.0.0` readiness, launch-gated language is scoped as follows:

- Draft framing may describe historical milestones, unreleased readiness work, provisional milestones, or future experimental material.
- Candidate v1 decisions may be documented before release, but they do not create a public release, certification program, or compatibility guarantee.
- Public-facing `v1.0.0` release material should not imply that unresolved draft work is stable.
- Any future experimental material after `v1.0.0` should be clearly labeled as experimental or future-facing.

## Cross-Artifact Consistency

The core terminology is aligned across the current release-candidate materials:

| Surface | Consistency evidence |
| --- | --- |
| [../spec/core.md](../spec/core.md) | Defines principles, identifier shape, entity types, source formats, source-truth boundaries, generated artifacts, provenance, diagnostics, and conformance summary. |
| [../README.md](../README.md) | States product repositories remain source truth and automation requires human approval. |
| [overview.md](overview.md) | Describes the same source-truth, derived-artifact, and tool-agnostic principles. |
| [../spec/README.md](../spec/README.md) | States non-goals and source-truth boundaries for the release-candidate specification. |
| [../examples/minimal/README.md](../examples/minimal/README.md) | States that example records and relationships become source truth only through normal review and generated views remain derived. |
| [../examples/realistic/README.md](../examples/realistic/README.md) | States the same source-truth and generated-artifact boundary for a fuller L4 example. |
| [../schemas/README.md](../schemas/README.md) | Describes candidate schema contracts and the record `type` versus ID type-segment invariant. |
| [../schemas/olts-record.schema.json](../schemas/olts-record.schema.json) | Validates record shape and documents core entity-type codes plus local extensions. |
| [../schemas/olts-generated-artifact.schema.json](../schemas/olts-generated-artifact.schema.json) | Requires generated artifact metadata and keeps generated artifacts derived by default. |

## Diagnostics

Reviewers and validators SHOULD diagnose:

- invalid identifier shape;
- record `type` mismatch with the ID type segment;
- unknown entity type without a documented local extension;
- generated artifact metadata that lacks source provenance;
- generated views presented as source truth without reviewed acceptance;
- missing or unreadable source inputs treated as healthy results.
