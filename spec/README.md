# OLTS Draft Specification

This directory holds the draft specification material for the Open Lifecycle Traceability Standard.

## Current Status

OLTS is an early draft being shaped before the stable public `v1.0.0` standard. The current repository focuses on:

- stable lifecycle identifiers;
- explicit lifecycle relationships;
- repo-native catalog and relationship files;
- provenance for generated artifacts;
- diagnostics for missing or malformed lifecycle data;
- staged conformance levels and draft claim language;
- draft machine-readable schema contracts.

## Draft Conformance Model

The provisional `L1` through `L5` levels now have draft claim language, diagnostics expectations, and validation guidance in [conformance.md](conformance.md).

## Core Terminology

Candidate `v1.0.0` entity types, identifier shape, source-of-truth boundaries, generated artifact semantics, and draft-only language scope are reviewed in [../docs/core-terminology.md](../docs/core-terminology.md).

## Normative Language

Normative keywords in OLTS specification files use the convention defined in [core.md](core.md#normative-language).

## Non-Goals

OLTS does not require:

- a specific console implementation;
- OpenSpec;
- a specific ALM platform;
- a specific database;
- a specific UI;
- a specific MBSE or architecture framework.

Product repositories remain the source of truth. Automation MAY propose changes, but humans MUST approve lifecycle truth through normal review.

## Draft Files

- [core.md](core.md) - initial OLTS Core principles, identifier shape, entity types, provenance, diagnostics, and conformance summary.
- [relationships.md](relationships.md) - initial explicit relationship model, relationship file shape, and OpenSpec/non-OpenSpec guidance.
- [conformance.md](conformance.md) - draft conformance levels, diagnostics expectations, validation guidance, and adopter claim language.
