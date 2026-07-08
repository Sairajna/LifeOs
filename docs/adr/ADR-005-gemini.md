# ADR-005: Gemini API for LLM Provider

## Status
Approved

## Context
LifeOS AI needs a foundational Large Language Model (LLM) to drive agent reasoning, planning, data summarization, and query routing. We need an API that offers low latency, high context windows (for RAG and long chat logs), cost-effective pricing, and advanced tooling like native structured outputs and tool calling.

Options considered: Gemini API (Google), OpenAI API, Anthropic API, Local models (Ollama).

## Decision
We select **Gemini API** as our initial primary LLM provider.

- Gemini 1.5 Pro and Gemini 1.5 Flash provide large context windows (up to 2 million tokens), which is uniquely suited for aggregating long-term memories and reading large directories of project files.
- Excellent tool calling (function calling) capabilities.
- Gemini API offers competitive pricing and a generous free tier for developers.
- Built-in support for structured JSON schema outputs.

## Consequences
- **Pros**: Access to huge context windows, reliable function calling, native integration via the `google-generativeai` SDK, cost-effective development.
- **Cons**: Dependency on Google Cloud/Gemini API endpoints (requires internet connectivity and an active API key). We will isolate this client under the `app/llm/` module so that adding other providers (e.g., OpenAI or Anthropic) in the future is straightforward.
