# Contributing to OLTS

OLTS is a private `v1.0.0` release candidate. Feedback is welcome, especially from product engineering, systems engineering, QA, DevOps, security, compliance, ALM, and MBSE practitioners.

## Good First Contributions

- Clarify the overview language.
- Add minimal examples for common repo layouts.
- Propose conformance-level refinements.
- Identify gaps against existing standards such as OSLC, ReqIF, SPDX, or common ALM workflows.
- Suggest diagnostics for missing, malformed, or ambiguous lifecycle data.

## How Changes Happen

The intended public flow is:

```text
Discussion -> Issue -> Pull Request -> Review -> Merge -> Milestone or release decision
```

After the `v1.0.0` public launch, use GitHub Discussions for broad questions, ideas, prior art, and adoption stories. Use Issues for trackable changes. Use Pull Requests for accepted edits to the standard, examples, docs, schemas, templates, or future tools. While the repository is private, maintainers may gather feedback through private or invited channels.

Small clarifications may start directly as an Issue or Pull Request when the problem and proposed wording are already clear.

Before contributing, read [docs/governance.md](docs/governance.md) and [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

Contributors should certify that they have the right to submit their contribution under Apache-2.0. A Developer Certificate of Origin sign-off is welcome but not required for pre-launch contributions.

Pull requests should describe the problem, proposed change, affected files or concepts, and any compatibility or migration impact. Changes that affect conformance levels, relationship semantics, schemas, or adopter claim language should call that out explicitly.

## Contribution Principles

- Keep OLTS tool-agnostic.
- Keep product repositories as source truth.
- Prefer explicit relationships over inference.
- Preserve human approval for canonical lifecycle changes.
- Make adoption incremental.

Unless explicitly stated otherwise, contributions are submitted under the Apache License 2.0.
