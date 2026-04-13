# Custom Slangfy Dictionary — Example

Use this file as a template to create your own team or project-specific shorthands.
Copy it to your project root under `dicts/` and rename it.

## How to use

**Project-specific (this project only):**
Place in `your-project/dicts/my-team.md`
The AI reads it automatically when working in that project.

**Global (all projects):**
Append your shorthands directly to your installed SKILL.md:
`~/.claude/skills/slangfy-on/SKILL.md`

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
