# OLTS Versioning and Readiness Plan

OLTS uses versioned milestones to separate draft maturity from stable standard commitments. Public release tags should wait until `v1.0.0` unless maintainers explicitly decide to publish an earlier draft.

## Current Maturity

OLTS is in the `v0.x` draft series. Draft milestones are intended for review, experimentation, compatibility feedback, and early adopter trials before a stable public `v1.0.0` release. They may change as the community clarifies terminology, schemas, conformance levels, and governance.

The first stable standard target is `v1.0.0`; see [v1-readiness.md](v1-readiness.md) for the launch gates. After `v1.0.0`, compatibility promises become stricter and breaking changes require a major version. `v0.1.0` introduces provisional conformance levels for orientation; `v0.2.0` is expected to formalize diagnostics, validation expectations, and adopter-claim language.

## Planned Readiness Path

| Version | Readiness Milestone | Expected Scope |
| --- | --- | --- |
| `v0.1.0` | Initial draft | Overview, core positioning, initial identifier and relationship direction, minimal examples, contribution path. |
| `v0.2.0` | Conformance draft | Formalize the provisional levels introduced in `v0.1.0` with diagnostics, validation expectations, and adopter claims such as `OLTS L1` or `OLTS L2`. |
| `v0.3.0` | Schemas draft | Machine-readable draft schemas for core records, parsed relationship rows, generated artifact metadata, diagnostics, and conformance reports. |
| `v1.0.0` | First stable public standard | Stable core terminology, conformance levels, compatibility expectations, governance flow, and reference examples. |

## Version Semantics

OLTS versions follow semantic-versioning style once the standard reaches `v1.0.0`:

- **Major:** breaking changes to standard-conforming records, conformance levels, relationship semantics, or required provenance rules.
- **Minor:** backward-compatible additions, new optional fields, new examples, additional diagnostics, or new optional integration guidance.
- **Patch:** clarifications, typo fixes, non-normative wording updates, examples that do not change conformance meaning, or tooling/documentation fixes.

During the `v0.x` draft period, minor versions may still include breaking changes. Each release should call out any known migration impact.

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

- adopters should treat OLTS as a draft;
- examples and schemas may change;
- conformance labels are provisional;
- release notes should describe migration impact clearly.

At and after `v1.0.0`:

- stable conformance levels should remain meaningful across minor releases;
- breaking changes require a major version;
- deprecated fields or relationships should include migration guidance;
- tooling and schemas should preserve backward-compatible behavior when practical.
