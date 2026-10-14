---
name: implementation-research
description: Research credible real-world codebases to extract implementation patterns and ecosystem conventions without copying code blindly.
---

# Implementation research

Use this skill to learn how credible systems implement a problem in a relevant
language, framework, or data stack. It complements, but does not substitute
for, conceptual architecture research.

## Boundaries

- Understand relevant project-local constraints before searching externally.
- Seek recurring patterns, not snippets to transplant.
- Do not treat stars, popularity, or repetition on GitHub as proof of quality
  or idiomatic practice.
- Do not modify application code unless explicitly asked.

## Workflow

1. **Frame the investigation.** Capture the language, framework and version,
   persistence and deployment model, required semantics, and the question to
   answer. Identify the local packages/interfaces/transaction boundaries that
   affect fit.
2. **Read decision-relevant local context.** Inspect `AGENTS.md`, domain and
   architecture material, ADRs, source, tests, schemas/migrations, dependency
   versions, and established conventions as needed. Do not exhaustively scan
   the repository.
3. **Find credible independent examples.** Prefer maintained libraries,
   framework repositories, established production organizations, and projects
   with substantive tests, history, documentation, multiple contributors, and
   stack similarity. Search source, interfaces, migrations, tests, and docs.
   Use available public-code search or documentation tools; do not depend on a
   specific MCP server.
4. **Evaluate the evidence.** Note why each example is credible and its limits.
   Inspect failure and concurrency behavior where relevant, rather than only a
   happy-path file. Compare several independent implementations when practical.
5. **Extract implementation families.** Describe recurring mechanisms,
   invariants, boundaries, and meaningful differences. Label a pattern
   **Observed** unless stronger evidence establishes it as a documented
   convention. Call out one-off approaches rather than silently generalizing
   them.
6. **Relate findings to this project when requested.** Identify fit and
   incompatibilities with local constraints, while keeping a proposed direction
   distinct from observation.

## Go focus

For Go, explicitly consider simple and idiomatic package ownership, interface
necessity, standard-library use, errors, transaction boundaries, database
constraints, concurrency, cancellation, and test strategy. Frequency alone
does not establish idiomatic Go.

## Evidence labels

- **Observed** — verified in named implementation(s).
- **Inferred** — synthesis from examples, with rationale.
- **Project-specific** — conclusion from local context.
- **Recommendation** — proposed action; not evidence.

## Output

For substantial research, provide:

1. Problem and local constraints
2. Sources evaluated and credibility notes
3. Real-world implementation families
4. Important differences, including tests/failure behavior where relevant
5. Project fit and bounded options, if requested
6. Remaining uncertainties and source links

Quote or summarize only what is necessary to support the pattern; do not copy
large code blocks or conceal uncertainty behind a generic abstraction.
