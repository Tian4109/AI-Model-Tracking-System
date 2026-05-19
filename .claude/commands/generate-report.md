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
- all available Markdown files in `drafts/*.md`

This includes both:

- core vendor drafts, such as `drafts/openai.md`
- additional vendor drafts, such as `drafts/mistral.md`

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

1. Read all available Markdown draft files in `drafts/`.
2. Treat drafts as structured intermediate data, not final prose.
3. Include both core vendor drafts and additional vendor drafts.
4. Validate and normalise draft data.
5. Apply project scope filtering.
6. Separate API / closed-weight models from open-weight models.
7. Compare models across vendors.
8. Generate scenario-based recommendations.
9. Generate the final report at `models.md`.

Do not:

- browse the web
- call any Researcher subagent
- modify vendor draft files
- modify `links.md`

---

## Missing Draft Handling

If a draft is missing, stale, or empty:

- Do not invent missing vendor information.
- Continue with available drafts.
- Add a short note in the final report indicating which vendor data was unavailable or not refreshed.

If no valid draft files exist in `drafts/`, stop and tell the user to run a tracking command first, such as:

```text
/track-openai
```

or:

```text
/track-vendor Mistral
```
