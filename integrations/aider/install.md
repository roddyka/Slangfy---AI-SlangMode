# Slangfy + Aider

## Option A — Per session (flag)

```bash
aider --system-prompt ../../slangfy.md
```

## Option B — Permanent (config file)

Add to your `.aider.conf.yml` in the project root or `~/.aider.conf.yml` for global use:

```yaml
system-prompt: path/to/slangfy.md
```

## Option C — Inline (no file)

Add to `.aider.conf.yml`:

```yaml
system-prompt: |
  Apply this protocol to all outputs.
  status: [ok|warn|err] | task @ context | action: [...] | out: [...] | ! [warning]
  Compress aggressively. No politeness. Use diff for code changes.
  Shorten any tech term >6 chars to its common abbreviation. Define-on-first-use for unknown terms.
```

## Verify it works

Ask aider:
> "what is your response format?"

Expected output follows Slangfy syntax.
