# OLTS Versioning and Readiness Plan

OLTS uses public version tags to separate draft maturity from stable standard commitments.

## Current Maturity

OLTS is in the `v0.x` draft series. Draft releases are intended for review, experimentation, compatibility feedback, and early adopter trials. They may change as the community clarifies terminology, schemas, conformance levels, and governance.

The first stable standard target is `v1.0.0`. After `v1.0.0`, compatibility promises become stricter and breaking changes require a major version. `v0.1.0` introduces provisional conformance levels for orientation; `v0.2.0` is expected to formalize diagnostics, validation expectations, and adopter-claim language.

## Planned Readiness Path

| Version | Readiness Milestone | Expected Scope |
| --- | --- | --- |
| `v0.1.0` | Initial public draft | Overview, core positioning, initial identifier and relationship direction, minimal examples, contribution path. |
| `v0.2.0` | Conformance draft | Formalize the provisional levels introduced in `v0.1.0` with diagnostics, validation expectations, and adopter claims such as `OLTS L1` or `OLTS L2`. |
| `v0.3.0` | Schemas draft | Machine-readable schemas for core records, relationship files, generated artifact metadata, diagnostics, and conformance reports. |
| `v1.0.0` | First stable standard | Stable core terminology, conformance levels, compatibility expectations, governance flow, and reference examples. |

## Version Semantics

OLTS versions follow semantic-versioning style once the standard reaches `v1.0.0`:

- **Major:** breaking changes to standard-conforming records, conformance levels, relationship semantics, or required provenance rules.
- **Minor:** backward-compatible additions, new optional fields, new examples, additional diagnostics, or new optional integration guidance.
- **Patch:** clarifications, typo fixes, non-normative wording updates, examples that do not change conformance meaning, or tooling/documentation fixes.

During the `v0.x` draft period, minor versions may still include breaking changes. Each release should call out any known migration impact.

## What Gets Tagged

A release tag should identify the state of:

- the draft specification under `spec/`;
- public guidance under `docs/`;
- examples under `examples/`;
- schemas under `schemas/`, when present;
- reference tooling under `tools/`, when present.

Tags should use the form:

```text
v0.1.0
v0.2.0
v0.3.0
v1.0.0
```

## Change Governance

The intended public flow is:

```text
Discussion -> Issue -> Pull Request -> Review -> Merge -> Release tag
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
