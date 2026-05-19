---
command: generate-report
description: Generate models.md from existing drafts only. Does not browse or run researchers.
---

# Generate Final Model Report

Generate the final model report from existing vendor drafts.

Use this command after one or more `track-*` commands have updated the relevant draft files.

---

## Command Contract

**Input files:**
- `drafts/openai.md`
- `drafts/anthropic.md`
- `drafts/google.md`
- `drafts/meta.md`
- `drafts/microsoft.md`

**Agent to launch:**
- `Reporter`

**Output file:**
- `models.md`

**Must not modify:**
- vendor draft files
- `links.md`
- README or project configuration files

**Must not browse:**
- This command uses existing drafts only.

---

## Workflow

```text
/generate-report
      ↓
Reporter
      ↓
reads drafts/*.md
      ↓
models.md
```

---

## Instructions

Launch the `Reporter` subagent.

The Reporter must:

1. Read all available vendor draft files in `drafts/`.
2. Treat drafts as structured intermediate data, not final prose.
3. Validate and normalise draft data.
4. Apply project scope filtering.
5. Separate API / closed-weight models from open-weight models.
6. Compare models across vendors.
7. Generate scenario-based recommendations.
8. Generate the final report at `models.md`.

Do not:

- browse the web
- call any Researcher subagent
- modify vendor draft files
- modify `links.md`

---

## Missing Draft Handling

If a vendor draft is missing, stale, or empty:

- Do not invent missing vendor information.
- Continue with available drafts.
- Add a short note in the final report indicating which vendor data was unavailable or not refreshed.
