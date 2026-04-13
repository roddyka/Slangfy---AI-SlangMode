# Slangfy + Gemini CLI

Gemini CLI uses `GEMINI.md` as instructions — all bundled dicts (Web Dev, Data Science, DevOps) are included automatically.

## Install

Copy the instructions file to your project root:

```bash
cp path/to/slangfy/integrations/gemini-cli/GEMINI.md ./GEMINI.md
```

Gemini CLI loads `GEMINI.md` automatically on session start.

## Custom dicts

To add team or project-specific shorthands, create a `dicts/my-team.md` in your project root following this format:

```markdown
| shorthand | full term   |
|-----------|-------------|
| `gw`      | API gateway |
| `pub`     | publisher   |
```

Gemini CLI reads project files as context — place the dict in your project and it will be picked up automatically.

## Verify it works

Ask Gemini CLI:
> "what is your response format?"

Expected output follows Slangfy syntax.
