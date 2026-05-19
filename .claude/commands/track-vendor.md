---
command: track-vendor
description: Track and update a custom vendor defined in links.md.
argument-hint: <VendorName>
---

# Track Vendor Command

Update one additional vendor defined in `links.md`.

Use this command when the vendor does not have a dedicated command such as `/track-openai` or `/track-google`.

Example:

```text
/track-vendor Mistral
```

---

## Command Contract

**Input:**
- vendor name provided by the user as `<VendorName>`
- matching top-level vendor section in `links.md`

**Agent to launch:**
- `Researcher-Vendor`

**Output file:**
- `drafts/<vendor-lowercase>.md`

Examples:

```text
drafts/mistral.md
drafts/cohere.md
drafts/xai.md
```

**Must not modify:**
- `models.md`
- unrelated draft files
- `links.md`
- README or project configuration files

---

## Workflow

```text
/track-vendor Mistral
      ↓
Read links.md
      ↓
Find # Mistral section
      ↓
Researcher-Vendor
      ↓
drafts/mistral.md
```

---

## Instructions

1. Read `links.md`.
2. Locate the top-level section matching `<VendorName>`.
3. If no matching section exists, stop and ask the user to add the vendor to `links.md` first.
4. Launch `Researcher-Vendor` with the vendor name and matching source section.
5. Follow `.claude/subagents/BaseResearcher.md` for output format and quality rules.
6. Write only the matching draft file in `drafts/`.

After this command finishes, run:

```text
/generate-report
```

to include the vendor in `models.md`.

---

## Notes

- The vendor name should match the heading in `links.md`.
- Use this command for additional vendors, not the five core vendors that already have dedicated commands.
- For the core vendors, prefer `/track-openai`, `/track-anthropic`, `/track-google`, `/track-meta`, or `/track-microsoft`.
