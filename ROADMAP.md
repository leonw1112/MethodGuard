# MethodGuard roadmap

## v0.1 objective

Prove that a Hamilton VENUS project can be scanned outside the vendor IDE and converted into a useful, deterministic dependency model.

## Definition of done

v0.1.0 is complete when MethodGuard can:

- accept a local VENUS project directory from the command line;
- discover supported project artifacts recursively;
- represent methods and dependencies in a typed intermediate model;
- build a directed dependency graph;
- detect and report `MG001 Missing Dependency`;
- detect and report `MG002 Circular Dependency`;
- return documented process exit codes;
- run against synthetic test fixtures without requiring VENUS;
- produce human-readable console output;
- export machine-readable analysis results;
- document known parser limitations.

## Milestones

### 0.1.0-alpha.1 — Project discovery

- define supported file types and discovery rules;
- implement recursive, read-only project scanning;
- normalize relative and absolute paths;
- add the first synthetic project fixtures.

### 0.1.0-alpha.2 — Intermediate representation

- define project, method, dependency, and source-location models;
- preserve evidence for every discovered relationship;
- serialize the intermediate representation for debugging.

### 0.1.0-alpha.3 — Dependency analysis

- build the directed dependency graph;
- implement `MG001`;
- implement `MG002`;
- test missing, duplicate, and cyclic references.

### 0.1.0-beta.1 — CLI and reports

- expose analysis through the CLI;
- define stable exit-code behavior;
- add readable console diagnostics;
- add machine-readable output;
- add graph export.

### 0.1.0 — First usable release

- document installation and supported VENUS artifacts;
- document limitations and non-goals;
- verify all fixtures and rule examples;
- publish the first tagged release.

## After v0.1

Possible later work includes richer semantic checks, configurable policies, additional report formats, CI integrations, and support for other laboratory automation platforms. These are not commitments for v0.1.
