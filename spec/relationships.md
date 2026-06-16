# OLTS Relationship Model

This file captures the OLTS relationship model for `v1.0.0`.

Normative keywords in this file use the convention defined in [core.md](core.md#normative-language).

## Relationship Principle

A lifecycle relationship is a reviewed statement that one lifecycle entity depends on another, is specified by provenance, is verified by a test, is validated by a scenario, is documented by an artifact, is explained by a decision, or is evidenced by a reviewable source.

Relationships SHOULD be explicit. OLTS-compatible tooling MUST NOT infer canonical relationships from text similarity, filename similarity, row order, heading names, generated diagrams, or AI guesses.

## Relationship Chain

A common traceability chain is:

```text
Capability --realizes--> Use Case --requires--> System Requirement --verified_by--> Verification Test --evidenced_by--> Evidence
```

Validation uses a parallel path:

```text
Use Case --validated_by--> Validation Scenario --evidenced_by--> Evidence
```

Other useful links include:

```text
Work Item --implements--> Capability, Use Case, or Requirement
Requirement --explained_by--> Decision
Capability, Use Case, Requirement, or Decision --documented_by--> Artifact
Artifact --evidenced_by--> Evidence
Decision --supersedes--> Decision
```

## Minimal Relationship File Shape

The recommended relationship file shape is:

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

## Relationship Vocabulary

| Relationship | Typical Source | Typical Target | Meaning |
| --- | --- | --- | --- |
| `implements` | Work item | Capability, use case, or requirement | Work delivers or contributes to the target. |
| `realizes` | Capability | Use case | Capability is expressed through the use case. |
| `requires` | Use case | Requirement | Use case depends on the requirement. |
| `specified_by` | Requirement | Spec, change, or scenario provenance | Requirement is specified by reviewed source. |
| `verified_by` | Requirement | Verification test | Test verifies the requirement. |
| `validated_by` | Use case | Validation scenario | Scenario validates the use case or stakeholder need. |
| `evidenced_by` | Test, validation, artifact, or release claim | Evidence | Evidence supports the source claim. |
| `documented_by` | Capability, use case, requirement, or decision | Artifact | Source lifecycle entity is documented by the artifact. |
| `explained_by` | Requirement, artifact, or work item | Decision | Decision explains rationale. |
| `supersedes` | Decision or artifact | Decision or artifact | Source replaces or supersedes target. |

The vocabulary is directed. Relationship names are not inverse aliases. For example, `requires` is written from use case to requirement; OLTS core does not define an inverse `supports` relationship from requirement to use case.

For lifecycle-to-artifact traceability, canonical stored relationship rows use `documented_by` from the lifecycle entity to the artifact. Artifact-centric tools MAY render the inverse display wording, such as "Artifact documents Requirement," but `documents` is not the canonical core stored relationship. Repositories that need inverse or domain-specific relationships MAY define them as local extensions, but they MUST document those extensions and keep them separate from core OLTS vocabulary.

Unknown relationships SHOULD be surfaced as diagnostics until a repo explicitly allows them.

See [../docs/relationship-semantics.md](../docs/relationship-semantics.md) for the `v1.0.0` relationship semantics review.

## Relationship Extensions

Repositories MAY define local relationship verbs. Local verbs MUST be documented before they are used in a conformance claim, and they MUST NOT be presented as core OLTS vocabulary unless accepted into the standard.

A relationship extension SHOULD define its source type, target type or external reference namespace, direction, meaning, and diagnostic behavior. Unknown relationship verbs SHOULD be surfaced as diagnostics unless a documented local extension or reviewed exception applies.

See [../docs/extensions.md](../docs/extensions.md) for the broader extension model.

## Relationship File Strategy

For early adoption, relationship-specific files are often easier to review than one large generic traceability file. Examples:

```text
docs/olts/links/capability-use-case-links.csv
docs/olts/links/use-case-requirement-links.csv
docs/olts/links/requirement-test-links.csv
docs/olts/links/test-evidence-links.csv
```

A single `relationships.csv` can work for small projects. Larger projects SHOULD prefer narrower files that match reviewer ownership and pipeline checks. The relationship schema in [../schemas/olts-relationship.schema.json](../schemas/olts-relationship.schema.json) validates parsed relationship rows rather than raw CSV text.

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
