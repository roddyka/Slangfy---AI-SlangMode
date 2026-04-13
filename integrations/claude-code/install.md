# Slangfy + Claude Code

## Install (personal — all your projects)

```bash
mkdir -p ~/.claude/skills/slangfy-on ~/.claude/skills/slangfy-off
cp .claude/skills/slangfy-on/SKILL.md ~/.claude/skills/slangfy-on/SKILL.md
cp .claude/skills/slangfy-off/SKILL.md ~/.claude/skills/slangfy-off/SKILL.md
```

## Install (project-level — one repo only)

```bash
mkdir -p .claude/skills/slangfy-on .claude/skills/slangfy-off
cp integrations/claude-code/.claude/skills/slangfy-on/SKILL.md .claude/skills/slangfy-on/SKILL.md
cp integrations/claude-code/.claude/skills/slangfy-off/SKILL.md .claude/skills/slangfy-off/SKILL.md
```

## Usage

```
/slangfy-on    — enable Slangfy mode for this session
/slangfy-off   — return to normal language
```
