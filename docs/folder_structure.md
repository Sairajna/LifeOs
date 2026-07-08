# Folder Structure Documentation — LifeOS AI

This document details the folder structure of LifeOS AI and explains the purpose of each directory.

---

## Repository Root Layout

```
LifeOS/
├── .github/              # GitHub metadata and CI/CD workflow configuration
│   └── workflows/        # GitHub actions workflow templates
│
├── backend/              # FastAPI Python backend application
│   ├── app/              # Main application source code
│   │   ├── api/          # Routers, path operations, request validation, dependencies
│   │   ├── core/         # Settings, database engine, security logic, startup events
│   │   ├── services/     # Pure business logic coordination
│   │   ├── llm/          # Gemini and other LLM clients and prompt interfaces
│   │   ├── rag/          # Text parsing, chunking, indexing, and embeddings retrieval
│   │   ├── memory/       # Session context management, episodic and semantic memory
│   │   ├── agents/       # Agent executor loops, planning algorithms, state engines
│   │   ├── tools/        # Actions available to the agent (filesystem, terminal commands)
│   │   ├── mcp/          # Model Context Protocol integration
│   │   ├── evaluation/   # Benchmarking tests for monitoring LLM and RAG responses
│   │   ├── models/       # Shared database schemas and models (relational & vector)
│   │   └── utils/        # Generic utility libraries, custom loggers, date converters
│   │
│   ├── tests/            # Backend unit and integration test suite
│   ├── pyproject.toml    # Python environment configurations and tool parameters (Ruff, mypy)
│   ├── .env.example      # Backend-specific environment variables template
│   └── README.md         # Backend-level development readme
│
├── frontend/             # Next.js React frontend web application
│
├── infrastructure/       # Deployment, hosting, and configuration orchestration
│
├── docs/                 # Product and system documentation
│   └── adr/              # Architecture Decision Records (ADRs)
│
├── scripts/              # Development script helpers and task runners
│
├── tests/                # System-wide and cross-component integration test suite
│
├── docker-compose.yml    # Main Docker Compose configuration at repository root
├── README.md             # Repository-level landing documentation
├── LICENSE               # MIT License declaration
├── CHANGELOG.md          # Project version update history
├── .gitignore            # File exclusions rules for Git version tracking
└── .env.example          # Root environment variables template
```

---

## Key Modules Explained

### 1. Modular AI Core (`backend/app/`)
AI capabilities are colocated inside the backend monolith as distinct modules:
- **llm**: Standardizes how the application connects to models. Starting with the Gemini API.
- **rag**: Decouples document splitting, embedding creation, and semantic searching.
- **memory**: Provides session retention, letting the AI remember past facts and recall them on context.
- **agents**: Implements reasoning loops that determine how the AI reacts to instructions.
- **tools**: Safe modules containing helper scripts allowing the agent to interface with files or run search.
- **mcp**: standardizes communication protocols so third-party integrations can occur cleanly.
- **evaluation**: Runs automated test evaluations to verify prompts and RAG retrieval accuracy.
