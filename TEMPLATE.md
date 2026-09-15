# Railway Template Composer Setup

## Marketplace listing

- **Title:** Deploy and Host FastAPI Postgres API with Railway
- **Short description:** Production-ready REST API with PostgreSQL, health checks, and API-key auth.
- **Category:** Starters
- **Overview:** paste `README.md`

## Services

| Service | Source | Volume | Public HTTP |
| --- | --- | --- | --- |
| FastAPI Postgres API | GitHub repo (this folder) | — | Yes |
| Postgres | Railway PostgreSQL plugin | `/var/lib/postgresql/data` | No |

## Variables — FastAPI Postgres API

| Variable | Value | Secret | Description |
| --- | --- | --- | --- |
| `DATABASE_URL` | `${{Postgres.DATABASE_URL}}` | Yes | Postgres over private network |
| `API_KEY` | `${{secret(32)}}` | Yes | `X-API-Key` for write/list routes |

## Settings — FastAPI Postgres API

- Healthcheck: `/health`
- Start command: `uvicorn app.main:app --host 0.0.0.0 --port $PORT` (from `railway.json`)
