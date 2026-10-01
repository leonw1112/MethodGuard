# MethodGuard

**Static analysis and CI for laboratory automation methods.**

MethodGuard is an early-stage developer tool for inspecting, understanding, and validating laboratory automation methods before they reach an instrument.

The first target is **Hamilton VENUS**. The long-term goal is a vendor-independent analysis platform for laboratory automation projects.

> [!IMPORTANT]
> MethodGuard is currently in the **v0.1 planning phase**. There is no functional implementation yet.

## Why MethodGuard?

Laboratory automation methods can grow into complex networks of submethods, scripts, libraries, paths, and instrument-specific dependencies. Failures are often discovered late: during manual review, deployment, or directly on an instrument.

MethodGuard aims to bring familiar software-engineering safeguards to laboratory automation:

- inspect projects without opening the vendor IDE;
- reveal method and dependency relationships;
- detect broken or unsafe project structures early;
- make automated checks available to CI pipelines;
- produce understandable reports for developers and regulated laboratories.

## v0.1 scope

The first release will focus on a small, verifiable core:

- scan a Hamilton VENUS project directory;
- discover method files, submethods, HSL files, variables, and referenced paths;
- normalize discovered information into a MethodGuard intermediate representation;
- build method-call and dependency graphs;
- report missing dependencies;
- report circular dependencies;
- provide a clear command-line report;
- export graph data for further visualization.

### Initial rules

| Rule | Meaning |
| --- | --- |
| `MG001` | Referenced dependency is missing |
| `MG002` | Circular dependency detected |

## Explicitly out of scope for v0.1

To keep the first release focused, v0.1 will not include:

- a web interface;
- AI-assisted analysis;
- cloud services;
- a database;
- React or FastAPI;
- automatic modification of laboratory methods;
- instrument execution or control.

## Planned architecture

```text
src/methodguard/
├── cli.py
├── project.py
├── ir/
│   ├── project.py
│   ├── method.py
│   └── dependency.py
├── parsers/
│   └── venus/
│       ├── scanner.py
│       ├── method_parser.py
│       └── hsl_parser.py
├── analyzers/
│   ├── dependencies.py
│   └── cycles.py
└── reporters/
    ├── console.py
    └── graphviz.py

tests/
├── fixtures/
│   ├── simple_project/
│   ├── broken_dependency/
│   └── cyclic_dependency/
└── test_dependencies.py
```

This structure is a plan, not an implemented API contract.

## Planned technology

- Python
- Pydantic
- Typer
- Rich
- NetworkX
- pytest

## Design principles

1. **Read-only by default** — analysis must not modify source projects.
2. **Deterministic results** — the same input must produce the same findings.
3. **Explainable diagnostics** — every finding needs a rule ID, location, and reason.
4. **Vendor isolation** — vendor-specific parsing stays separate from the core model.
5. **CI-friendly behavior** — structured output and meaningful exit codes are first-class requirements.
6. **No laboratory claims without evidence** — MethodGuard supports engineering review; it does not replace validation or regulatory processes.

## Documentation

- [v0.1 roadmap](ROADMAP.md)
- [Architecture](docs/architecture.md)
- [Contributing](CONTRIBUTING.md)
- [Security policy](SECURITY.md)

## Status

MethodGuard is at the project-definition stage. Interfaces, file-format assumptions, and rule behavior may change before v0.1.0.

## License

Licensed under the [Apache License 2.0](LICENSE).
