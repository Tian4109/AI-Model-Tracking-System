---
command: track-google
description: Update Google model draft only. Does not generate models.md.
---

# Track Google Models

Update only the Google draft file.

---

## Command Contract

**Input source:**
- `links.md` → `Google` section
- supplemental official Google sources only when needed

**Agent to launch:**
- `Researcher-Google`

**Output file:**
- `drafts/google.md`

**Must not modify:**
- `models.md`
- other vendor draft files
- `links.md`
- README or project configuration files

---

## Workflow

```text
/track-google
      ↓
Researcher-Google
      ↓
drafts/google.md
```

---

## Instructions

Launch `Researcher-Google`.

The subagent must:

1. Read `links.md`.
2. Use the `Google` section as the primary source list.
3. Follow `.claude/subagents/BaseResearcher.md`.
4. Fetch official documentation and pricing sources first.
5. Use targeted web search only for newer or missing official Google sources.
6. Extract structured model data.
7. Write the result to `drafts/google.md`.

After this command finishes, run `/generate-report` if the final `models.md` should reflect the updated Google draft.

---

## Scope Rules

- Separate Gemini API / closed-weight models from Gemma open-weight models.
- Clearly classify specialised Google models such as embedding, image, video, audio, or live/realtime models when official sources support them.
- Keep pricing modality notes clear when text, image, video, or audio pricing differs.
- Do not classify third-party models hosted on Google platforms as Google-owned models.
- Do not include Chinese-origin model families.
