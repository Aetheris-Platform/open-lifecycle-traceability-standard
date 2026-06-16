# Changelog

All notable changes to OLTS will be documented in this file.

OLTS is currently in the `v0.x` draft series. See [docs/versioning.md](docs/versioning.md) for the versioning and readiness plan.

## Unreleased

### Added

- Draft `v0.2.0` conformance model with level expectations, diagnostics guidance, validation reporting, extension guidance, and adopter claim language.
- Draft `v0.3.0` schema contracts for lifecycle records, relationship rows, diagnostics, conformance reports, and generated artifact metadata.
- `v1.0.0` readiness plan with stable-standard gates, launch settings, release evidence, and explicit approval requirements.
- Realistic multi-entity example covering capability, work item, use case, requirement, validation, verification, evidence, decision, and artifact records.
- Draft normative keyword convention for OLTS spec files, using RFC 2119 and RFC 8174 uppercase terms.
- Tool-agnostic schema validation path for records, CSV relationship rows, semantic checks, diagnostics, and example validation.
- Local extension model for records, relationship rows, diagnostics, conformance reports, generated artifacts, and schema overlays.

### Changed

- Linked README, overview, adoption, pipeline, and core spec guidance to the draft conformance model.
- Linked README, overview, and v1 readiness guidance to the realistic example.
- Updated schema guidance to describe draft machine-readable contracts and CSV relationship row validation.
- Clarified draft maturity language so pre-`v1.0.0` work does not imply a public stable release.
- Clarified that public community processes activate at `v1.0.0`, while `v0.x` feedback may use private or invited channels.
- Added `v1.0.0` gates for normative keywords, stable schema identifiers, record ID/type consistency, approval evidence, and license posture.
- Applied normative keywords consistently across the core, relationship, and conformance draft specs.
- Hardened `L1` through `L5` conformance criteria with scoped claim requirements, explicit criteria, diagnostics guidance, and adopter-facing scope language.
- Promoted schema `$id` values and cross-schema references to candidate stable v1 URNs, and documented the record `type` versus ID type-segment semantic check.
- Reviewed relationship vocabulary direction, naming, overlap, and canonical-chain consistency across spec, README, overview, examples, and schema guidance.

## `v0.1.0` - 2026-06-16

Initial draft of OLTS.

### Added

- Initial README and overview draft.
- Minimal OLTS example record and relationship file.
- Draft repository structure for `spec/`, `schemas/`, `tools/`, `examples/`, and `docs/`.
- Contribution, notice, trademark, and ignore-file scaffolding.
- Versioning and readiness plan.
- Draft core and relationship specification files.
- Adoption guide, pipeline integration guide, AI-agent adoption prompt, and governance guide.
- Security policy, code of conduct, pull request template, and issue templates.

## Planned Releases

### `v0.2.0` - Conformance draft

Expected scope:

- formalized conformance levels introduced provisionally in `v0.1.0`;
- diagnostics guidance;
- validation expectations;
- adopter claim language such as `OLTS L1` or `OLTS L2`.

### `v0.3.0` - Schemas draft

Expected scope:

- machine-readable schemas for core records;
- relationship file schemas;
- generated artifact metadata schemas;
- diagnostic and conformance report schemas.

### `v1.0.0` - First stable public standard

Expected scope:

- stable core terminology;
- stable conformance levels;
- stable compatibility expectations;
- public governance flow;
- reference examples suitable for broad adoption.
