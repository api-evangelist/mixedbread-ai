# Mixedbread (mixedbread-ai)

Mixedbread is a Berlin-based AI search and retrieval platform. It pairs open-weight embedding and reranking
models (mxbai-embed, Wholembed v3, mxbai-rerank v1/v2/v3-listwise) with a hosted REST API at
`api.mixedbread.com` that ships multimodal stores, document parsing, structured extraction, and connector-based
ingestion. Models are published on Hugging Face; the platform powers RAG and agent retrieval across text, PDFs,
images, audio, and video in 100+ languages.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/mixedbread-ai/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

 - AI, Artificial Intelligence, Embeddings, Reranking, Search, Retrieval, RAG, Vector Database, Multimodal, Parsing, Open Weights

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## Models

| Model | Type | Modality | Parameters | Notes |
|---|---|---|---|---|
| `mixedbread-ai/wholembed-v3` | Embedding | Omnimodal (text/image/audio/video), multilingual | — | Default store retriever; SOTA on LIMIT and BrowseComp-Plus (Mar 2026). |
| `mixedbread-ai/mxbai-embed-large-v1` | Embedding | Text | 0.3B | Matryoshka + binary embeddings; 4.7M+ downloads on HF. |
| `mixedbread-ai/mxbai-embed-xsmall-v1` | Embedding | Text | 24M | Edge-deployable. |
| `mixedbread-ai/deepset-mxbai-embed-de-large-v1` | Embedding | German text | 0.5B | German-optimised, jointly with deepset. |
| `mixedbread-ai/mxbai-edge-colbert-v0-32m` | Late-interaction | Text | 32M | ColBERT-style for on-device retrieval. |
| `mixedbread-ai/mxbai-edge-colbert-v0-17m` | Late-interaction | Text | 17M | Smallest edge ColBERT variant. |
| `mxbai-rerank-v3-listwise` | Reranker | Text | — | Instruction-following listwise reranker (May 2026). |
| `mixedbread-ai/mxbai-rerank-large-v2` | Reranker | Text | 2B | Strongest pointwise reranker. |
| `mixedbread-ai/mxbai-rerank-base-v2` | Reranker | Text | 0.5B | Balanced size/quality. |
| `mixedbread-ai/mxbai-rerank-large-v1` | Reranker | Text | — | v1 generation, broadly deployed. |
| `mixedbread-ai/mxbai-rerank-base-v1` | Reranker | Text | 0.2B | — |
| `mixedbread-ai/mxbai-rerank-xsmall-v1` | Reranker | Text | 71M | Lightweight inference. |

## APIs

### Mixedbread Embeddings API
`POST /v1/embeddings` creates dense or multi-encoding embeddings for text and images. Supports Matryoshka
dimensions, binary/int8/float32 encodings, normalization, and prompt instructions.

**Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)

- [OpenAPI](openapi/mixedbread-embeddings-api-openapi.yml)
- [JSON Schema](json-schema/mixedbread-embedding-schema.json)
- [JSON-LD](json-ld/mixedbread-ai-context.jsonld)
- [Naftiko Capability — Embeddings](capabilities/embeddings-embeddings.yaml)
- [Example](examples/mixedbread-embeddings-example.json)

### Mixedbread Reranking API
`POST /v1/reranking` reorders candidate documents against a query using mxbai-rerank v1/v2 plus the
v3-listwise instruction-following reranker. Documents may be strings or structured objects with `rank_fields`.

**Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)

- [OpenAPI](openapi/mixedbread-reranking-api-openapi.yml)
- [JSON Schema](json-schema/mixedbread-rerank-schema.json)
- [Naftiko Capability — Reranking](capabilities/reranking-reranking.yaml)
- [Example](examples/mixedbread-reranking-example.json)

### Mixedbread Stores API
Multimodal search indexes. CRUD on `/v1/stores` plus per-store file management, semantic search, regex grep,
chunk listing, question answering, query enhancement, metadata facets, search rules, and events. Replaces the
deprecated `/v1/vector_stores` surface (kept for backward compatibility).

**Human URL:** [https://www.mixedbread.com/docs/stores/overview](https://www.mixedbread.com/docs/stores/overview)

- [OpenAPI](openapi/mixedbread-stores-api-openapi.yml)
- [JSON Schema — Store](json-schema/mixedbread-store-schema.json)
- [Naftiko Capability — Stores CRUD](capabilities/stores-stores.yaml)
- [Naftiko Capability — Store Files](capabilities/stores-files.yaml)
- [Naftiko Capability — Search & QA](capabilities/stores-search.yaml)
- [Example](examples/mixedbread-stores-search-example.json)

### Mixedbread Parsing API
Asynchronous document parsing as jobs. `POST /v1/parsing/jobs` starts a parse with configurable chunking
strategy and return format (markdown/HTML/text). Produces typed chunks for text, code, tables, images, audio,
and video.

**Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)

- [OpenAPI](openapi/mixedbread-parsing-api-openapi.yml)
- [Naftiko Capability — Parsing Jobs](capabilities/parsing-jobs.yaml)

### Mixedbread Extractions API
Schema-guided structured extraction. `POST /v1/extractions/jobs` runs against a file; `POST /v1/extractions/content`
extracts from raw strings. `/v1/extractions/schema` create / enhance / validate JSON Schemas that drive the
extraction pipeline.

**Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)

- [OpenAPI](openapi/mixedbread-extractions-api-openapi.yml)
- [Naftiko Capability — Extraction Jobs](capabilities/extractions-jobs.yaml)
- [Naftiko Capability — Schema](capabilities/extractions-schema.yaml)

### Mixedbread Files API
Workspace file storage shared across stores, parsing, and extraction. Single-shot `POST /v1/files` plus
multipart upload via `/v1/files/uploads` (create / complete / abort / list) and standard CRUD plus content
download.

**Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)

- [OpenAPI](openapi/mixedbread-files-api-openapi.yml)
- [Naftiko Capability — Files](capabilities/files-files.yaml)
- [Naftiko Capability — Multipart Uploads](capabilities/files-uploads.yaml)

### Mixedbread Chat Completions API
`POST /v1/chat/completions` is an OpenAI-compatible chat surface that grounds responses in Mixedbread Stores.
Drives question-answering and agentic flows over indexed multimodal content.

- [OpenAPI](openapi/mixedbread-completions-api-openapi.yml)
- [Naftiko Capability — Chat](capabilities/completions-chat.yaml)

### Mixedbread Data Sources API
Manage external data sources and their connectors, including OAuth2 authorization/callback flows. Used to
ingest content from third-party SaaS systems into stores.

- [OpenAPI](openapi/mixedbread-data-sources-api-openapi.yml)
- [Naftiko Capability — Data Sources](capabilities/data-sources-data-sources.yaml)
- [Naftiko Capability — Connectors](capabilities/data-sources-connectors.yaml)

### Mixedbread API Keys API
CRUD plus rotation (reroll) and revocation under `/v1/api-keys`.

- [OpenAPI](openapi/mixedbread-api-keys-api-openapi.yml)
- [Naftiko Capability — API Keys](capabilities/api-keys-api-keys.yaml)

### Mixedbread Billing API
Read-only billing telemetry — workspace summary, per-store costs, and parsing/store cost histograms. Maps to
the FOCUS-aligned FinOps definition in this repo.

- [OpenAPI](openapi/mixedbread-billing-api-openapi.yml)
- [Naftiko Capability — Billing](capabilities/billing-billing.yaml)

### Mixedbread Schemas API
`GET /v1/schemas/mxjson` returns the canonical mxbai JSON schema for client validation.

- [OpenAPI](openapi/mixedbread-schemas-api-openapi.yml)

### Mixedbread Admin API
Platform-administrator operations. `POST /v1/admin/stores/{organization_id}/{store_identifier}/reingest`
triggers a full tenant-store reingest.

- [OpenAPI](openapi/mixedbread-admin-api-openapi.yml)

## SDKs

- **Python:** [`mixedbread-ai/mixedbread-python`](https://github.com/mixedbread-ai/mixedbread-python) (current), [`mixedbread-ai/python-sdk`](https://github.com/mixedbread-ai/python-sdk) (legacy)
- **TypeScript:** [`mixedbread-ai/mixedbread-ts`](https://github.com/mixedbread-ai/mixedbread-ts) (current), [`mixedbread-ai/typescript-sdk`](https://github.com/mixedbread-ai/typescript-sdk) (legacy)
- **CLI:** Mixedbread CLI for bulk document syncing — `mxbai stores sync`
- **Agent Skills:** `npx skills add mixedbread-ai/skills` for Claude Code / Cursor / Claude Desktop

## Integrations

- LangChain — [`mixedbread-ai-langchain`](https://github.com/mixedbread-ai/mixedbread-ai-langchain)
- Haystack — [`mixedbread-ai-haystack`](https://github.com/mixedbread-ai/mixedbread-ai-haystack)
- LlamaIndex — Python and TypeScript forks under `mixedbread-ai/llama_index` and `LlamaIndexTS`
- Vercel — [`vercel-marketplace-mixedbread`](https://github.com/mixedbread-ai/vercel-marketplace-mixedbread)
- Astro Starlight — [`mixedbread-starlight`](https://github.com/mixedbread-ai/mixedbread-starlight)
- Next.js docs search — [`nextjs-docs-search`](https://github.com/mixedbread-ai/nextjs-docs-search) and [`mxbai-docs-chat`](https://github.com/mixedbread-ai/mxbai-docs-chat)
- Model Context Protocol — first-class MCP server for AI assistants

## Open-Source Tooling

- [`mxbai-rerank`](https://github.com/mixedbread-ai/mxbai-rerank) — Open reranker models and reference code
- [`baguetter`](https://github.com/mixedbread-ai/baguetter) — Flexible sparse / dense / hybrid search library
- [`batched`](https://github.com/mixedbread-ai/batched) — Dynamic batching API for inference workloads
- [`maxsim-cpu`](https://github.com/mixedbread-ai/maxsim-cpu) — CPU late-interaction MaxSim kernels
- [`mgrep`](https://github.com/mixedbread-ai/mgrep) — Semantic CLI grep (code, images, PDFs)
- [`astchunk`](https://github.com/mixedbread-ai/astchunk) — AST-aware code chunking
- [`openbread`](https://github.com/mixedbread-ai/openbread) — Open-source collection
- [`binary-embeddings`](https://github.com/mixedbread-ai/binary-embeddings) — 32x storage savings demo

## Plans and Pricing

| Plan | Price | Stores | Rate limit | Notes |
|---|---|---|---|---|
| Starter | Free + $5 one-time credit | 10 | 100 req/min | 3 workspace users, community Slack |
| Scale | $20/mo + $20 included credit | 10,000 | 1,200 query/min, 360 ingestion/min | Unlimited users, automatic backups, priority Slack |
| Enterprise | Custom | Unlimited | Custom | BYOC, dedicated support, PITR backups |
| Startup Program | Up to $250 one-time credit | — | — | VC-funded or raised up to $20M |

**Usage-based pricing:**

| Category | SKU | Unit | Price (USD) |
|---|---|---|---|
| Index — Fast | `index_fast` | 1M tokens | $1.50 |
| Index — High Quality | `index_high_quality` | 1M tokens | $3.00 |
| Search — Basic | `search_basic` | 1K queries | $4.00 |
| Search — Rerank | `search_rerank` | 1K queries | $7.50 |
| Search — Agentic | `search_agentic` | 1K queries | $20.00 |
| Storage | `data_storage` | 1M tokens / month | $0.50 |

See [`plans/mixedbread-ai-plans-pricing.yml`](plans/mixedbread-ai-plans-pricing.yml),
[`rate-limits/mixedbread-ai-rate-limits.yml`](rate-limits/mixedbread-ai-rate-limits.yml), and
[`finops/mixedbread-ai-finops.yml`](finops/mixedbread-ai-finops.yml) for machine-readable detail.

## Common Properties

- Portal: [https://www.mixedbread.com/](https://www.mixedbread.com/)
- Docs: [https://www.mixedbread.com/docs](https://www.mixedbread.com/docs)
- API Reference: [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- Pricing: [https://www.mixedbread.com/pricing](https://www.mixedbread.com/pricing)
- Blog: [https://www.mixedbread.com/blog](https://www.mixedbread.com/blog)
- Platform: [https://platform.mixedbread.com/](https://platform.mixedbread.com/)
- GitHub: [https://github.com/mixedbread-ai](https://github.com/mixedbread-ai)
- Hugging Face: [https://huggingface.co/mixedbread-ai](https://huggingface.co/mixedbread-ai)
- LinkedIn: [https://www.linkedin.com/company/mixedbread-ai/](https://www.linkedin.com/company/mixedbread-ai/)
- X (Twitter): [https://x.com/mixedbreadai](https://x.com/mixedbreadai)
- Discord: [https://discord.gg/mixedbread](https://discord.gg/mixedbread)

## Vocabulary and Rules

- [Vocabulary](vocabulary/mixedbread-ai-vocabulary.yml)
- [Spectral Rules](rules/mixedbread-ai-rules.yml)
