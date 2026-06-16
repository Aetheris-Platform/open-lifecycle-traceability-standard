# OLTS Conformance Model Draft

This file defines the draft OLTS conformance model intended for the `v0.2.0` conformance draft. It is not a stable `v1.0.0` certification policy.

OLTS conformance is designed to help adopters make honest, incremental claims about lifecycle traceability without requiring a specific tool, database, UI, ALM platform, MBSE framework, OpenSpec workflow, or AI agent.

Normative keywords in this file use the convention defined in [core.md](core.md#normative-language).

## Conformance Principles

1. Conformance levels are cumulative. A repository claiming `OLTS L3` MUST satisfy `L1`, `L2`, and `L3` for the stated scope.
2. Claims SHOULD name their scope. A claim MAY cover a whole repository, one product area, one release line, or one reviewed path such as `docs/olts/`.
3. Source truth MUST be explicit. Generated diagrams, dashboards, indexes, and reports are derived unless accepted by normal review.
4. Unknown, missing, or ambiguous lifecycle data SHOULD produce diagnostics, not false confidence.
5. Automation MAY validate, diagnose, summarize, and propose. Humans MUST approve canonical lifecycle truth.
6. Adopters MAY define local extensions, but claims SHOULD separate draft OLTS vocabulary from repository-specific extensions.

## Claim Shape

During the `v0.x` draft period, claims SHOULD be phrased as draft adoption statements, not certification statements.

A draft conformance claim MUST identify:

- the claimed OLTS level;
- the repository, product area, release line, source path, or other scope being claimed;
- any documented local extensions that are needed to understand the claim;
- any reviewed exceptions that affect the claimed scope.

A draft conformance claim MUST NOT imply coverage outside its stated scope.

Good examples:

```text
This repository is experimenting with OLTS L1 for requirements under docs/olts/records/.
This release branch maintains an OLTS L2 draft relationship set for selected use cases and system requirements.
This product area targets OLTS L3 for requirements that are in active release scope.
```

Claims MUST NOT use certification language unless a certification policy exists. Avoid:

```text
OLTS certified.
Fully OLTS compliant.
All requirements are verified.
```

OLTS has no official third-party certification program during the `v0.x` draft series.

## Level Summary

| Level | Name | Meaning |
| --- | --- | --- |
| `L1` | Stable IDs | Lifecycle entities have durable identifiers. |
| `L2` | Explicit Relationships | Key relationships are recorded in reviewable files or fields. |
| `L3` | Verification Coverage | Requirements and use cases in scope link to tests or validation scenarios. |
| `L4` | Evidence Coverage | Tests, validation scenarios, and release claims in scope link to evidence. |
| `L5` | Automated Conformance | Automated checks validate identifiers, relationships, provenance, and diagnostics. |

## Criteria and Diagnostics

Each level below separates claim criteria from diagnostics.

Claim criteria define what MUST or SHOULD be true for a repository to make a scoped draft claim at that level. Diagnostics define the gaps, malformed facts, or blocked checks that reviewers and validators SHOULD surface when evaluating the claim.

Diagnostics do not automatically make a repository non-conforming. A scoped claim MAY include reviewed exceptions, advisory diagnostics, or deferred work when the level criteria explicitly allow them and the claim identifies the affected scope.

## L1: Stable IDs

An `OLTS L1` draft claim means lifecycle entities in scope have stable IDs.

Claim criteria:

- each lifecycle record in scope MUST have an `id`;
- IDs MUST follow the draft shape `<DOMAIN>-<TYPE>-<NNNNN>`;
- `TYPE` values MUST be draft OLTS entity type codes or explicitly documented local extensions;
- IDs MUST NOT be reused for different lifecycle entities;
- retired or deprecated records SHOULD preserve their IDs.

Expected diagnostics:

- invalid identifier shape;
- duplicate identifier;
- unknown entity type without documented extension;
- missing identifier on an in-scope lifecycle record.

L1 does not require relationship coverage. It gives the repository stable handles that later levels can connect.

## L2: Explicit Relationships

An `OLTS L2` draft claim means key lifecycle relationships in scope are explicit and reviewable.

Claim criteria:

- relationships in scope MUST be stored in reviewed files or reviewed fields;
- relationship verbs MUST use the draft OLTS relationship vocabulary or documented local extensions;
- relationship direction MUST be consistent with the vocabulary or documented extension;
- referenced OLTS IDs MUST resolve to known records or documented external references;
- relationship source files SHOULD be part of normal review.

Expected diagnostics:

- missing referenced entity;
- unknown relationship type;
- relationship direction mismatch;
- malformed relationship record;
- ambiguous external reference.

L2 does not require every requirement to have verification or evidence. It requires the relationships that are claimed to exist to be explicit enough for review.

## L3: Verification Coverage

An `OLTS L3` draft claim means requirements and use cases in scope have verification or validation coverage.

Claim criteria:

- system requirements in scope MUST link to verification tests through `verified_by` or an equivalent documented relationship, unless a reviewed exception applies;
- use cases in scope MUST link to validation scenarios through `validated_by` or another documented lifecycle path, unless a reviewed exception applies;
- intentionally deferred or not-applicable coverage MUST be documented as a reviewed exception;
- coverage gaps SHOULD be visible as diagnostics or tracked follow-up work.

Expected diagnostics:

- requirement without verification coverage;
- use case without validation coverage;
- validation or verification target that cannot be resolved;
- undocumented coverage exception.

L3 helps reviewers see whether the product behavior in scope has a planned way to be checked. It does not prove that evidence exists or that tests passed.

## L4: Evidence Coverage

An `OLTS L4` draft claim means verification, validation, and release claims in scope link to evidence.

Claim criteria:

- verification tests in scope MUST link to evidence records through `evidenced_by` or an equivalent documented relationship, unless a reviewed exception applies;
- validation scenarios in scope MUST link to evidence records when execution evidence is required, unless a reviewed exception applies;
- release claims in scope MUST link to evidence, exceptions, or reviewed release decisions;
- evidence records SHOULD preserve enough provenance to identify the source result, report, log, artifact, or review record.

Expected diagnostics:

- test without required evidence;
- validation scenario without required evidence;
- release claim without evidence or reviewed exception;
- evidence record with missing provenance;
- stale, ambiguous, or inaccessible evidence reference.

L4 supports release review and audit preparation, but it does not by itself prove regulatory compliance.

## L5: Automated Conformance

An `OLTS L5` draft claim means automated checks validate the lower-level expectations for the stated scope.

Claim criteria:

- automated checks MUST run locally, in CI, or in another reviewed automation path for the claimed scope;
- check results MUST include diagnostics for failed or incomplete criteria;
- generated reports SHOULD identify source files, inspected versions, and omitted or unresolved facts when practical;
- repository maintainers MUST define which diagnostics are informational, warning-level, or blocking;
- blocking checks SHOULD only be enabled after the team trusts the diagnostic quality.

Expected diagnostics:

- parser or source-read failure;
- missing required source path;
- invalid ID, relationship, coverage, evidence, or provenance fact;
- generated artifact without source metadata;
- conformance report that cannot identify the checked scope.

L5 does not require OLTS reference tooling. A repository can satisfy an L5 draft claim with its own checks if the checks preserve OLTS semantics and produce reviewable diagnostics.

## Diagnostic Severity

OLTS diagnostics SHOULD be understandable before they are enforceable. A draft validator or manual review process SHOULD classify diagnostics in a way maintainers can act on.

Recommended severities:

| Severity | Meaning |
| --- | --- |
| `info` | Useful context that does not indicate a traceability gap. |
| `warning` | A likely gap or ambiguity that warrants review. |
| `error` | A conformance expectation failed for the stated scope. |
| `blocked` | The source could not be read, so the checker cannot make a trustworthy claim. |

A missing file, parser failure, inaccessible external source, or disabled data source MUST NOT be treated as a healthy zero-result scan.

## Validation Expectations

Candidate v1 machine-readable schemas are available under [../schemas/](../schemas/). Adopters MAY also validate conformance with reviewed checklists, repository scripts, CI jobs, or external tooling.

A repeatable, tool-agnostic validation path is described in [../docs/schema-validation.md](../docs/schema-validation.md). It is one acceptable way to validate parsed records, parsed relationship rows, semantic checks, and diagnostics without making any one implementation mandatory.

A useful validation report SHOULD identify:

- claimed level and scope;
- source files or external systems inspected;
- version, commit, timestamp, or source hash when practical;
- diagnostics found;
- explicit exceptions;
- whether the report is advisory or blocking.

The `v0.3.0` schemas draft translates the conformance semantics into small reviewable contracts. Schemas SHOULD support diagnostics and adoption without replacing human-approved lifecycle truth.

## Extensions

Adopters MAY define local entity types, relationship verbs, external reference namespaces, and diagnostic codes during the draft period.

Extensions SHOULD be documented with:

- name;
- meaning;
- expected source and target when the extension is a relationship;
- whether the extension is local-only or proposed for future OLTS standardization.

A repository MUST NOT present local extensions as core OLTS vocabulary unless they are accepted into the standard.

## OpenSpec and Non-OpenSpec Workflows

OpenSpec MAY satisfy change-provenance needs in an OLTS workflow, but OpenSpec is not required for conformance.

Non-OpenSpec repositories MAY use GitHub Issues, GitLab Issues, Jira tickets, Azure Boards work items, ADRs, release plans, pull requests, change request documents, or other reviewed records as provenance.

The conformance requirement is explicit, reviewable provenance. It is not a requirement to use any one planning or change-governance tool.
