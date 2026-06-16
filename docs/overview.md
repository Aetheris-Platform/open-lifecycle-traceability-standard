# Open Lifecycle Traceability Standard (OLTS)

OLTS turns scattered lifecycle knowledge into explicit, version-controlled relationships your existing tools, reviewers, CI systems, and AI assistants can read.

It connects requirements, tests, evidence, decisions, release readiness, artifacts, and implementation work without requiring a new database, UI, modeling framework, or vendor platform.

## TL;DR

- No new ALM platform required: OLTS can work with Markdown, CSV, YAML, JSON, GitHub, GitLab, Jira, Azure DevOps, OpenSpec, and MBSE tools.
- Product repositories remain the source of truth.
- Automation can diagnose, visualize, and propose changes, but humans approve lifecycle truth through normal review.

## Maturity

OLTS is an early draft. It is being shaped before the stable public `v1.0.0` standard, conformance levels, examples, and governance model are finalized.

The intent is practical: make lifecycle traceability usable in real development pipelines, not only in specialized tools or after-the-fact compliance reviews.

## The Problem

Most teams already produce lifecycle information:

- product capabilities;
- roadmap items;
- user needs and use cases;
- system requirements;
- architecture decisions;
- implementation tickets and pull requests;
- tests and validation scenarios;
- release evidence;
- diagrams, reports, and generated artifacts.

But this information is often scattered across issue trackers, documents, spreadsheets, PRs, test reports, CI logs, and chat history.

That creates recurring friction:

- Reviewers ask what a change is for.
- QA teams ask what validates a requirement.
- Release leads ask which blockers remain.
- Compliance reviewers ask where the evidence is.
- Architects ask whether diagrams reflect current source truth.
- AI assistants guess from filenames, text similarity, or incomplete tickets.

OLTS gives teams a shared way to make these relationships explicit, inspectable, and automatable.

## What OLTS Provides

OLTS defines a repo-native traceability contract for the development lifecycle:

- stable lifecycle identifiers;
- explicit relationship fields;
- catalog and relationship file guidance;
- provenance for generated views and artifacts;
- diagnostics for missing or malformed lifecycle data;
- conformance checks for local development, CI, release review, and audits;
- optional integration with OpenSpec, issue trackers, ADRs, PRs, test frameworks, RTMs, ALM tools, and MBSE workflows.

OLTS is not a replacement for a team's existing tools. It is a thin, portable layer that helps those tools agree on lifecycle meaning.

## How OLTS Fits With OpenSpec

OLTS and OpenSpec are complementary, but they solve different problems.

**OpenSpec defines change intent.** It captures what behavior is being proposed, why it matters, what requirements must hold, and which scenarios validate the change.

**OLTS defines lifecycle traceability.** It connects capabilities, work items, use cases, requirements, tests, evidence, artifacts, decisions, pull requests, generated diagrams, and release readiness across the full lifecycle.

In an OpenSpec-based workflow, OLTS can use OpenSpec as change provenance:

```text
Capability
  -> Work Item
    -> OpenSpec Change
      -> Requirement / Scenario
        -> Pull Request
          -> Test
            -> Evidence
```

But OpenSpec is not required to adopt OLTS. Teams can also use GitHub Issues, Jira tickets, ADRs, change request documents, release plans, pull requests, or other repo-native planning records as their change-provenance layer.

In short:

```text
OpenSpec makes change intent reviewable.
OLTS makes the full lifecycle traceable.
```

## How OLTS Relates to Existing Standards

OLTS is designed to sit alongside existing lifecycle and engineering standards, not pretend they do not exist.

OSLC helps tools collaborate through linked lifecycle services. ReqIF helps exchange requirements between tools. SPDX helps describe software bill of materials and related supply-chain metadata.

OLTS focuses on a different layer: making lifecycle relationships repo-native, reviewable in pull requests, visible to CI, and usable even when a team does not operate a full ALM platform.

A practical team might use:

- ReqIF to exchange requirements with an external tool;
- OSLC to connect live lifecycle systems;
- SPDX to describe software components and supply-chain metadata;
- OLTS to keep product lifecycle relationships explicit, versioned, reviewable, and automatable in the repo.

## A Minimal Example

An OLTS-compatible record can be simple:

```yaml
id: APP-SR-00014
type: SR
title: Operator can revoke an API token
verified_by:
  - APP-VT-00221
explained_by:
  - APP-ADR-00007
```

That small record lets a reviewer ask:

- Which test verifies this requirement?
- Which decision explains the design?
- Which relationship file links the requirement to a use case?
- Which relationship file links the test to evidence?

That is the core value of OLTS: important lifecycle relationships become explicit facts instead of reconstructed memories.

## Benefits Across Development Pipelines

### Product Planning

OLTS connects roadmap intent to implementation reality.

Product managers can see which capabilities are proposed, accepted, in progress, delivered, deferred, or blocked. They can also see which work items, requirements, tests, and evidence support each capability.

This reduces manual status reconciliation across roadmaps, trackers, release plans, and review notes.

### Engineering Execution

Developers get better context before making changes.

A work item can point to the capability it supports, the use case it enables, the requirements it affects, related ADRs, expected tests, and required evidence.

That means less time digging through tickets and documents, and fewer changes that drift away from product intent.

### Code Review

Reviewers can evaluate changes against explicit lifecycle impact.

Instead of asking "what is this for?" or "how do we know it is validated?", reviewers can inspect linked requirements, scenarios, tests, evidence, and decisions directly.

This makes review more focused and reduces clarification loops.

### QA and Validation

QA teams can find coverage gaps earlier.

OLTS makes it easier to identify:

- requirements without verification tests;
- use cases without validation scenarios;
- tests without evidence;
- evidence that is stale or disconnected;
- release candidates with unresolved lifecycle gaps.

This turns traceability from a late release scramble into a normal development signal.

### DevOps and CI/CD

OLTS gives CI/CD systems lifecycle-aware checks.

Pipelines can detect missing links, invalid identifiers, malformed relationship files, stale generated artifacts, and absent evidence before release review.

That creates a practical CI/CD compliance gate without forcing lifecycle truth into a proprietary system.

### Security and Compliance

Security and compliance teams get a clearer evidence chain.

OLTS does not magically prove compliance. It gives reviewers a navigable path from requirement to test to evidence to release decision.

That is especially useful for regulated teams, security-sensitive products, and organizations that repeatedly assemble audit evidence by hand.

### Architecture and Systems Engineering

OLTS supports generated diagrams and systems views without making diagrams the source of truth.

Diagrams can be generated from explicit lifecycle relationships and optional model metadata. Each generated artifact can preserve provenance: source files, source hashes, relationship inputs, omitted facts, diagnostics, and generator version.

This supports systems engineering, RTMs, MBSE workflows, and architecture review while remaining framework-agnostic.

### AI-Assisted Engineering

OLTS gives AI assistants safer context.

AI tools are most useful when they can inspect explicit source truth instead of guessing from filenames, issue titles, or fuzzy text similarity.

With OLTS, AI assistants can draft recommendations, identify missing links, summarize release risk, or propose traceability updates while preserving the rule that humans approve canonical truth.

## Illustrative Time-Savings Targets

These are illustrative estimates based on common manual-reconstruction patterns, not measured benchmarks. Actual savings depend on team size, release cadence, process maturity, and how much traceability work is manual today.

OLTS targets time teams commonly spend on:

| Area | Manual work OLTS targets |
| --- | --- |
| Planning | Reconciling roadmap, tracker, and release status |
| Development | Looking up requirement, decision, and validation context |
| Review | Clarifying why a change exists and how it is verified |
| QA | Finding missing test, validation, and evidence links |
| CI/CD | Repeating release-readiness checks manually |
| Compliance | Rebuilding evidence chains for audits |
| Architecture | Updating diagrams and traceability views by hand |

A small team of eight engineers shipping weekly might recover several hours per week once core relationships and checks are in place, mostly from reduced review clarification, faster release-readiness checks, and less manual evidence reconstruction.

For larger teams, regulated programs, multi-repo platforms, or systems engineering workflows, the upside can be larger because the cost of reconstructing lifecycle context increases with every repository, artifact, reviewer, and release gate.

## Conformance Levels

OLTS should be adoptable in stages. The draft conformance model is defined in [../spec/conformance.md](../spec/conformance.md), including level expectations, diagnostics, validation reporting, and claim language.

| Level | Meaning |
| --- | --- |
| `L1`: Stable IDs | Lifecycle entities have durable identifiers. |
| `L2`: Explicit Relationships | Key relationships are recorded in reviewable files or fields. |
| `L3`: Verification Coverage | Requirements and use cases in scope link to tests or validation scenarios. |
| `L4`: Evidence Coverage | Tests, validation scenarios, and release claims in scope link to evidence. |
| `L5`: Automated Conformance | Automated checks validate identifiers, relationships, provenance, and diagnostics. |

This gives teams a practical adoption ladder. During the `v0.x` draft period, teams should phrase claims as scoped adoption statements, such as "this repository is experimenting with OLTS L2 for selected requirements," rather than broad certification claims.

## What Makes OLTS Different

OLTS is built around a few principles:

1. Product repositories remain the source of truth.
2. Relationships must be explicit.
3. Automation proposes; humans approve.
4. Generated artifacts are derived and rebuildable.
5. The standard is tool-agnostic.
6. Adoption should be incremental.
7. Missing lifecycle data should produce diagnostics, not false confidence.

These principles matter because traceability only works if teams trust it. OLTS is designed to make that trust inspectable.

## Example Lifecycle Chain

```text
Capability
  --realizes--> Use Case
    --requires--> System Requirement
      --verified_by--> Verification Test
        --evidenced_by--> Evidence
```

A release reviewer can then ask:

- What capability does this requirement support?
- What test verifies it?
- What evidence proves the test ran?
- Which release is blocked if the evidence is missing?

## Adoption Path

Teams can adopt OLTS gradually:

1. Define stable lifecycle identifiers.
2. Add capability and work-item linkage.
3. Add use case and requirement catalogs.
4. Add explicit use case to requirement relationships.
5. Add requirement to test relationships.
6. Add validation and evidence records.
7. Add artifact and architecture decision links.
8. Add conformance checks to local development and CI.
9. Generate dashboards, diagrams, and review artifacts from explicit source data.
10. Use automation and AI assistants to propose improvements through normal PR review.

## Get Started

1. Read this overview and the [minimal example](../examples/minimal/README.md).
2. Review the [realistic example](../examples/realistic/README.md) when you need to see capability, work item, use case, requirement, validation, test, evidence, decision, and artifact records together.
3. Pick a domain prefix and a first conformance target, usually L1 or L2. See the [adoption guide](adoption-guide.md).
4. Add one record file and one relationship file in a reviewed path such as `docs/olts/`.
5. Connect OLTS to your pipeline with the [pipeline integration guide](pipeline-integration.md).
6. If you use an AI coding agent, start with the [AI agent adoption prompt](ai-agent-adoption-prompt.md).

Conformance tooling under `tools/` is planned. Until it lands, run these steps as reviewed pull requests.

## Repository Layout

- `spec/` - draft core and relationship standard material.
- `examples/` - minimal and realistic OLTS-compatible examples.
- `schemas/` - draft machine-readable validation contracts for records, relationships, diagnostics, conformance reports, and generated artifacts.
- `tools/` - planned conformance and migration tooling.
- `docs/` - overview, adoption, pipeline, governance, and versioning guidance.

## The Outcome

OLTS helps teams move from scattered lifecycle memory to connected lifecycle intelligence.

It gives product managers better visibility, developers better context, reviewers better evidence, QA teams better coverage insight, DevOps teams better readiness checks, compliance teams better audit trails, and AI assistants safer operating boundaries.

Most importantly, it does this without forcing teams into a single toolchain.

OLTS is an open standard for making software and systems development easier to trace, easier to review, easier to automate, and easier to trust.
