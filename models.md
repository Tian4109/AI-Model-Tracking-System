# Large Language Model Report

## Introduction

This report synthesises current model data from five major LLM vendors — OpenAI, Anthropic, Google, Meta, and Microsoft — into a practical comparison for stakeholders evaluating AI deployment options. Data is sourced from official vendor documentation and pricing pages, structured via intermediate draft files in `drafts/`.

The scope covers both API/closed-weight models (accessible via cloud endpoints) and open-weight models (publicly downloadable for self-hosted deployment). Chinese-origin model families are excluded per project scope.

## Executive Summary

The LLM landscape as of May 2026 is characterised by:

- **Frontier reasoning models** from OpenAI (GPT-5.5, o3/o4 series), Anthropic (Claude Opus 4.7), and Google (Gemini 3.1 Pro) competing on complex reasoning, coding, and agentic workflows, with context windows now standardised at 1M+ tokens.
- **Cost-efficient tiers** expanding rapidly: OpenAI's GPT-5.4 nano ($0.20/$1.25), Google's Gemini 3.1 Flash-Lite ($0.25/$1.50), and Anthropic's Haiku 4.5 ($1.00/$5.00) make high-volume production workloads economically viable.
- **Open-weight models** growing in capability: Meta's Llama 4 Maverick (400B total params, 10M context), Google's Gemma 4 31B (frontier-level on single H100), and OpenAI's gpt-oss-120b (Apache 2.0) narrow the gap with closed-weight frontier models.
- **Multimodality** is now table stakes across all vendors, with text, image, audio, and video support in flagship models.
- **Specialised models** for embedding, image generation, video generation, music generation, robotics, and safety classification are increasingly available alongside general-purpose LLMs.

## Vendor Coverage

| Vendor | API/Closed-Weight Models | Open-Weight Models | Total |
|---|---|---|---|
| OpenAI | 38 | 4 | 42 |
| Anthropic | 10 | 0 | 10 |
| Google | 20 | 27 | 47 |
| Meta | 0 | 22 | 22 |
| Microsoft | 4 | 13 | 17 |
| **Total** | **72** | **66** | **138** |

## API / Closed-Weight Models

### Flagship Generation & Reasoning Models

| Model | Provider | Context | Input $/1M | Output $/1M | Release |
|---|---|---|---|---|---|
| GPT-5.5 | OpenAI | 1M | $5.00 | $30.00 | 2026-04 |
| GPT-5.5 Pro | OpenAI | 1M | $30.00 | $180.00 | 2026-04 |
| GPT-5.4 | OpenAI | 1M | $2.50 | $15.00 | 2026-03 |
| GPT-5.4 Pro | OpenAI | 1M | $30.00 | $180.00 | 2026-03 |
| Claude Opus 4.7 | Anthropic | 1M | $5.00 | $25.00 | 2026-04 |
| Claude Opus 4.6 | Anthropic | 1M | $5.00 | $25.00 | 2026-02 |
| Claude Sonnet 4.6 | Anthropic | 1M | $3.00 | $15.00 | 2026-02 |
| Gemini 3.1 Pro Preview | Google | 1M | $2.00/$4.00* | $12.00/$18.00* | 2026-02 |
| Gemini 2.5 Pro | Google | 1M | $1.25/$2.50* | $10.00/$15.00* | 2025-06 |

*Tiered pricing: lower rate for prompts ≤200K tokens, higher rate above.

### Mid-Tier & Cost-Efficient Models

| Model | Provider | Context | Input $/1M | Output $/1M | Release |
|---|---|---|---|---|---|
| GPT-5.4 mini | OpenAI | 400K | $0.75 | $4.50 | 2026-03 |
| GPT-5.1 | OpenAI | 400K | $1.25 | $10.00 | 2025-11 |
| GPT-5 | OpenAI | 400K | $1.25 | $10.00 | 2025-08 |
| Claude Sonnet 4.5 | Anthropic | 200K | $3.00 | $15.00 | 2025-09 |
| Claude Haiku 4.5 | Anthropic | 200K | $1.00 | $5.00 | 2025-10 |
| Gemini 3 Flash Preview | Google | 1M | $0.50 | $3.00 | 2025-12 |
| Gemini 3.1 Flash-Lite | Google | 1M | $0.25 | $1.50 | 2026-05 |
| Gemini 2.5 Flash | Google | 1M | $0.30 | $2.50 | 2025-06 |
| Gemini 2.5 Flash-Lite | Google | 1M | $0.10 | $0.40 | 2025-07 |

### Reasoning-Specialised Models

| Model | Provider | Context | Input $/1M | Output $/1M | Release |
|---|---|---|---|---|---|
| o1 | OpenAI | 200K | $15.00 | $60.00 | 2024-09 |
| o1 Pro | OpenAI | 200K | $150.00 | $600.00 | 2025-03 |
| o3 | OpenAI | 200K | $2.00 | $8.00 | 2025-04 |
| o3 Pro | OpenAI | 200K | $20.00 | $80.00 | 2025-06 |
| o4-mini | OpenAI | 200K | $1.10 | $4.40 | 2025-04 |
| o3-mini | OpenAI | 200K | $1.10 | $4.40 | 2025-01 |
| o1-mini | OpenAI | 128K | $1.10 | $4.40 | 2024-09 |
| MAI-DS-R1 | Microsoft | 163K | — | — | 2025-05 |

### Embedding Models

| Model | Provider | Context | Input $/1M |
|---|---|---|---|
| text-embedding-3-small | OpenAI | 8K | $0.02 |
| text-embedding-3-large | OpenAI | 8K | $0.13 |
| text-embedding-ada-002 | OpenAI | 8K | $0.10 |
| Gemini Embedding 2 | Google | 8K | $0.20 (text) |
| Gemini Embedding 001 | Google | 2K | $0.15 |

### Audio Models

| Model | Provider | Context | Input $/1M | Output $/1M |
|---|---|---|---|---|
| gpt-realtime-2 | OpenAI | 128K | $4.00 (text) / $32.00 (audio) | $24.00 (text) / $64.00 (audio) |
| gpt-realtime-1.5 | OpenAI | 32K | $4.00 | $16.00 |
| gpt-realtime-mini | OpenAI | 32K | $0.60 | $2.40 |
| GPT-4o Transcribe | OpenAI | 16K | $2.50 | $10.00 |
| GPT-4o mini Transcribe | OpenAI | 16K | $1.25 | $5.00 |
| Gemini 3.1 Flash Live Preview | Google | 131K | $0.75 (text) / $3.00 (audio) | $4.50 (text) / $12.00 (audio) |
| Gemini 3.1 Flash TTS Preview | Google | 8K | $1.00 (text) | $20.00 (audio) |
| TTS-1 | OpenAI | — | $15.00/1M chars | — |
| TTS-1 HD | OpenAI | — | $30.00/1M chars | — |

### Image & Video Generation Models

| Model | Provider | Type | Pricing |
|---|---|---|---|
| GPT-Image-2 | OpenAI | Image | $5.00/$8.00 input, $30.00 output/1M tokens |
| Gemini 3.1 Flash Image Preview (Nano Banana 2) | Google | Image | $0.25 input, $60.00 output/1M tokens |
| Gemini 3 Pro Image Preview (Nano Banana Pro) | Google | Image | $2.00 input, $120.00 output/1M tokens |
| Imagen 4 (Standard/Ultra/Fast) | Google | Image | $0.02–$0.06 per image |
| Veo 3.1 (Standard/Fast) | Google | Video | Per-second pricing |
| Lyria 3 Pro Preview | Google | Music | $0.08 per song |
| Lyria 3 Clip Preview | Google | Music | $0.04 per song |
| MAI-Image-2 / MAI-Image-2e | Microsoft | Image | — |

### Specialised API Models

| Model | Provider | Type | Context |
|---|---|---|---|
| Gemini Deep Research Pro Preview | Google | Research agent | 1M |
| Gemini 2.5 Computer Use Preview | Google | UI automation | 128K |
| Gemini Robotics-ER 1.6 Preview | Google | Robotics reasoning | 131K |
| model-router | Microsoft | LLM routing | 200K |

## Open-Weight Models

### Large-Scale Open-Weight Models (70B+)

| Model | Provider | Params | Context | License | Open-Source |
|---|---|---|---|---|---|
| Llama 4 Maverick 17B-128E Instruct | Meta | 17B active / 400B total (MoE) | 1M | Llama 4 Community License | No |
| Llama 4 Scout 17B-16E Instruct | Meta | 17B active / 109B total (MoE) | 10M | Llama 4 Community License | No |
| Llama 3.1 405B Instruct | Meta | 405B dense | 128K | Llama 3.1 Community License | No |
| Gemma 4 31B | Google | 31B dense | 256K | Apache 2.0 | Yes |
| Gemma 4 26B A4B | Google | 26B MoE | 256K | Apache 2.0 | Yes |

### Mid-Scale Open-Weight Models (10B–30B)

| Model | Provider | Params | Context | License | Open-Source |
|---|---|---|---|---|---|
| Llama 3.3 70B Instruct | Meta | 70B | 128K | Llama 3.3 Community License | No |
| Llama 3.1 70B Instruct | Meta | 70B | 128K | Llama 3.1 Community License | No |
| Gemma 3 27B | Google | 27B | 128K | Gemma Terms of Use | No |
| Gemma 2 27B | Google | 27B | 8K | Gemma Terms of Use | No |
| Phi-4 | Microsoft | 14B | 16K | MIT | Yes |
| Phi-3-medium-4k/128k-instruct | Microsoft | 14B | 4K/128K | MIT | Yes |

### Compact Open-Weight Models (<10B)

| Model | Provider | Params | Context | License | Open-Source |
|---|---|---|---|---|---|
| Llama 3.1 8B Instruct | Meta | 8B | 128K | Llama 3.1 Community License | No |
| Llama 3.2 1B Instruct | Meta | 1.23B | 128K | Llama 3.2 Community License | No |
| Llama 3.2 3B Instruct | Meta | 3.21B | 128K | Llama 3.2 Community License | No |
| gpt-oss-120b | OpenAI | 117B total / 5.1B active (MoE) | 128K | Apache 2.0 | Yes |
| gpt-oss-20b | OpenAI | 21B total / 3.6B active (MoE) | 128K | Apache 2.0 | Yes |
| Gemma 4 E4B | Google | 4B | 128K | Apache 2.0 | Yes |
| Gemma 4 E2B | Google | 2B | 128K | Apache 2.0 | Yes |
| Gemma 3 12B | Google | 12B | 128K | Gemma Terms of Use | No |
| Gemma 3 4B | Google | 4B | 128K | Gemma Terms of Use | No |
| Gemma 3 1B | Google | 1B | 32K | Gemma Terms of Use | No |
| Phi-4-mini-instruct | Microsoft | 3.8B | 128K | MIT | Yes |
| Phi-4-multimodal-instruct | Microsoft | 5.6B | 128K | MIT | Yes |
| Phi-4-reasoning | Microsoft | — | 32K | MIT | Yes |
| Phi-4-mini-reasoning | Microsoft | — | 128K | MIT | Yes |
| Phi-3.5-mini-instruct | Microsoft | 3.8B | 128K | MIT | Yes |
| Phi-3.5-MoE-instruct | Microsoft | 6.6B active | 128K | MIT | Yes |
| Phi-3-mini-4k/128k-instruct | Microsoft | 3.8B | 4K/128K | MIT | Yes |
| Phi-3-small-8k/128k-instruct | Microsoft | 7B | 128K | MIT | Yes |

### Specialised Open-Weight Models

| Model | Provider | Type | Context | License |
|---|---|---|---|---|
| Llama Guard 4 12B | Meta | Safety classifier (multimodal) | — | Llama 4 Community License |
| Llama Guard 3 8B | Meta | Safety classifier (text) | 128K | Llama 3 Community License |
| Llama Guard 3 1B | Meta | Safety classifier (text) | 128K | Llama 3.2 Community License |
| Llama Guard 3 11B Vision | Meta | Safety classifier (multimodal) | 128K | Llama 3.2 Community License |
| Code Llama 7B/13B/34B/70B Instruct | Meta | Code generation | 16K | Llama 2 Community License |
| Llama 3.2 11B/90B Vision Instruct | Meta | Multimodal (vision) | 128K | Llama 3.2 Community License |
| Gemma 3n E2B/E4B | Google | Edge multimodal | 32K | Gemma Terms of Use |
| PaliGemma (3B / 3B,10B,28B) | Google | Vision-language | — | Gemma Terms of Use |
| ShieldGemma 2 (4B) | Google | Image safety | — | Gemma Terms of Use |
| FunctionGemma (270M) | Google | Function calling | 32K | Gemma Terms of Use |
| EmbeddingGemma (308M) | Google | Text embedding | 2K | Gemma Terms of Use |
| TranslateGemma (4B/12B/27B) | Google | Translation | 128K | Gemma Terms of Use |
| MedGemma (4B/27B) | Google | Medical imaging | 128K | Gemma Terms of Use |
| Whisper large-v3 | OpenAI | Speech recognition | — | MIT |
| Whisper large-v3-turbo | OpenAI | Speech recognition | — | MIT |

## Comparative Analysis

### Pricing Tiers (Input $/1M tokens, cheapest to most expensive)

| Tier | Models | Input $/1M |
|---|---|---|
| Ultra-low | GPT-5 nano ($0.05), GPT-5.4 nano ($0.20), GPT-4.1 nano ($0.10), GPT-3.5 Turbo ($0.50) | $0.05–$0.50 |
| Low | Gemini 2.5 Flash-Lite ($0.10), Gemini 3.1 Flash-Lite ($0.25), GPT-5 mini ($0.25), GPT-4o mini ($0.15) | $0.10–$0.30 |
| Mid | GPT-5.4 mini ($0.75), GPT-5.1 ($1.25), GPT-5 ($1.25), Claude Haiku 4.5 ($1.00), o4-mini ($1.10) | $0.75–$1.25 |
| High | Claude Sonnet 4.6 ($3.00), GPT-4.1 ($2.00), GPT-4o ($2.50), GPT-5.4 ($2.50) | $2.00–$3.00 |
| Premium | Claude Opus 4.7 ($5.00), GPT-5.5 ($5.00), o1 ($15.00) | $5.00–$15.00+ |

### Context Window Comparison

| Context | Models |
|---|---|
| 10M | Llama 4 Scout (open-weight) |
| 1M | GPT-5.5/5.4, Claude Opus 4.7/4.6, Sonnet 4.6, Gemini 3.1 Pro, 3 Flash, 2.5 Pro/Flash/Flash-Lite, GPT-4.1, Llama 4 Maverick |
| 200K–400K | Claude Opus 4.5/4.1, Sonnet 4.5/4, GPT-5.2/5/5.1 (+ Pro variants), o1/o3/o4-mini, GPT-4o |
| 128K | Llama 3.1/3.2/3.3, Gemma 3/4, Phi-4 series, gpt-oss, GPT-4o |
| ≤32K | Gemma 3 1B/270M, Gemma 3n, Phi-3-mini-4k, GPT-4, GPT-3.5 Turbo |

### Deployment Flexibility

| Deployment Option | Vendors & Models |
|---|---|
| API only | All OpenAI API models, all Anthropic Claude models, all Google Gemini API models, Microsoft MAI series |
| Open-weight (self-hosted) | All Meta Llama, all Gemma, all Phi, OpenAI gpt-oss & Whisper |
| Hybrid (API + self-host) | Microsoft Phi series (Azure API + downloadable weights) |

### Licensing Comparison

| License Type | Models |
|---|---|
| Apache 2.0 (OSI-approved) | Gemma 4 series, OpenAI gpt-oss-120b/20b |
| MIT (OSI-approved) | Microsoft Phi series, OpenAI Whisper |
| Custom community license | Meta Llama 2/3/4 series (commercial use permitted with conditions) |
| Custom vendor license | Gemma 1/2/3/3n (Gemma Terms of Use) |
| Proprietary / API-only | All OpenAI API models, all Anthropic models, all Google Gemini API models |

## Scenario-Based Recommendations

### 1. High-Volume Production Chat (Cost-Sensitive)
**Recommendation:** Gemini 2.5 Flash-Lite or GPT-4o mini
- Both offer sub-$0.10/$0.50 per 1M token pricing with 1M context windows.
- Gemini 2.5 Flash-Lite is the cheapest option at $0.10/$0.40 with multimodal support.
- GPT-4o mini at $0.15/$0.60 is a strong alternative with broad ecosystem support.

### 2. Complex Reasoning & Agentic Workloads
**Recommendation:** GPT-5.4 or Claude Opus 4.7
- GPT-5.4 ($2.50/$15.00) offers configurable reasoning effort and strong coding benchmarks at a moderate price.
- Claude Opus 4.7 ($5.00/$25.00) provides the highest capability for the most demanding enterprise tasks with 1M context and 128K max output.
- For budget-constrained reasoning: o4-mini ($1.10/$4.40) delivers strong STEM and coding performance.

### 3. Long-Context Document Processing
**Recommendation:** Llama 4 Scout (open-weight) or Gemini 3.1 Pro (API)
- Llama 4 Scout offers a 10M token context window — the largest available — and can run on a single H100 with int4 quantization.
- Gemini 3.1 Pro provides 1M context via API with tiered pricing, suitable when self-hosting is not feasible.
- GPT-4.1 (1M context, $2.00/$8.00) is a cost-effective API alternative.

### 4. Self-Hosted / On-Premises Deployment
**Recommendation:** Llama 4 Maverick or Gemma 4 31B
- Llama 4 Maverick (17B active / 400B total, 1M context) fits on a single H100 with FP8 and supports native multimodality.
- Gemma 4 31B (Apache 2.0) offers frontier-level performance with a permissive open-source license, ranked #3 open model on Arena AI.
- For resource-constrained environments: gpt-oss-20b (16GB VRAM) or Gemma 4 E2B (runs on mobile/edge).

### 5. Edge & On-Device AI
**Recommendation:** Gemma 4 E2B or Llama 3.2 1B
- Gemma 4 E2B runs on phones, Raspberry Pi, and Jetson Nano with near-zero latency and multimodal support.
- Llama 3.2 1B (~2.4GB) is proven for mobile and edge deployment.
- Microsoft Phi-4-mini-instruct (3.8B, 128K context) offers strong capability in a small footprint.

### 6. Code Generation & Software Engineering
**Recommendation:** GPT-5.4 or Claude Opus 4.7
- GPT-5.4 is specifically noted for strong coding and professional work at $2.50/$15.00.
- Claude Opus 4.7 provides step-change improvement in agentic coding.
- For open-weight: Code Llama 70B supports up to 100K inference context for large codebases.

### 7. Multimodal Applications (Vision + Language)
**Recommendation:** Gemini 2.5 Flash or Llama 3.2 90B Vision
- Gemini 2.5 Flash supports text, image, video, and audio input via API at $0.30/$2.50.
- Llama 3.2 90B Vision offers strong document AI and visual reasoning as an open-weight model.
- Gemma 3 4B/12B/27B provide multimodal open-weight options at various scales.

### 8. Content Safety & Moderation
**Recommendation:** Llama Guard 4 12B or ShieldGemma 2
- Llama Guard 4 12B supports multimodal (text + image) safety classification across 14 hazard categories.
- ShieldGemma 2 provides image-specific safety filtering.
- Both are open-weight and can be self-hosted for data privacy.

### 9. Speech-to-Text & Voice
**Recommendation:** GPT-4o Transcribe or Whisper large-v3
- GPT-4o Transcribe offers improved word error rates over original Whisper with API convenience.
- Whisper large-v3 (MIT License, open-weight) is suitable for offline/self-hosted transcription.
- For realtime voice: gpt-realtime-2 supports text and audio I/O with configurable reasoning.

### 10. Image Generation
**Recommendation:** Imagen 4 or GPT-Image-2
- Imagen 4 offers per-image pricing ($0.02–$0.06) with improved text rendering and SynthID watermarking.
- GPT-Image-2 supports up to 4K resolution with multiple quality levels.
- For high-volume: Gemini 3.1 Flash Image Preview at $0.25/$60.00 per 1M tokens.

## Vendor Notes

### OpenAI
- Broadest model portfolio spanning generation, reasoning, embedding, audio, image, and realtime voice.
- GPT-5.x series introduces configurable reasoning effort levels (low/medium/high/xhigh).
- o-series (o1, o3, o4-mini) provides dedicated reasoning models with tool use capabilities.
- First open-weight models released: gpt-oss-120b/20b (Apache 2.0, August 2025) and Whisper (MIT).
- Legacy models (GPT-4, GPT-3.5 Turbo, davinci-002, babbage-002) remain available but are superseded.

### Anthropic
- Focused portfolio with three tiers: Opus (highest capability), Sonnet (balanced), Haiku (fastest).
- All models are API-only with no open-weight offerings.
- 1M context window now available on Opus 4.7/4.6 and Sonnet 4.6.
- Two models deprecated (Opus 4, Sonnet 4) with retirement date June 15, 2026.
- Haiku 3.5 retired from Claude API but still available on Bedrock/Vertex AI.

### Google
- Largest total model count when including Gemma open-weight family.
- Gemini 3.1 Pro features tiered pricing (2x above 200K tokens).
- Gemma 4 (March 2026) is the first Gemma model under Apache 2.0; prior generations use custom Gemma Terms of Use.
- Broadest media generation suite: Imagen (image), Veo (video), Lyria (music).
- Specialised models for robotics (Robotics-ER), computer use, and deep research.
- Several deprecated models excluded from this report (Gemini 2.0 series, Gemini 3 Pro Preview).

### Meta
- Entirely open-weight portfolio — no closed-weight API-only models.
- Llama 4 series introduces Mixture-of-Experts architecture with native multimodality and extreme context windows (up to 10M tokens for Scout).
- All Llama models use custom community licenses (not OSI-approved open-source).
- Code Llama and Llama Guard provide specialised code generation and safety classification.
- Llama 2 models have limited 4K context; Llama 3+ models support 128K+.

### Microsoft
- Phi family is the core offering: compact, MIT-licensed, hybrid deployment (API + downloadable).
- Phi-4 series adds multimodal, reasoning, and mini variants.
- MAI-Image, MAI-DS-R1, and model-router are Microsoft-developed API models on Azure AI Foundry.
- Phi models are notable for their small size-to-capability ratio and permissive MIT license.
- Azure AI Foundry hosts many third-party models (excluded from this report).

## Excluded Models and Scope Notes

- **Chinese-origin model families** (DeepSeek, Qwen, ERNIE, GLM, Kimi, MiniMax, Baichuan, Yi, InternLM) are excluded per project scope.
- **Deprecated/retired models** are generally excluded unless still accessible (e.g., Claude Opus 4/Sonnet 4 marked as deprecated with retirement date noted).
- **Third-party models on platform marketplaces** (e.g., DeepSeek on Azure AI Foundry, Meta Llama on Azure) are attributed to their original vendor, not the platform host.
- **MAI-DS-R1** is included as a Microsoft model per official Foundry documentation, though it is derived from DeepSeek-R1 (Chinese-origin base). Users should be aware of this provenance.
- **Preview/research-only models** are included but should not be used as stable production defaults.

## Notes and Limitations

- This report is generated from existing vendor draft files last updated 2026-05-18.
- Pricing is in USD per 1M tokens and may change. Tiered pricing is noted where applicable.
- Missing or unavailable values are shown as `—`.
- Recommendations are AI-assisted and should be validated against specific project requirements.
- Open-weight does not always mean open-source. Licensing terms vary significantly between vendors and model generations.
- Context windows reflect maximum documented values; actual usable context may vary by deployment configuration.
- Memory requirements for open-weight models depend heavily on quantization and are not officially documented in most cases.
- Not all models may be available in all regions.
