# Slangfy + OpenCode

## Option A — Project-level instructions

Create a `.opencode/instructions.md` file in your project root and paste the contents of `slangfy.md` into it. OpenCode loads this automatically on session start.

```bash
mkdir -p .opencode
cp path/to/slangfy.md .opencode/instructions.md
```

## Option B — Global instructions

Copy to your global OpenCode config directory:

```bash
mkdir -p ~/.config/opencode
cp path/to/slangfy.md ~/.config/opencode/instructions.md
```

## Verify it works

Ask OpenCode:
> "what is your response format?"

Expected output follows Slangfy syntax.
