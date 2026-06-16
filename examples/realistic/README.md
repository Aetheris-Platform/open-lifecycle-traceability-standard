# Realistic OLTS Example

This example shows a small but realistic OLTS traceability set for a generic application feature. It is still compact enough to review in one pull request, but it exercises the main draft entities, relationship directions, evidence coverage, and provenance expectations.

The example targets draft `OLTS L4` for this scoped feature:

- `L1`: records have durable OLTS identifiers;
- `L2`: relationships are explicit and reviewable;
- `L3`: the use case and requirement have validation or verification coverage;
- `L4`: the validation scenario and verification test link to evidence.

It does not claim `L5` because no automated conformance checker is included here.

## Scenario

The product team is adding passwordless sign-in. Reviewers need to see:

- which capability the work belongs to;
- which tracker item delivers the work;
- which user scenario is in scope;
- which system requirement captures the behavior;
- how the scenario and requirement are checked;
- what evidence proves the checks ran;
- which decision and design artifact explain the approach.

## Files

| File | Purpose |
| --- | --- |
| [records.yaml](records.yaml) | Reviewable lifecycle records for the scoped feature. |
| [relationships.csv](relationships.csv) | Canonical OLTS relationships between the records. |

The `openspec:` reference in this example is only one possible external-reference namespace. A team could use `jira:`, `issue:`, `adr:`, or another reviewed provenance source instead.

## Relationship Chain

```text
APP-TRK-00042 --implements--> APP-CAP-00002
APP-CAP-00002 --realizes--> APP-UC-00011
APP-UC-00011 --requires--> APP-SR-00027
APP-UC-00011 --validated_by--> APP-VAL-00006 --evidenced_by--> APP-EVD-00034
APP-SR-00027 --verified_by--> APP-VT-00019 --evidenced_by--> APP-EVD-00033
APP-SR-00027 --explained_by--> APP-ADR-00004
APP-ART-00008 --documents--> APP-SR-00027
APP-ART-00008 --evidenced_by--> APP-EVD-00035
```

These directions match the draft vocabulary in [../../spec/relationships.md](../../spec/relationships.md) and the relationship semantics review in [../../docs/relationship-semantics.md](../../docs/relationship-semantics.md).

In a real repository, records and relationships like these become source truth only when accepted through normal review. Generated diagrams, dashboards, RTMs, reports, or indexes built from them remain derived unless the repository explicitly accepts a generated artifact as source truth.

## Draft Conformance Notes

This example is intended to be read as a scoped draft adoption statement:

```text
The examples/realistic/ folder demonstrates OLTS L4 draft traceability for one passwordless sign-in feature slice.
```

Known limits:

- the example is not a full product traceability matrix;
- relationship rows are plain CSV and require a parser before JSON Schema validation;
- no automated `L5` validation report is produced;
- evidence records point to example paths, not real audit artifacts.

## Review Checklist

When reviewing this example, check that:

- each `id` follows `<DOMAIN>-<TYPE>-<NNNNN>`;
- each record `type` matches the type segment in its `id`;
- each relationship verb is defined in [../../spec/relationships.md](../../spec/relationships.md);
- each relationship direction matches the draft vocabulary;
- every referenced OLTS ID is present in [records.yaml](records.yaml);
- evidence attaches to validation, verification, or artifact records instead of being used as unexplained direct proof for a requirement.
