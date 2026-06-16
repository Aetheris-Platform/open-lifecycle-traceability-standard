# Changelog

All notable changes to OLTS will be documented in this file.

OLTS is currently a private `v1.0.0` release candidate. See [docs/versioning.md](docs/versioning.md), [docs/v1-readiness.md](docs/v1-readiness.md), and [docs/v1-release-evidence.md](docs/v1-release-evidence.md) for the versioning, readiness, and launch approval plan.

## Unreleased

No post-`v1.0.0` changes yet.

## `v1.0.0` - Pending maintainer approval

This section records the intended first stable public OLTS standard. It is not a release announcement. Do not create a public tag, GitHub Release, or visibility change until maintainers explicitly approve the launch.

### Stable Scope

- Stable core terminology, entity types, identifier shape, source-of-truth boundaries, and generated-artifact posture.
- Stable relationship vocabulary and direction, including `documented_by` as the canonical stored lifecycle-to-artifact relationship.
- Stable `L1` through `L5` conformance levels with scoped adopter claim language, diagnostics guidance, and non-goals.
- Candidate v1 schema identifiers and validation guidance for records, relationship rows, diagnostics, conformance reports, and generated artifacts.
- Minimal and realistic examples suitable for public adopters.
- Governance, contribution, security, trademark, license, community, and public launch settings guidance.

### Migration Notes

- Pre-`v1.0.0` adopters should update stored artifact relationships from `documents` to `documented_by` when using core OLTS lifecycle-to-artifact traceability.
- Relationship files should use only core OLTS verbs or documented local extensions.
- Record `type` should match the type segment in `id`.
- Conformance claims should name scope, level, sources inspected, diagnostics posture, and reviewed exceptions.
- Generated diagrams, dashboards, reports, and indexes remain derived unless accepted through reviewed source truth.
- Public community processes should activate only after maintainers verify Issues, Discussions, branch protection, security settings, templates, and release approval evidence.

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
- Reviewed core entity types, identifier shape, source-of-truth boundaries, generated artifact semantics, and draft-only language scope for `v1.0.0` readiness.
- Hardened conformance claim language, diagnostic severity guidance, advisory/blocking pipeline posture, and vendor-neutral validation-path language for scoped adopter claims.
- Reviewed candidate schema contracts against the prose standard and documented semantic checks that remain outside portable JSON Schema.
- Validated the minimal and realistic examples with documented equivalent checks, including complete minimal records and relationship target resolution.
- Canonicalized lifecycle-to-artifact traceability on `documented_by`, with `documents` retained only as inverse display wording or local extension language.
- Hardened the AI-agent adoption prompt so copy/paste usage defaults to plan-only unless maintainers explicitly authorize edits.
- Reviewed governance and community readiness, including stewardship expectations, contribution flow, private-vs-public feedback channels, community files, and Apache-2.0 license posture.
- Added public launch settings guidance, including recommended repository description, topics, features, Discussion categories, branch protection, and security setting checks.
- Recorded public launch settings evidence for repository description, topics, Issues, branch protection, security settings, Wiki, Projects, and private/local scrub posture.
- Updated README maturity language to describe OLTS as a private `v1.0.0` release candidate pending explicit visibility, tag, and release approval.
- Updated public-facing maturity language across overview, spec, schema, governance, adoption, pipeline, and validation docs to reflect the private `v1.0.0` release-candidate posture.

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
