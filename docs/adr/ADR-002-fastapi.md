# ADR-002: FastAPI for Backend Framework

## Status
Approved

## Context
We need a robust web framework to build the LifeOS AI backend APIs. The backend must handle high-throughput network requests, support real-time WebSocket communication for agent task streams, and integrate seamlessly with modern asynchronous Python packages (like `asyncpg`, `aioredis`, and `google-generativeai`).

Other options include Django, Flask, or Node.js (Express/NestJS).

## Decision
We select **FastAPI** as our core backend web framework.

- FastAPI is natively built on ASGI and supports asynchronous (`async`/`await`) routing out of the box, which is critical for I/O bound LLM and database calls.
- It provides automatic OpenAPI and Swagger documentation.
- It uses Pydantic for fast request/response validation and strict type safety.
- Python is the dominant language for the AI ecosystem, making it easy to use libraries for RAG, chunking, and evaluation.

## Consequences
- **Pros**: Outstanding asynchronous performance, rapid development with auto-docs, native type hinting and validation via Pydantic, seamless python AI ecosystem integration.
- **Cons**: Lesser default structure than full-stack frameworks like Django (requires us to define our own folder structure, which we have done).
