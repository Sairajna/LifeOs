# Coding Guidelines — LifeOS AI

This document establishes the code style, guidelines, and quality standards for the LifeOS AI repository.

---

## 1. Python Standards (Backend)

We adhere strictly to modern Python standards and Clean Architecture conventions.

### 1.1 Style Guide & Linting
- **PEP 8**: Code must strictly conform to PEP 8 standards.
- **Ruff**: We use `ruff` for linting, code quality checks, and imports sorting.
- **Line Length**: Maximum line length is set to 88 characters (black style standard).

### 1.2 Type Hints
- **Strict Typing**: Type hints are required for *all* function parameters, return values, and class fields.
- **Mypy**: We run `mypy` for static type checking in strict mode:
  ```bash
  mypy --strict .
  ```

### 1.3 Asynchronous Code
- Use `async`/`await` for I/O bound operations (database calls, LLM requests, external API fetches).
- Ensure async database sessions are properly closed using context managers.

---

## 2. Frontend Standards (Next.js/React)

*(To be expanded in future sprints)*
- Use TypeScript for all components and utilities (no `any` types).
- Use Vanilla CSS or tailwind utility guidelines depending on component layout.

---

## 3. Git Commit Standards

We use conventional commit messages to keep our Git history structured and readable:
- `feat`: A new feature.
- `fix`: A bug fix.
- `docs`: Documentation changes only.
- `style`: Changes that do not affect the meaning of the code (white-space, formatting).
- `refactor`: A code change that neither fixes a bug nor adds a feature.
- `perf`: A code change that improves performance.
- `test`: Adding missing tests or correcting existing tests.
- `chore`: Changes to the build process or auxiliary tools and libraries.

Examples:
- `chore: create project structure`
- `docs: add architecture decision records`
- `build: add docker infrastructure`
