# ADR-003: PostgreSQL for Primary Relational Storage

## Status
Approved

## Context
LifeOS AI requires database storage for structured, relational metadata: users, session states, configuration variables, API keys, long-term memory logs, and job definitions. We need a database that supports transactions, relational constraints (ACID compliance), and has mature Python integration tools.

Options considered: PostgreSQL, MySQL, SQLite, MongoDB.

## Decision
We select **PostgreSQL** as the primary relational database.

- PostgreSQL is a highly robust, open-source object-relational database.
- It supports advanced data types like JSONB, which is helpful for storing unstructured configurations or agent logs.
- It integrates seamlessly with `SQLAlchemy` (ORM) and `Alembic` (migrations) using the asynchronous `asyncpg` driver.

## Consequences
- **Pros**: Relational integrity, ACID compliance, native JSONB support, widely supported in production, stable async integration in Python.
- **Cons**: Requires more server resources compared to lightweight SQLite, but is necessary for a multi-user, multi-service setup.
