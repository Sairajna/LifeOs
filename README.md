# LifeOS AI

An Agentic Personal Operating System built using a Modular Monolith architecture, featuring a FastAPI backend, a Next.js frontend, and standard open-source data infrastructure (PostgreSQL, Redis, Qdrant).

---

## Architecture Overview

LifeOS AI is structured as a **Modular Monolith** to balance separation of concerns and build/deployment simplicity. 

Key stack components:
- **Backend**: FastAPI (Python)
- **Frontend**: Next.js (TypeScript)
- **Database**: PostgreSQL (Relational metadata)
- **Cache**: Redis (Key-value cache and message broker)
- **Vector DB**: Qdrant (Semantic search and RAG memory storage)
- **AI Integration**: Gemini API (Initial LLM provider)

---

## Directory Structure

The project has the following top-level structure:
- [backend/](file:///d:/LifeOs/backend/): FastAPI application, modular AI engine sub-modules, and unit/integration tests.
- [frontend/](file:///d:/LifeOs/frontend/): Next.js web application interface.
- [infrastructure/](file:///d:/LifeOs/infrastructure/): Configuration templates, provisioning scripts, and deployments.
- [docs/](file:///d:/LifeOs/docs/): Complete documentation, including PRD, High Level Design, architecture notes, and Architecture Decision Records (ADRs).
- [scripts/](file:///d:/LifeOs/scripts/): Development and automation utilities.
- [tests/](file:///d:/LifeOs/tests/): Repository-level integration and system tests.
- [.github/](file:///d:/LifeOs/.github/): Workflows and templates for repository governance and CI/CD pipelines.

---

## Getting Started

### Prerequisites

To run and contribute to LifeOS AI, you will need:
- **Git**
- **Docker & Docker Desktop** (for running database services)
- **Python 3.13+** (with `uv` or `pip`)
- **Node.js 20+ & npm**

### Run Infrastructure

Dependencies are run using Docker Compose:
```bash
docker compose up -d
```
This spins up PostgreSQL, Redis, and Qdrant locally.

For detailed instructions, refer to the [Development Guide](file:///d:/LifeOs/docs/development.md).

---

## License

This project is licensed under the [MIT License](file:///d:/LifeOs/LICENSE).
