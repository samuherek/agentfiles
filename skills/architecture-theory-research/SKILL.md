---
name: Architecture Theory Research
description: Research established architecture concepts, guarantees, failure modes, and trade-offs before implementation design.
---

# Architecture theory research

Use this skill for conceptual questions such as delivery guarantees, consistency
semantics, protocol behavior, or pattern trade-offs. Do not use it merely to
find code conventions; use `implementation-research` for that.

## Boundaries

- Investigate the question, not a preselected solution or buzzword.
- Read only enough project-local context to define the domain and constraints.
- Do not modify application code or produce an implementation plan unless the
  user explicitly asks to continue beyond research.
- A valid conclusion is that no useful general architecture literature exists
  and that the question is principally an ecosystem convention problem.

## Workflow

1. **Frame the question.** State the decision, desired semantics, scope, and
   unknowns. Separate terms that might be overloaded (for example, operation
   deduplication versus HTTP response replay).
2. **Inspect necessary local context.** Look first for `AGENTS.md`, glossary or
   domain documents, ADRs, architecture and API documents, and the relevant
   interfaces, persistence boundaries, dependencies, and versions. Do not read
   the whole repository. Record constraints that constrain the research.
3. **Classify the question.** Confirm that conceptual research is warranted. If
   it is mostly a framework or language convention, say so and direct the user
   to implementation research.
4. **Research authoritative evidence.** Prefer standards/specifications,
   primary documentation, canonical technical literature, relevant papers, and
   credible engineering publications. Use secondary writing only when stronger
   evidence is unavailable, and label it accordingly. Use current official
   documentation tools when version-specific behavior matters.
5. **Extract, do not merely cite.** Identify terminology, semantic distinctions,
   assumptions, guarantees, failure modes, and pattern families. Explain which
   claims are direct evidence and which are synthesis.
6. **Stop at decision support.** Present viable conceptual options and their
   trade-offs; do not choose classes, tables, APIs, or code structure unless
   explicitly requested.

## Evidence discipline

Label material clearly:

- **Established** — directly supported by an authoritative source.
- **Inferred** — reasoned synthesis across evidence; include the reasoning.
- **Project-specific** — derived from the inspected local context.
- **Recommendation** — the agent's proposed direction, not a fact.

Never elevate a vendor-specific convention, an implementation observation, or
an unsupported article into an established rule.

## Output

Scale the response to the question. For a substantial investigation, use:

1. Problem and local constraints
2. Relevant established concepts and semantic distinctions
3. Pattern families, guarantees, trade-offs, and failure modes
4. Implications or bounded options for this project (only if requested)
5. Remaining uncertainties
6. Sources, with enough detail to revisit each claim

Keep recommendation separate from evidence. If implementation examples would
materially reduce uncertainty, recommend or hand off to
`implementation-research` rather than inventing them.
