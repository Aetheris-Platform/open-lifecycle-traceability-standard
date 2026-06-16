# OLTS Schema Contract Review

This review records the candidate `v1.0.0` schema contracts against the prose standard.

It is launch-readiness evidence, not a release announcement. OLTS remains in the `v0.x` draft series until maintainers explicitly approve `v1.0.0`.

## Review Scope

Reviewed schema files:

- [../schemas/olts-record.schema.json](../schemas/olts-record.schema.json)
- [../schemas/olts-relationship.schema.json](../schemas/olts-relationship.schema.json)
- [../schemas/olts-diagnostic.schema.json](../schemas/olts-diagnostic.schema.json)
- [../schemas/olts-conformance-report.schema.json](../schemas/olts-conformance-report.schema.json)
- [../schemas/olts-generated-artifact.schema.json](../schemas/olts-generated-artifact.schema.json)

Reviewed prose sources:

- [../spec/core.md](../spec/core.md)
- [../spec/relationships.md](../spec/relationships.md)
- [../spec/conformance.md](../spec/conformance.md)
- [core-terminology.md](core-terminology.md)
- [relationship-semantics.md](relationship-semantics.md)
- [extensions.md](extensions.md)
- [schema-validation.md](schema-validation.md)

## Review Findings

The candidate schema files match the prose standard at the level portable JSON Schema is intended to express.

| Schema | Prose alignment |
| --- | --- |
| `olts-record.schema.json` | Requires `id`, `type`, and `title`; uses the shared OLTS ID shape; allows core and documented local entity types; exposes the core inline relationship fields; preserves extension room with `additionalProperties` and `extensions`. |
| `olts-relationship.schema.json` | Requires `Source_Key`, `Target_Key`, and `Relationship`; validates parsed CSV row shape; accepts OLTS IDs as sources and OLTS IDs or external references as targets; enumerates the same 10 core relationship verbs documented in the relationship prose. |
| `olts-diagnostic.schema.json` | Requires `code`, `severity`, and `message`; limits severity to `info`, `warning`, `error`, and `blocked`; allows source location, expected/actual values, remediation, and extension metadata. |
| `olts-conformance-report.schema.json` | Requires claimed level, scope, generation time, advisory posture, and diagnostics; allows source lists, summaries, reviewed exceptions, tool metadata, and extension metadata. |
| `olts-generated-artifact.schema.json` | Requires artifact identity, artifact type, generation time, generator metadata, and at least one source; supports included relationships, omitted facts, diagnostics, and the derived-by-default rule. |

## Vocabulary Consistency

The relationship schema enum matches the core relationship vocabulary:

```text
implements, realizes, requires, specified_by, verified_by, validated_by, evidenced_by, documents, explained_by, supersedes
```

The record schema describes the same candidate entity types documented in the core terminology review:

```text
CAP, TRK, UC, SR, VT, VAL, EVD, ART, ADR
```

Other entity type values remain local extensions and should be documented by the adopting repository.

## Semantic Checks Outside Portable JSON Schema

Several OLTS expectations are intentionally semantic and remain outside portable JSON Schema validation:

- `record.type` MUST match the `<TYPE>` segment in `record.id`.
- Lifecycle IDs MUST NOT be reused for different entities in the checked scope.
- Relationship direction SHOULD match the core vocabulary or documented local extension.
- Relationship targets SHOULD resolve to known records unless they are documented external references.
- Inline relationship fields SHOULD align with relationship-file rows when both are present.
- Missing files, parser failures, inaccessible sources, and disabled data sources MUST NOT be treated as healthy zero-result scans.
- Generated artifacts remain derived unless accepted through a reviewed source-truth process.

These checks are documented in [schema-validation.md](schema-validation.md) and should be implemented by manual review, local scripts, CI jobs, external validators, or platform-native checks when they are used as conformance evidence.

## Extension Behavior

The schemas intentionally use `additionalProperties: true` and optional `extensions` objects so adopters can carry local metadata without forking the core contracts.

That flexibility does not make local vocabulary core OLTS vocabulary. Local entity types, relationship verbs, diagnostic codes, report fields, and artifact metadata should be documented as extensions and identified in scoped conformance claims when they are needed to understand the claim.

## Stability Decision

No schema behavior changes are required by this review.

The candidate schema contracts are aligned with the prose standard for `v1.0.0` readiness, subject to the documented semantic checks and extension guidance above. Future changes to required fields, schema identifiers, relationship vocabulary, diagnostic severity values, report posture fields, or generated-artifact provenance expectations should be treated as compatibility-impacting v1 readiness decisions.
