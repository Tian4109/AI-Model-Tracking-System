---
command: track-meta
description: Update Meta model draft only. Does not generate models.md.
---

# Track Meta Models

Update only the Meta draft file.

---

## Command Contract

**Input source:**
- `links.md` → `Meta` section
- supplemental official Meta sources only when needed

**Agent to launch:**
- `Researcher-Meta`

**Output file:**
- `drafts/meta.md`

**Must not modify:**
- `models.md`
- other vendor draft files
- `links.md`
- README or project configuration files

---

## Workflow

```text
/track-meta
      ↓
Researcher-Meta
      ↓
drafts/meta.md
```

---

## Instructions

Launch `Researcher-Meta`.

The subagent must:

1. Read `links.md`.
2. Use the `Meta` section as the primary source list.
3. Follow `.claude/subagents/BaseResearcher.md`.
4. Fetch official documentation, model cards, license pages, and download sources first.
5. Use targeted web search only for newer or missing official Meta sources.
6. Extract structured model data.
7. Write the result to `drafts/meta.md`.

After this command finishes, run `/generate-report` if the final `models.md` should reflect the updated Meta draft.

---

## Scope Rules

- Focus on Meta-owned Llama model families.
- Treat Llama models as open-weight when official weights are available.
- Do not classify Llama models as fully open-source unless official license terms clearly support that classification.
- Capture license restrictions and deployment notes when official sources provide them.
- Do not include third-party derivatives as Meta-owned models.
- Do not include Chinese-origin model families.
