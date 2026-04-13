# Custom Slangfy Dictionary — Example (OpenCode)

Use this file as a template for your own team or project-specific shorthands.
Copy it to your project root under `dicts/` and rename it.

## How to use

Place in `your-project/dicts/my-team.md`
OpenCode reads project files as context — no extra config needed.

## Template — add your shorthands here

| shorthand | full term |
|-----------|-----------|
| `gw`      | API gateway |
| `pub`     | publisher |
| `sub`     | subscriber |
| `tenant`  | tenant (multi-tenant system) |
| `plan`    | subscription plan |

## Rules for custom shorthands

- Keep shorthands 2–5 chars
- Must be unambiguous in your domain context
- If it conflicts with a base shorthand, your custom one takes priority (Rule 6)
- Want to share it with the community? Open a PR to `dicts/` in the Slangfy repo
