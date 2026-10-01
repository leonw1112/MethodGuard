# Architecture

This document describes the intended v0.1 architecture. No implementation exists yet.

## Processing pipeline

1. **Discovery** scans a project directory and identifies supported artifacts.
2. **Parsing** extracts methods, HSL references, variables, paths, and relationships.
3. **Normalization** converts vendor-specific data into the MethodGuard intermediate representation.
4. **Analysis** evaluates the normalized model using independent rules.
5. **Reporting** renders findings for people, CI systems, and graph tools.

## Component boundaries

### Core model

The intermediate representation contains vendor-neutral project concepts:

- project;
- method;
- dependency;
- source location;
- finding;
- rule identifier.

It must not depend on Hamilton-specific parser classes.

### VENUS adapter

The initial adapter owns all Hamilton VENUS discovery and parsing assumptions. It translates observed project artifacts into the core model and retains source evidence for traceability.

Because vendor file formats may be undocumented or version-dependent, parsing behavior must be backed by synthetic fixtures and clearly documented assumptions.

### Analyzers

Analyzers consume only the normalized model. The first analyzers cover missing and circular dependencies. They must be deterministic and side-effect free.

### Reporters

Reporters transform findings without changing their meaning. Planned v0.1 outputs are:

- human-readable console output;
- machine-readable structured output;
- dependency graph export.

## Safety boundary

MethodGuard v0.1 is strictly read-only. It will not:

- execute laboratory methods;
- connect to or control instruments;
- rewrite source projects;
- claim that a project is validated or compliant.

## Architectural constraints

- vendor-specific code stays behind adapter boundaries;
- diagnostics retain source locations and supporting evidence;
- parsing and analysis can be tested without proprietary software;
- filesystem access is isolated from rule evaluation;
- output remains stable enough for CI use.
