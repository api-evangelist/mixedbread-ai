# Mixedbread (mixedbread-ai)

Mixedbread is a Berlin-based AI search and retrieval platform. It provides embeddings (mxbai-embed, Wholembed v3), rerankers (mxbai-rerank v1/v2/v3-listwise), multimodal stores, document parsing, structured extraction, and connector-based ingestion. Models are published as open weights on Hugging Face and consumed via a hosted REST API at api.mixedbread.com. The platform powers RAG and agent retrieval over text, PDFs, images, audio, and video across 100+ languages.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/mixedbread-ai/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/mixedbread-ai/refs/heads/main/apis.yml)

## Scope

- **Access:** 3rd-Party

## Tags

- AI
- Artificial Intelligence
- Embeddings
- Reranking
- Search
- Retrieval
- RAG
- Vector Database
- Multimodal
- Parsing
- Open Weights

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### Mixedbread Embeddings API

POST /v1/embeddings creates dense or multi-encoding embeddings for text and images using mxbai embedding models (mxbai-embed-large-v1, deepset-mxbai-embed-de-large-v1, mxbai-embed-xsmall-v1, Wholembed v3). Supports Matryoshka dimensions, binary/int8/float32 encodings, and prompt instructions. Returns Embedding objects with token usage.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- Embeddings
- Vectors
- Multimodal

#### Properties

- [Documentation](https://www.mixedbread.com/api-reference)
- [OpenAPI](openapi/mixedbread-embeddings-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-embeddings-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-embeddings-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/mixedbread-embedding-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/mixedbread-ai-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Mixedbread Reranking API

POST /v1/reranking reorders a candidate document list against a query using the mxbai-rerank family (xsmall-v1, base-v1, large-v1, base-v2, large-v2, plus the v3-listwise instruction-following reranker). Documents can be raw strings or structured objects with a return_input flag. Top-K results returned with relevance scores.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- Reranking
- Search
- Retrieval

#### Properties

- [Documentation](https://www.mixedbread.com/api-reference)
- [OpenAPI](openapi/mixedbread-reranking-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-reranking-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-reranking-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/mixedbread-rerank-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Mixedbread Stores API

Stores are AI-powered multimodal search indexes. CRUD for stores plus file upload, semantic search, grep, list-chunks, question-answering, query enhancement, metadata facets, search rules, and events. Replaces the deprecated /v1/vector_stores surface; deprecated endpoints kept for backward compatibility.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- Search
- Vector Database
- RAG
- Retrieval

#### Properties

- [Documentation](https://www.mixedbread.com/docs/stores/overview)
- [OpenAPI](openapi/mixedbread-stores-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-stores-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-stores-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/mixedbread-store-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Mixedbread Parsing API

Asynchronous document parsing as jobs. POST /v1/parsing/jobs starts a parse over an uploaded file with configurable chunking strategy, return format (markdown/HTML/text), and element extraction. GET/PATCH/DELETE on /v1/parsing/jobs/{job_id} for retrieval, cancellation, and deletion. Produces structured chunks with type metadata for text, code, tables, images, audio, video.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- Parsing
- Documents
- Chunking
- OCR

#### Properties

- [Documentation](https://www.mixedbread.com/api-reference)
- [OpenAPI](openapi/mixedbread-parsing-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-parsing-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-parsing-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Mixedbread Extractions API

Schema-guided structured extraction. POST /v1/extractions/jobs runs an extraction job against a file; POST /v1/extractions/content extracts from raw strings. The /v1/extractions/schema family creates, enhances, and validates JSON Schema definitions used by the extraction pipeline.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- Extraction
- Structured Output
- JSON Schema

#### Properties

- [Documentation](https://www.mixedbread.com/api-reference)
- [OpenAPI](openapi/mixedbread-extractions-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-extractions-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-extractions-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Mixedbread Files API

Workspace file management for files used across stores, parsing, and extraction. Single-shot upload via POST /v1/files plus multipart upload via /v1/files/uploads (create, complete, abort, list). Standard CRUD on /v1/files/{file_id} including content download.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- Files
- Storage
- Multipart Upload

#### Properties

- [Documentation](https://www.mixedbread.com/api-reference)
- [OpenAPI](openapi/mixedbread-files-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-files-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-files-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Mixedbread Chat Completions API

POST /v1/chat/completions exposes an OpenAI-compatible chat completion surface that grounds responses in Mixedbread Stores. Used to drive question-answering and agentic flows on top of indexed multimodal content.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- Chat
- Completions
- LLM

#### Properties

- [Documentation](https://www.mixedbread.com/api-reference)
- [OpenAPI](openapi/mixedbread-completions-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-completions-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-completions-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Mixedbread Data Sources API

Manage external data sources and their connectors, including OAuth2 authorization/callback flows. Lets stores ingest content from third-party SaaS systems through reusable connector definitions.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- Data Sources
- Connectors
- Integrations
- OAuth2

#### Properties

- [Documentation](https://www.mixedbread.com/api-reference)
- [OpenAPI](openapi/mixedbread-data-sources-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-data-sources-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-data-sources-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Mixedbread API Keys API

Programmatic management of workspace API keys. CRUD plus rotation (reroll) and revocation under /v1/api-keys.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- Administration
- API Keys
- Security

#### Properties

- [Documentation](https://www.mixedbread.com/api-reference)
- [OpenAPI](openapi/mixedbread-api-keys-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-api-keys-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-api-keys-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Mixedbread Billing API

Read-only billing telemetry. GET /v1/billing/summary returns workspace-level spend; /v1/billing/stores breaks cost down per store; histogram endpoints chart store and parsing costs over time. Aligns with the workspace's usage-based pricing.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- Billing
- Usage
- FinOps
- Cost

#### Properties

- [Documentation](https://www.mixedbread.com/api-reference)
- [OpenAPI](openapi/mixedbread-billing-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-billing-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-billing-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Mixedbread Schemas API

GET /v1/schemas/mxjson returns the mxbai JSON schema definition. Used by clients and the CLI to validate Mixedbread-flavored JSON payloads.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- JSON Schema
- Discovery

#### Properties

- [Documentation](https://www.mixedbread.com/api-reference)
- [OpenAPI](openapi/mixedbread-schemas-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-schemas-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-schemas-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Mixedbread Admin API

Reserved operations for Mixedbread platform administrators. POST /v1/admin/stores/{organization_id}/{store_identifier}/reingest triggers a full reingest of a tenant store.

- **Human URL:** [https://www.mixedbread.com/api-reference](https://www.mixedbread.com/api-reference)
- **Base URL:** `https://api.mixedbread.com`

#### Tags

- AI
- Administration
- Operations

#### Properties

- [Documentation](https://www.mixedbread.com/api-reference)
- [OpenAPI](openapi/mixedbread-admin-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/mixedbread-admin-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/mixedbread-admin-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://www.mixedbread.com/)
- [Documentation](https://www.mixedbread.com/docs)
- [Documentation](https://www.mixedbread.com/api-reference)
- [Sign Up](https://platform.mixedbread.com/)
- [Pricing](https://www.mixedbread.com/pricing)
- [Blog](https://www.mixedbread.com/blog)
- [Git Hub](https://github.com/mixedbread-ai)
- [Hugging Face](https://huggingface.co/mixedbread-ai)
- [SDK](https://github.com/mixedbread-ai/mixedbread-python)
- [SDK](https://github.com/mixedbread-ai/mixedbread-ts)
- [SDK](https://github.com/mixedbread-ai/python-sdk)
- [SDK](https://github.com/mixedbread-ai/typescript-sdk)
- [C L I](https://www.mixedbread.com/docs/cli)
- [Tools](https://github.com/mixedbread-ai/skills)
- [Tools](https://github.com/mixedbread-ai/mxbai-rerank)
- [Tools](https://github.com/mixedbread-ai/baguetter)
- [Tools](https://github.com/mixedbread-ai/batched)
- [Tools](https://github.com/mixedbread-ai/maxsim-cpu)
- [Tools](https://github.com/mixedbread-ai/mgrep)
- [Integration](https://github.com/mixedbread-ai/mixedbread-ai-langchain)
- [Integration](https://github.com/mixedbread-ai/mixedbread-ai-haystack)
- [Integration](https://github.com/mixedbread-ai/vercel-marketplace-mixedbread)
- [Integration](https://www.mixedbread.com/docs/mcp)
- [Authentication](https://www.mixedbread.com/api-reference)
- [LinkedIn](https://www.linkedin.com/company/mixedbread-ai/)
- [Twitter](https://x.com/mixedbreadai)
- [Discord](https://discord.gg/mixedbread)
- [Plans](plans/mixedbread-ai-plans-pricing.yml)
- [Rate Limits](rate-limits/mixedbread-ai-rate-limits.yml)
- [Fin Ops](finops/mixedbread-ai-finops.yml)
