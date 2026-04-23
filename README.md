# Codex Explanatory Output Style Skill

English | **[中文](README.zh-TW.md)**

## Introduction

`explanatory-output-style` is an OpenAI Codex skill package that recreates Claude's explanatory output style as closely as Codex skills allow. When the skill is active, Codex keeps working toward the user's coding task while adding brief educational context about implementation choices, local patterns, tradeoffs, and repository-specific details.

The package is distributed as the `explanatory-output-style/` directory in this repository. Copy that directory into your Codex skills path and use it as the installed skill.

The reference source for this skill is Anthropic's official Claude plugin:
`https://github.com/anthropics/claude-plugins-official/tree/main/plugins/explanatory-output-style`

## Behavior

- Treats explanatory guidance as a session-wide response mode for the current coding task.
- Adds a short `★ Insight` block immediately before meaningful code-writing work.
- Adds a matching `★ Insight` block immediately after meaningful code-writing work.
- Adds another pair of `★ Insight` blocks when the task moves into a new substantial coding phase.
- Keeps the educational content concrete and tied to the active files, modules, data flow, tests, and failure modes.
- Keeps the insights in the conversation rather than writing them into source files.
- Allows implicit invocation through `explanatory-output-style/agents/openai.yaml`.

## Insight Format

The skill uses the following `★ Insight` wrapper:

```markdown
`★ Insight ──────────────────────────────────────`
[2-3 key educational points]
`─────────────────────────────────────────────────`
```

The points are intended to emphasize:

- The concrete implementation approach chosen for the task.
- The local pattern or convention used by the repository.
- The tradeoff or design decision behind the change.
- The repository-specific detail that helps the user understand why the implementation fits.

## Trigger Examples

Typical natural-language requests that should help Codex choose this skill include:

- `use explanatory mode`
- `use explanatory output style`
- `explain as you code`
- `teach while coding`
- `walk me through your implementation choices`

## Installation

Copy the `explanatory-output-style/` directory from this repository into one of the following locations:

```text
${CWD}/.codex/skills/explanatory-output-style/
${CODEX_HOME}/skills/explanatory-output-style/
```

The installed directory should contain:

```text
explanatory-output-style/
  SKILL.md
  agents/
    openai.yaml
```

Restart Codex after copying the directory so the skill is discovered in a new session.
