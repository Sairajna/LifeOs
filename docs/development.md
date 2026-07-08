# Development Guide — LifeOS AI

This document provides instructions on how to set up, run, and test LifeOS AI.

---

## 1. Prerequisites

Ensure you have the following installed:
- **Git**
- **Docker Desktop** (virtualization support must be enabled in BIOS and BCD)
- **Python 3.13+** (we use `uv` for python dependency packaging)
- **Node.js 20+ & npm**

---

## 2. Setting Up the Project

### 2.1 Clone the Repository
```bash
git clone https://github.com/Sairajna/LifeOs.git
cd LifeOs
```

### 2.2 Environment Configurations
Copy `.env.example` templates to `.env` files:
```bash
# Root environment variables
cp .env.example .env

# Backend environment variables
cp backend/.env.example backend/.env
```

---

## 3. Running Infrastructure

We use Docker Compose to run local development dependencies (PostgreSQL, Redis, Qdrant).

### 3.1 Start Services
```bash
docker compose up -d
```

### 3.2 Stop Services
```bash
docker compose down
```

---

## 4. Running the Backend

### 4.1 Install dependencies
We use `uv` to manage environments. Install dependencies and activate the virtual environment:
```bash
cd backend
uv sync
```

### 4.2 Run development server
```bash
uv run uvicorn app.main:app --reload
```

---

## 5. Running the Frontend

*(Instructions will be added once frontend scaffolding is finalized in Sprint 4)*
```bash
cd frontend
npm install
npm run dev
```

---

## 6. Testing

### 6.1 Running Backend Tests
```bash
cd backend
uv run pytest
```
