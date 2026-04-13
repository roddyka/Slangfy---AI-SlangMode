# Slangfy + OpenCode

| Variant | File | Overhead |
|---------|------|----------|
| **Nano** | `slangfy-nano.md` | ~40 tokens — recommended for general use |
| **Full** | `slangfy.md` | ~2 000 tokens — aggressive dict compression |

## Option A — Project-level (this project only)

```bash
mkdir -p .opencode

# Nano (recommended)
cp path/to/slangfy-nano.md .opencode/instructions.md

# Full
# cp path/to/slangfy.md .opencode/instructions.md
```

OpenCode loads `.opencode/instructions.md` automatically on session start.

## Option B — Global (all projects)

```bash
mkdir -p ~/.config/opencode

# Nano (recommended)
cp path/to/slangfy-nano.md ~/.config/opencode/instructions.md

# Full
# cp path/to/slangfy.md ~/.config/opencode/instructions.md
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
