# BaseResearcher

This file contains the shared research workflow for all vendor-specific Researcher agents.

Vendor-specific agents must read and follow this file before collecting model data. The vendor-specific agent file provides the vendor name, scope, output path, source section, search queries, and special classification notes.

---

## Purpose

A Researcher agent collects accurate, current, structured model information for one vendor and writes a vendor-specific draft file under `drafts/`.

Researcher agents do **not** generate the final report. The `Reporter` agent reads the draft files and generates `models.md`.

---

## Core Principles

1. **Official sources first**
   - Start from the relevant vendor section in `links.md`.
   - Treat `links.md` as the primary official-source whitelist.
   - Supplemental search is allowed only when it leads to official vendor documentation, official pricing pages, official model cards, official GitHub repositories, official Hugging Face organisation pages, or official announcements.

2. **Do not rely on third-party summaries**
   - Do not use blogs, Reddit, benchmark leaderboards, news articles, unofficial documentation, or random GitHub repositories as primary evidence.
   - Third-party pages may only be used to discover an official source, not as final evidence.

3. **No unsupported guessing**
   - Do not fabricate prices, release dates, context windows, licenses, memory requirements, API IDs, or capabilities.
   - Use `—` for unavailable or unclear fields.
   - Record uncertainty in `Research Notes`.

4. **Open-weight is not the same as open-source**
   - `is_open_weight = true` means official weights are publicly available for download or self-deployment.
   - `is_open_source = true` only if official documentation or license clearly states an open-source license such as Apache 2.0, MIT, or another recognised open-source license.
   - Community licenses and custom vendor licenses should normally be treated as open-weight but not automatically open-source.

5. **Exclude Chinese-origin model families for this project**
   - Do not add DeepSeek, Qwen, ERNIE, GLM, Kimi, MiniMax, Baichuan, Yi, InternLM, or other Chinese-origin model families.
   - If they appear in a platform catalogue, ignore them unless the project scope is explicitly changed later.

6. **Keep vendor boundaries clear**
   - A vendor platform may host third-party models. Do not classify those third-party models as belonging to the platform vendor.
   - Example: Azure AI Foundry may host models from multiple providers; only Microsoft-owned model families should be recorded in the Microsoft draft unless the project scope changes.

---

## Required Workflow

### Step 1 — Read links.md

Read `links.md` from the project root.

Use only the vendor section specified in the vendor-specific Researcher file.

The links in `links.md` are the primary official sources. Use them first before performing supplemental search.

### Step 2 — Fetch official documentation

Use `WebFetch` to retrieve official URLs listed for the vendor.

Extract relevant model data from official pages, including but not limited to:

- model names and API IDs
- model family or generation
- availability type
- context window
- max output tokens
- pricing
- release date or update date
- modality support
- open-weight / open-source status
- license terms
- recommended use cases
- official source URL

### Step 3 — Supplement with targeted official search

Use `WebSearch` only to fill gaps, check recency, or discover newer official pages.

Supplemental search results must not override the official links from `links.md` unless they point to a newer or more specific official source.

### Step 4 — Extract required fields

For every model, collect these fields:

| Field | Description |
|---|---|
| `model_name` | Full model name and version string |
| `provider` | Vendor/provider name from the vendor-specific Researcher file |
| `origin_country` | Country of origin if clear from vendor identity or official documentation |
| `is_chinese_origin` | Boolean compliance flag; normally `false` for the current supported vendors |
| `release_date` | `YYYY-MM` if available, otherwise `—` |
| `model_type` | One or more of: `embedding`, `generation`, `reasoning`, `multimodal`, `image`, `audio`, `video` |
| `availability_type` | `api`, `open-weight`, `hybrid`, or `unknown` |
| `is_open_weight` | `true` if official model weights are publicly available |
| `is_open_source` | `true` only if official source clearly states an open-source license |
| `is_online` | `true` for API-only models; `false` for local/offline deployable models |
| `context_length` | Maximum context window in tokens |
| `cost_input_per_1m` | USD per 1M input tokens; use `—` if unavailable or not applicable |
| `cost_output_per_1m` | USD per 1M output tokens; use `—` if unavailable or not applicable |
| `memory_requirement_gb` | Official or clearly documented VRAM/RAM requirement; otherwise `—`; use `—` for API-only models |
| `strengths` | Short evidence-based description of what the model is best at |
| `recommended_use_case` | Practical use case recommendation based on official capabilities and extracted fields |
| `source` | Official source URL used for the row |

### Step 5 — Classify models consistently

Use these conventions:

| Situation | Classification |
|---|---|
| Hosted API model with no public weights | `availability_type = api`, `is_online = true`, `is_open_weight = false` |
| Public weights available for local deployment | `availability_type = open-weight`, `is_online = false`, `is_open_weight = true` |
| Model available both as hosted API and downloadable weights | `availability_type = hybrid` |
| Official source unclear | `availability_type = unknown`, explain uncertainty in notes |

### Step 6 — Write the vendor draft

Write the result to the output path specified in the vendor-specific Researcher file.

Use this exact Markdown structure, replacing placeholders with the vendor-specific values:

```markdown
# {Vendor} Model Data — Draft

> This file is generated by `{ResearcherName}`.
> Primary source: `links.md` → `{Vendor}` section.
> Last updated: YYYY-MM-DD.

---

## Research Notes

- Official documentation links used:
- Supplemental searches used:
- Missing / uncertain fields:
- Important classification notes:

---

## API / Closed-weight Models

| model_name | provider | origin_country | is_chinese_origin | release_date | model_type | availability_type | is_open_weight | is_open_source | is_online | context_length | cost_input_per_1m | cost_output_per_1m | memory_requirement_gb | strengths | recommended_use_case | source |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

## Open-weight Models

| model_name | provider | origin_country | is_chinese_origin | release_date | model_type | availability_type | is_open_weight | is_open_source | is_online | context_length | cost_input_per_1m | cost_output_per_1m | memory_requirement_gb | strengths | recommended_use_case | source |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
```

If a section has no models, keep the section and add one short note below the table explaining that no official in-scope models were found.

---

## Quality Checklist Before Writing

Before writing the draft, verify:

- The vendor section of `links.md` was read.
- Official links were used before supplemental search.
- Every row has an official source URL.
- Missing values use `—` instead of guessed data.
- Open-weight and open-source are not confused.
- Chinese-origin models are excluded.
- Third-party hosted models are not misclassified as the current vendor's own models.
- The final output uses the exact table columns required above.
