# Agents

Reusable, personal tooling for AI coding agents. This repository currently
contains OpenCode skills for researching unfamiliar software architecture before
implementation. It deliberately does not contain application-specific
architecture, credentials, security policy, or OpenCode's whole user
configuration.

## Contents

| Skill | Use it for |
| --- | --- |
| `architecture-theory-research` | Established concepts, guarantees, terminology, and trade-offs. Stops before implementation design. |
| `implementation-research` | Credible real-world implementations, ecosystem conventions, and recurring code patterns. |
| `architecture-research` | Questions that need local context plus theory and/or implementation evidence, followed by a bounded recommendation. |

The skills are composable. `architecture-research` classifies the question and
uses the focused research modes only when they add value; either focused skill
can also be invoked directly (for example, `@implementation-research`).

## Install and discover

OpenCode v2 discovers directory-based skills from an external directory listed
in its `skills` configuration. Clone this repository at a stable path in each
execution environment, then let the dotfiles repository own the corresponding
global OpenCode configuration.

Example future dotfiles-managed `~/.config/opencode/opencode.jsonc` addition:

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "skills": ["~/.local/share/agents/skills"],
}
```

`skills` entries are additive in OpenCode v2, so retain any existing entries.
The path is resolved in the environment where OpenCode runs.

### Docker Sandbox and other persistent environments

A sandbox does not automatically have the host filesystem. Bootstrap the same
Git checkout inside each persistent environment at a predictable path, such as
`/opt/agents`, and configure that environment's OpenCode with:

```jsonc
{
  "skills": ["/opt/agents/skills"],
}
```

Update the checkout through Git as part of that environment's normal bootstrap
or maintenance process. Network policy, credentials, MCP configuration, and
permission/security policy remain outside this repository and outside an
application checkout.

## Invocation

Ask normally when the skill description is an obvious match, or explicitly use
`@architecture-research`, `@architecture-theory-research`, or
`@implementation-research`. Give the question, relevant constraints, and the
desired depth. The skills inspect only decision-relevant project-local context
and, unless asked otherwise, report findings and recommendations without
changing application code.

## Research tools

The skills use available capabilities rather than requiring a particular MCP
server. Context7 is useful for current official, version-specific documentation;
grep.app or equivalent code search is useful for finding public implementations.
Both remain ordinary tools that can be used independently. Missing tools reduce
available evidence but do not invalidate the workflow.

## Validation

Each skill is a directory containing a `SKILL.md` file with OpenCode v2
frontmatter. After adding this checkout to `skills`, restart/reload OpenCode if
needed and verify the three IDs appear among available skills. Skill IDs derive
from the directory names, not their display names.
