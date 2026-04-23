# Codex Explanatory Output Style Skill

English | **[中文](README.zh-TW.md)**

## Introduction

`explanatory-output-style` is an OpenAI Codex skill that adds brief educational guidance to coding sessions. When the skill is active, it encourages the agent to explain concrete implementation choices, local design patterns, tradeoffs, and repository-specific details while still completing the requested task.

The skill is designed for users who want coding help and practical teaching at the same time. It adds short `★ Insight` blocks before and after coding work so the session stays action-oriented while still exposing the reasoning behind the implementation.

## Features

- Adds a short educational `★ Insight` block before coding starts.
- Adds a second `★ Insight` block after coding ends.
- Focuses the explanation on concrete implementation approaches instead of generic programming theory.
- Explains design patterns and local code conventions when they are relevant to the change.
- Highlights tradeoffs, design decisions, and the reasons one approach fits the repository better than others.
- Prioritizes repository-specific observations such as existing abstractions, naming conventions, module boundaries, state flow, and test style.
- Enables implicit invocation through `agents/openai.yaml` so the skill can participate in session setup automatically.

## Format Example

The skill uses the following `★ Insight` format:

```markdown
`★ Insight ──────────────────────────────────────`
- [Educational point about the implementation approach]
- [Educational point about the design pattern, tradeoff, or codebase detail]
`─────────────────────────────────────────────────`
```

## Installation

Install the repository as a Codex skill directory named `explanatory-output-style`.

### Project-scope installation

Copy this repository into:

```text
.codex/skills/explanatory-output-style/
```

The resulting structure should include:

```text
.codex/skills/explanatory-output-style/
  SKILL.md
  agents/openai.yaml
```

### User-scope installation

Copy this repository into:

```text
${CODEX_HOME}/skills/explanatory-output-style/
```

If `CODEX_HOME` is not set, use:

```text
~/.codex/skills/explanatory-output-style/
```

### Final step

Restart Codex after copying the files so the skill can be discovered in new sessions.
