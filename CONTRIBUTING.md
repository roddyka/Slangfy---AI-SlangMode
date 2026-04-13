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
slangfy.md                        — core protocol (universal, any LLM)
integrations/
├── claude-code/                  — Claude Code CLI skill
│   ├── install.md
│   └── .claude/skills/
├── gemini-cli/                   — Gemini CLI
│   └── GEMINI.md
├── aider/                        — Aider
│   └── install.md
└── opencode/                     — OpenCode
    └── install.md
```

## Adding a new CLI integration

1. Create `integrations/<cli-name>/`
2. Add an `install.md` explaining how to activate Slangfy in that CLI
3. If the CLI uses a config/instructions file, include it ready to copy
4. Update `README.md` install section with a short entry

## Rules

- Keep `slangfy.md` and all integration skill files in sync — if you change the protocol, update all of them
- No code, no dependencies — this project is pure spec/docs
- PRs that add shorthands must justify why the term is common enough to warrant a permanent entry
