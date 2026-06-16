# Pipeline Integration Guide

This guide describes how OLTS can fit into common development pipelines. It is draft guidance for `v0.1.0`.

OLTS is not a pipeline vendor. It is a repo-native traceability layer that existing tools can read, validate, and review.

## Integration Pattern

A practical OLTS integration usually follows this pattern:

```text
Repo source truth -> OLTS records and links -> local checks -> CI diagnostics -> review gates -> release evidence
```

Start with diagnostics. Promote only trusted checks to merge or release gates. Use the draft conformance model in [../spec/conformance.md](../spec/conformance.md) to decide whether checks are advisory or blocking for the claimed scope.

Any pipeline claim should name the checked scope, the claimed level, inspected sources, and whether diagnostics are advisory or blocking. A pipeline should not report an unscoped `OLTS L3`, `OLTS L4`, or `OLTS L5` result when it only inspected selected paths, entity types, release records, or generated artifacts.

## Advisory and Blocking Posture

Diagnostic severity and gate posture are related but separate:

| Severity | Pipeline meaning |
| --- | --- |
| `info` | Context for reviewers; usually advisory. |
| `warning` | A likely traceability gap or ambiguity; usually advisory until the team agrees it should block. |
| `error` | A conformance expectation failed for the stated scope; may block when the rule is trusted for that scope. |
| `blocked` | The source could not be read; should block any trustworthy pass/fail claim for the affected scope. |

Early pipelines should publish diagnostics without blocking merges. Later pipelines can block on selected severities or diagnostic codes, but the blocking rule should be documented with the checked scope.

Acceptable validation paths include manual release checklists, local scripts, CI jobs, external validators, and platform-native checks. OLTS does not require a hosted service, reference validator, GitHub Actions, GitLab CI, Azure Pipelines, Jira, OpenSpec, or any other vendor platform.

## GitHub Pipeline

Recommended GitHub flow:

1. Add OLTS files under `docs/olts/` or another reviewed path.
2. Add issue templates for requirements, proposals, or evidence gaps.
3. Add a PR checklist item for lifecycle impact.
4. Run OLTS checks in GitHub Actions when tooling exists. Early checks can validate parsed records and relationship rows against the candidate v1 schemas in [../schemas/](../schemas/) using the repeatable path in [schema-validation.md](schema-validation.md).
5. Publish diagnostics as PR comments or check summaries.
6. Require relationship fixes only after the team trusts the check.

Suggested PR checklist text:

```markdown
- [ ] Lifecycle impact reviewed.
- [ ] New or changed requirements have stable IDs where applicable.
- [ ] Requirement, test, evidence, artifact, or ADR links were updated where applicable.
- [ ] Missing OLTS links are documented as diagnostics or follow-up issues.
```

## GitLab Pipeline

Recommended GitLab flow:

1. Keep OLTS files in the repository with the product source.
2. Add merge request checklist items for lifecycle impact.
3. Run OLTS validation jobs in `.gitlab-ci.yml` when tooling exists. Early jobs can validate parsed records and relationship rows against the candidate v1 schemas in [../schemas/](../schemas/) using the repeatable path in [schema-validation.md](schema-validation.md).
4. Publish diagnostics as job artifacts.
5. Use protected branches for standard or product-truth updates.

## Azure DevOps Pipeline

Recommended Azure DevOps flow:

1. Map Azure Boards work items to OLTS `TRK`, `UC`, `SR`, or local extension records.
2. Keep canonical OLTS relationship files in the repo.
3. Link pull requests to work items and OLTS records.
4. Run validation in Azure Pipelines when tooling exists. Early jobs can validate parsed records and relationship rows against the candidate v1 schemas in [../schemas/](../schemas/) using the repeatable path in [schema-validation.md](schema-validation.md).
5. Keep release evidence linked to test and validation records.

## Jira Pipeline

Recommended Jira flow:

1. Keep Jira as planning/workflow truth if the team already uses it.
2. Store OLTS IDs in Jira fields, labels, or issue descriptions.
3. Keep relationship files in the repository for review and CI.
4. Link Jira issues to PRs and OLTS lifecycle records.
5. Treat Jira exports as inputs, not automatic replacements for reviewed repo files.

## OpenSpec Pipeline

OpenSpec fits naturally as change provenance.

Recommended mapping:

```text
OLTS work item -> OpenSpec change -> scenarios/requirements -> PR -> tests -> evidence
```

Guidance:

- Do not rename OpenSpec changes to look like OLTS IDs.
- Use OLTS IDs for durable lifecycle entities.
- Use OpenSpec IDs for proposed change intent and acceptance criteria.
- Link the two explicitly through a field or relationship file.

## Non-OpenSpec Pipeline

Teams that do not use OpenSpec can still adopt OLTS.

Acceptable change-provenance sources include:

- GitHub Issues;
- GitLab Issues;
- Jira tickets;
- Azure Boards work items;
- ADRs;
- design documents;
- release plans;
- pull request templates.

The key requirement is that provenance is explicit and reviewable.

## CI/CD Checks

Useful early checks, usually aligned with `L1` and `L2` claims:

- validate ID shape;
- detect duplicate IDs;
- detect missing relationship targets;
- detect unknown relationship values;
- detect missing required files;
- detect generated artifact metadata gaps.

Useful later checks, usually aligned with `L3`, `L4`, and `L5` claims:

- requirements without verification tests;
- tests without evidence;
- validation scenarios without evidence;
- artifacts without provenance;
- release candidates with unresolved lifecycle diagnostics.

## Release Review

OLTS can support release readiness by producing a review packet:

- capabilities included in the release;
- requirements changed or added;
- tests and validation scenarios linked to those requirements;
- evidence records;
- unresolved diagnostics;
- generated diagrams or RTMs with provenance;
- known manual review decisions.

This packet can be generated by tools, but the source relationships should remain reviewable in the repo or source systems.

## Compliance and Audit

OLTS can help assemble evidence chains, but it does not prove compliance by itself.

A useful evidence chain looks like:

```text
Requirement -> Verification Test -> Evidence -> Release Decision
```

For compliance controls, namespace external references clearly:

```text
NIST-SP-800-53:AU-2
ISO-27001:A.5.15
```

Avoid bare control names that can collide with OLTS IDs.

## AI-Assisted Pipelines

AI agents can help inventory sources, propose IDs, draft relationship files, and identify gaps. They should not silently rewrite canonical product truth.

Recommended guardrails:

- AI-generated OLTS changes land through PRs.
- The agent must report assumptions and uncertain mappings.
- The agent must not infer canonical relationships from fuzzy similarity without marking them as candidates.
- Humans approve all adopted IDs and relationships.

See [ai-agent-adoption-prompt.md](ai-agent-adoption-prompt.md) for a copy/paste prompt.
