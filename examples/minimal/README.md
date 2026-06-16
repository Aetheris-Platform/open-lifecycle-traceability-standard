# Minimal OLTS Example

This example shows the smallest useful shape of OLTS-style lifecycle traceability.

It includes:

- one use case;
- one requirement;
- one verification test;
- one evidence record;
- explicit relationships between them.

## Requirement Record

```yaml
id: APP-SR-00014
type: SR
title: Operator can revoke an API token
verified_by:
  - APP-VT-00221
explained_by:
  - APP-ADR-00007
```

## Relationship Chain

```text
APP-UC-00003 --requires--> APP-SR-00014 --verified_by--> APP-VT-00221 --evidenced_by--> APP-EVD-00098
```

This is enough for a reviewer to inspect which use case requires the requirement, how the requirement is verified, and which evidence proves the verification ran.

The relationship direction matches the draft vocabulary in [../../spec/relationships.md](../../spec/relationships.md).
