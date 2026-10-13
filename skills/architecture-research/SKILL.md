---
name: Architecture Research
description: Investigate an unfamiliar architecture decision using local context, disciplined theory and implementation research, then present bounded options before implementation.
---

# Architecture research

Use this skill for a decision that may need both established architectural
concepts and evidence from real implementations. It orchestrates focused
research, but remains a research workflow—not an implementation instruction.

## Non-negotiable boundaries

- Understand the relevant local repository before external research.
- Do not modify application source, migrations, or configuration unless the
  user explicitly asks to leave the research phase.
- Do not assume a named pattern is the right answer. Establish the required
  semantics first.
- Keep fact, observation, inference, local constraint, and recommendation
  visibly distinct.

## Workflow

1. **Frame and classify.** Restate the decision, desired outcome, scope, and
   uncertainties. Classify it as:
   - **A — conceptual:** guarantees, semantics, or pattern trade-offs. Run
     `architecture-theory-research`; implementation research is optional.
   - **B — ecosystem/implementation convention:** code organization, framework
     practice, or library usage. Run `implementation-research`; theory may be
     unnecessary.
   - **C — mixed:** both semantics and implementation choices matter. Use local
     context → theory research → implementation research → synthesis.
   If the focused skills are available, load them for their detailed workflow.
2. **Establish local context.** Read only what bears on the decision: `AGENTS.md`,
   glossary/domain material, ADRs and architecture docs, relevant source and
   tests, persistence model and transaction boundaries, dependency versions,
   interfaces, and local conventions. State the constraints found and gaps that
   remain.
3. **Research in the classified order.** Keep theory evidence and implementation
   observations separate. Prefer authoritative sources for concepts and credible,
   independent, well-tested codebases for implementation patterns. Use available
   documentation and public-code tools without requiring a particular MCP.
4. **Synthesize into genuine alternatives.** Extract pattern families and reject
   false choices or alternatives that do not meet required semantics. For each
   viable option, explain scope, guarantees, advantages, disadvantages, failure
   modes, operational implications, and project fit.
5. **Recommend and stop.** Give a bounded recommendation with explicit
   assumptions and unresolved questions. Stop for a human architectural decision
   before an implementation plan or code, unless the user expressly requests
   the next phase.

## Evidence labels

- **Established** — authoritative direct support.
- **Observed** — verified in one or more real implementations.
- **Inferred** — synthesis from evidence; explain why.
- **Project-specific** — derived from inspected local context.
- **Recommendation** — the proposed direction.

An observed repository pattern is not an established rule. Local constraints do
not disappear because external research suggests a different default.

## Output

Keep trivial questions brief. For a material decision, structure the response
as:

1. Problem and local constraints
2. Relevant established concepts and semantic distinctions
3. Real-world implementation families
4. Option A / B / C, with guarantees, trade-offs, and project fit
5. Recommendation and why it fits this repository
6. Remaining questions or uncertainties
7. Sources

For example, research into idempotency must distinguish, where relevant,
operation deduplication, HTTP response replay, and asynchronous-consumer
deduplication before recommending storage, keys, transactions, or expiry rules.
