# Slangfy + OpenCode

OpenCode uses `slangfy.md` as instructions — all bundled dicts (Web Dev, Data Science, DevOps) are included automatically.

## Option A — Project-level (this project only)

```bash
mkdir -p .opencode
cp path/to/slangfy.md .opencode/instructions.md
```

OpenCode loads `.opencode/instructions.md` automatically on session start.

## Option B — Global (all projects)

```bash
mkdir -p ~/.config/opencode
cp path/to/slangfy.md ~/.config/opencode/instructions.md
```

## Custom dicts

To add team or project-specific shorthands, create a `dicts/my-team.md` in your project root following this format:

```markdown
| shorthand | full term  |
|-----------|------------|
| `gw`      | API gateway |
| `pub`     | publisher  |
```

OpenCode reads project files as context — place the dict in your project and it will be picked up automatically.

## Verify it works

Ask OpenCode:
> "what is your response format?"

Expected output follows Slangfy syntax.
