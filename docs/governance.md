# OLTS Governance

OLTS is `v1.0.0`. Governance should be lightweight enough to invite feedback and structured enough to protect the standard from unclear changes.

## Public Change Flow

This flow describes public operation for OLTS.

The intended public flow is:

```text
Discussion -> Issue -> Pull Request -> Review -> Merge -> Milestone or release decision
```

Small clarifications may start directly as an Issue or Pull Request when the problem and proposed wording are already clear.

## Stewardship

OLTS is currently stewarded by the repository maintainers listed in [../MAINTAINERS.md](../MAINTAINERS.md).

Maintainers are responsible for protecting tool neutrality, source-of-truth boundaries, conformance semantics, relationship vocabulary, schema compatibility, public readability, and release decisions. Maintainers should also prevent certification, compliance, or official-conformance claims unless a future policy explicitly defines those claims.

## Discussions

Use Discussions for broad questions, adoption stories, prior art, standards compatibility, early ideas, governance questions, and conformance concepts.

Discussions are not automatically accepted changes.

Recommended public Discussion categories are:

| Category | Purpose | Format |
| --- | --- | --- |
| General | Broad questions about OLTS concepts, adoption, and project direction. | Open-ended discussion |
| Ideas | Early proposals that are not ready for an Issue or Pull Request. | Open-ended discussion |
| Adoption Stories | Reports from teams evaluating or adopting OLTS. | Open-ended discussion |
| Prior Art | Notes on related standards, tools, research, and practices. | Open-ended discussion |
| Conformance | Questions about levels, diagnostics, schemas, validation, or claims. | Question and answer |
| Governance | Questions about contribution flow, releases, licensing, stewardship, or public process. | Question and answer |

## Issues

Use Issues for trackable work:

- spec clarification;
- concrete proposals;
- documentation gaps;
- conformance questions;
- schema requests;
- tooling requests;
- compatibility notes.

An issue should describe the problem, expected outcome, and any affected files or concepts.

## Pull Requests

Accepted changes land through pull requests.

A good PR should include:

- clear scope;
- rationale;
- affected docs/spec/examples;
- compatibility or migration notes;
- related discussion or issue links.

## Maintainer Review

Maintainers should review for:

- tool neutrality;
- source-of-truth boundaries;
- clarity for adopters;
- compatibility with existing standards;
- conformance impact;
- migration impact;
- public readability.

## Conformance and Diagnostics

Changes that affect conformance levels, adopter claim language, diagnostic severity, or blocking-gate guidance should call out the impact in the pull request.

Severity guidance should stay consistent with the conformance model and pipeline guidance:

- `info` and `warning` diagnostics are usually advisory unless a repository documents a stricter gate;
- `error` diagnostics identify failed expectations for the stated scope, but maintainers still define whether they block a pull request or release;
- `blocked` diagnostics mean the source could not be read, so a trustworthy pass/fail claim should not be made for the affected scope.

OLTS governance should not accept certification, compliance, or full-coverage claims unless a future policy explicitly defines who can make those claims, what evidence is required, and how disputes are handled.

## Decision Principles

OLTS should prefer changes that make lifecycle relationships more explicit, reduce tool lock-in, preserve human review, support incremental adoption, improve diagnostics and provenance, and work with both OpenSpec and non-OpenSpec workflows.

OLTS should avoid changes that require a specific vendor platform, require a database for conformance, depend on AI inference as source truth, replace source repositories with generated artifacts, or blur compliance claims without evidence.

## Release Decisions

Milestones and release decisions should happen after reviewed changes are merged and the changelog is updated.

At `v1.0.0`, the project satisfies the [v1 readiness plan](v1-readiness.md). Future releases should follow the compatibility and deprecation expectations in [versioning.md](versioning.md).
