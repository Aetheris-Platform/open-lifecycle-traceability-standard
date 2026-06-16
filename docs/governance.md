# OLTS Governance

OLTS is an early open draft. Governance should be lightweight enough to invite feedback and structured enough to protect the standard from unclear changes.

## Public Change Flow

The intended public flow is:

```text
Discussion -> Issue -> Pull Request -> Review -> Merge -> Release tag
```

## Discussions

Use Discussions for broad questions, adoption stories, prior art, standards compatibility, early ideas, governance questions, and conformance concepts.

Discussions are not automatically accepted changes.

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

## Decision Principles

OLTS should prefer changes that make lifecycle relationships more explicit, reduce tool lock-in, preserve human review, support incremental adoption, improve diagnostics and provenance, and work with both OpenSpec and non-OpenSpec workflows.

OLTS should avoid changes that require a specific vendor platform, require a database for conformance, depend on AI inference as source truth, replace source repositories with generated artifacts, or blur compliance claims without evidence.

## Release Decisions

Release tags should be created after reviewed changes are merged and the changelog is updated.

During `v0.x`, releases are draft milestones. At `v1.0.0`, the project should publish a clearer compatibility and deprecation policy.
