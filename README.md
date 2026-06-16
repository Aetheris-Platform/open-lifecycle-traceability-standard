# OLTS: Open Lifecycle Traceability Standard

OLTS turns scattered lifecycle knowledge into explicit, version-controlled relationships your existing tools, reviewers, CI systems, and AI assistants can read.

It connects requirements, tests, evidence, decisions, release readiness, artifacts, and implementation work without requiring a new database, UI, modeling framework, or vendor platform.

## TL;DR

- No new ALM platform required: OLTS can work with Markdown, CSV, YAML, JSON, GitHub, GitLab, Jira, Azure DevOps, OpenSpec, and MBSE tools.
- Product repositories remain the source of truth.
- Automation can diagnose, visualize, and propose changes, but humans approve lifecycle truth through normal review.
- Generated diagrams, dashboards, indexes, and reports are derived unless accepted through reviewed source truth.

## Maturity

OLTS is `v1.0.0`, the first stable public version of the Open Lifecycle Traceability Standard. Core terminology, relationship semantics, conformance levels, schemas, examples, and governance guidance are stable for adopter use.

See [docs/v1-readiness.md](docs/v1-readiness.md) and [docs/v1-release-evidence.md](docs/v1-release-evidence.md) for the launch record and separate tag/GitHub Release status.

The intent is practical: make lifecycle traceability usable in real development pipelines, not only in specialized tools or after-the-fact compliance reviews.

## Why OLTS

Most teams already produce lifecycle information: product capabilities, roadmap items, use cases, requirements, decisions, implementation work, tests, validation scenarios, release evidence, diagrams, and generated artifacts.

The problem is that this information is often scattered across issue trackers, documents, spreadsheets, PRs, test reports, CI logs, and chat history. OLTS gives teams a shared way to make those relationships explicit, inspectable, and automatable.

Read the full overview: [docs/overview.md](docs/overview.md). To try OLTS in an existing repository, start with the [adoption guide](docs/adoption-guide.md), the [pipeline integration guide](docs/pipeline-integration.md), or the [AI agent adoption prompt](docs/ai-agent-adoption-prompt.md).

## A Minimal Example

```yaml
id: APP-SR-00014
type: SR
title: Operator can revoke an API token
verified_by:
  - APP-VT-00221
explained_by:
  - APP-ADR-00007
```

That small record lets a reviewer ask which test verifies the requirement and which decision explains the design. The related relationship file links the use case to the requirement and the test to its evidence.

The canonical relationship direction is:

```text
Use Case --requires--> Requirement --verified_by--> Test --evidenced_by--> Evidence
```

## How OLTS Fits With OpenSpec

OpenSpec makes change intent reviewable. OLTS makes the full lifecycle traceable.

In an OpenSpec-based workflow, OLTS can use OpenSpec as change provenance. OpenSpec is not required to adopt OLTS; teams can also use GitHub Issues, Jira tickets, ADRs, change request documents, release plans, pull requests, or other repo-native planning records.

## Conformance Levels

OLTS defines an adoption ladder from stable IDs through automated conformance. See [spec/conformance.md](spec/conformance.md) for level expectations, diagnostics guidance, validation reporting, and scoped adopter claim language.

| Level | Meaning |
| --- | --- |
| `L1`: Stable IDs | Lifecycle entities have durable identifiers. |
| `L2`: Explicit Relationships | Key relationships are recorded in reviewable files or fields. |
| `L3`: Verification Coverage | Requirements and use cases in scope link to tests or validation scenarios. |
| `L4`: Evidence Coverage | Tests, validation scenarios, and release claims in scope link to evidence. |
| `L5`: Automated Conformance | Automated checks validate identifiers, relationships, provenance, and diagnostics. |

## Versioning

OLTS is currently `v1.0.0`. The readiness path was:

- `v0.1.0` initial draft
- `v0.2.0` conformance draft
- `v0.3.0` schemas draft
- `v1.0.0` first stable standard

See [docs/versioning.md](docs/versioning.md), [docs/v1-readiness.md](docs/v1-readiness.md), and [CHANGELOG.md](CHANGELOG.md).

Core entity types, identifier shape, source-truth boundaries, and generated artifact semantics are reviewed in [docs/core-terminology.md](docs/core-terminology.md).

## Repository Layout

- [docs/](docs/) - overview, adoption notes, pipeline integration, governance, and migration guidance.
- [spec/](spec/) - core and relationship standard material.
- [examples/](examples/) - minimal and realistic OLTS-compatible examples.
- [schemas/](schemas/) - machine-readable validation contracts for records, relationships, diagnostics, conformance reports, and generated artifacts.
- [tools/](tools/) - future conformance and migration tooling.

## Get Started

1. Read the short [overview](docs/overview.md) to understand OLTS concepts and benefits.
2. Open the [minimal example](examples/minimal/README.md) and copy its shape for one requirement, one test, one evidence record, and one relationship file.
3. Choose a domain prefix for your repository, such as `APP`, and start with an `OLTS L1` or `OLTS L2` scoped adoption target.
4. Add one reviewed record file and one reviewed relationship file, usually under a path such as `docs/olts/`.
5. Use the [adoption guide](docs/adoption-guide.md) to expand the first slice without migrating everything at once.
6. Use the [pipeline integration guide](docs/pipeline-integration.md) when you are ready to add local, CI, release-review, or evidence checks.
7. Review the [realistic example](examples/realistic/README.md) when you need a fuller capability-to-evidence chain.
8. If using an AI coding agent, start with the [AI agent adoption prompt](docs/ai-agent-adoption-prompt.md); it defaults to plan-only unless edits are explicitly authorized.

## License

OLTS is licensed under the [Apache License 2.0](LICENSE).
