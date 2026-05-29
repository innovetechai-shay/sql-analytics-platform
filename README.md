# SQL Analytics MVP Platform

Synthetic-first MVP repository for a natural-language analytics product over SQL Server.

The current implementation is safe by default: it uses a synthetic SQL Server-style fixture, never connects to production, never reads customer data, never uses secrets, and does not execute generated SQL against a database.

## What Is Included

- Backend prototype for metadata ingestion, schema graph inference, SQL safety, chat planning, report responses, and local API endpoints.
- Static frontend demo for schema review, natural-language question planning, report output, generated SQL inspection, and safety state.
- Synthetic SQL Server fixture and expected evaluation cases.
- Documentation for repository adoption, SQL Server adapter design, LLM orchestration, QA, security, and operations.
- Local verification script and GitHub Actions CI workflow.

## Repository Layout

```text
backend/
  sql_analytics_mvp/       Python backend package
  tests/                   Unittest smoke coverage
  synthetic-*.sql          Synthetic SQL Server fixture
frontend/                  Static app shell
docs/                      Architecture, QA, security, ops, and integration docs
scripts/                   Local verification scripts
.github/workflows/         CI workflow
```

## Run Checks

```bash
./scripts/run_checks.sh
```

The script verifies backend compile, evaluation gates, unittest smoke tests, API health/plan endpoints, frontend JavaScript syntax, and frontend static serving.

## Run Backend API

```bash
cd backend
python -m sql_analytics_mvp.api_server --port 4180
```

Endpoints:

- `GET /api/health`
- `GET /api/metadata`
- `GET /api/graph`
- `GET /api/plan?question=Which%20customers%20generated%20the%20most%20revenue%3F`

## Run Frontend Demo

```bash
cd frontend
python -m http.server 4173
```

Open `http://127.0.0.1:4173/`. The frontend calls the local API when available and falls back to static demo responses when it is not.

## Safety Gates

Still requires explicit CEO approval before:

- Production deployment.
- Production/customer database access.
- Secret access.
- New paid infrastructure or material model spend.
- External release/publication.
- Irreversible data or infrastructure changes.

## Current Status

Approved for internal prototype baseline only. Not production-ready.
