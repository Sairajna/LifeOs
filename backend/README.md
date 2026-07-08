# LifeOS AI Backend

FastAPI-based modular monolith backend for the LifeOS AI personal operating system.

---

## Architecture and Structure

The backend follows Clean Architecture principles structured inside a modular monolith layout:

```
backend/
├── app/                  # Main application package
│   ├── api/              # API router endpoints and HTTP request handlers
│   ├── core/             # Configuration, database connections, security, middleware
│   ├── services/         # Domain business logic layer
│   ├── llm/              # Large Language Model abstraction and connection handlers
│   ├── rag/              # Retrieval Augmented Generation logic (chunking, vector indexing)
│   ├── memory/           # Agentic memory models (short-term, long-term semantic/episodic)
│   ├── agents/           # Agent systems, reasoning loops, and planner frameworks
│   ├── tools/            # Tools and actions available to the agent (filesystem, terminal)
│   ├── mcp/              # Model Context Protocol integrations
│   ├── evaluation/       # Performance evaluation and benchmarking of agent runs
│   ├── models/           # Shared Pydantic schemas and database models
│   └── utils/            # Helper utils, timing, and formatting libraries
│
├── tests/                # Test suite
├── pyproject.toml        # Development tooling and dependency management
├── .env.example          # Environment variables template
└── README.md             # This documentation file
```

---

## Development Setup

### Dependencies

We use `uv` for managing python environments and dependencies.

Install dependencies and activate the virtual environment:
```bash
uv sync
```

### Configuration

Copy `.env.example` to `.env` and fill in your Gemini API key and database configurations:
```bash
cp .env.example .env
```

### Running the Server

Run the development server:
```bash
uv run uvicorn app.main:app --reload
```
*(Note: `app.main:app` will be created when application logic implementation begins).*
