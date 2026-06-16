# OLTS Versioning and Readiness Plan

OLTS uses versioned milestones to separate draft maturity from stable standard commitments. Public release tags should wait until `v1.0.0` unless maintainers explicitly decide to publish an earlier draft.

## Current Maturity

OLTS is a private `v1.0.0` release candidate. Earlier `v0.x` milestones organized draft review, experimentation, compatibility feedback, and invited adopter trials before the first stable public release. The remaining launch work is tracked in [v1-readiness.md](v1-readiness.md) and [v1-release-evidence.md](v1-release-evidence.md).

The first stable standard target is `v1.0.0`. After `v1.0.0`, compatibility promises become stricter and breaking changes require a major version. Earlier draft milestones introduced provisional conformance levels, diagnostics, validation expectations, adopter-claim language, and schema contracts.

## Planned Readiness Path

| Version | Readiness Milestone | Expected Scope |
| --- | --- | --- |
| `v0.1.0` | Initial draft | Overview, core positioning, initial identifier and relationship direction, minimal examples, contribution path. |
| `v0.2.0` | Conformance draft | Formalize the provisional levels introduced in `v0.1.0` with diagnostics, validation expectations, and adopter claims such as `OLTS L1` or `OLTS L2`. |
| `v0.3.0` | Schemas draft | Initial machine-readable schemas for core records, parsed relationship rows, generated artifact metadata, diagnostics, and conformance reports. |
| `v1.0.0` | First stable public standard | Stable core terminology, conformance levels, compatibility expectations, governance flow, and reference examples. |

## Version Semantics

OLTS versions follow semantic-versioning style once the standard reaches `v1.0.0`:

- **Major:** breaking changes to standard-conforming records, conformance levels, relationship semantics, or required provenance rules.
- **Minor:** backward-compatible additions, new optional fields, new examples, additional diagnostics, or new optional integration guidance.
- **Patch:** clarifications, typo fixes, non-normative wording updates, examples that do not change conformance meaning, or tooling/documentation fixes.

Before the approved `v1.0.0` public launch, release-candidate changes may still include corrections needed for stable publication. Each release or launch note should call out any known migration impact.

## Release and Tag Policy

Before `v1.0.0`, maintainers may use version labels, changelog sections, branches, or private/internal tags to organize draft milestones. A draft milestone does not automatically mean the repository is publicly released.

At `v1.0.0` and later, after the [v1 readiness gates](v1-readiness.md) are satisfied, a public release tag should identify the state of:

- the draft or stable specification under `spec/`;
- public guidance under `docs/`;
- examples under `examples/`;
- schemas under `schemas/`, when present;
- reference tooling under `tools/`, when present.

Public tags should use the form:

```text
v1.0.0
v1.1.0
v2.0.0
```

Draft milestone labels may still use forms such as `v0.2.0` or `v0.3.0` in changelog and planning docs.

## Change Governance

The intended public flow is:

```text
Discussion -> Issue -> Pull Request -> Review -> Merge -> Milestone or release decision
```

Exploratory feedback belongs in Discussions. Trackable changes belong in Issues. Accepted changes land through reviewed pull requests.

## Compatibility Promises

Before `v1.0.0`:

- adopters should treat OLTS as a launch-gated release candidate;
- examples and schemas may change;
- conformance labels are provisional;
- release notes should describe migration impact clearly.

At and after `v1.0.0`:

- stable conformance levels should remain meaningful across minor releases;
- breaking changes require a major version;
- deprecated fields or relationships should include migration guidance;
- tooling and schemas should preserve backward-compatible behavior when practical.
