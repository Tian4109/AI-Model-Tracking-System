---
command: update-report
description: Full refresh. Update all vendor drafts, then generate models.md.
---

# Update Model Report

Run the complete pipeline: update all vendor drafts first, then generate the final report.

Use this command when the report has not been refreshed for a long time or when most supported vendors may have changed.

For a faster targeted update, run one vendor command such as `/track-openai`, then run `/generate-report`.

---

## Command Contract

**Phase 1 agents:**
1. `Researcher-OpenAI`
2. `Researcher-Anthropic`
3. `Researcher-Google`
4. `Researcher-Meta`
5. `Researcher-Microsoft`

**Phase 1 outputs:**
- `drafts/openai.md`
- `drafts/anthropic.md`
- `drafts/google.md`
- `drafts/meta.md`
- `drafts/microsoft.md`

**Phase 2 agent:**
- `Reporter`

**Final output:**
- `models.md`

**Must not modify:**
- `links.md`
- README or project configuration files

---

## Workflow

```text
/update-report
      ↓
Researcher-OpenAI       → drafts/openai.md
Researcher-Anthropic    → drafts/anthropic.md
Researcher-Google       → drafts/google.md
Researcher-Meta         → drafts/meta.md
Researcher-Microsoft    → drafts/microsoft.md
      ↓
Reporter
      ↓
models.md
```

---

## Instructions

### Phase 1 — Refresh vendor drafts

Launch the vendor Researcher subagents sequentially.

Each Researcher must:

1. Read `links.md`.
2. Use only its own vendor section.
3. Follow `.claude/subagents/BaseResearcher.md`.
4. Update only its own file in `drafts/`.
5. Use official sources first.
6. Use supplemental search only for official sources.

### Phase 2 — Generate final report

After all draft files are updated, launch `Reporter`.

The Reporter must:

1. Read all updated files in `drafts/`.
2. Validate and normalise the draft data.
3. Generate comparative analysis and scenario recommendations.
4. Write the final report to `models.md`.

---

## Scope Rules

- Supported vendors: OpenAI, Anthropic, Google, Meta, Microsoft.
- Do not include unsupported vendors unless the project scope is updated.
- Do not include Chinese-origin model families.
- Do not classify third-party hosted models as belonging to the hosting platform vendor.
