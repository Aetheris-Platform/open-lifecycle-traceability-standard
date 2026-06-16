# OLTS Relationship Semantics Review

This review records the candidate `v1.0.0` relationship direction, naming, overlap, and canonical-chain decisions.

It is launch-readiness evidence, not a release announcement. OLTS remains in the `v0.x` draft series until maintainers explicitly approve `v1.0.0`.

## Direction Rule

OLTS relationship rows use a directed source-to-target shape:

```text
Source_Key --Relationship--> Target_Key
```

Inline relationship fields use the same verb names and directions as relationship rows. For example:

```yaml
id: APP-SR-00014
type: SR
verified_by:
  - APP-VT-00221
```

has the same direction as:

```csv
APP-SR-00014,APP-VT-00221,verified_by
```

Relationship names are not inverse aliases. A repository SHOULD NOT use `supports` as an inverse of `requires` unless it defines `supports` as a local extension.

## Canonical Chain

The canonical chain uses these draft core verbs:

```text
Capability --realizes--> Use Case --requires--> System Requirement --verified_by--> Verification Test --evidenced_by--> Evidence
```

Validation uses the parallel `validated_by` path:

```text
Use Case --validated_by--> Validation Scenario --evidenced_by--> Evidence
```

Implementation, rationale, and artifact links are adjacent paths:

```text
Work Item --implements--> Capability, Use Case, or Requirement
Requirement --explained_by--> Decision
Capability, Use Case, Requirement, or Decision --documented_by--> Artifact
Artifact --evidenced_by--> Evidence
Decision --supersedes--> Decision
```

## Vocabulary Review

The current draft vocabulary intentionally separates these concerns:

| Relationship | Direction | Distinct meaning |
| --- | --- | --- |
| `implements` | Work item -> lifecycle entity | Work delivers or contributes to the target. |
| `realizes` | Capability -> use case | Capability is expressed through a user or stakeholder scenario. |
| `requires` | Use case -> requirement | Scenario depends on a requirement. |
| `specified_by` | Requirement -> provenance | Requirement is specified by reviewed source. |
| `verified_by` | Requirement -> verification test | Requirement has a test that checks system behavior. |
| `validated_by` | Use case -> validation scenario | Stakeholder or user need has a validation scenario. |
| `evidenced_by` | Test, validation, artifact, or release claim -> evidence | Source claim has evidence. |
| `documented_by` | lifecycle entity -> artifact | Source lifecycle entity is documented by the artifact. |
| `explained_by` | Requirement, artifact, or work item -> decision | Decision explains rationale. |
| `supersedes` | Decision or artifact -> decision or artifact | Source replaces or supersedes target. |

No two core verbs are intended to be synonyms. Repositories MAY define local relationship extensions, but local verbs MUST remain separate from core OLTS vocabulary unless accepted into the standard.

## Artifact Display Guidance

Canonical stored rows for lifecycle-to-artifact traceability use `documented_by`:

```text
System Requirement --documented_by--> Artifact
```

Artifact-centric views MAY render the inverse display wording, such as "Artifact documents System Requirement," as long as the stored relationship direction remains explicit and reviewable. `documents` is inverse display wording or local extension language, not the canonical core stored relationship.

## Cross-Artifact Consistency

The canonical chain is aligned across the current draft materials:

| Surface | Consistency evidence |
| --- | --- |
| [../spec/relationships.md](../spec/relationships.md) | Defines verb direction and the canonical chain. |
| [../README.md](../README.md) | Describes the minimal example and links use case -> requirement -> test -> evidence. |
| [overview.md](overview.md) | Uses the canonical verb chain in the lifecycle-chain section. |
| [../examples/minimal/relationships.csv](../examples/minimal/relationships.csv) | Uses `requires`, `verified_by`, `evidenced_by`, and `explained_by` in the same direction as the spec. |
| [../examples/realistic/relationships.csv](../examples/realistic/relationships.csv) | Exercises the broader chain with `implements`, `realizes`, `requires`, `specified_by`, `validated_by`, `verified_by`, `evidenced_by`, `documented_by`, and `explained_by`. |
| [../schemas/olts-relationship.schema.json](../schemas/olts-relationship.schema.json) | Enumerates the same core relationship verbs used by the spec and examples. |

## Diagnostics

Validators and reviewers SHOULD diagnose:

- unknown relationship verbs that are not documented local extensions;
- relationship directions that do not match the core vocabulary or documented local extension;
- unresolved OLTS targets that are not documented external references;
- inline relationship fields that use a different direction than relationship rows.

These diagnostics protect relationship meaning without requiring any one validator implementation.
