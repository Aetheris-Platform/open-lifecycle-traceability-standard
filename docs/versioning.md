# OLTS Versioning and Readiness Plan

OLTS uses versioned milestones to separate draft maturity from stable standard commitments. Public release tags should wait until `v1.0.0` unless maintainers explicitly decide to publish an earlier draft.

## Current Maturity

OLTS is `v1.0.0`, the first stable public version of the standard. Earlier `v0.x` milestones organized draft review, experimentation, compatibility feedback, and invited adopter trials before the stable release. The launch record is tracked in [v1-readiness.md](v1-readiness.md) and [v1-release-evidence.md](v1-release-evidence.md).

At and after `v1.0.0`, compatibility promises are stricter and breaking changes require a major version. Earlier draft milestones introduced provisional conformance levels, diagnostics, validation expectations, adopter-claim language, and schema contracts.

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

Each release or launch note should call out any known migration impact.

## Release and Tag Policy

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

Draft milestone labels may still use forms such as `v0.2.0` or `v0.3.0` in changelog and planning docs for historical pre-`v1.0.0` work.

## Change Governance

The intended public flow is:

```text
Discussion -> Issue -> Pull Request -> Review -> Merge -> Milestone or release decision
```

Exploratory feedback belongs in Discussions. Trackable changes belong in Issues. Accepted changes land through reviewed pull requests.

## Compatibility Promises

At and after `v1.0.0`:

- stable conformance levels should remain meaningful across minor releases;
- breaking changes require a major version;
- deprecated fields or relationships should include migration guidance;
- tooling and schemas should preserve backward-compatible behavior when practical.
