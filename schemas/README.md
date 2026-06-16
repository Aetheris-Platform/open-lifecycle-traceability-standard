# OLTS Schemas Draft

This directory contains draft machine-readable schemas for OLTS `v0.3.0` planning. They are reviewable contracts for early adopters and tooling authors, not stable `v1.0.0` compatibility guarantees.

## Schema Files

| File | Purpose |
| --- | --- |
| [olts-record.schema.json](olts-record.schema.json) | Validates one lifecycle record with a stable ID, entity type, title, optional provenance, and inline relationship fields. |
| [olts-relationship.schema.json](olts-relationship.schema.json) | Validates one parsed relationship row using the draft relationship vocabulary. |
| [olts-diagnostic.schema.json](olts-diagnostic.schema.json) | Validates one diagnostic emitted by review, local scripts, CI, or future reference tooling. |
| [olts-conformance-report.schema.json](olts-conformance-report.schema.json) | Validates one conformance report for a stated level and scope. |
| [olts-generated-artifact.schema.json](olts-generated-artifact.schema.json) | Validates metadata for generated diagrams, dashboards, RTMs, reports, indexes, or review packets. |

## Draft Scope

The schemas intentionally stay small and readable. They cover the shared shape of OLTS facts while leaving room for repository-specific extensions during the `v0.x` draft period.

They are designed around the current draft specs:

- [../spec/core.md](../spec/core.md)
- [../spec/relationships.md](../spec/relationships.md)
- [../spec/conformance.md](../spec/conformance.md)

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

## Extension Guidance

Local extensions are allowed during the draft period, but they should be documented. A repository that adds local entity types, relationship verbs, diagnostic codes, or metadata fields should state whether those extensions are local-only or proposed for future OLTS standardization.

The core relationship schema accepts only the draft OLTS relationship vocabulary. Repositories that intentionally use local relationship verbs should layer their own schema overlay on top of the draft schema rather than presenting local verbs as core OLTS vocabulary.

## Stability

These schemas are draft contracts. They may change before `v1.0.0` as the conformance model, examples, and adopter feedback mature.
