# OLTS Specification

This directory holds the `v1.0.0` specification material for the Open Lifecycle Traceability Standard.

## Current Status

OLTS `v1.0.0` focuses on:

- stable lifecycle identifiers;
- explicit lifecycle relationships;
- repo-native catalog and relationship files;
- provenance for generated artifacts;
- diagnostics for missing or malformed lifecycle data;
- staged conformance levels and scoped claim language;
- machine-readable schema contracts.

## Conformance Model

The `L1` through `L5` levels have scoped claim language, diagnostics expectations, and validation guidance in [conformance.md](conformance.md).

## Core Terminology

`v1.0.0` entity types, identifier shape, source-of-truth boundaries, and generated artifact semantics are reviewed in [../docs/core-terminology.md](../docs/core-terminology.md).

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

## Specification Files

- [core.md](core.md) - OLTS Core principles, identifier shape, entity types, provenance, diagnostics, and conformance summary.
- [relationships.md](relationships.md) - explicit relationship model, relationship file shape, and OpenSpec/non-OpenSpec guidance.
- [conformance.md](conformance.md) - conformance levels, diagnostics expectations, validation guidance, and adopter claim language.
