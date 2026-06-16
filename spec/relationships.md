# OLTS Relationship Model Draft

This file captures the initial direction for explicit OLTS relationships. It is draft material, not a stable `v1.0.0` standard.

Normative keywords in this file use the convention defined in [core.md](core.md#normative-language).

## Relationship Principle

A lifecycle relationship is a reviewed statement that one lifecycle entity depends on, supports, verifies, validates, documents, explains, or provides evidence for another lifecycle entity.

Relationships SHOULD be explicit. OLTS-compatible tooling MUST NOT infer canonical relationships from text similarity, filename similarity, row order, heading names, generated diagrams, or AI guesses.

## Draft Relationship Chain

A common traceability chain is:

```text
Capability -> Use Case -> System Requirement -> Verification Test -> Evidence
```

Other useful links include:

```text
Work Item -> Capability
Work Item -> Use Case
Work Item -> Requirement
Requirement -> Artifact
Requirement -> Decision
Artifact -> Evidence
Decision -> Decision
```

## Minimal Relationship File Shape

The recommended `v0.1.0` relationship file shape is:

```csv
Source_Key,Target_Key,Relationship,Notes
APP-UC-00003,APP-SR-00014,requires,Use case depends on requirement
APP-SR-00014,APP-VT-00221,verified_by,Requirement is verified by test
APP-VT-00221,APP-EVD-00098,evidenced_by,Test run has evidence record
APP-SR-00014,APP-ADR-00007,explained_by,Requirement design rationale
```

Recommended future columns include:

```text
Status,Rationale,Source_File,Source_Row,Owner,Last_Reviewed
```


## Inline Fields and Relationship Files

A record's inline relationship fields, such as `verified_by` or `explained_by`, MUST use the same verb names and directions as the relationship vocabulary below or a documented repository extension. Every relationship used in a record or relationship file MUST appear in this vocabulary or in a documented repository extension. Unknown verbs are diagnostics, not accepted truth.

## Draft Relationship Vocabulary

| Relationship | Typical Source | Typical Target | Meaning |
| --- | --- | --- | --- |
| `implements` | Work item | Capability, use case, or requirement | Work delivers or contributes to the target. |
| `realizes` | Capability | Use case | Capability is expressed through the use case. |
| `requires` | Use case | Requirement | Use case depends on the requirement. |
| `specified_by` | Requirement | Spec, change, or scenario provenance | Requirement is specified by reviewed source. |
| `verified_by` | Requirement | Verification test | Test verifies the requirement. |
| `validated_by` | Use case | Validation scenario | Scenario validates the use case or stakeholder need. |
| `evidenced_by` | Test, validation, artifact, or release claim | Evidence | Evidence supports the source claim. |
| `documents` | Artifact | Capability, use case, requirement, or decision | Artifact documents the target. |
| `explained_by` | Requirement, artifact, or work item | Decision | Decision explains rationale. |
| `supersedes` | Decision or artifact | Decision or artifact | Source replaces or supersedes target. |

The vocabulary is intentionally draft. Unknown relationships SHOULD be surfaced as diagnostics until a repo explicitly allows them.

## Relationship File Strategy

For early adoption, relationship-specific files are often easier to review than one large generic traceability file. Examples:

```text
docs/olts/links/capability-use-case-links.csv
docs/olts/links/use-case-requirement-links.csv
docs/olts/links/requirement-test-links.csv
docs/olts/links/test-evidence-links.csv
```

A single `relationships.csv` can work for small projects. Larger projects SHOULD prefer narrower files that match reviewer ownership and pipeline checks. The draft relationship schema in [../schemas/olts-relationship.schema.json](../schemas/olts-relationship.schema.json) validates parsed relationship rows rather than raw CSV text.

## OpenSpec Integration

OpenSpec MAY be used as change provenance. For example:

```text
TRK -> OpenSpec change -> scenario -> PR -> test -> evidence
```

OpenSpec IDs SHOULD NOT replace OLTS lifecycle IDs. OpenSpec answers what change is proposed and how it is accepted. OLTS answers which lifecycle entities are connected.

## Non-OpenSpec Integration

Teams that do not use OpenSpec MAY use GitHub Issues, GitLab Issues, Jira tickets, Azure Boards work items, ADRs, design documents, change request documents, release plans, and pull requests.

The requirement is not OpenSpec. The requirement is explicit provenance.

## Generated Artifacts

Generated diagrams, reports, dashboards, and RTMs SHOULD preserve their source relationships and metadata. They are derived views unless a repository explicitly accepts them as source truth through normal review.
