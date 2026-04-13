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
