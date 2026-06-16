# OLTS v1.0.0 Release Evidence

This checklist records the evidence maintainers should review before making OLTS public and tagging `v1.0.0`.

It is a release-readiness workspace, not a release announcement. Merging this file does not approve public visibility, create a tag, publish a GitHub Release, or certify any adopter.

## Current Status

- Release target: `v1.0.0`
- Repository visibility: private until explicit maintainer approval
- Public tag: not approved
- GitHub Release: not approved
- Source readiness plan: [v1-readiness.md](v1-readiness.md)
- Launch settings runbook: [public-launch-settings.md](public-launch-settings.md)

## Required Approval

Before public launch, maintainers should record explicit approval for both separate actions:

1. changing the repository visibility to public;
2. creating and pushing the `v1.0.0` tag and GitHub Release.

Approval should be recorded in a tracked issue or final checklist pull request. Do not infer approval from merged readiness documentation alone.

## Stable Scope To Confirm

The `v1.0.0` release candidate is intended to stabilize:

- core terminology and entity types;
- identifier shape;
- source-of-truth boundaries;
- relationship vocabulary and direction;
- `documented_by` as the canonical lifecycle-to-artifact stored relationship;
- conformance levels `L1` through `L5`;
- candidate v1 schema identifiers and validation guidance;
- minimal and realistic examples;
- governance, contribution, license, and public feedback posture.

## Migration Notes To Confirm

Before tagging, confirm the changelog migration notes still match the final repository state:

- Pre-`v1.0.0` adopters should update stored artifact relationships from `documents` to `documented_by` when using core OLTS lifecycle-to-artifact traceability.
- Relationship files should use only core verbs or documented local extensions.
- Record `type` should match the type segment in `id`.
- Conformance claims should name scope, level, sources inspected, diagnostics posture, and reviewed exceptions.
- Generated diagrams, dashboards, reports, and indexes remain derived unless accepted through reviewed source truth.
- Public community processes should activate at launch only after Issues, Discussions, branch protection, security settings, and templates are verified.

## Final Validation Checklist

Run or document equivalent checks at the final launch candidate commit:

- [ ] `git status --short --branch` is clean on `main`.
- [ ] `git diff --check` passes.
- [ ] Final private/local reference scrub has no matches.
- [ ] Markdown relative-link check passes.
- [ ] All schema files parse as JSON.
- [ ] Schema files validate against the selected JSON Schema validator path or documented equivalent.
- [ ] Minimal example passes the selected schema or documented equivalent checks.
- [ ] Realistic example passes the selected schema or documented equivalent checks.
- [ ] Public README, overview, and Get Started path reflect the actual public repository state.
- [ ] GitHub repository settings match [public-launch-settings.md](public-launch-settings.md).
- [ ] `CHANGELOG.md` has a `v1.0.0` section with stable scope and migration notes.
- [ ] Maintainers approve public visibility.
- [ ] Maintainers approve the `v1.0.0` tag and GitHub Release.

## GitHub Settings Evidence

Record the final operational setting evidence here before launch:

| Setting | Required state | Evidence |
| --- | --- | --- |
| Issues | Enabled | Pending final verification |
| Discussions | Enabled and categories configured | Pending final verification |
| Main branch protection | Pull requests and review required | Pending final verification |
| Conversation resolution | Required before merge | Pending final verification |
| Force pushes | Blocked on protected branches | Pending final verification |
| Branch deletion | Blocked on protected branches | Pending final verification |
| Security settings | Reviewed where available | Pending final verification |
| Wiki/projects | Match governance posture | Pending final verification |

## Final Launch Decision

Use this section only when maintainers are ready to launch.

- Public visibility approval: pending
- Approver(s): pending
- Approval link: pending
- Tag approval: pending
- GitHub Release approval: pending
- Final launch commit: pending
- Final launch date: pending

If any approval is missing, do not change visibility, create the tag, or publish a GitHub Release.
