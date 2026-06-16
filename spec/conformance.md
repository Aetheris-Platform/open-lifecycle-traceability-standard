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

## L1: Stable IDs

An `OLTS L1` draft claim means lifecycle entities in scope have stable IDs.

Expected facts:

- each lifecycle record in scope has an `id`;
- IDs follow the draft shape `<DOMAIN>-<TYPE>-<NNNNN>`;
- `TYPE` values are draft OLTS entity type codes or explicitly documented local extensions;
- IDs are not reused for different lifecycle entities;
- retired or deprecated records preserve their IDs.

Expected diagnostics:

- invalid identifier shape;
- duplicate identifier;
- unknown entity type without documented extension;
- missing identifier on an in-scope lifecycle record.

L1 does not require relationship coverage. It gives the repository stable handles that later levels can connect.

## L2: Explicit Relationships

An `OLTS L2` draft claim means key lifecycle relationships in scope are explicit and reviewable.

Expected facts:

- relationships are stored in reviewed files or reviewed fields;
- relationship verbs use the draft OLTS relationship vocabulary or documented local extensions;
- relationship direction is consistent with the vocabulary;
- referenced OLTS IDs resolve to known records or documented external references;
- relationship source files are part of normal review.

Expected diagnostics:

- missing referenced entity;
- unknown relationship type;
- relationship direction mismatch;
- malformed relationship record;
- ambiguous external reference.

L2 does not require every requirement to have verification or evidence. It requires the relationships that are claimed to exist to be explicit enough for review.

## L3: Verification Coverage

An `OLTS L3` draft claim means requirements and use cases in scope have verification or validation coverage.

Expected facts:

- system requirements in scope link to verification tests through `verified_by` or an equivalent approved relationship;
- use cases in scope link to validation scenarios through `validated_by` or another documented lifecycle path;
- intentionally deferred or not-applicable coverage is documented as a reviewed exception;
- coverage gaps are visible as diagnostics or tracked follow-up work.

Expected diagnostics:

- requirement without verification coverage;
- use case without validation coverage;
- validation or verification target that cannot be resolved;
- undocumented coverage exception.

L3 helps reviewers see whether the product behavior in scope has a planned way to be checked. It does not prove that evidence exists or that tests passed.

## L4: Evidence Coverage

An `OLTS L4` draft claim means verification, validation, and release claims in scope link to evidence.

Expected facts:

- verification tests in scope link to evidence records through `evidenced_by` or an approved equivalent;
- validation scenarios in scope link to evidence records when execution evidence is required;
- release claims in scope link to evidence, exceptions, or reviewed release decisions;
- evidence records preserve enough provenance to identify the source result, report, log, artifact, or review record.

Expected diagnostics:

- test without required evidence;
- validation scenario without required evidence;
- release claim without evidence or reviewed exception;
- evidence record with missing provenance;
- stale, ambiguous, or inaccessible evidence reference.

L4 supports release review and audit preparation, but it does not by itself prove regulatory compliance.

## L5: Automated Conformance

An `OLTS L5` draft claim means automated checks validate the lower-level expectations for the stated scope.

Expected facts:

- checks run locally, in CI, or in another reviewed automation path;
- check results include diagnostics for failed or incomplete expectations;
- generated reports identify source files, inspected versions, and omitted or unresolved facts when practical;
- repository maintainers define which diagnostics are informational, warning-level, or blocking;
- blocking checks are only enabled after the team trusts the diagnostic quality.

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
| `warning` | A likely gap or ambiguity that should be reviewed. |
| `error` | A conformance expectation failed for the stated scope. |
| `blocked` | The source could not be read, so the checker cannot make a trustworthy claim. |

A missing file, parser failure, inaccessible external source, or disabled data source MUST NOT be treated as a healthy zero-result scan.

## Validation Expectations

Draft machine-readable schemas are available under [../schemas/](../schemas/). Adopters MAY also validate conformance with reviewed checklists, repository scripts, CI jobs, or external tooling.

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
