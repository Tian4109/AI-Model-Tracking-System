---
command: track-all
description: Update all vendor drafts from links.md. Does not generate models.md.
---

# Track All Vendors

Update all vendor draft files, but do not generate the final report.

Use this command when many or all vendor sources may have changed and the user wants a full refresh of `drafts/*.md`.

This command supports two categories of vendors:

1. **Core vendors** with dedicated Researcher agents.
2. **Additional vendors** defined in `links.md`, handled by `Researcher-Vendor`.

---

## Command Contract

**Input source:**
- `links.md` vendor sections
- supplemental official or official-ecosystem sources only when needed

**Core vendor agents to launch, in order:**
1. `Researcher-OpenAI` → `drafts/openai.md`
2. `Researcher-Anthropic` → `drafts/anthropic.md`
3. `Researcher-Google` → `drafts/google.md`
4. `Researcher-Meta` → `drafts/meta.md`
5. `Researcher-Microsoft` → `drafts/microsoft.md`

**Additional vendor handling:**
- Scan `links.md` for additional top-level vendor sections.
- Exclude the document title and non-vendor sections.
- Exclude the five core vendors listed above.
- For each remaining vendor, call `Researcher-Vendor`.
- Generate `drafts/<vendor-lowercase>.md`.

**Must not modify:**
- `models.md`
- `links.md`
- README or project configuration files

---

## Workflow

```text
/track-all
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
```

---

## Instructions

Launch the core vendor Researcher subagents sequentially.

Each core Researcher must:

1. Read `links.md`.
2. Use only its own vendor section.
3. Follow `.claude/subagents/BaseResearcher.md`.
4. Update only its own file in `drafts/`.
5. Avoid modifying unrelated files.

After the five core vendors are updated, scan `links.md` for additional top-level vendor sections.

When scanning for additional vendors:

1. Treat top-level Markdown headings (`# Vendor Name`) as candidate vendor sections.
2. Exclude the document title:
   - `Official Vendor Links`
3. Exclude non-vendor sections such as:
   - `Notes`
   - `Source Policy`
   - `Supported Vendors`
4. Exclude core vendors:
   - OpenAI
   - Anthropic
   - Google
   - Meta
   - Microsoft
5. For each remaining vendor, call `Researcher-Vendor` with that vendor name.
6. Write the output to `drafts/<vendor-lowercase>.md`.

Do not generate `models.md` in this command.

After `/track-all` finishes, run `/generate-report` to produce the final report.

---

## Scope Notes

- The core five vendors remain handled by dedicated Researcher agents for higher consistency.
- Additional vendors are handled by `Researcher-Vendor` for flexibility.
- Chinese-origin model families remain outside the current project scope unless the project scope changes later.
- If an additional vendor section does not contain useful official or official-ecosystem links, skip it and mention the issue to the user.
