# ADR-004: Qdrant for Vector Database

## Status
Approved

## Context
For RAG (Retrieval Augmented Generation) capabilities, episodic memory storage, and semantic searches, LifeOS AI needs a database that can store and perform fast similarity searches on high-dimensional vector embeddings.

Options considered: Qdrant, pgvector (PostgreSQL extension), Pinecone, Milvus, Chroma.

## Decision
We select **Qdrant** as our vector database.

- Qdrant is an open-source, highly performant vector similarity search engine written in Rust.
- It supports filtering by payload, which allows us to restrict semantic search results by metadata (e.g., user ID, document category) easily.
- It runs efficiently as a lightweight Docker container, ideal for local development.
- It provides a robust, native async Python client library (`qdrant-client`).

## Consequences
- **Pros**: Fast similarity searches, robust metadata payload filtering, native async Python integration, easy local containerization.
- **Cons**: Running a separate database service (Qdrant) alongside PostgreSQL increases operational complexity slightly, but it offers better vector search performance and advanced filters compared to general-purpose databases.
