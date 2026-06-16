# OLTS Draft Specification

This directory will hold the public draft specification for the Open Lifecycle Traceability Standard.

## Current Status

OLTS is an early open draft. The initial repository focuses on:

- stable lifecycle identifiers;
- explicit lifecycle relationships;
- repo-native catalog and relationship files;
- provenance for generated artifacts;
- diagnostics for missing or malformed lifecycle data;
- staged conformance levels.

## Draft Conformance Levels

| Level | Meaning |
| --- | --- |
| L1: Stable IDs | Lifecycle entities have durable identifiers. |
| L2: Explicit Relationships | Key relationships are recorded in reviewable files. |
| L3: Verification Coverage | Requirements and use cases link to tests or validation scenarios. |
| L4: Evidence Coverage | Tests, validation scenarios, and release claims link to evidence. |
| L5: Automated Conformance | CI checks validate identifiers, links, provenance, and diagnostics. |

## Non-Goals

OLTS does not require:

- a specific console implementation;
- OpenSpec;
- a specific ALM platform;
- a specific database;
- a specific UI;
- a specific MBSE or architecture framework.

Product repositories remain the source of truth. Automation may propose changes, but humans approve lifecycle truth through normal review.

## Draft Files

- [core.md](core.md) - initial OLTS Core principles, identifier shape, entity types, provenance, diagnostics, and conformance levels.
- [relationships.md](relationships.md) - initial explicit relationship model, relationship file shape, and OpenSpec/non-OpenSpec guidance.
