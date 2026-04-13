# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Slangfy is an **AI plugin / mode** for Claude and other LLMs. Developers write naturally; the AI responds in compressed Slangfy syntax. The compression happens on the **AI output side only** — developers never need to learn the syntax, but the AI's responses are token-efficient and still fully readable. The project is documentation-only (no build process, no dependencies, no executable code).

## Repository Structure

This is a three-file specification project:

- **`slangfy.md`** — The core protocol: system instructions, syntax, operators, dictionary (shorthands), and rules. This is the artifact users paste into their LLM system prompts or custom instructions.
- **`SKILL.md`** — A Claude-specific skill wrapper that enables `/slangfy-on` and `/slangfy-off` commands.
- **`README.md`** — User-facing overview and integration guide.

## The Protocol

**Syntax:**
```
status: [ok|warn|err] | task @ context | action: [what_you_did] | out: [result] | ! [optional_warning]
```

**Operators:** `|` (separator), `@` (scope/target), `->` (transformation), `+` (addition), `!` (critical alert)

**Shorthands:** `fn` (function), `db` (database), `perf` (performance), `auth` (authentication), `docs` (documentation), `refac` (refactor), `env` (environment), `comp` (component)

**Rules:** No politeness markers. No markdown headers unless requested in `out:`. Use `diff` for code changes. Translate user input into protocol syntax.

## Integration

Users add `slangfy.md` content to their LLM system prompt, custom instructions, or project knowledge. The Skill (`SKILL.md`) is the Claude-specific implementation of the same concept.

## Contributing

Community contributions are welcome via Issues or PRs. Priority areas:
- New shorthands for specific domains (Data Science, DevOps, Legal)
- Token usage benchmarks
- CLI tool integrations
