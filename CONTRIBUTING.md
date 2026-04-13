# Contributing to Slangfy

Community contributions are welcome. This is a documentation-only project — no build process, no dependencies.

## What to contribute

- **New compression rules** — better patterns for auto-shorthand
- **Domain shorthands** — coverage for specific domains (Data Science, DevOps, Legal, Mobile, etc.)
- **New CLI integrations** — add a folder under `integrations/` for any CLI not yet covered
- **Token benchmarks** — real before/after comparisons using the API
- **Bug fixes** — incorrect shorthands, broken install instructions

## How to contribute

1. Fork the repo
2. Create a branch: `git checkout -b feat/your-change`
3. Make your changes
4. Open a PR with a clear description of what changed and why

## File structure

```
slangfy.md                           — core protocol (universal, any LLM) — bundled dicts included
dicts/                               — contribution source for community dictionaries
│   ├── web-dev.md                   — Frontend + Backend
│   ├── data-science.md              — Data Science / ML
│   ├── devops.md                    — DevOps / Cloud
│   └── example-custom.md (*)        — template for user custom dicts
integrations/
├── claude-code/                     — Claude Code CLI skill
│   ├── install.md
│   ├── dicts/example-custom.md      — template for user custom dicts (Claude Code)
│   └── .claude/skills/
│       ├── slangfy-on/SKILL.md      — bundled dicts included
│       └── slangfy-off/SKILL.md
├── gemini-cli/
│   └── GEMINI.md                    — bundled dicts included
├── aider/
│   └── install.md
└── opencode/
    └── install.md
```

## Adding a new CLI integration

1. Create `integrations/<cli-name>/`
2. Add an `install.md` explaining how to activate Slangfy in that CLI
3. If the CLI uses a config/instructions file, include it ready to copy
4. Update `README.md` install section with a short entry

## Adding a new community dict

1. Create `dicts/<domain>.md` with a markdown table (see existing files for format)
2. Bundle it into `slangfy.md` (section 5), `integrations/claude-code/.claude/skills/slangfy-on/SKILL.md`, and `integrations/gemini-cli/GEMINI.md`
3. Update the Community dictionaries table in `README.md`
4. Open a PR — all four files must be in sync

## Rules

- Keep `slangfy.md` and all integration skill files in sync — if you change the protocol or add a dict, update all plugin files
- No code, no dependencies — this project is pure spec/docs
- PRs that add shorthands must justify why the term is common enough to warrant a permanent entry
- Never bundle a dict that isn't also in `dicts/` — the folder is the source of truth
