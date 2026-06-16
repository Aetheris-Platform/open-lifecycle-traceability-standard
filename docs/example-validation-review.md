# OLTS Example Validation Review

This review records the documented equivalent checks used to validate the minimal and realistic examples for `v1.0.0` readiness.

It is launch-readiness evidence, not a release announcement. OLTS remains a private `v1.0.0` release candidate until maintainers explicitly approve public visibility, the `v1.0.0` tag, and the GitHub Release.

## Review Scope

Reviewed example files:

- [../examples/minimal/records.yaml](../examples/minimal/records.yaml)
- [../examples/minimal/relationships.csv](../examples/minimal/relationships.csv)
- [../examples/realistic/records.yaml](../examples/realistic/records.yaml)
- [../examples/realistic/relationships.csv](../examples/realistic/relationships.csv)

Reviewed validation guidance:

- [schema-validation.md](schema-validation.md)
- [schema-contract-review.md](schema-contract-review.md)
- [../schemas/olts-record.schema.json](../schemas/olts-record.schema.json)
- [../schemas/olts-relationship.schema.json](../schemas/olts-relationship.schema.json)

## Documented Equivalent Checks

These checks are equivalent to the schema-shape and semantic checks documented in [schema-validation.md](schema-validation.md):

1. Parse every example record file as YAML.
2. Treat each YAML list item, or a single YAML mapping when used, as one lifecycle record.
3. Confirm each record has `id`, `type`, and non-empty `title`.
4. Confirm each `id` follows `<DOMAIN>-<TYPE>-<NNNNN>`.
5. Confirm each `type` matches the `<TYPE>` segment in `id`.
6. Parse each relationship CSV file with one object per row.
7. Confirm each relationship row has `Source_Key`, `Target_Key`, and `Relationship`.
8. Confirm each relationship verb is in the core OLTS relationship vocabulary.
9. Confirm each OLTS relationship source and target resolves to a record in the same example.
10. Allow documented external references, such as `openspec:passwordless-sign-in`, as relationship targets.
11. Confirm evidence attaches through validation, verification, or artifact records rather than as unexplained direct proof for a requirement.

These checks do not create an `OLTS L5` claim and do not require OLTS reference tooling.

## Minimal Example Result

The minimal example passes the documented equivalent checks:

- all five records parse from [../examples/minimal/records.yaml](../examples/minimal/records.yaml);
- each record has `id`, `type`, and `title`;
- each `id` follows the OLTS identifier shape;
- each `type` matches the ID type segment;
- all four rows in [../examples/minimal/relationships.csv](../examples/minimal/relationships.csv) parse with required relationship fields;
- all relationship verbs are core OLTS verbs;
- every OLTS relationship source and target resolves to a record in the minimal example.

The minimal example is a compact record-and-relationship validation case, not a full product traceability matrix.

## Realistic Example Result

The realistic example passes the documented equivalent checks:

- all records parse from [../examples/realistic/records.yaml](../examples/realistic/records.yaml);
- each record has `id`, `type`, and `title`;
- each `id` follows the OLTS identifier shape;
- each `type` matches the ID type segment;
- all rows in [../examples/realistic/relationships.csv](../examples/realistic/relationships.csv) parse with required relationship fields;
- all relationship verbs are core OLTS verbs;
- each OLTS relationship source and target resolves to a record in the realistic example;
- the external `openspec:passwordless-sign-in` target is shaped as a documented external reference;
- the `documented_by` relationship points from the requirement to the design artifact;
- evidence attaches to validation, verification, or artifact records.

The realistic example remains a scoped `OLTS L4` example. It does not claim `L5` because the repository does not include an automated conformance checker or generated conformance report.

## Stability Decision

The examples are suitable as reference examples for `v1.0.0` readiness when paired with the documented equivalent checks above.

Future changes to example IDs, entity types, relationship directions, evidence attachment, or external-reference handling should re-run or update this review before the examples are used as public launch evidence.
