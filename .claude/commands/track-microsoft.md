---
command: track-microsoft
description: Update Microsoft model draft only. Does not generate models.md.
---

# Track Microsoft Models

Update only the Microsoft draft file.

---

## Command Contract

**Input source:**
- `links.md` → `Microsoft` section
- supplemental official Microsoft sources only when needed

**Agent to launch:**
- `Researcher-Microsoft`

**Output file:**
- `drafts/microsoft.md`

**Must not modify:**
- `models.md`
- other vendor draft files
- `links.md`
- README or project configuration files

---

## Workflow

```text
/track-microsoft
      ↓
Researcher-Microsoft
      ↓
drafts/microsoft.md
```

---

## Instructions

Launch `Researcher-Microsoft`.

The subagent must:

1. Read `links.md`.
2. Use the `Microsoft` section as the primary source list.
3. Follow `.claude/subagents/BaseResearcher.md`.
4. Fetch official Microsoft documentation, model cards, GitHub/Hugging Face organisation pages, and pricing sources first.
5. Use targeted web search only for newer or missing official Microsoft sources.
6. Extract structured model data.
7. Write the result to `drafts/microsoft.md`.

After this command finishes, run `/generate-report` if the final `models.md` should reflect the updated Microsoft draft.

---

## Scope Rules

- Focus on Microsoft-owned Phi model families.
- Clearly separate Microsoft-owned models from third-party models available through Azure AI Foundry.
- Include API pricing only when the official source clearly provides it.
- Capture license terms and local deployment notes when official sources provide them.
- Do not include Chinese-origin model families.
