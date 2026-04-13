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

---

## Quick activation

No CLI? Paste this directly into any chat (ChatGPT, Claude, Gemini, etc.):

```
From now on, respond using Slangfy protocol:
status: [ok|warn|err] | task @ context | action: [...] | out: [...] | ! [warning]
Compress all tech terms. No politeness. No markdown headers unless inside out:.
Shorten any term >6 chars to its common abbreviation. Define-on-first-use for unknown terms.
```

---

## Benchmark

Real test — same question, same model (Claude Sonnet via claude.ai), word count measured manually:

| Prompt | Without Slangfy | With Slangfy | Reduction |
|--------|----------------|--------------|-----------|
| "How do I set up JWT authentication in a Node.js REST API?" | 449 words · 3,632 chars | 323 words · 2,406 chars | **~28% fewer words / ~34% fewer chars** |

> Results vary by question and domain. Got your own numbers? Open a PR and add them.

---

## Install

All CLI integrations live in the `integrations/` folder. Pick your tool:

### Claude Code

```bash
mkdir -p ~/.claude/skills/slangfy-on ~/.claude/skills/slangfy-off
cp integrations/claude-code/.claude/skills/slangfy-on/SKILL.md ~/.claude/skills/slangfy-on/SKILL.md
cp integrations/claude-code/.claude/skills/slangfy-off/SKILL.md ~/.claude/skills/slangfy-off/SKILL.md
```

Then toggle in any project:
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

---

## Syntax reference

```
status: [ok|warn|err] | task @ context | action: [what_you_did] | out: [result] | ! [warning]
```

## How compression works

Slangfy uses **6 auto-compression rules** — no static dictionary to maintain:

| Rule | Description | Example |
|------|-------------|---------|
| 1. Universal abbreviations | Established industry standards always used | `k8s`, `CI`, `JWT`, `ORM` |
| 2. Compound terms | Multi-word concepts compressed to initials | `pull request → PR`, `load balancer → LB` |
| 3. Long word compression | Any tech term >6 chars shortened if unambiguous | `authentication → auth`, `deployment → deploy` |
| 4. Define-on-first-use | Unknown terms defined once, abbreviated after | `PostgreSQL (PG)` → `PG` |
| 5. Domain auto-detect | AI detects context, applies ALL known domain conventions — unbounded | DevOps: `pod`, `ns`, `helm` / ML: `feat`, `epoch` |
| 6. User-defined dicts | Custom shorthands you create — highest priority over all other rules | your team's own terms |

**All rules activate automatically on install — zero extra setup.**

---

## Community dictionaries

Domain shorthands are **bundled inside the plugin** — install once, get everything.

| Dictionary | Domain | Status |
|------------|--------|--------|
| [`dicts/web-dev.md`](dicts/web-dev.md) | Frontend + Backend web development | bundled |
| [`dicts/data-science.md`](dicts/data-science.md) | Data Science, ML, AI engineering | bundled |
| [`dicts/devops.md`](dicts/devops.md) | DevOps, cloud, infrastructure | bundled |

The `dicts/` folder is the **contribution source** — PRs are reviewed and bundled into the next plugin release.

### Contribute a new dict

Create a markdown table file in `dicts/`:

```markdown
| shorthand | full term    |
|-----------|--------------|
| `gw`      | API gateway  |
| `pub`     | publisher    |
| `sub`     | subscriber   |
```

Open a PR — accepted dicts get bundled in the next release for all users. See [CONTRIBUTING.md](CONTRIBUTING.md).

---

## Contributing

Community-driven protocol. We want:
- New community dictionaries (`dicts/`) for specific domains
- Real benchmark results with before/after word counts
- New CLI integrations under `integrations/`
- Better compression rules

Open an Issue or PR!
