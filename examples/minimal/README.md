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
type: requirement
title: Operator can revoke an API token
supports:
  - APP-UC-00003
verified_by:
  - APP-VT-00221
evidence:
  - APP-EVD-00098
decisions:
  - APP-ADR-00007
```

## Relationship Chain

```text
APP-UC-00003 -> APP-SR-00014 -> APP-VT-00221 -> APP-EVD-00098
```

This is enough for a reviewer to inspect what the requirement supports, how it is verified, and which evidence proves the verification ran.
