# ADR-001: Modular Monolith Architecture

## Status
Approved

## Context
We need to design a scalable architecture for the LifeOS AI agentic operating system. The system will grow to support multiple complex features (LLM orchestration, RAG pipelines, long-term memory, tools execution, evaluation pipelines). 

A microservices architecture would split these components into separate services from day one. However, this introduces substantial operational overhead: multiple repositories, network latency, distributed logging, network security, and complex local developer setup.

A traditional monolith would lack modular boundaries, leading to spaghetti code and high dependency coupling between different parts of the code.

## Decision
We will build LifeOS AI as a **Modular Monolith**. 

- Code will reside in a single repository and deploy as a single service.
- We will enforce strict directory segregation inside `backend/app/` (e.g., `llm/`, `rag/`, `memory/`, `agents/`, `tools/`, `mcp/`, `evaluation/`).
- Modules should interact via defined service interfaces rather than directly importing internal utilities of other modules.
- If any module becomes a performance bottleneck or requires custom scaling in the future, its clean boundaries will make it easy to refactor into a separate microservice.

## Consequences
- **Pros**: Very simple local development setup, single deployable process, fast in-memory communication, clear directory organization, low infrastructure overhead.
- **Cons**: Monolith can grow large; we must remain disciplined to prevent direct cross-module import coupling.
