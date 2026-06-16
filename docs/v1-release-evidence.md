# OLTS v1.0.0 Release Evidence

This checklist records the evidence maintainers reviewed for OLTS `v1.0.0`.

It records the public visibility approval for maintainer action after the final launch-record pull request merges. Creating the `v1.0.0` tag and publishing a GitHub Release remain separate launch actions unless maintainers explicitly approve them.

## Current Status

- Version: `v1.0.0`
- Repository visibility: approved for maintainer action after the final launch-record pull request merges
- Public tag: pending separate maintainer approval
- GitHub Release: pending separate maintainer approval
- Source readiness plan: [v1-readiness.md](v1-readiness.md)
- Launch settings runbook: [public-launch-settings.md](public-launch-settings.md)

## Required Approval

Maintainers record launch approval as separate actions:

1. changing the repository visibility to public after the final launch-record pull request merges;
2. creating and pushing the `v1.0.0` tag and GitHub Release.

Approval should be recorded in a tracked issue or final checklist pull request. This document records public visibility approval only. It does not approve the tag or GitHub Release.

## Stable Scope To Confirm

`v1.0.0` stabilizes:

- core terminology and entity types;
- identifier shape;
- source-of-truth boundaries;
- relationship vocabulary and direction;
- `documented_by` as the canonical lifecycle-to-artifact stored relationship;
- conformance levels `L1` through `L5`;
- v1 schema identifiers and validation guidance;
- minimal and realistic examples;
- governance, contribution, license, and public feedback posture.

## Migration Notes To Confirm

The changelog migration notes match the final repository state:

- Pre-`v1.0.0` adopters should update stored artifact relationships from `documents` to `documented_by` when using core OLTS lifecycle-to-artifact traceability.
- Relationship files should use only core verbs or documented local extensions.
- Record `type` should match the type segment in `id`.
- Conformance claims should name scope, level, sources inspected, diagnostics posture, and reviewed exceptions.
- Generated diagrams, dashboards, reports, and indexes remain derived unless accepted through reviewed source truth.
- Public community processes should activate at launch only after Issues, Discussions, branch protection, security settings, and templates are verified.

## Final Validation Checklist

Run or document equivalent checks at the final launch-record commit:

- [x] `git status --short --branch` is clean on `main` before the final launch-record branch is created.
- [x] `git diff --check` passes.
- [x] Final private/local reference scrub has no matches.
- [x] Markdown relative-link check passes.
- [x] All schema files parse as JSON.
- [x] Schema files validate against the selected JSON Schema validator path or documented equivalent.
- [x] Minimal example passes the selected schema or documented equivalent checks.
- [x] Realistic example passes the selected schema or documented equivalent checks.
- [x] Public README, overview, and Get Started path reflect the actual public repository state.
- [x] GitHub repository settings match [public-launch-settings.md](public-launch-settings.md).
- [x] `CHANGELOG.md` has a `v1.0.0` section with stable scope and migration notes.
- [x] Maintainers approve public visibility after the final launch-record pull request merges.
- [ ] Maintainers approve the `v1.0.0` tag and GitHub Release.

## Launch-Candidate Evidence Run

Evidence run: `2026-06-16`

Evidence branch: `codex/finalize-v1-launch-candidate-evidence`

Launch-candidate base commit: `a2a2b9b`

This run records launch-candidate evidence only. It does not approve public visibility, create a tag, publish a GitHub Release, or certify an adopter.

| Check | Result | Evidence |
| --- | --- | --- |
| Working tree posture | Passed before evidence edits | `git status --short --branch` reported a clean `codex/finalize-v1-launch-candidate-evidence` branch created from synced `main`. Final `main` recheck remains required after this evidence PR is merged. |
| Whitespace diff check | Passed | `git diff --check` returned no output. |
| Private/local scrub | Passed | Search for local paths, private product names, personal names, ignored description draft, secrets, credentials, and internal-only assumptions returned no matches in tracked files. |
| Stale maturity wording scan | Passed | Search for obsolete pre-release maturity wording returned no matches in Markdown files. |
| Markdown relative links | Passed | Repository Markdown relative-link check returned `markdown links ok`. |
| Schema JSON parse | Passed | All five schema files parsed as JSON: conformance report, diagnostic, generated artifact, record, and relationship. |
| Schema identifier consistency | Passed | v1 schema set has 5 `$id` values and 3 internal `$ref` values; all refs resolve to existing v1 IDs. |
| Relationship vocabulary consistency | Passed | Relationship schema enum is exactly `implements`, `realizes`, `requires`, `specified_by`, `verified_by`, `validated_by`, `evidenced_by`, `documented_by`, `explained_by`, `supersedes`. Minimal and realistic examples use only in-vocabulary verbs. |
| Example documented-equivalent checks | Passed | Minimal and realistic examples contain 16 records total; required record fields are present, ID shape is valid, `type` matches the ID type segment, relationship rows have required fields, sources resolve, and targets resolve to records or valid external references. |
| README and overview public-state review | Passed | README and overview describe OLTS as `v1.0.0` and include a public Get Started path for adopters. |
| Remote repository settings | Passed | Repository was private at verification time; description/topics match the runbook; Issues and Discussions are enabled; required Discussion categories are present; `Conformance` and `Governance` are question-and-answer categories; Wiki and Projects are disabled; security policy, Dependabot security updates, secret scanning, and push protection are enabled where available; `main` branch protection requires pull requests, conversation resolution, and linear history. Required approving reviews intentionally remain at `0` until after launch. |

## Final Launch-Record Evidence Run

Evidence run: `2026-06-16`

Evidence branch: `codex/final-v1-launch-approval-record`

Final launch-record base commit: `531f9eb`

This run records the final tracked launch evidence before maintainers make the repository public. It does not create the `v1.0.0` tag, publish a GitHub Release, certify any adopter, or change repository visibility from this branch.

| Check | Result | Evidence |
| --- | --- | --- |
| Clean `main` before final branch | Passed | `git status --short --branch` reported clean `main` synced with `origin/main` before `codex/final-v1-launch-approval-record` was created. |
| Version language | Passed | README, overview, versioning, spec, schema, governance, pipeline, validation, and review docs now describe OLTS as `v1.0.0`. |
| README Get Started path | Passed | README provides a public adopter path from overview, to minimal example, to domain prefix, to first record and relationship files, to adoption and pipeline guides. |
| Whitespace diff check | Passed | `git diff --check` returned no output. |
| Private/local scrub | Passed | Search for local paths, private product names, personal names, ignored description draft, secrets, credentials, and internal-only assumptions returned no matches in tracked files. |
| Stale maturity wording scan | Passed | Search for obsolete pre-launch maturity wording returned no matches in Markdown files. |
| Markdown relative links | Passed | Repository Markdown relative-link check returned `markdown links ok`. |
| Schema JSON parse | Passed | All five schema files parsed as JSON: conformance report, diagnostic, generated artifact, record, and relationship. |
| Schema identifier consistency | Passed | v1 schema set has 5 `$id` values and 3 internal `$ref` values; all refs resolve to existing v1 IDs. |
| Relationship vocabulary consistency | Passed | Relationship schema enum is exactly `implements`, `realizes`, `requires`, `specified_by`, `verified_by`, `validated_by`, `evidenced_by`, `documented_by`, `explained_by`, `supersedes`. Minimal and realistic examples use only in-vocabulary verbs. |
| Example documented-equivalent checks | Passed | Minimal and realistic examples contain 16 records total; required record fields are present, ID shape is valid, `type` matches the ID type segment, relationship rows have required fields, sources resolve, and targets resolve to records or valid external references. |
| Remote repository settings | Passed | Repository was private at verification time and approved for public visibility after this pull request; description/topics match the runbook; Issues and Discussions are enabled; `Conformance`, `Governance`, and `Questions` are question-and-answer categories; Wiki and Projects are disabled; security policy is enabled; `main` branch protection requires pull requests, conversation resolution, and linear history. Required approving reviews intentionally remain at `0` until after launch. |
| Public visibility approval | Passed | Maintainer approval is recorded for making the repository public after the final launch-record pull request merges. |
| Tag and GitHub Release approval | Pending | Maintainers have not separately approved creating the `v1.0.0` tag or publishing a GitHub Release. |

## GitHub Settings Evidence

Record the final operational setting evidence here before launch:

| Setting | Required state | Evidence |
| --- | --- | --- |
| Repository visibility | Approved for public visibility after the final launch-record pull request merges | Verified private on `2026-06-16`; no visibility change performed from this branch; maintainer approval recorded for public visibility after the final launch-record pull request merges. |
| Repository description | Matches [public-launch-settings.md](public-launch-settings.md) | Verified on `2026-06-16`. |
| Topics | Match [public-launch-settings.md](public-launch-settings.md) | Verified on `2026-06-16`: `traceability`, `requirements`, `requirements-management`, `verification`, `validation`, `evidence`, `devops`, `software-lifecycle`, `open-standard`, `systems-engineering`, `mbse`, `ci-cd`. |
| Issues | Enabled | Verified enabled on `2026-06-16`. |
| Discussions | Enabled and categories configured | Verified on `2026-06-16`: Discussions are enabled and required category names are present. `Conformance` and `Governance` are question-and-answer categories. |
| Main branch protection | Pull request workflow required; approving-review count deferred until after launch | Verified on `2026-06-16`: `main` requires pull requests, stale review dismissal is enabled, conversation resolution is required, linear history is required, force pushes are blocked, and branch deletion is blocked. Required approving reviews intentionally remain at `0` until after launch, per maintainer direction. |
| Conversation resolution | Required before merge | Verified enabled on `2026-06-16`. |
| Force pushes | Blocked on protected branches | Verified blocked on `2026-06-16`. |
| Branch deletion | Blocked on protected branches | Verified blocked on `2026-06-16`. |
| Security settings | Reviewed where available | Verified on `2026-06-16`: security policy enabled, Dependabot security updates enabled, secret scanning enabled, push protection enabled. Advanced Security returned `422` as unavailable for this repository and not a prerequisite for security features. |
| Wiki/projects | Match governance posture | Verified on `2026-06-16`: Wiki disabled, Projects disabled. |
| Private/local scrub | No local paths, private product names, secrets, credentials, or internal-only assumptions in tracked files | Final scrub passed on `2026-06-16`. |

## Final Launch Decision

Use this section only when maintainers are ready to launch.

- Public visibility approval: approved for maintainer action after the final launch-record pull request merges
- Approver(s): repository maintainer
- Approval link: final launch-record pull request
- Tag approval: pending separate maintainer approval
- GitHub Release approval: pending separate maintainer approval
- Final launch commit: final launch-record pull request merge commit
- Final launch date: 2026-06-16

If tag or GitHub Release approval is missing, do not create the tag or publish a GitHub Release.
