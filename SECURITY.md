# Security Policy

OLTS is a standard and documentation repository. It does not currently ship production runtime software.

## Reporting Security Issues

If you find a security issue in OLTS reference material, examples, schemas, or future tooling, please open a private security advisory if available or contact the maintainers through the repository owner.

Do not disclose sensitive vulnerabilities publicly until maintainers have had a reasonable opportunity to respond.

## Scope

Security-relevant issues may include:

- unsafe example automation;
- guidance that would encourage leaking secrets or evidence;
- tooling behavior that mutates source truth without review;
- generated artifact guidance that could expose private data;
- CI/CD examples that weaken branch, PR, or release controls.

## Non-Scope

OLTS does not provide security guarantees for adopting repositories. Adopters are responsible for their own access control, CI/CD security, evidence handling, privacy review, and compliance obligations.

## Safe Automation Principle

Automation may diagnose, visualize, and propose changes. It must not silently rewrite canonical lifecycle truth, evidence, requirements, or release records.
