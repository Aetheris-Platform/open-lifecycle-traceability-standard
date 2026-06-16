# Minimal OLTS Example

This example shows the smallest useful shape of OLTS-style lifecycle traceability.

It includes:

- one use case;
- one requirement;
- one verification test;
- one evidence record;
- one decision record;
- explicit relationships between them.

## Files

| File | Purpose |
| --- | --- |
| [records.yaml](records.yaml) | Minimal lifecycle records for the example chain. |
| [relationships.csv](relationships.csv) | Canonical OLTS relationships between the records. |

## Relationship Chain

```text
APP-UC-00003 --requires--> APP-SR-00014 --verified_by--> APP-VT-00221 --evidenced_by--> APP-EVD-00098
APP-SR-00014 --explained_by--> APP-ADR-00007
```

This is enough for a reviewer to inspect which use case requires the requirement, how the requirement is verified, which evidence proves the verification ran, and which decision explains the rationale.

The relationship direction matches the draft vocabulary in [../../spec/relationships.md](../../spec/relationships.md).

The documented equivalent validation checks for this example are recorded in [../../docs/example-validation-review.md](../../docs/example-validation-review.md).

In a real repository, these records and relationships become source truth only when accepted through normal review. Generated views built from them remain derived unless the repository explicitly accepts a generated artifact as source truth.
