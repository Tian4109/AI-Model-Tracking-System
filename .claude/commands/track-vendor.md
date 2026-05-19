---
description: Track and update a custom vendor defined in links.md
argument-hint: <VendorName>
---

# Track Vendor Command

This command updates a custom vendor defined in `links.md`.

Example:

```text
/track-vendor Mistral
```

Workflow:

```text
Read links.md
        ↓
Find matching vendor section
        ↓
Call Researcher-Vendor
        ↓
Generate drafts/<vendor>.md
```

Requirements:

- Vendor name must match a section title in `links.md`
- Use official or official-ecosystem sources first
- Follow BaseResearcher formatting rules
- Output file should use lowercase vendor naming

Examples:

```text
drafts/mistral.md
drafts/cohere.md
drafts/xai.md
```

After generation, users can run:

```text
/generate-report
```

to include the vendor in the final report.
