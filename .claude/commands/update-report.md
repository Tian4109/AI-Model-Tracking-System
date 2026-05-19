---
command: update-report
description: Full refresh. Update all vendor drafts from links.md, then generate models.md.
---

# Update Model Report

Run the complete pipeline: update all vendor drafts first, then generate the final report.

Use this command when the report has not been refreshed for a long time or when most vendor information may have changed.

For a faster targeted update, run one vendor command such as `/track-openai` or `/track-vendor Mistral`, then run `/generate-report`.

---

## Command Contract

**Phase 1 core vendor agents:**
1. `Researcher-OpenAI`
2. `Researcher-Anthropic`
3. `Researcher-Google`
4. `Researcher-Meta`
5. `Researcher-Microsoft`

**Phase 1 core outputs:**
- `drafts/openai.md`
- `drafts/anthropic.md`
- `drafts/google.md`
- `drafts/meta.md`
- `drafts/microsoft.md`

**Phase 1 additional vendor handling:**
- Scan `links.md` for additional vendor sections.
- Exclude the document title, non-vendor sections, and the five core vendors.
- Use `Researcher-Vendor` for additional vendors.
- Generate `drafts/<vendor-lowercase>.md`.

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
Core vendors:
Researcher-OpenAI       → drafts/openai.md
Researcher-Anthropic    → drafts/anthropic.md
Researcher-Google       → drafts/google.md
Researcher-Meta         → drafts/meta.md
Researcher-Microsoft    → drafts/microsoft.md
      ↓
Additional vendors from links.md:
Researcher-Vendor       → drafts/<vendor>.md
      ↓
Reporter
      ↓
models.md
```

---

## Instructions

### Phase 1 — Refresh vendor drafts

Launch the five core vendor Researcher subagents sequentially.

Each core Researcher must:

1. Read `links.md`.
2. Use only its own vendor section.
3. Follow `.claude/subagents/BaseResearcher.md`.
4. Update only its own file in `drafts/`.
5. Use official sources first.
6. Use supplemental search only for official or official-ecosystem sources.

After the five core vendors are updated, scan `links.md` for additional top-level vendor sections.

When scanning for additional vendors:

1. Exclude the document title:
   - `Official Vendor Links`
2. Exclude non-vendor sections such as:
   - `Notes`
   - `Source Policy`
   - `Supported Vendors`
3. Exclude core vendors:
   - OpenAI
   - Anthropic
   - Google
   - Meta
   - Microsoft
4. For each remaining vendor, call `Researcher-Vendor`.
5. Write the output to `drafts/<vendor-lowercase>.md`.

### Phase 2 — Generate final report

After all draft files are updated, launch `Reporter`.

The Reporter must:

1. Read all available files in `drafts/*.md`.
2. Include both core vendor drafts and additional vendor drafts.
3. Validate and normalise the draft data.
4. Generate comparative analysis and scenario recommendations.
5. Write the final report to `models.md`.

---

## Scope Rules

- Core vendors: OpenAI, Anthropic, Google, Meta, Microsoft.
- Additional vendors are supported when they are defined in `links.md`.
- Chinese-origin model families remain outside the current project scope unless the scope changes later.
- Do not classify third-party hosted models as belonging to the hosting platform vendor.
