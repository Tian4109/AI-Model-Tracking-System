# CLAUDE.md

This file provides guidance to Claude Code when working in this repository.

---

## Project Overview

This is an **AI Model Tracking Documentation System** — not a web app. It uses Claude Code commands and subagents to collect LLM model information from official vendor sources, generate structured draft files, and produce a final comparison report (`models.md`).

The report helps answer: *"Which model should we consider for this situation, and why?"*

---

## Project Structure

```
.
├── links.md                        # Official source URLs for each vendor
├── models.md                       # Final client-facing report (output)
├── drafts/                         # Intermediate structured vendor data
│   ├── openai.md
│   ├── anthropic.md
│   ├── google.md
│   ├── meta.md
│   ├── microsoft.md
│   └── mistral.md
├── .claude/
│   ├── commands/                   # Slash commands (user-facing)
│   └── subagents/                  # Research + Reporter agents
│       ├── BaseResearcher.md       # Shared research rules, schema, quality checklist
│       ├── Reporter.md             # Final synthesis agent for models.md
│       ├── Researcher-OpenAI.md
│       ├── Researcher-Anthropic.md
│       ├── Researcher-Google.md
│       ├── Researcher-Meta.md
│       ├── Researcher-Microsoft.md
│       └── Researcher-Vendor.md    # Generic researcher for additional vendors
├── README.md
└── WORKFLOW.md
```

---

## Commands

All commands are Claude Code slash commands defined in `.claude/commands/`. Run them from within a Claude Code session started at the project root.

| Command | What it does |
|---|---|
| `/track-openai` | Update `drafts/openai.md` via Researcher-OpenAI |
| `/track-anthropic` | Update `drafts/anthropic.md` via Researcher-Anthropic |
| `/track-google` | Update `drafts/google.md` via Researcher-Google |
| `/track-meta` | Update `drafts/meta.md` via Researcher-Meta |
| `/track-microsoft` | Update `drafts/microsoft.md` via Researcher-Microsoft |
| `/track-vendor <Name>` | Update `drafts/<vendor>.md` via Researcher-Vendor |
| `/track-all` | Update all core vendor drafts (no report generation) |
| `/generate-report` | Read all `drafts/*.md` and write `models.md` via Reporter |
| `/update-report` | Full pipeline: `/track-all` + `/generate-report` |

### Common Workflows

**Update a single vendor:**
```
/track-openai
/generate-report
```

**Add a new vendor:**
1. Add a vendor section to `links.md`
2. `/track-vendor Mistral`
3. `/generate-report`

**Full refresh:**
```
/update-report
```

---

## Architecture

### Two-Phase Pipeline

```
Phase 1 — Research                Phase 2 — Report
┌─────────────────────┐           ┌─────────────────────┐
│ links.md            │           │ drafts/*.md         │
│   ↓                 │           │   ↓                 │
│ Researcher-OpenAI   │ —> .md —> │ Reporter            │
│ Researcher-Anthropic│ ─> .md —> │   ↓                 │
│ Researcher-Google   │ ─> .md —> │ models.md           │
│ Researcher-Meta     │ ─> .md —> │                     │
│ Researcher-Microsoft│ ─> .md —> │                     │
│ Researcher-Vendor   │ ─> .md —> │                     │
└─────────────────────┘           └─────────────────────┘
```

### Key Design Points

- **Each vendor has a dedicated Researcher subagent** that writes only its own `drafts/<vendor>.md`. Refreshing one vendor does not touch others.
- **All Researchers inherit from `BaseResearcher.md`** — shared rules, field schema, source policy, classification rules, and quality checklist live in one place. No duplicated logic.
- **The Reporter reads all `drafts/*.md` and synthesises `models.md`** — it does not browse the web or call Researchers.
- **`links.md` is the source whitelist** — it lists official URLs per vendor. Researchers start from these links before any supplemental search.
- **Chinese-origin model families are excluded** (DeepSeek, Qwen, ERNIE, etc.) unless the project scope is explicitly changed.

### Core vs. Additional Vendors

**Core vendors** have dedicated Researcher agents and dedicated slash commands:
OpenAI, Anthropic, Google, Meta, Microsoft.

**Additional vendors** (e.g., Mistral) are handled by the generic `Researcher-Vendor` via `/track-vendor <Name>`. They are auto-discovered by scanning top-level headings in `links.md`.

---

## Data Schema

Every model row in a draft file uses these fields (defined in `BaseResearcher.md`):

`model_name`, `provider`, `origin_country`, `is_chinese_origin`, `release_date`, `model_type`, `availability_type`, `is_open_weight`, `is_open_source`, `is_online`, `context_length`, `cost_input_per_1m`, `cost_output_per_1m`, `memory_requirement_gb`, `strengths`, `recommended_use_case`, `source`

Required sections in each draft: **API / Closed-weight Models** and **Open-weight Models** (as tables).

---

## Source Policy

1. **Official sources first:** official docs, pricing pages, GitHub repos, Hugging Face org pages, model cards.
2. **Never use third-party summaries** (blogs, Reddit, benchmark leaderboards, news) as primary evidence.
3. **No unsupported guessing** — use `—` for unavailable fields.
4. **Open-weight ≠ open-source** — `is_open_source = true` only when an official recognised license (Apache 2.0, MIT, etc.) is explicitly stated.

---

## Scope Rules

- Include OpenAI API / closed-weight models and OpenAI open-weight models.
- Include official open-weight models only when public weights and license terms are confirmed.
- Do not classify third-party hosted models as belonging to the hosting platform vendor.
- Keep GPT-series, reasoning models, embedding models, realtime/audio/image/video models clearly classified.
- Do not include Chinese-origin model families.
