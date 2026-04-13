# Slangfy + Aider

| Variant | File | Overhead |
|---------|------|----------|
| **Nano** | `slangfy-nano.md` | ~40 tokens — recommended for general use |
| **Full** | `slangfy.md` | ~2 000 tokens — aggressive dict compression |

## Option A — Per session (flag)

```bash
# Nano (recommended)
aider --system-prompt path/to/slangfy-nano.md

# Full
aider --system-prompt path/to/slangfy.md
```

## Option B — Permanent (config file)

Add to `.aider.conf.yml` in your project root or `~/.aider.conf.yml` for global use:

```yaml
# Nano (recommended)
system-prompt: path/to/slangfy-nano.md

# Full
# system-prompt: path/to/slangfy.md
```

## Custom dicts

To add team or project-specific shorthands, create a `dicts/my-team.md` in your project root following this format:

```markdown
| shorthand | full term  |
|-----------|------------|
| `gw`      | API gateway |
| `pub`     | publisher  |
```

Aider reads project files as context — place the dict in your project and it will be picked up automatically.

## Verify it works

Ask aider:
> "what is your response format?"

Expected output follows Slangfy syntax.
