# Slangfy + Claude Code

## Which variant?

| Variant | Overhead | Best for |
|---------|----------|----------|
| **Nano** | ~40 tokens | Daily general use |
| **Full** | ~2 000 tokens | Long sessions needing aggressive dict compression |

---

## Nano (recommended for general use)

### Option A — Hook (always-on, zero /command overhead)

Add to `.claude/settings.json` (project) or `~/.claude/settings.json` (global):

```json
{
  "hooks": {
    "SessionStart": [
      {
        "type": "command",
        "command": "cat path/to/slangfy-nano.md"
      }
    ]
  }
}
```

### Option B — Skill (/slangfy-nano-on on demand)

```bash
# Personal (all projects)
mkdir -p ~/.claude/skills/slangfy-nano-on
cp integrations/claude-code/.claude/skills/slangfy-nano-on/SKILL.md ~/.claude/skills/slangfy-nano-on/SKILL.md

# Project-level (one repo only)
mkdir -p .claude/skills/slangfy-nano-on
cp integrations/claude-code/.claude/skills/slangfy-nano-on/SKILL.md .claude/skills/slangfy-nano-on/SKILL.md
```

Usage:
```
/slangfy-nano-on   — enable Nano mode for this session
/slangfy-off       — return to normal language
```

---

## Full (aggressive dict compression)

### Install (personal — all your projects)

```bash
mkdir -p ~/.claude/skills/slangfy-on ~/.claude/skills/slangfy-off
cp .claude/skills/slangfy-on/SKILL.md ~/.claude/skills/slangfy-on/SKILL.md
cp .claude/skills/slangfy-off/SKILL.md ~/.claude/skills/slangfy-off/SKILL.md
```

### Install (project-level — one repo only)

```bash
mkdir -p .claude/skills/slangfy-on .claude/skills/slangfy-off
cp integrations/claude-code/.claude/skills/slangfy-on/SKILL.md .claude/skills/slangfy-on/SKILL.md
cp integrations/claude-code/.claude/skills/slangfy-off/SKILL.md .claude/skills/slangfy-off/SKILL.md
```

Usage:
```
/slangfy-on    — enable Full mode for this session
/slangfy-off   — return to normal language
```

## Custom dictionaries

**Project-specific** (only active in one project):
```bash
mkdir -p your-project/dicts
cp integrations/claude-code/dicts/example-custom.md your-project/dicts/my-team.md
# edit my-team.md with your shorthands
# Claude reads dicts/ from project context automatically
```

**Global** (active in all projects):
Append your shorthands to the installed skill file:
```bash
cat integrations/claude-code/dicts/example-custom.md >> ~/.claude/skills/slangfy-on/SKILL.md
```
