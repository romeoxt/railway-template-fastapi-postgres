# Deploy and Host FastAPI Postgres API with Railway

Production-ready REST API with PostgreSQL, health checks, and API-key authentication.

## About FastAPI Postgres API

A FastAPI starter with async SQLAlchemy and PostgreSQL. Includes a working "notes" example — list and create notes — so you have real endpoints to extend instead of an empty scaffold.

## About Hosting FastAPI Postgres API

Deploying on Railway gives you automatic builds from GitHub, private Postgres networking via reference variables, health-check integration, and HTTPS without configuring nginx or load balancers.

## Environment Variables

| Variable | Description | Secret | Example/Notes |
| --- | --- | --- | --- |
| `DATABASE_URL` | PostgreSQL connection string | Yes | `${{Postgres.DATABASE_URL}}` |
| `API_KEY` | Protects write/list routes | Yes | `${{secret(32)}}` — send as `X-API-Key` header |

## Deploy and Host

1. Deploy this repo from GitHub on Railway.
2. Add **PostgreSQL** and attach a **volume** at `/var/lib/postgresql/data`.
3. Set `DATABASE_URL` and `API_KEY` on the API service.
4. Enable **public HTTP** networking and deploy.
5. Confirm `/health` returns OK.
6. Test the notes API:

```bash
curl -X POST https://YOUR-URL/notes \
  -H "Content-Type: application/json" \
  -H "X-API-Key: YOUR_KEY" \
  -d "{\"title\":\"My note\",\"body\":\"Hello world\"}"
```

## Common Use Cases

- REST backends for web and mobile apps
- Internal APIs with Postgres persistence
- Starter templates for CRUD services
- Prototypes that need auth and a database on day one

## Dependencies for FastAPI Postgres API Hosting

The Railway template includes:

- **FastAPI Postgres API** — this GitHub repo
- **PostgreSQL** — Railway PostgreSQL plugin with persistent volume

## Deployment Dependencies

- [FastAPI documentation](https://fastapi.tiangolo.com/)
- [SQLAlchemy async docs](https://docs.sqlalchemy.org/en/20/orm/extensions/asyncio.html)
- [Railway PostgreSQL docs](https://docs.railway.com/databases/postgresql)

## Why Deploy FastAPI Postgres API on Railway?

GitHub deploy, `${{Postgres.DATABASE_URL}}` over private networking, `/health` health checks, and horizontal scaling — minimal DevOps for a production-shaped API.

## Template Content

| Service | Source |
| --- | --- |
| FastAPI Postgres API | GitHub repo (this template) |
| Postgres | Railway PostgreSQL plugin |

## Run locally

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
copy .env.example .env
uvicorn app.main:app --reload --port 8000
```

## Author

romeoxt — herbylegall9@gmail.com

## License

MIT
