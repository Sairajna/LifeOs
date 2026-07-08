# Architecture Strategy — LifeOS AI

This document details the architectural choices, patterns, and principles guiding the development of LifeOS AI.

---

## 1. Architectural Strategy: Modular Monolith

LifeOS AI is developed as a **Modular Monolith**. 

### 1.1 Why a Modular Monolith?
- **Simplicity in Deployment**: Runs as a single process (FastAPI server) rather than a complex network of microservices.
- **Strong Module Boundaries**: Code is strictly segregated by functionality (e.g., `llm`, `rag`, `memory`, `agents`) under the `app/` folder. Inter-module communication should happen via defined service interfaces, avoiding direct imports of private module helpers.
- **Easy Transition to Microservices**: If a specific module (e.g., `ai-engine` or `rag` services) becomes a performance bottleneck, it can be easily extracted into a standalone service because its boundaries are already clearly defined.

---

## 2. Design Principles

### 2.1 SOLID Principles
- **Single Responsibility Principle (SRP)**: Each service class or file handles one distinct function (e.g., `GeminiClient` only handles API interaction, `EmbeddingGenerator` only handles vector generation).
- **Open/Closed Principle (OCP)**: Code is designed for extension without modification (e.g., LLM clients inherit from a base `LLMProvider` interface).
- **Liskov Substitution Principle (LSP)**: Derived classes must remain substitutable for their base interfaces.
- **Interface Segregation Principle (ISP)**: Clients should not be forced to depend on interfaces they do not use.
- **Dependency Inversion Principle (DIP)**: High-level modules do not depend directly on low-level modules; both depend on abstractions (interfaces).

### 2.2 Clean Architecture
- Inner core contains core models and domain logic.
- Outer ring contains API endpoints, databases, and external network clients.
- Dependencies flow **inward**. API routes call services; services use repositories; repositories talk to database drivers.

---

## 3. Communication Patterns

- **Synchronous (REST)**: Next.js Frontend calls FastAPI REST API for dashboard renders and user queries.
- **Asynchronous (Redis/Celery)**: Long-running agent reasoning and batch document ingestion tasks are offloaded to background queues using Redis.
- **Vector Search**: Semantic context retrieval query cycles occur directly against Qdrant database API.
