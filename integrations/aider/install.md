# Slangfy + Aider

Aider uses `slangfy.md` as the system prompt — all bundled dicts (Web Dev, Data Science, DevOps) are included automatically.

## Option A — Per session (flag)

```bash
aider --system-prompt path/to/slangfy.md
```

## Option B — Permanent (config file)

Add to `.aider.conf.yml` in your project root or `~/.aider.conf.yml` for global use:

```yaml
system-prompt: path/to/slangfy.md
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
