# Large Language Model Landscape Report

> **Generated**: 2026-05-25
> **Sources**: Vendor draft files (anthropic.md, google.md, meta.md, microsoft.md, mistral.md, openai.md)
> **Data current as of**: Draft last updates between 2026-05-18 and 2026-05-19
>
> **Method**: All model data was extracted from pre-researched vendor draft files. Model names, specs, and pricing have been validated and normalised. Deprecated and retired models are noted but separated. Chinese-origin model families are excluded per project scope.

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Market Overview](#2-market-overview)
3. [API / Closed-weight Models](#3-api--closed-weight-models)
4. [Open-weight Models](#4-open-weight-models)
5. [Vendor Comparison](#5-vendor-comparison)
6. [Pricing Comparison](#6-pricing-comparison)
7. [Context Window Comparison](#7-context-window-comparison)
8. [Scenario-based Recommendations](#8-scenario-based-recommendations)
9. [Model Deprecation & Migration Notes](#9-model-deprecation--migration-notes)
10. [Data Quality Notes](#10-data-quality-notes)

---

## 1. Executive Summary

As of May 2026, the large language model market is dominated by **six major vendors** offering a combined portfolio of **152 unique models** across API/closed-weight and open-weight categories:

- **64 API / Closed-weight Models** (including legacy/superseded)
- **88 Open-weight Models** (including specialist variants)

Key trends:
- **Reasoning models** are now standard across all major vendors (OpenAI o/GPT-5, Anthropic Claude 4.x, Google Gemini 2.5+/3.1, Mistral Magistral/Devstral).
- **1M+ token context windows** are increasingly common in frontier API models.
- **Mixture-of-Experts (MoE)** architectures are widespread across both API and open-weight categories.
- **Multimodality** (text + image + audio + video) is becoming a baseline expectation for flagship models.
- **Open-weight models** have reached frontier-tier capability, with GPT-oss-120b, Llama 4 Maverick, Mistral Large 3, Gemma 4 31B, and Phi-4 matching or approaching API model performance.

---

## 2. Market Overview

| Vendor | API/Closed Models | Open-weight Models | Total Active | Origin |
|---|---|---|---|---|
| Google | 19 | 24 | 43 | United States |
| Meta | 0 | 28 | 28 | United States |
| OpenAI | 26 | 3 | 29 | United States |
| Mistral AI | 8 | 19 | 27 | France |
| Microsoft | 4 | 14 | 18 | United States |
| Anthropic | 7 | 0 | 7 | United States |
| **Total** | **64** | **88** | **152** | — |

> Note: Totals include some models that serve overlapping use cases. "Active" counts exclude deprecated/retired models. Google's count includes specialised image/video/audio generation models.

---

## 3. API / Closed-weight Models

These models are accessible primarily via API with proprietary, non-downloadable weights. They require internet connectivity and are billed per token or per usage unit.

### 3.1 Flagship / Frontier Tier

| Model | Vendor | Type | Context | Input $/1M | Output $/1M | Release |
|---|---|---|---|---|---|---|
| **GPT-5.5 Pro** | OpenAI | reasoning, generation, multimodal | 1.05M | $30.00 | $180.00 | 2026-04 |
| **GPT-5.5** | OpenAI | reasoning, generation, multimodal | 1.05M | $5.00 | $30.00 | 2026-04 |
| **GPT-5.4 Pro** | OpenAI | reasoning, generation, multimodal | 1.0M | $30.00 | $180.00 | 2026-03 |
| **GPT-5.4** | OpenAI | reasoning, generation, multimodal | 1.0M | $2.50 | $15.00 | 2026-03 |
| **Claude Opus 4.7** | Anthropic | generation, multimodal, reasoning | 1.0M | $5.00 | $25.00 | 2026-04 |
| **Claude Opus 4.6** | Anthropic | generation, multimodal, reasoning | 1.0M | $5.00 | $25.00 | 2026-02 |
| **Gemini 3.1 Pro Preview** | Google | generation, reasoning, multimodal | 1.05M | $2.00 / $4.00* | $12.00 / $18.00* | 2026-02 |
| **GPT-5.2 Pro** | OpenAI | reasoning, generation, multimodal | 400K | $21.00 | $168.00 | 2025-12 |
| **GPT-5 Pro** | OpenAI | reasoning, generation, multimodal | 400K | $15.00 | $120.00 | 2025-08 |
| **o1 Pro** | OpenAI | reasoning, generation, multimodal | 200K | $150.00 | $600.00 | 2025-03 |
| **o3 Pro** | OpenAI | reasoning, generation, multimodal | 200K | $20.00 | $80.00 | 2025-06 |
| **Claude Opus 4.5** | Anthropic | generation, multimodal, reasoning | 200K | $5.00 | $25.00 | 2025-11 |
| **Claude Opus 4.1** | Anthropic | generation, multimodal, reasoning | 200K | $15.00 | $75.00 | 2025-08 |

*\*Tiered pricing: lower rate for prompts <=200K tokens, higher rate for >200K tokens.*

### 3.2 Mid-tier / Production Tier

| Model | Vendor | Type | Context | Input $/1M | Output $/1M | Release |
|---|---|---|---|---|---|---|
| **Claude Sonnet 4.6** | Anthropic | generation, multimodal, reasoning | 1.0M | $3.00 | $15.00 | 2026-02 |
| **Claude Sonnet 4.5** | Anthropic | generation, multimodal, reasoning | 200K | $3.00 | $15.00 | 2025-09 |
| **GPT-5.2** | OpenAI | reasoning, generation, multimodal | 400K | $1.75 | $14.00 | 2025-12 |
| **GPT-5.1** | OpenAI | reasoning, generation, multimodal | 400K | $1.25 | $10.00 | 2025-11 |
| **GPT-5** | OpenAI | reasoning, generation, multimodal | 400K | $1.25 | $10.00 | 2025-08 |
| **o1** | OpenAI | reasoning, generation, multimodal | 200K | $15.00 | $60.00 | 2024-09 |
| **o3** | OpenAI | reasoning, generation, multimodal | 200K | $2.00 | $8.00 | 2025-04 |
| **GPT-4.1** | OpenAI | generation, multimodal | 1.05M | $2.00 | $8.00 | 2025-04 |
| **Gemini 2.5 Pro** | Google | generation, reasoning, multimodal | 1.05M | $1.25 / $2.50* | $10.00 / $15.00* | 2025-06 |
| **Gemini 3 Flash Preview** | Google | generation, multimodal | 1.05M | $0.50 | $3.00 | 2025-12 |
| **GPT-4o** | OpenAI | generation, multimodal | 128K | $2.50 | $10.00 | 2024-05 |
| **Mistral Medium 3** | Mistral | generation, multimodal | 128K | $0.40 | $2.00 | 2025-05 |
| **Mistral Medium 3.1 (2508)** | Mistral | generation, multimodal | 131K | $0.40 | $2.00 | 2025-08 |
| **Pixtral Large (2411)** | Mistral | generation, multimodal | 131K | $2.00 | $6.00 | 2024-11 |

### 3.3 Cost-efficient / Fast Tier

| Model | Vendor | Type | Context | Input $/1M | Output $/1M | Release |
|---|---|---|---|---|---|---|
| **GPT-5 nano** | OpenAI | generation, multimodal | 400K | $0.05 | $0.40 | 2025-08 |
| **GPT-5 mini** | OpenAI | reasoning, generation, multimodal | 400K | $0.25 | $2.00 | 2025-08 |
| **GPT-5.4 nano** | OpenAI | generation, multimodal | 400K | $0.20 | $1.25 | 2026-03 |
| **GPT-5.4 mini** | OpenAI | reasoning, generation, multimodal | 400K | $0.75 | $4.50 | 2026-03 |
| **GPT-4.1 nano** | OpenAI | generation, multimodal | 1.05M | $0.10 | $0.40 | 2025-04 |
| **GPT-4.1 mini** | OpenAI | generation, multimodal | 1.05M | $0.40 | $1.60 | 2025-04 |
| **GPT-4o mini** | OpenAI | generation, multimodal | 128K | $0.15 | $0.60 | 2024-07 |
| **o1-mini** | OpenAI | reasoning, generation | 128K | $1.10 | $4.40 | 2024-09 |
| **o3-mini** | OpenAI | reasoning, generation | 200K | $1.10 | $4.40 | 2025-01 |
| **o4-mini** | OpenAI | reasoning, generation, multimodal | 200K | $1.10 | $4.40 | 2025-04 |
| **Claude Haiku 4.5** | Anthropic | generation, multimodal, reasoning | 200K | $1.00 | $5.00 | 2025-10 |
| **Gemini 2.5 Flash-Lite** | Google | generation, multimodal | 1.05M | $0.10 (text) | $0.40 | 2025-07 |
| **Gemini 3.1 Flash-Lite** | Google | generation, multimodal | 1.05M | $0.25 | $1.50 | 2026-05 |
| **Gemini 2.5 Flash** | Google | generation, multimodal | 1.05M | $0.30 (text) | $2.50 | 2025-06 |
| **Codestral (2508)** | Mistral | generation | 256K | $0.30 | $0.90 | 2025-08 |

### 3.4 Specialised API Models (Audio, Image, Video, Embedding, Reasoning)

| Model | Vendor | Type | Context | Pricing | Release |
|---|---|---|---|---|---|
| **gpt-realtime-2** | OpenAI | audio, generation, multimodal | 128K | $4.00 (text) / $32.00 (audio) in; $24.00 / $64.00 out | — |
| **gpt-realtime-1.5** | OpenAI | audio, generation | 32K | $4.00 in / $16.00 out | 2026-05 |
| **gpt-realtime-mini** | OpenAI | audio, generation | 32K | $0.60 in / $2.40 out | — |
| **GPT-4o Transcribe** | OpenAI | audio | 16K | $2.50 in / $10.00 out | — |
| **GPT-4o mini Transcribe** | OpenAI | audio | 16K | $1.25 in / $5.00 out | — |
| **whisper-1** | OpenAI | audio | — | $0.006/min | — |
| **Voxtral Mini Transcribe 2 (2602)** | Mistral | audio | 32K | Per-second audio pricing | 2026-02 |
| **Gemini 3.1 Flash Live Preview** | Google | audio, generation, multimodal | 131K | $0.75 (text) / $3.00 (audio) in | 2026-03 |
| **Gemini 3.1 Flash TTS Preview** | Google | audio, generation | 8K | $1.00 (text) in / $20.00 (audio) out | 2026-04 |
| **Gemini 3.1 Flash Image Preview** | Google | image, multimodal | 131K | $0.25 in / $60.00 out | 2026-02 |
| **Gemini 3 Pro Image Preview** | Google | image, multimodal | — | $2.00 in / $120.00 out | 2025-11 |
| **Imagen 4** | Google | image | 480 | $0.02-0.06/image | 2025-06 |
| **GPT-Image-2** | OpenAI | image, multimodal | — | $5.00 (text) / $8.00 (image) in; $30.00 out | 2026-04 |
| **Veo 3.1** | Google | video, multimodal | 1K | Per-second of video | 2026-01 |
| **Lyria 3 Pro Preview** | Google | audio, generation | — | $0.08/song | 2025-11 |
| **Lyria 3 Clip Preview** | Google | audio, generation | — | $0.04/song | 2025-11 |
| **OCR 3 (2512)** | Mistral | multimodal | — | $2/1000 pages | 2025-12 |
| **Magistral Medium 1.2** | Mistral | reasoning, multimodal | 128K | — | 2025-09 |
| **Gemini Deep Research Pro Preview** | Google | reasoning, generation | 1.05M | — | 2025-12 |
| **Gemini 2.5 Computer Use Preview** | Google | reasoning, multimodal | 128K | $1.25 / $2.50 in; $10.00 / $15.00 out | 2025-10 |
| **Gemini Robotics-ER 1.6 Preview** | Google | reasoning, multimodal | 131K | $1.00 (text) / $2.00 (audio) in; $5.00 out | 2025-12 |
| **MAI-DS-R1** | Microsoft | reasoning | 164K | — | 2025-05 |
| **model-router** | Microsoft | generation | 200K | — | 2025-08 |
| **MAI-Image-2 / 2e** | Microsoft | image | 32K | — | 2025-12 |
| **text-embedding-3-small** | OpenAI | embedding | 8K | $0.02/1M | — |
| **text-embedding-3-large** | OpenAI | embedding | 8K | $0.13/1M | — |
| **Gemini Embedding 001** | Google | embedding | 2K | $0.15/1M | 2025-06 |
| **Gemini Embedding 2** | Google | embedding, multimodal | 8K | $0.20 (text) / $0.45 (image) | 2026-04 |
| **Mistral Embed (2312)** | Mistral | embedding | 8K | $0.10/1M | 2023-12 |

### 3.5 Legacy / Superseded API Models (Still Supported)

| Model | Vendor | Context | Input $/1M | Output $/1M | Notes |
|---|---|---|---|---|---|
| GPT-4 Turbo | OpenAI | 128K | $10.00 | $30.00 | Superseded by GPT-4o / GPT-4.1 |
| GPT-4 | OpenAI | 8K | $30.00 | $60.00 | Superseded |
| GPT-4 32K | OpenAI | 32K | $60.00 | $120.00 | Superseded |
| GPT-3.5 Turbo | OpenAI | 16K | $0.50 | $1.50 | Superseded by GPT-4o mini |
| GPT-3.5 Turbo 16K | OpenAI | 16K | $3.00 | $4.00 | Superseded |
| davinci-002 | OpenAI | 16K | $2.00 | $2.00 | Legacy |
| babbage-002 | OpenAI | 16K | $0.40 | $0.40 | Legacy |
| text-embedding-ada-002 | OpenAI | 8K | $0.10 | — | Still supported, not deprecated |

---

## 4. Open-weight Models

These models provide downloadable weights for local or self-hosted deployment. They range from ultra-lightweight edge models to frontier-tier large models.

### 4.1 Frontier Open-weight Models (>= 20B parameters)

| Model | Vendor | Params | Context | License | Multimodal | Release |
|---|---|---|---|---|---|---|
| **Mistral Large 3 (2512)** | Mistral | 41B active / 675B total | 262K | MRL | text + image | 2025-12 |
| **Mistral Small 4 (2603)** | Mistral | 119B total / 6B active | 256K | Apache 2.0 | text + image | 2026-03 |
| **Mistral Medium 3.5 (2604)** | Mistral | 128B dense | 256K | Modified MIT | text + image | 2026-04 |
| **Devstral 2 (2512)** | Mistral | 123B dense | 256K | Modified MIT | text | 2025-12 |
| **Llama 4 Maverick 17B-128E Instruct** | Meta | 17B active / 400B total | 1.0M | Llama 4 Community | text + image | 2025-04 |
| **Llama 4 Scout 17B-16E Instruct** | Meta | 17B active / 109B total | 10.0M | Llama 4 Community | text + image | 2025-04 |
| **Llama 3.1 405B Instruct** | Meta | 405B dense | 131K | Llama 3.1 Community | text | 2024-07 |
| **Gemma 4 31B** | Google | 31B dense | 256K | Apache 2.0 | text + image + video + audio | 2026-03 |
| **Gemma 4 26B A4B** | Google | 26B MoE | 256K | Apache 2.0 | text + image + video + audio | 2026-03 |
| **gpt-oss-120b** | OpenAI | 117B total / 5.1B active | 128K | Apache 2.0 | text | 2025-08 |
| **Mixtral 8x22B** | Mistral | 141B total / 39B active | 64K | Apache 2.0 | text | 2024-04 |
| **Llama 3.3 70B Instruct** | Meta | 70B dense | 131K | Llama 3.3 Community | text | 2024-12 |
| **Llama 3.1 70B Instruct** | Meta | 70B dense | 131K | Llama 3.1 Community | text | 2024-07 |
| **Phi-3-medium-128k-instruct** | Microsoft | 14B | 131K | MIT | text | 2024-04 |
| **Phi-3-medium-4k-instruct** | Microsoft | 14B | 4K | MIT | text | 2024-04 |

### 4.2 Mid-size Open-weight Models (7B - 20B)

| Model | Vendor | Params | Context | License | Multimodal | Release |
|---|---|---|---|---|---|---|
| **Llama 3.1 8B Instruct** | Meta | 8B | 131K | Llama 3.1 Community | text | 2024-07 |
| **Llama 4 Scout 17B-16E (Base)** | Meta | 17B active / 109B total | 256K | Llama 4 Community | text + image | 2025-04 |
| **Llama 4 Maverick 17B-128E (Base)** | Meta | 17B active / 400B total | 256K | Llama 4 Community | text + image | 2025-04 |
| **Phi-4** | Microsoft | 14B | 16K | MIT | text | 2024-12 |
| **Phi-4-reasoning** | Microsoft | 14B | 33K | MIT | text | 2025-04 |
| **Phi-3-small-128k-instruct** | Microsoft | 7B | 131K | MIT | text | 2024-04 |
| **Phi-3-small-8k-instruct** | Microsoft | 7B | 131K | MIT | text | 2024-04 |
| **Phi-3.5-MoE-instruct** | Microsoft | 6.6B active | 131K | MIT | text | 2024-08 |
| **Gemma 3 27B** | Google | 27B | 128K | Gemma ToU | text + image | 2025-03 |
| **Gemma 3 12B** | Google | 12B | 128K | Gemma ToU | text + image | 2025-03 |
| **Gemma 3 4B** | Google | 4B | 128K | Gemma ToU | text + image | 2025-03 |
| **Gemma 2 27B** | Google | 27B | 8K | Gemma ToU | text | 2024-06 |
| **Gemma 2 9B** | Google | 9B | 8K | Gemma ToU | text | 2024-06 |
| **Mistral Small 3.1 (24B)** | Mistral | 24B | 128K | Apache 2.0 | text + image | 2025-03 |
| **Mistral Small 3.2 (2506)** | Mistral | 24B | 131K | Apache 2.0 | text + image | 2025-06 |
| **Devstral Small 2 (2512)** | Mistral | 24B | 256K | Apache 2.0 | text + image | 2025-12 |
| **Magistral Small (24B)** | Mistral | 24B | — | Apache 2.0 | text | 2025-06 |
| **Ministral 3 14B (2512)** | Mistral | 14B | 262K | Apache 2.0 | text + image | 2025-12 |
| **Ministral 3 8B (2512)** | Mistral | 8B | 262K | Apache 2.0 | text + image | 2025-12 |
| **Mistral Nemo 12B (2407)** | Mistral | 12B | 128K | Apache 2.0 | text | 2024-07 |
| **Meta-Llama-3-70B Instruct** | Meta | 70B | 8K | Llama 3 Community | text | 2024-04 |
| **Llama 2 70B Chat** | Meta | 70B | 4K | Llama 2 Community | text | 2023-07 |
| **Code Llama 70B Instruct** | Meta | 70B | 16K | Llama 2 Community | text | 2024-01 |
| **Code Llama 34B Instruct** | Meta | 34B | 16K | Llama 2 Community | text | 2023-08 |
| **Code Llama 13B Instruct** | Meta | 13B | 16K | Llama 2 Community | text | 2023-08 |
| **Code Llama 7B Instruct** | Meta | 7B | 16K | Llama 2 Community | text | 2023-08 |
| **Meta-Llama-3-8B Instruct** | Meta | 8B | 8K | Llama 3 Community | text | 2024-04 |
| **Llama 2 13B Chat** | Meta | 13B | 4K | Llama 2 Community | text | 2023-07 |
| **Llama 2 7B Chat** | Meta | 7B | 4K | Llama 2 Community | text | 2023-07 |

### 4.3 Lightweight / Edge Open-weight Models (< 7B)

| Model | Vendor | Params | Context | License | Multimodal | Release |
|---|---|---|---|---|---|---|
| **Gemma 4 E4B** | Google | 4B | 128K | Apache 2.0 | text + image + video + audio | 2026-03 |
| **Gemma 4 E2B** | Google | 2B | 128K | Apache 2.0 | text + image + video + audio | 2026-03 |
| **gpt-oss-20b** | OpenAI | 21B total / 3.6B active | 128K | Apache 2.0 | text | 2025-08 |
| **Phi-4-mini-instruct** | Microsoft | 3.8B | 131K | MIT | text | 2025-02 |
| **Phi-4-mini-reasoning** | Microsoft | 3.8B | 128K | MIT | text | 2025-04 |
| **Phi-4-multimodal-instruct** | Microsoft | 5.6B | 131K | MIT | text + image + audio | 2025-02 |
| **Phi-3.5-mini-instruct** | Microsoft | 3.8B | 131K | MIT | text | 2024-08 |
| **Phi-3.5-vision-instruct** | Microsoft | — | 131K | MIT | text + image | 2024-08 |
| **Phi-3-mini-128k-instruct** | Microsoft | 3.8B | 131K | MIT | text | 2024-04 |
| **Phi-3-mini-4k-instruct** | Microsoft | 3.8B | 4K | MIT | text | 2024-04 |
| **Ministral 3 3B (2512)** | Mistral | 3B | 131K | Apache 2.0 | text + image | 2025-12 |
| **Gemma 3 1B** | Google | 1B | 32K | Gemma ToU | text + image | 2025-03 |
| **Gemma 3 270M** | Google | 270M | 32K | Gemma ToU | text | 2025-08 |
| **Gemma 3n E4B** | Google | 4B | 32K | Gemma ToU | text + visual + audio | 2025-06 |
| **Gemma 3n E2B** | Google | 2B | 32K | Gemma ToU | text + visual + audio | 2025-06 |
| **Gemma 2 2B** | Google | 2B | 8K | Gemma ToU | text | 2024-07 |
| **Gemma 1 7B** | Google | 7B | — | Gemma ToU | text | 2024-02 |
| **Gemma 1 2B** | Google | 2B | — | Gemma ToU | text | 2024-02 |
| **Llama 3.2 3B Instruct** | Meta | 3.2B | 131K | Llama 3.2 Community | text | 2024-09 |
| **Llama 3.2 1B Instruct** | Meta | 1.2B | 131K | Llama 3.2 Community | text | 2024-09 |
| **Llama 3.2 11B Vision Instruct** | Meta | 11B | 131K | Llama 3.2 Community | text + image | 2024-09 |
| **Llama 3.2 90B Vision Instruct** | Meta | 90B | 131K | Llama 3.2 Community | text + image | 2024-09 |

### 4.4 Specialist Open-weight Models

| Model | Vendor | Type | Params | Context | License | Release |
|---|---|---|---|---|---|---|
| **Whisper large-v3** | OpenAI | audio | 1.55B | — | MIT | 2023-11 |
| **Whisper large-v3-turbo** | OpenAI | audio | 809M | — | MIT | 2024-09 |
| **Voxtral Mini 3B (2507)** | Mistral | audio | 3B | 32K | Apache 2.0 | 2025-07 |
| **Voxtral Mini 4B Realtime (2602)** | Mistral | audio | 4.4B | 131K | Apache 2.0 | 2026-02 |
| **Voxtral Small 24B (2507)** | Mistral | audio | 24B | 32K | Apache 2.0 | 2025-07 |
| **Voxtral TTS (2603)** | Mistral | audio | 4B | — | CC BY-NC 4.0 | 2026-03 |
| **Codestral Mamba (2407)** | Mistral | generation | 7B | 256K | Apache 2.0 | 2024-07 |
| **Mathstral 7B** | Mistral | reasoning | 7B | 32K | Apache 2.0 | 2024-07 |
| **Leanstral (2603)** | Mistral | generation | 119B total / 6.5B active | 256K | Apache 2.0 | 2026-03 |
| **PaliGemma (3B)** | Google | image | 3B | — | Gemma ToU | 2024-05 |
| **PaliGemma 2 (3B/10B/28B)** | Google | image | 3B-28B | — | Gemma ToU | 2024-12 |
| **ShieldGemma 2 (4B)** | Google | image | 4B | — | Gemma ToU | 2025-03 |
| **MedGemma (4B/27B)** | Google | image | 4B-27B | 128K | Gemma ToU | 2025-05 |
| **MedGemma 1.5 (4B)** | Google | image | 4B | 128K | Gemma ToU | 2026-01 |
| **EmbeddingGemma (308M)** | Google | embedding | 308M | 2K | Gemma ToU | 2025-09 |
| **FunctionGemma (270M)** | Google | generation | 270M | 32K | Gemma ToU | 2025-12 |
| **TranslateGemma (4B/12B/27B)** | Google | generation | 4B-27B | 128K | Gemma ToU | 2026-01 |
| **Llama Guard 4 12B** | Meta | safety | 12B | — | Llama 4 Community | 2025-04 |
| **Llama Guard 3 8B** | Meta | safety | 8B | 131K | Llama 3 Community | 2024-07 |
| **Llama Guard 3 1B** | Meta | safety | 1B | 131K | Llama 3.2 Community | 2024-09 |
| **Llama Guard 3 11B Vision** | Meta | safety | 11B | 131K | Llama 3.2 Community | 2024-09 |
| **DataGemma (2B)** | Google | generation | 2B | — | Gemma ToU | 2024-09 |
| **RecurrentGemma (9B)** | Google | generation | 9B | — | Gemma ToU | 2024-06 |

---

## 5. Vendor Comparison

### 5.1 Strategy Overview

| Vendor | Primary Strategy | Open-weight Commitment | API Revenue Model | Geographic Origin |
|---|---|---|---|---|
| **OpenAI** | API-first, frontier capability leader | Limited (3 models: gpt-oss-120b, gpt-oss-20b, Whisper) | Per-token pricing, broad tier range | United States |
| **Google** | Dual-track: Gemini API + Gemma open-weight | Strong (24 Gemma models, Apache 2.0 for Gemma 4) | Per-token pricing, free tiers available | United States |
| **Meta** | Open-weight-first, ecosystem building | Full (28 models, all open-weight) | No official API pricing; third-party hosting | United States |
| **Mistral AI** | Dual-track: API + open-weight | Strong (19 models, mix of Apache 2.0 and research licenses) | Per-token pricing, Premier tier | France |
| **Microsoft** | Hybrid: Azure AI Foundry + open-weight Phi | Moderate (14 Phi models, MIT license) | Azure-based pricing, serverless API | United States |
| **Anthropic** | API-only, safety-focused | None (0 open-weight models) | Per-token pricing, premium positioning | United States |

### 5.2 Capability Comparison (Flagship Models)

| Dimension | OpenAI GPT-5.5 | Anthropic Claude Opus 4.7 | Google Gemini 3.1 Pro | Mistral Large 3 | Meta Llama 4 Maverick |
|---|---|---|---|---|---|
| **Context Window** | 1.05M | 1.0M | 1.05M | 262K | 1.0M |
| **Input Price** | $5.00/1M | $5.00/1M | $2.00/1M* | $0.50/1M | Free (weights) |
| **Output Price** | $30.00/1M | $25.00/1M | $12.00/1M* | $1.50/1M | Free (weights) |
| **Reasoning** | Yes (configurable) | Yes (adaptive thinking) | Yes | Yes | Yes |
| **Multimodal** | Text + image | Text + image | Text + image + video + audio + PDF | Text + image | Text + image |
| **Architecture** | — (closed) | — (closed) | — (closed) | 41B active / 675B total MoE | 17B active / 400B total MoE |
| **Weights Access** | No | No | No | Yes (MRL) | Yes (Community License) |

### 5.3 Open-weight License Comparison

| Vendor | License Type | Commercial Use | Modification | OSI Approved |
|---|---|---|---|---|
| **Google (Gemma 4)** | Apache 2.0 | Yes | Yes | Yes |
| **Google (Gemma 1-3)** | Gemma Terms of Use | Yes (with conditions) | Yes | No |
| **Meta (Llama 2-4)** | Custom Community License | Yes (700M MAU threshold) | Yes | No |
| **Mistral (most models)** | Apache 2.0 | Yes | Yes | Yes |
| **Mistral (research models)** | MRL / MNPL / Modified MIT | Restricted | Yes | No |
| **Microsoft (Phi)** | MIT | Yes | Yes | Yes |
| **OpenAI (gpt-oss)** | Apache 2.0 | Yes | Yes | Yes |
| **OpenAI (Whisper)** | MIT | Yes | Yes | Yes |

---

## 6. Pricing Comparison

### 6.1 API Model Pricing Tiers (Input $/1M tokens)

| Tier | Models | Price Range |
|---|---|---|
| **Ultra-premium** | o1 Pro ($150), GPT-5.5 Pro ($30), GPT-5.4 Pro ($30), GPT-5.2 Pro ($21), o3 Pro ($20), GPT-5 Pro ($15), Claude Opus 4.1 ($15), o1 ($15) | $15 - $150 |
| **Premium** | GPT-5.5 ($5), Claude Opus 4.7/4.6/4.5 ($5), GPT-5.4 ($2.50), GPT-4 ($30), GPT-4 32K ($60), GPT-4 Turbo ($10) | $2.50 - $60 |
| **Mid-range** | Claude Sonnet 4.6/4.5 ($3), GPT-5.2 ($1.75), GPT-5.1 ($1.25), GPT-5 ($1.25), GPT-4.1 ($2), Gemini 3.1 Pro ($2/$4), Gemini 2.5 Pro ($1.25/$2.50), GPT-4o ($2.50), Pixtral Large ($2), o3 ($2) | $1 - $3 |
| **Cost-efficient** | GPT-5.4 mini ($0.75), GPT-5 mini ($0.25), GPT-5 nano ($0.05), GPT-4.1 mini ($0.40), GPT-4.1 nano ($0.10), GPT-4o mini ($0.15), o1-mini ($1.10), o3-mini ($1.10), o4-mini ($1.10), Claude Haiku 4.5 ($1), Gemini 3 Flash ($0.50), Gemini 2.5 Flash ($0.30), Gemini 2.5 Flash-Lite ($0.10), Gemini 3.1 Flash-Lite ($0.25), Mistral Medium 3 ($0.40), Codestral ($0.30) | $0.05 - $1.10 |

### 6.2 Open-weight Model "Cost" (Self-hosted)

Open-weight models have no per-token API cost but require compute infrastructure. Key cost factors:

| Model Size | Typical VRAM (BF16) | Consumer GPU Feasible | Cloud GPU Est. Cost/hr |
|---|---|---|---|
| < 2B | 2-4 GB | Yes (laptop) | $0.30-0.50 |
| 3-7B | 6-14 GB | Yes (RTX 3060+) | $0.50-1.00 |
| 8-14B | 16-28 GB | Yes (RTX 4090) | $1.00-2.00 |
| 20-40B | 40-80 GB | Marginal (A100) | $2.00-4.00 |
| 70B+ | 140+ GB | No (multi-GPU) | $4.00-12.00 |
| 100B+ MoE | 80-160 GB | No (multi-GPU) | $4.00-15.00 |

---

## 7. Context Window Comparison

### 7.1 API Models by Context Window

| Context | Models |
|---|---|
| **10M+ tokens** | Llama 4 Scout Instruct (10M) -- open-weight only |
| **1M - 1.05M tokens** | GPT-5.5 (1.05M), GPT-5.4 (1.0M), GPT-4.1 (1.05M), Claude Opus 4.7/4.6 (1.0M), Claude Sonnet 4.6 (1.0M), Gemini 3.1 Pro (1.05M), Gemini 2.5 Pro/Flash/Flash-Lite (1.05M), Gemini 3 Flash (1.05M), Gemini 3.1 Flash-Lite (1.05M), Llama 4 Maverick Instruct (1.0M) -- open-weight |
| **400K tokens** | GPT-5.2/5.1/5/Pro/mini/nano (400K), GPT-5.4 mini/nano (400K) |
| **200K - 262K tokens** | Claude Sonnet 4.5/4, Claude Opus 4.5/4.1, Claude Haiku 4.5 (200K), o1/o1 Pro/o3/o3 Pro/o4-mini/o3-mini (200K), Mistral Large 3 (262K), Mistral Small 4 (256K), Mistral Medium 3.5 (256K), Devstral 2 (256K), Ministral 3 8B/14B (262K) |
| **128K - 164K tokens** | GPT-4o (128K), o1-mini (128K), Mistral Medium 3/3.1 (128K/131K), Pixtral Large (131K), MAI-DS-R1 (164K), gpt-oss-120b/20b (128K) |
| **32K - 64K tokens** | GPT-4 32K (32K), Mixtral 8x22B (64K), model-router (200K), Phi-4-reasoning (33K) |
| **8K - 16K tokens** | GPT-4 (8K), GPT-3.5 Turbo (16K), davinci-002 (16K), Phi-4 (16K), Meta-Llama-3 (8K), Code Llama (16K) |

### 7.2 Open-weight Models by Context Window

| Context | Models |
|---|---|
| **10M tokens** | Llama 4 Scout Instruct |
| **1M tokens** | Llama 4 Maverick Instruct |
| **256K - 262K tokens** | Mistral Large 3, Mistral Small 4, Mistral Medium 3.5, Devstral 2, Devstral Small 2, Ministral 3 8B/14B, Gemma 4 26B/31B, Llama 4 Scout/Maverick Base, Codestral Mamba, Leanstral |
| **128K - 131K tokens** | Llama 3.1/3.2/3.3 series, Phi-4-mini, Phi-4-multimodal, Phi-4-mini-reasoning, Phi-3.5 series, Phi-3 small/medium 128k, Ministral 3 3B, Gemma 3 series, Gemma 4 E2B/E4B, gpt-oss-120b/20b, Llama Guard 3 series |
| **32K tokens** | Gemma 3 270M, Gemma 3 1B, Gemma 3n E2B/E4B, FunctionGemma, Mathstral 7B |
| **8K tokens** | Meta-Llama-3 series, Gemma 2 series |
| **4K tokens** | Llama 2 series, Phi-3-mini-4k, Phi-3-medium-4k |

---

## 8. Scenario-based Recommendations

### 8.1 Best for Maximum Intelligence (API)

| Rank | Model | Why |
|---|---|---|
| 1 | **GPT-5.5 Pro** | Highest-tier reasoning and coding; 1.05M context; configurable reasoning effort |
| 2 | **Claude Opus 4.7** | Most capable generally available Claude; step-change in agentic coding; 1M context |
| 3 | **GPT-5.5** | Near-Pro capability at 1/6 the cost; excellent reasoning and coding |

### 8.2 Best for Cost-Sensitive Production (API)

| Rank | Model | Input $/1M | Output $/1M | Why |
|---|---|---|---|---|
| 1 | **GPT-5 nano** | $0.05 | $0.40 | Cheapest GPT-5 tier; 400K context |
| 2 | **Gemini 2.5 Flash-Lite** | $0.10 | $0.40 | 1.05M context; multimodal; free tier available |
| 3 | **GPT-4.1 nano** | $0.10 | $0.40 | 1.05M context; strong instruction following |
| 4 | **Gemini 3.1 Flash-Lite** | $0.25 | $1.50 | 1.05M context; multimodal; frontier-class performance |
| 5 | **GPT-5 mini** | $0.25 | $2.00 | Reasoning support; 400K context |

### 8.3 Best for Open-weight / Self-hosted

| Rank | Model | Params | Context | Why |
|---|---|---|---|---|
| 1 | **Llama 4 Maverick 17B-128E** | 17B active / 400B total | 1.0M | Fits on single H100 (FP8); strong multimodal reasoning; 1M context |
| 2 | **Mistral Large 3** | 41B active / 675B total | 262K | #2 OSS non-reasoning on LMArena; strong generalist |
| 3 | **Gemma 4 31B** | 31B dense | 256K | #3 open model on Arena AI; GPQA Diamond 84.3%; Apache 2.0 |
| 4 | **gpt-oss-120b** | 117B total / 5.1B active | 128K | Near-parity with o4-mini; Apache 2.0; from OpenAI |
| 5 | **Llama 4 Scout 17B-16E** | 17B active / 109B total | 10.0M | Largest context window of any model; fits on single H100 |

### 8.4 Best for Coding & Software Engineering

| Rank | Model | Type | Why |
|---|---|---|---|
| 1 | **GPT-5.5** | API | State-of-the-art coding; configurable reasoning effort |
| 2 | **Claude Opus 4.7** | API | Step-change in agentic coding; adaptive thinking |
| 3 | **Devstral 2 (2512)** | Open-weight (123B) | 72.2% SWE-bench Verified; frontier agentic coding |
| 4 | **Devstral Small 2 (2512)** | Open-weight (24B) | 68.0% SWE-bench Verified; runs on single RTX 4090 |
| 5 | **Codestral (2508)** | API | Code fill-in-the-middle; +30% accepted completions; 256K context |
| 6 | **Phi-4** | Open-weight (14B) | Specializes in complex reasoning, math, and coding; MIT license |

### 8.5 Best for Long Context

| Rank | Model | Context | Type | Why |
|---|---|---|---|---|
| 1 | **Llama 4 Scout Instruct** | 10.0M | Open-weight | Largest context window available in any model |
| 2 | **Llama 4 Maverick Instruct** | 1.0M | Open-weight | 1M context; fits on single H100 |
| 3 | **GPT-5.5 / GPT-5.5 Pro** | 1.05M | API | 1.05M context; frontier reasoning |
| 4 | **GPT-4.1 series** | 1.05M | API | 1.05M context; cost-efficient |
| 5 | **Claude Opus 4.7 / 4.6** | 1.0M | API | 1M context; adaptive thinking |
| 6 | **Claude Sonnet 4.6** | 1.0M | API | 1M context; better price/performance than Opus |
| 7 | **Gemini 3.1 Pro / 2.5 series** | 1.05M | API | 1.05M context; multimodal |
| 8 | **Leanstral (2603)** | 256K | Open-weight | 256K context; formal proof engineering |
| 9 | **Codestral (2508)** | 256K | API | 256K context; code-specialized |

### 8.6 Best for Edge / On-device Deployment

| Rank | Model | Params | Min VRAM | Why |
|---|---|---|---|---|
| 1 | **Gemma 4 E2B** | 2B | 3.2 GB (4-bit) | Runs on phones, Raspberry Pi, Jetson Nano; multimodal |
| 2 | **Gemma 3 270M** | 270M | — | Ultra-lightweight; on-device text generation |
| 3 | **Ministral 3 3B** | 3B | — | Lightweight edge; native multimodal; 40+ languages |
| 4 | **gpt-oss-20b** | 21B total / 3.6B active | 16 GB | Comparable to o3-mini; runs on edge devices with 16GB |
| 5 | **Phi-3-mini-4k-instruct** | 3.8B | — | Compact and efficient; designed for edge and on-device |
| 6 | **Llama 3.2 1B** | 1.2B | ~2.4 GB | Ultra-lightweight; runs on mobile/edge devices |
| 7 | **Devstral Small 2** | 24B | ~16 GB (RTX 4090) | 68% SWE-bench; runs on single consumer GPU |

### 8.7 Best for Multimodal (Vision + Language)

| Rank | Model | Type | Modalities | Why |
|---|---|---|---|---|
| 1 | **GPT-5.5** | API | Text + image | State-of-the-art multimodal reasoning |
| 2 | **Gemini 3 Flash Preview** | API | Text + image + video + audio + PDF | Frontier-class multimodal at low cost |
| 3 | **Claude Opus 4.7** | API | Text + image | Strong multimodal with adaptive thinking |
| 4 | **Llama 4 Maverick Instruct** | Open-weight | Text + image | Fits on single H100; strong multimodal reasoning |
| 5 | **Gemma 4 31B** | Open-weight | Text + image + video + audio | Full multimodality; Apache 2.0; frontier intelligence |
| 6 | **Mistral Small 4** | Open-weight | Text + image | 119B total / 6B active MoE; unified instruct/reasoning/coding |

### 8.8 Best for Audio / Speech

| Rank | Model | Type | Why |
|---|---|---|---|
| 1 | **gpt-realtime-2** | API | Most capable realtime voice model; configurable reasoning |
| 2 | **Gemini 3.1 Flash Live Preview** | API | Low-latency Live API; real-time dialogue |
| 3 | **Voxtral Mini 4B Realtime** | Open-weight | Sub-500ms latency; real-time streaming ASR; single GPU >=16GB |
| 4 | **Whisper large-v3** | Open-weight | Gold standard for multilingual ASR; MIT license |
| 5 | **Voxtral Small 24B** | Open-weight | State-of-the-art transcription and translation |

### 8.9 Best for Embeddings / RAG

| Rank | Model | Type | Dimensions | Why |
|---|---|---|---|---|
| 1 | **Gemini Embedding 2** | API | 128-3072 | Multimodal embeddings (text, image, video, audio) |
| 2 | **text-embedding-3-large** | API | 3072 default | Highest performing OpenAI embedding; 64.6% MTEB |
| 3 | **text-embedding-3-small** | API | 1536 default | 5x cheaper than ada-002; efficient |
| 4 | **EmbeddingGemma (308M)** | Open-weight | 128-768 | On-device; <200MB RAM; <22ms on EdgeTPU; 100+ languages |
| 5 | **Mistral Embed (2312)** | API | 1024 | 1024-dimensional; optimized for semantic search |

### 8.10 Best Value Summary

| Use Case | Best API Choice | Best Open-weight Choice |
|---|---|---|
| Maximum intelligence | GPT-5.5 Pro ($30/$180) | Llama 4 Maverick (free weights) |
| Budget production | GPT-5 nano ($0.05/$0.40) | Ministral 3 3B (free weights) |
| Coding | GPT-5.5 ($5/$30) | Devstral 2 (free weights) |
| Long context | Claude Sonnet 4.6 ($3/$15, 1M ctx) | Llama 4 Scout (10M ctx, free weights) |
| Edge deployment | GPT-4o mini ($0.15/$0.60) | Gemma 4 E2B (free weights, 3.2GB) |
| Multimodal | Gemini 3 Flash ($0.50/$3.00) | Gemma 4 31B (free weights) |
| Audio/Speech | gpt-realtime-mini ($0.60/$2.40) | Whisper large-v3 (free weights) |
| Embeddings | text-embedding-3-small ($0.02) | EmbeddingGemma (free weights) |

---

## 9. Model Deprecation & Migration Notes

### 9.1 Deprecated / Retiring Soon

| Model | Vendor | Status | Retirement Date | Migrate To |
|---|---|---|---|---|
| Claude Opus 4 | Anthropic | Deprecated | 2026-06-15 | Claude Opus 4.7 |
| Claude Sonnet 4 | Anthropic | Deprecated | 2026-06-15 | Claude Sonnet 4.6 |
| Claude Haiku 3.5 | Anthropic | Retired from Claude API | — | Claude Haiku 4.5 |

### 9.2 Superseded (Still Supported)

| Model | Vendor | Superseded By |
|---|---|---|
| GPT-4 Turbo | OpenAI | GPT-4o, GPT-4.1 |
| GPT-4 | OpenAI | GPT-4o, GPT-4.1 |
| GPT-3.5 Turbo | OpenAI | GPT-4o mini |

---

## 10. Data Quality Notes

### 10.1 Completeness

- All six vendor drafts were successfully read and contained substantial model data.
- Draft last update dates ranged from 2026-05-18 to 2026-05-19, indicating very recent data.
- **No drafts were missing, stale, or empty.**

### 10.2 Known Gaps

- **Pricing**: Several API models (particularly Microsoft's MAI series, Mistral's Magistral Medium, Google's Deep Research and Robotics models) do not have publicly listed per-token pricing. These are marked as `---`.
- **Memory requirements**: VRAM requirements for open-weight models are not always officially documented. Where available (Gemma 4 series, gpt-oss series, Devstral Small 2), they are included.
- **Release dates**: Some legacy models (GPT-4 Turbo, GPT-4, GPT-3.5 Turbo, davinci-002, babbage-002) lack confirmed release dates from available sources.
- **Context windows**: A few models (Leanstral, Magistral Small, some Gemma 1/PaliGemma/ShieldGemma variants) have context windows that are inherited from parent models rather than explicitly documented.

### 10.3 Normalisation Applied

- All context window values standardised to numeric tokens (e.g., "128K" shown as "128K" or "131K" for readability).
- All pricing standardised to "per 1 million tokens" in USD.
- Model type categories normalised across vendors (generation, reasoning, multimodal, audio, image, video, embedding).
- License classifications verified against official vendor documentation.
- Chinese-origin model families excluded per project scope.

### 10.4 Exclusions

- **Mixtral 8x7B** (Mistral) — retired March 2025.
- **Pixtral 12B** (Mistral) — deprecated December 2025.
- **Gemini 3 Pro Preview** (Google) — shut down March 9, 2026.
- **Gemini 2.0 Flash / 2.0 Flash-Lite** (Google) — deprecated.
- **Gemini 2.5 Flash Preview 09-2025** (Google) — shut down.
- **Claude Mythos Preview** (Anthropic) — invitation-only research preview, not generally available.
- **gpt-oss-safeguard** (OpenAI) — limited public spec data.
- All third-party models on Azure AI Foundry (DeepSeek, Meta Llama, Cohere, Mistral, xAI) — not Microsoft-owned.
- All Chinese-origin model families.

---

*Report generated by Reporter agent. Data sourced from vendor draft files in `drafts/` directory. For the latest information, refer to official vendor documentation.*
