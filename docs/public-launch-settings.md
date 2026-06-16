# Public Launch Settings

This runbook records the GitHub repository settings OLTS maintainers should verify before making the repository public. It is launch-readiness guidance, not approval to change visibility, create a tag, or publish a GitHub Release.

OLTS remains private and in the `v0.x` draft series until maintainers explicitly approve both public visibility and the `v1.0.0` release.

## Repository Description and Topics

Recommended public repository description:

```text
A repo-native standard for explicit lifecycle traceability across requirements, tests, evidence, decisions, artifacts, and release readiness without requiring a specific tool, database, or platform.
```

Recommended topics:

```text
traceability
requirements
requirements-management
verification
validation
evidence
devops
software-lifecycle
open-standard
systems-engineering
mbse
ci-cd
```

Settings location:

```text
Repo -> Settings -> General -> Repository details
```

## Features

Recommended feature settings:

| Setting | Intended state | Location |
| --- | --- | --- |
| Issues | Enabled | `Repo -> Settings -> General -> Features` |
| Discussions | Enabled | `Repo -> Settings -> General -> Features` |
| Wiki | Disabled unless maintainers decide to maintain wiki content | `Repo -> Settings -> General -> Features` |
| Projects | Optional; disable unless maintainers plan to use GitHub Projects for public roadmap work | `Repo -> Settings -> General -> Features` |

## Discussion Categories

Create or verify these categories after Discussions are enabled:

| Category | Short description | Format |
| --- | --- | --- |
| General | Broad questions about OLTS concepts, adoption, and project direction. | Open-ended discussion |
| Ideas | Early proposals that are not ready for an Issue or Pull Request. | Open-ended discussion |
| Adoption Stories | Reports from teams evaluating or adopting OLTS. | Open-ended discussion |
| Prior Art | Notes on related standards, tools, research, and practices. | Open-ended discussion |
| Conformance | Questions about levels, diagnostics, schemas, validation, or claims. | Question and answer |
| Governance | Questions about contribution flow, releases, licensing, stewardship, or public process. | Question and answer |

Settings location:

```text
Repo -> Discussions -> Manage discussion categories
```

## Branch Protection

Before public launch, protect `main`.

Minimum intended settings:

- require a pull request before merging;
- require at least one approving review;
- require conversation resolution before merging;
- block force pushes;
- block deletion of the protected branch.

Optional settings to consider when CI exists:

- require selected status checks before merging;
- require branches to be up to date before merging;
- require signed commits if maintainers choose that project posture.

Settings locations:

```text
Repo -> Settings -> Branches
Repo -> Settings -> Rules -> Rulesets
```

## Security and Vulnerability Reporting

Before public launch, review the security settings available to the repository and organization.

Recommended checks:

- enable private vulnerability reporting when available;
- review dependency graph and Dependabot alerts where applicable;
- review secret scanning and push protection where available;
- confirm [../SECURITY.md](../SECURITY.md) matches the enabled reporting path.

Settings location:

```text
Repo -> Settings -> Code security and analysis
```

## Issue and Pull Request Templates

The repository already includes issue templates and a pull request template. Before public launch, verify that GitHub renders them as expected:

- spec clarification;
- proposal;
- conformance question;
- adoption story;
- prior art or compatibility note;
- issue chooser contact link to Discussions;
- pull request checklist.

Settings/files:

```text
.github/ISSUE_TEMPLATE/
.github/pull_request_template.md
Repo -> Issues -> New issue
Repo -> Pull requests -> New pull request
```

## Visibility and Release Stop Gates

Do not make the repository public until:

- the `v1.0.0` readiness gates are complete or explicitly accepted by maintainers;
- final private/local scrub has passed;
- the public README and overview reflect the actual public repository state;
- maintainers record explicit approval for public visibility;
- maintainers separately record explicit approval for the `v1.0.0` tag and GitHub Release.

Changing visibility and creating the release tag are separate actions. Neither should happen automatically as a side effect of merging readiness documentation.
