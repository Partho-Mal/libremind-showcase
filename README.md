# LibreMind - 3D AI Mental Wellness Chatbot (Architecture Showcase)

**Live Demo:** [libremind.in](https://libremind.in)

> **Note:** This repository is a technical showcase of the system architecture, infrastructure, and backend orchestration for LibreMind. The core proprietary source code is closed-source.

## Overview
LibreMind is a 3D AI mental wellness chatbot featuring a decoupled Python FastAPI intelligence layer. It orchestrates low-latency interactions between Google Gemini (reasoning), Groq (Speech-to-Text), and a custom TTS engine to drive a responsive React Three Fiber WebGL frontend.

## Key Backend Systems
* **AI Orchestration (FastAPI):** Manages asynchronous LLM reasoning, STT, and custom TTS generation for low-latency end-to-end conversational interactions.
* **Dual-Layer Memory:** Utilizes Supabase (PostgreSQL) to condense extended conversation histories into long-term vector summaries for contextual retrieval.
* **Dual-Layer Safety Pipeline:** Integrates a frontend intent listener with a backend risk engine to evaluate and filter unsafe LLM generations.
* **Infrastructure:** Manages persistent state and sliding-window rate limiting via Redis to ensure stable API performance under concurrent load.

## Core Tech Stack
* **Backend & AI:** Python, FastAPI, Google Gemini, Groq STT
* **Data & Cache:** PostgreSQL (Supabase), Redis
* **Frontend:** Next.js, React Three Fiber (WebGL)

## Architecture Documentation
Explore the detailed system design, pipelines, and data models:
* [System Overview & Architecture](./docs/01_architecture/01_system_overview.md)
* [Authentication & BFF Security Flow](./docs/01_architecture/02_auth_flow.md)
* [Message Pipeline & Lifecycle](./docs/01_architecture/03_message_pipeline.md)
* [Database Models & ERD](./docs/01_architecture/04_data_models.md)
* [Dual-Layer Risk & Escalation Engine](./docs/02_features/03_risk_escalation.md)
* [API Endpoints & Orchestration](./docs/03_api/endpoints.md)
* [AI Guardrails & Prompt Safety](./docs/03_api/guardrails.md)

## Architecture Tree

```text
.
├── backend/                  # FastAPI Intelligence & Orchestration Layer
│   ├── app/
│   │   ├── infra/            # Redis & Supabase Connection Pooling
│   │   ├── routers/          # API Endpoints (Chat, STT, Sessions)
│   │   ├── services/
│   │   │   ├── llm/          # Gemini & Groq Integration Factory
│   │   │   ├── risk_service/ # Dual-layer Safety Pipeline
│   │   │   ├── stt_service/  # Speech-to-Text Processing
│   │   │   └── tts_service/  # Text-to-Speech & Viseme Generation
│   │   └── utils/
│   ├── Dockerfile
│   └── tests/                # Load, Failover, and Risk Integration Tests
├── docs/                     # System Architecture & Data Models
├── frontend/                 # Next.js & React Three Fiber UI (Proprietary)
└── supabase/                 # PostgreSQL Schemas & Edge Functions
```

## Author
**Partho Mal**
* **Portfolio:** [parthomal.vercel.app](https://parthomal.vercel.app)
* **LinkedIn:** [linkedin.com/in/parthomal](https://www.linkedin.com/in/parthomal)
* **Email:** Parthomal7@gmail.com
