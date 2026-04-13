# Slangfy — AI Slang Mode

> **Status:** Alpha | **Goal:** Token Efficiency | **Type:** AI Plugin / Protocol

Slangfy is an open-source plugin for Claude and other LLMs. It enables a **one-way compression mode**: you write naturally, the AI responds in compact Slangfy syntax — reducing output tokens while staying fully readable to developers.

## How it works

**You write normally:**
> "Can you check if there is a memory leak in my database connection?"

**AI responds in Slangfy:**
```
status: warn | mem_leak @ db_conn | action: ctx_manager_fix | out: [code_diff]
```

The compression is on the **AI output side only** — you never need to learn the syntax.

## Install

All CLI integrations live in the `integrations/` folder. Pick your tool:

### Claude Code

```bash
mkdir -p ~/.claude/skills/slangfy-on ~/.claude/skills/slangfy-off
cp integrations/claude-code/.claude/skills/slangfy-on/SKILL.md ~/.claude/skills/slangfy-on/SKILL.md
cp integrations/claude-code/.claude/skills/slangfy-off/SKILL.md ~/.claude/skills/slangfy-off/SKILL.md
```

Then use it in any project:
```
/slangfy-on   — enable Slangfy mode
/slangfy-off  — return to normal
```

See `integrations/claude-code/install.md` for project-level install.

### Gemini CLI

```bash
cp integrations/gemini-cli/GEMINI.md ./GEMINI.md
```

Gemini CLI loads `GEMINI.md` automatically on session start.

### Aider

```bash
aider --system-prompt slangfy.md
```

See `integrations/aider/install.md` for config file options.

### OpenCode

```bash
mkdir -p .opencode && cp slangfy.md .opencode/instructions.md
```

See `integrations/opencode/install.md` for global install.

### Other LLMs (ChatGPT, Gemini web, etc.)

Paste the contents of `slangfy.md` into your system prompt or custom instructions.

## Syntax reference

```
status: [ok|warn|err] | task @ context | action: [what_you_did] | out: [result] | ! [warning]
```

## How compression works

Slangfy uses **5 auto-compression rules** — no static dictionary to maintain:

| Rule | Description | Example |
|------|-------------|---------|
| 1. Universal abbreviations | Established industry standards always used | `k8s`, `CI`, `JWT`, `ORM` |
| 2. Compound terms | Multi-word concepts compressed to initials | `pull request → PR`, `load balancer → LB` |
| 3. Long word compression | Any tech term >6 chars shortened if unambiguous | `authentication → auth`, `deployment → deploy` |
| 4. Define-on-first-use | Unknown terms defined once, abbreviated after | `PostgreSQL (PG)` → `PG` |
| 5. Domain auto-detect | AI detects context, applies domain conventions | DevOps: `pod`, `ns`, `helm` / ML: `feat`, `epoch` |

**Covered domains:** Frontend · Backend · DevOps · Data/ML · Security · Mobile

## Contributing

Community-driven protocol. We want:
- New compression rules or domain patterns
- Benchmarks comparing token usage before/after
- Integrations with other CLI tools

Open an Issue or PR!
