# AI Agent Adoption Prompt

Use this prompt with an AI coding agent to produce a first OLTS adoption plan or, when explicitly authorized, a pull request for an existing repository.

Before using it, decide whether the agent may edit files directly or should only produce a plan. If edits are allowed, state that authorization inside the prompt you send to the agent.

## Copy/Paste Prompt

```text
You are helping adopt the Open Lifecycle Traceability Standard (OLTS) in this repository.

Default to plan-only. Do not create, edit, or delete any files unless the maintainer explicitly authorizes edits in this prompt.

Authorization mode:
- If this prompt does not include an explicit "Edits authorized" statement from the maintainer, produce a plan only.
- If edits are authorized, make the smallest useful change on a branch and preserve normal human review.
- Never treat the ability to edit files as permission to rewrite source truth, delete lifecycle records, or bypass review.

Goal:
Create a conservative first OLTS adoption slice that makes lifecycle traceability more explicit without rewriting product truth or inventing relationships.

Context:
OLTS is an early draft. Product repository files, issue trackers, tests, evidence, ADRs, and release records remain source truth. OLTS records and relationship files should make existing lifecycle meaning explicit and reviewable.

Primary objectives:
1. Inspect the repository for lifecycle sources:
   - roadmap or planning docs;
   - requirements;
   - use cases or user stories;
   - issue or tracker references;
   - ADRs or decision records;
   - tests and validation scenarios;
   - evidence or release records;
   - diagrams and artifacts;
   - CI/CD workflows;
   - PR or issue templates.
2. Recommend an initial OLTS conformance target, usually L1 or L2.
3. Propose a stable domain prefix for IDs, or ask the maintainer to choose one if unclear.
4. Create or propose a minimal repo-native OLTS layout, such as:
   docs/olts/README.md
   docs/olts/records/requirements.yaml
   docs/olts/links/relationships.csv
5. Add only a small representative sample unless the maintainer explicitly asks for broad migration.
6. Mark uncertain links as candidates or diagnostics, not source truth.
7. Preserve normal review: branch, diff, pull request, human approval.

Hard constraints:
- Do not silently mutate canonical requirements, tests, evidence, or release records.
- Do not infer canonical relationships from fuzzy text similarity, row order, filenames, or AI confidence alone.
- Do not delete, rename, or replace existing lifecycle records unless explicitly requested.
- Do not claim compliance or verification coverage unless evidence is explicit.
- Do not treat generated diagrams, dashboards, or reports as source truth.
- Do not introduce a database, hosted service, or mandatory tool unless requested.
- Do not present generated or proposed OLTS records as accepted source truth until they are reviewed.
- Do not make broad migration changes unless the maintainer explicitly requests that scope.

Expected output:
1. A short repository inventory.
2. Recommended OLTS conformance target.
3. Proposed domain prefix and identifier strategy.
4. Proposed file layout.
5. A small sample of OLTS records and relationships.
6. Known gaps and diagnostics.
7. A review plan for the first PR.
8. If and only if edits are explicitly authorized, create the minimal files and summarize the diff.

Suggested first PR contents:
- docs/olts/README.md explaining source truth, scope, and adoption level;
- one minimal record file;
- one minimal relationship file;
- a known-gaps section;
- PR checklist updates if appropriate.

When in doubt, stop and ask for maintainer review rather than guessing.
```

## Optional Authorization Template

Maintainers can paste one of these lines into the prompt:

```text
Authorization: Plan only. Do not create, edit, delete, stage, commit, push, or open a pull request.
```

```text
Authorization: Edits authorized for a minimal OLTS adoption slice. Use a branch, keep the diff small, and do not rewrite canonical lifecycle truth.
```

## Optional Maintainer Answers

Before running the prompt, maintainers can provide:

- preferred domain prefix;
- desired first conformance target;
- source-of-truth files;
- paths the agent must not edit;
- whether the agent may edit files, create a branch, commit, push, or open a pull request;
- whether OpenSpec, Jira, GitHub Issues, GitLab Issues, or Azure Boards is the change-provenance source.

## Review Checklist for AI-Generated OLTS Changes

- [ ] IDs are stable and do not encode status, priority, release, or owner.
- [ ] Relationships are explicit and reviewable.
- [ ] Candidate or uncertain links are not presented as accepted truth.
- [ ] Source truth boundaries are documented.
- [ ] Generated files are not treated as canonical unless accepted by review.
- [ ] The first adoption scope is small enough to review.
- [ ] Diagnostics and gaps are visible.
