# OLTS Extension Model

This guide describes how adopters can add local OLTS extensions without confusing repository-specific practice with core OLTS vocabulary.

Extensions are allowed so OLTS can fit real development pipelines, regulated domains, existing trackers, and domain-specific lifecycle models. They should remain explicit, reviewed, and clearly scoped.

## Extension Principles

1. Core OLTS vocabulary remains portable.
2. Local extensions are repository-specific unless accepted into the standard.
3. Extension meaning SHOULD be documented before validators rely on it.
4. Unknown values SHOULD produce diagnostics unless a reviewed extension allows them.
5. A local extension MUST NOT weaken source-of-truth, provenance, diagnostic, or human-approval expectations.

An adopter can make a draft conformance claim with local extensions, but the claim SHOULD identify which extensions were used and which scope they affect.

## What Can Be Extended

Adopters may define local extensions for:

- entity types, such as a domain-specific lifecycle entity beyond `CAP`, `TRK`, `UC`, `SR`, `VT`, `VAL`, `EVD`, `ART`, and `ADR`;
- relationship verbs, such as a domain-specific traceability edge;
- external reference namespaces, such as `jira:`, `ado:`, `issue:`, `reqif:`, or `openspec:`;
- diagnostic codes used by local review or CI checks;
- additional metadata fields on records, relationship rows, diagnostics, conformance reports, or generated artifact metadata.

Extensions SHOULD be documented in a reviewed path. A small repository might use `docs/olts/extensions.md`; a larger repository might keep separate files for entity types, relationship verbs, diagnostics, and validation policy.

## Required Extension Documentation

Each extension SHOULD document:

- name;
- kind, such as entity type, relationship verb, external reference namespace, diagnostic code, or metadata field;
- meaning;
- allowed values or shape when practical;
- source and target expectations for relationship verbs;
- whether the extension is local-only or proposed for OLTS standardization;
- which records, relationship files, reports, or generated artifacts may use it;
- any validation rule or diagnostic that should apply.

Relationship extensions SHOULD also document direction. For example, if `mitigates` is defined locally, the extension should say whether the source is a requirement, control, test, risk, or other entity, and what target type it expects.

## Records

The candidate record schema allows local metadata through normal object fields and the `extensions` object.

Record extensions may add:

- local entity type codes;
- local status fields;
- ownership, domain, release, control, safety, security, or compliance metadata;
- local inline relationship fields that are documented as relationship extensions.

Record extensions MUST preserve the core record shape. A lifecycle record still needs `id`, `type`, and `title` when it is presented as an OLTS record. The `type` value MUST match the type segment in `id`, including documented local entity types.

Local inline relationship fields SHOULD use the same verb name and direction as the documented relationship extension. Unknown inline relationship fields SHOULD be surfaced as diagnostics unless they are documented metadata fields rather than relationship fields.

## Relationship Rows

The core relationship-row schema accepts the draft OLTS relationship vocabulary. Local relationship verbs SHOULD be handled through a documented schema overlay, validator configuration, or reviewed exception.

A relationship extension SHOULD define:

- relationship verb;
- source type or allowed source types;
- target type, external reference namespace, or allowed target types;
- direction;
- meaning;
- whether it contributes to an `L2`, `L3`, `L4`, or `L5` scoped claim;
- diagnostic behavior when source, target, or direction is invalid.

Unknown relationship verbs SHOULD be diagnostics unless the repository has explicitly allowed them through a reviewed extension. A validator SHOULD NOT silently treat an unknown relationship as core OLTS truth.

## Diagnostics

Local diagnostic codes are allowed when a repository has checks that are more specific than the core diagnostic categories.

Diagnostic extensions SHOULD define:

- diagnostic code;
- severity guidance;
- subject type, if applicable;
- whether the diagnostic is advisory or can become blocking;
- remediation guidance when practical.

Local diagnostic codes SHOULD NOT hide core OLTS failures. For example, a local `release_gate_missing` diagnostic can add more context, but it SHOULD NOT replace an `invalid_identifier`, `unknown_relationship_type`, or missing-evidence diagnostic when that core issue is present.

## Conformance Reports

Conformance-report extensions can record local check configuration, policy decisions, exception categories, external tool metadata, or organization-specific summaries.

Report extensions SHOULD NOT broaden the claim beyond the stated scope. If a report validates only selected paths, entity types, release lines, or repositories, its `scope` and `sources` should say so even when local report fields add more detail.

A report that depends on local extensions SHOULD list those extensions or link to the reviewed extension documentation.

## Generated Artifacts

Generated artifact metadata extensions can describe local diagram types, report formats, dashboard configuration, review packets, export formats, or omitted-fact categories.

Generated artifact extensions MUST preserve provenance. A generated diagram, dashboard, report, traceability matrix, or index remains derived unless the repository accepts it as source truth through normal review.

Generated artifact metadata SHOULD identify:

- source records and relationship rows used;
- source files, commits, timestamps, or hashes when practical;
- omitted facts and reasons when the artifact is partial;
- diagnostics that affected the generated artifact.

## Schema Overlays

The candidate OLTS schemas are intentionally small. A repository that needs stricter or broader validation can layer a local schema overlay on top of them.

A local overlay may:

- restrict allowed local entity types;
- add required local metadata fields;
- allow documented local relationship verbs;
- add diagnostic codes;
- require report or artifact metadata used by the repository.

A local overlay SHOULD NOT change the meaning of core OLTS fields. If an overlay accepts a local relationship verb, the repository SHOULD still distinguish that verb from the core OLTS vocabulary in documentation and conformance claims.

## Validation Behavior

Validators SHOULD distinguish:

- accepted core OLTS vocabulary;
- documented local extensions;
- unknown values;
- malformed values;
- reviewed exceptions.

Unknown values SHOULD produce diagnostics unless a documented extension or reviewed exception applies. Missing files, parser failures, inaccessible sources, and disabled data sources MUST NOT be treated as healthy zero-result scans.

## Proposing Extensions for Standardization

An adopter may propose a local extension for future OLTS standardization. A useful proposal SHOULD explain:

- the lifecycle problem the extension solves;
- why existing core vocabulary is insufficient;
- examples from real reviewed usage;
- expected source and target semantics for relationship verbs;
- validation and diagnostic expectations;
- migration impact if the extension is accepted, renamed, or rejected.

Until an extension is accepted into OLTS, it remains local extension vocabulary.
