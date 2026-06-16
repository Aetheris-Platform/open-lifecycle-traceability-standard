# OLTS v1.0.0 Readiness Plan

This plan defines what should be true before OLTS becomes the first stable public standard. It is a launch-readiness checklist, not a release announcement.

OLTS should remain draft material until maintainers explicitly decide that the `v1.0.0` gates below are satisfied.

## Release Principle

`v1.0.0` should mean that adopters can rely on OLTS terminology, relationship semantics, conformance levels, schemas, and governance expectations without guessing which parts are experimental.

Before `v1.0.0`, draft milestones such as `v0.2.0` and `v0.3.0` may organize private or pre-release work. They do not automatically create a public release, public tag, certification program, or compatibility guarantee.

Public community processes such as Discussions, external issues, outside pull requests, and public adopter trials should activate at the `v1.0.0` public launch. During `v0.x`, feedback should be gathered through private or invited channels unless maintainers explicitly approve an earlier public draft.

## Stable Standard Gates

### 1. Core Terminology

Before `v1.0.0`:

- [ ] Core entity types are reviewed and intentionally accepted, renamed, or deferred.
- [ ] Identifier shape is stable enough for adopters to assign durable IDs.
- [ ] Source-of-truth boundaries are stated consistently across README, docs, spec, examples, and schemas.
- [ ] Generated artifacts are clearly described as derived unless accepted through reviewed source truth.
- [ ] Draft-only language is removed or scoped to future experimental material.
- [x] Normative keyword conventions, such as RFC 2119/8174 `MUST`, `SHOULD`, and `MAY`, are defined and applied consistently across `spec/`.

Evidence to review:

- [../spec/core.md](../spec/core.md)
- [../spec/README.md](../spec/README.md)
- [../spec/relationships.md](../spec/relationships.md)
- [../spec/conformance.md](../spec/conformance.md)
- [../README.md](../README.md)
- [overview.md](overview.md)

### 2. Relationship Semantics

Before `v1.0.0`:

- [ ] Relationship vocabulary is reviewed for direction, naming, and overlap.
- [ ] The canonical lifecycle chain is internally consistent across spec, README, examples, and schemas.
- [ ] Local extension guidance is clear enough that adopters do not confuse local verbs with core OLTS verbs.
- [ ] Unknown relationships are consistently described as diagnostics unless explicitly allowed by a repository extension.

Evidence to review:

- [../spec/relationships.md](../spec/relationships.md)
- [../examples/minimal/README.md](../examples/minimal/README.md)
- [../schemas/olts-relationship.schema.json](../schemas/olts-relationship.schema.json)

### 3. Conformance Model

Before `v1.0.0`:

- [ ] `L1` through `L5` are stable enough for scoped adopter claims.
- [ ] Each level has clear expectations, diagnostics, and non-goals.
- [ ] Claim language avoids overstatement and does not imply certification unless a certification policy exists.
- [ ] Diagnostic severity guidance is consistent with pipeline and governance docs.
- [ ] Manual, scripted, CI, and external-tool validation paths are all allowed without requiring a vendor platform.

Evidence to review:

- [../spec/conformance.md](../spec/conformance.md)
- [adoption-guide.md](adoption-guide.md)
- [pipeline-integration.md](pipeline-integration.md)

### 4. Schema Contracts

Before `v1.0.0`:

- [ ] Draft schema files are reviewed against the prose standard.
- [ ] Schema identifiers and cross-schema references are stable and vendor-neutral.
- [ ] Draft schema `$id` URNs are promoted to stable, versioned identifiers and all cross-references are updated together.
- [ ] The record `type` field and the type segment in `id` are either checked for consistency or explicitly documented as intentionally decoupled.
- [ ] CSV relationship-row validation guidance is clear.
- [ ] Local extension behavior is documented for records, relationships, diagnostics, conformance reports, and generated artifacts.
- [ ] At least one validator path is documented or tested without making one implementation mandatory.

Evidence to review:

- [../schemas/README.md](../schemas/README.md)
- [../schemas/olts-record.schema.json](../schemas/olts-record.schema.json)
- [../schemas/olts-relationship.schema.json](../schemas/olts-relationship.schema.json)
- [../schemas/olts-diagnostic.schema.json](../schemas/olts-diagnostic.schema.json)
- [../schemas/olts-conformance-report.schema.json](../schemas/olts-conformance-report.schema.json)
- [../schemas/olts-generated-artifact.schema.json](../schemas/olts-generated-artifact.schema.json)

### 5. Examples and Adopter Guidance

Before `v1.0.0`:

- [ ] Minimal example validates against the stable schema contracts or documented equivalent checks.
- [x] A realistic multi-entity example exists for adopters who need more than the minimal chain.
- [ ] Adoption guide explains a first `L1` or `L2` slice without requiring a full migration.
- [ ] AI-agent adoption prompt preserves source truth and defaults to plan-only unless edits are explicitly authorized.
- [ ] Pipeline guide explains advisory checks, blocking gates, and evidence expectations without promising unavailable tooling.

Evidence to review:

- [../examples/minimal/README.md](../examples/minimal/README.md)
- [../examples/realistic/README.md](../examples/realistic/README.md)
- [adoption-guide.md](adoption-guide.md)
- [pipeline-integration.md](pipeline-integration.md)
- [ai-agent-adoption-prompt.md](ai-agent-adoption-prompt.md)

### 6. Governance and Community Health

Before `v1.0.0`:

- [ ] Maintainer/steward expectations are clear.
- [ ] Contribution flow is clear enough for outside comments, issues, and pull requests once the repository is public.
- [ ] Private or invited `v0.x` feedback channels are documented separately from public `v1.0.0` community processes.
- [ ] Code of Conduct, security policy, trademark guidance, notice, license, issue templates, and PR template are reviewed.
- [ ] License posture for specification text and tooling is explicitly confirmed before stable publication.
- [ ] Discussion categories and repository settings support public feedback.
- [ ] Branch protection and review requirements are configured before public launch.

Evidence to review:

- [governance.md](governance.md)
- [../CONTRIBUTING.md](../CONTRIBUTING.md)
- [../MAINTAINERS.md](../MAINTAINERS.md)
- [../SECURITY.md](../SECURITY.md)
- [../TRADEMARKS.md](../TRADEMARKS.md)

### 7. Public Launch Settings

Before making the repository public:

- [ ] Repository description and topics are reviewed.
- [ ] Issues are enabled.
- [ ] Discussions are enabled and categories are configured.
- [ ] Main branch protection requires pull requests and review.
- [ ] Required conversation resolution is enabled.
- [ ] Force pushes and branch deletion are blocked for protected branches.
- [ ] Security alerts, secret scanning, and vulnerability reporting settings are reviewed where available.
- [ ] Wiki/projects settings match the intended governance model.
- [ ] No local paths, private product names, secrets, credentials, or internal-only assumptions are present in tracked files.

Manual settings should be checked in GitHub before visibility changes:

```text
Repo -> Settings -> General
Repo -> Settings -> Branches
Repo -> Settings -> Rules -> Rulesets
Repo -> Settings -> Code security and analysis
Repo -> Discussions -> Manage discussion categories
```

### 8. Release Evidence

Before tagging `v1.0.0`:

- [ ] Changelog has a `v1.0.0` section with stable scope and migration notes.
- [ ] All intended launch PRs are merged.
- [ ] Final private/local scrub is clean.
- [ ] Markdown links are checked.
- [ ] Schema files parse as JSON and validate against the selected JSON Schema validator path.
- [ ] Minimal examples validate against the selected schema or documented equivalent checks.
- [ ] Public README, overview, and Get Started path reflect the actual public repo state.
- [ ] Maintainers explicitly approve public visibility and tag creation.
- [ ] A tracked release-readiness issue or final checklist PR records the approval evidence and links to this plan.

## Non-Goals for v1.0.0

`v1.0.0` does not need to provide:

- a hosted service;
- a required database;
- a required UI;
- a required AI agent;
- a required OpenSpec workflow;
- a required ALM, MBSE, issue tracker, or CI platform;
- a formal third-party certification program;
- complete reference tooling for every adopter environment.

Those may evolve later, but the first stable standard should remain portable and tool-agnostic.

## Recommended Final Validation

Before `v1.0.0`, run or document equivalent checks:

```text
git status --short --branch
git diff --check
private/local reference scrub
Markdown relative-link check
JSON schema parse check
minimal and realistic example schema-shape check
```

If a stronger JSON Schema validator is adopted, document the exact command and validator version in the release evidence.

## Launch Decision

A `v1.0.0` launch should require explicit maintainer approval for both actions, recorded in a tracked release-readiness issue or final checklist PR:

1. changing repository visibility to public;
2. creating and pushing the `v1.0.0` tag and GitHub Release.

These actions should not happen automatically as part of merging readiness documentation.
