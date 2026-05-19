---
command: track-anthropic
description: Update Anthropic model draft only. Does not generate models.md.
---

# Track Anthropic Models

Update only the Anthropic draft file.

---

## Command Contract

**Input source:**
- `links.md` → `Anthropic` section
- supplemental official Anthropic sources only when needed

**Agent to launch:**
- `Researcher-Anthropic`

**Output file:**
- `drafts/anthropic.md`

**Must not modify:**
- `models.md`
- other vendor draft files
- `links.md`
- README or project configuration files

---

## Workflow

```text
/track-anthropic
      ↓
Researcher-Anthropic
      ↓
drafts/anthropic.md
```

---

## Instructions

Launch `Researcher-Anthropic`.

The subagent must:

1. Read `links.md`.
2. Use the `Anthropic` section as the primary source list.
3. Follow `.claude/subagents/BaseResearcher.md`.
4. Fetch official documentation and pricing sources first.
5. Use targeted web search only for newer or missing official Anthropic sources.
6. Extract structured model data.
7. Write the result to `drafts/anthropic.md`.

After this command finishes, run `/generate-report` if the final `models.md` should reflect the updated Anthropic draft.

---

## Scope Rules

- Include Claude API / closed-weight models.
- Classify current, legacy, deprecated, and preview models clearly.
- Capture context window, output limits, tool/computer-use support, prompt caching, batch pricing, and relevant pricing notes when official sources provide them.
- Do not include third-party models.
- Do not include Chinese-origin model families.
