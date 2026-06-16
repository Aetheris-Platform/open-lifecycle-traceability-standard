# OLTS Adoption Guide

This guide helps a team adopt OLTS incrementally in an existing development repository.

OLTS adoption should start small. A useful first milestone is usually L1 or L2, not full evidence automation.

## Adoption Goals

A good first OLTS adoption should let a reviewer answer:

1. What lifecycle entities exist?
2. Which IDs are stable?
3. Which relationships are explicit?
4. Which gaps are known?
5. Which files are source truth?
6. Which automation may diagnose or propose changes?

## Step 1: Pick a Domain Prefix

Choose a short uppercase prefix for the product, platform, service, or project.

Examples:

```text
APP
PAY
CORE
MOB
```

The prefix should be stable and should not encode team, release, status, or priority.

## Step 2: Choose a First Conformance Target

Recommended starting points:

- **L1:** Assign stable IDs to existing lifecycle records.
- **L2:** Add explicit relationships between a small number of records.

See [../spec/conformance.md](../spec/conformance.md) for the level expectations, diagnostics, validation guidance, and claim language.

Avoid starting at L5 unless the repo already has strong requirements, test, evidence, and CI discipline.

A first claim can be narrow. For example, a team can target `OLTS L1` for one reviewed path or `OLTS L2` for one release branch without migrating every tracker, requirement, test plan, or evidence source.

## Step 3: Inventory Current Sources

Find existing lifecycle material:

- roadmaps;
- issue trackers;
- requirements documents;
- use cases or user stories;
- ADRs;
- test plans;
- CI workflows;
- release checklists;
- evidence folders;
- diagrams and design docs;
- pull request templates.

Record what exists and where it lives. Do not move everything on day one.

## Step 4: Add Minimal OLTS Files

A conservative repo-native layout is:

```text
docs/olts/
  README.md
  records/
    requirements.yaml
  links/
    relationships.csv
```

Small projects may start with one YAML file and one relationship file. Larger projects may split by entity type.

## Step 5: Assign Stable IDs

Use the candidate shape:

```text
<DOMAIN>-<TYPE>-<NNNNN>
```

Examples:

```text
APP-UC-00001
APP-SR-00001
APP-VT-00001
APP-EVD-00001
```

Do not reuse IDs. Deprecated or retired records should keep their IDs and carry status.

## Step 6: Add Explicit Relationships

Start with one or two high-value chains:

```text
Use Case -> Requirement
Requirement -> Verification Test
Verification Test -> Evidence
```

Example relationship file:

```csv
Source_Key,Target_Key,Relationship,Notes
APP-UC-00003,APP-SR-00014,requires,Use case depends on requirement
APP-SR-00014,APP-VT-00221,verified_by,Requirement is verified by test
APP-VT-00221,APP-EVD-00098,evidenced_by,Test run has evidence record
```

## Step 7: Preserve Source Truth

OLTS files should not silently override product truth. If the adopting repo already has authoritative requirements, tests, issues, or release records, decide whether OLTS records are source truth, a reviewed index over existing truth, a migration bridge, or generated derived state.

State that decision in `docs/olts/README.md`.

## Step 8: Add Diagnostics Before Gates

Early adoption should report gaps before blocking merges. Useful first diagnostics:

- invalid ID shape;
- duplicate ID;
- missing relationship target;
- unknown relationship type;
- missing verification link;
- missing evidence link.

Once the team trusts the diagnostics, selected checks can become CI gates.

## Step 9: Review Through Pull Requests

OLTS adoption should land through normal review:

```text
branch -> pull request -> review -> merge
```

Do not mass-edit requirements, tests, or evidence without a focused review plan.

## Step 10: Publish the Adoption Claim

Once the team has reviewed the first adoption slice, document the claim with its level, scope, source files, and any reviewed exceptions:

```text
This repository is experimenting with OLTS L1.
```

or:

```text
This repository maintains explicit OLTS L2 relationship files for selected requirements and tests.
```

Before OLTS publishes a stable certification or trademark policy, conformance claims should be phrased as scoped adoption targets or experiments. Avoid certification-style claims until a policy defines who can make those claims and what evidence is required.

Every claim should name its scope. A scope might be a repository, release branch, product area, source path, or selected record set. Do not imply that an OLTS claim covers records outside the stated scope.

Examples:

```text
This repository is experimenting with OLTS L1 for lifecycle records under docs/olts/records/.
This release branch maintains an OLTS L2 relationship set for selected authentication requirements.
This product area targets OLTS L3 for active release-scope requirements, with reviewed exceptions listed in the OLTS adoption notes.
```

If automation is part of the claim evidence, also state whether the result is advisory or blocking. A warning or error diagnostic should remain reviewable and should not be hidden behind a summary such as `OLTS passed`.

## Recommended First Pull Request

The first OLTS PR should usually include:

- `docs/olts/README.md` explaining source truth and scope;
- one minimal record file;
- one minimal relationship file;
- a known-gaps section;
- a scoped statement of the target conformance level.

## Stop Gates

Pause adoption and ask for human review if:

- canonical requirements would need to be rewritten;
- test evidence is ambiguous;
- IDs conflict across teams or repositories;
- automation proposes deleting or replacing lifecycle truth;
- generated artifacts are being treated as source truth;
- compliance claims would be made without evidence.
