---
command: track-openai
description: Update OpenAI model draft only. Does not generate models.md.
---

# Track OpenAI Models

Update only the OpenAI draft file.

---

## Command Contract

**Input source:**
- `links.md` → `OpenAI` section
- supplemental official OpenAI sources only when needed

**Agent to launch:**
- `Researcher-OpenAI`

**Output file:**
- `drafts/openai.md`

**Must not modify:**
- `models.md`
- other vendor draft files
- `links.md`
- README or project configuration files

---

## Workflow

```text
/track-openai
      ↓
Researcher-OpenAI
      ↓
drafts/openai.md
```

---

## Instructions

Launch `Researcher-OpenAI`.

The subagent must:

1. Read `links.md`.
2. Use the `OpenAI` section as the primary source list.
3. Follow `.claude/subagents/BaseResearcher.md`.
4. Fetch official documentation and pricing sources first.
5. Use targeted web search only for newer or missing official OpenAI sources.
6. Extract structured model data.
7. Write the result to `drafts/openai.md`.

After this command finishes, run `/generate-report` if the final `models.md` should reflect the updated OpenAI draft.

---

## Scope Rules

- Include OpenAI API / closed-weight models.
- Include official OpenAI open-weight models only if public weights and license terms are confirmed by official sources.
- Keep GPT-series, reasoning models, embedding models, realtime/audio/image/video models clearly classified.
- Do not include third-party models.
- Do not include Chinese-origin model families.
