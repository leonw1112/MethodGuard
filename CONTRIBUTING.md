# Contributing to MethodGuard

MethodGuard is currently in the v0.1 planning phase. Contributions should remain aligned with the defined first-release scope.

## Before contributing

- read the [v0.1 roadmap](ROADMAP.md);
- keep analysis read-only and deterministic;
- do not add cloud, web UI, AI, database, or instrument-control features to v0.1;
- do not commit proprietary Hamilton files, production laboratory data, credentials, or patient information;
- use synthetic and non-sensitive fixtures only.

## Planned development workflow

1. Open an issue describing the behavior or rule.
2. Keep changes small and independently testable.
3. Add synthetic fixtures for parser behavior.
4. Add tests for successful and failing cases.
5. Document assumptions about vendor-specific formats.
6. Link diagnostics to stable MethodGuard rule IDs.

## Diagnostic design

Every diagnostic should eventually include:

- a stable rule ID;
- a concise title;
- a clear explanation;
- the relevant source location when known;
- evidence supporting the finding;
- a practical remediation hint.

## Scope

Ideas beyond v0.1 are welcome as discussion, but should not expand the first release until the core project scanner and dependency analysis are proven.
