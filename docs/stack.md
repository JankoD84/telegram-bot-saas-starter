# Tech Stack Detail

A breakdown of every technology used in the Telegram Bot SaaS Starter Kit and the rationale behind each choice.

---

## Bot Layer

| Technology | Version | Role |
|---|---|---|
| [aiogram](https://docs.aiogram.dev/) | 3.x | Telegram Bot API framework |
| Python | 3.11+ | Runtime |

**Why aiogram 3?**  
Fully async, modern FSM (Finite State Machine) support, clean router/middleware architecture. The only Telegram bot library worth using in production in 2024+.

---

## API Layer

| Technology | Version | Role |
|---|---|---|
| [FastAPI](https://fastapi.tiangolo.com/) | 0.100+ | HTTP API framework |
| [Uvicorn](https://www.uvicorn.org/) | latest | ASGI server |
| Pydantic | v2 | Request/response validation |

**Why FastAPI?**  
Handles Stripe webhooks, admin endpoints, and health checks. Native async, automatic OpenAPI docs, Pydantic v2 validation. Pairs naturally with aiogram's async model.

---

## Database Layer

| Technology | Version | Role |
|---|---|---|
| [PostgreSQL](https://www.postgresql.org/) | 15+ | Primary data store |
| [SQLAlchemy](https://www.sqlalchemy.org/) | 2.x async | ORM |
| [Alembic](https://alembic.sqlalchemy.org/) | latest | Schema migrations |
| [asyncpg](https://magicstack.github.io/asyncpg/) | latest | Async PostgreSQL driver |

**Why PostgreSQL + SQLAlchemy async?**  
No ORMs that block the event loop. SQLAlchemy 2.x async mode + asyncpg gives full non-blocking DB access with type-safe queries and migration history via Alembic.

---

## Queue / Cache Layer

| Technology | Version | Role |
|---|---|---|
| [Redis](https://redis.io/) | 7+ | Rate limiting + task queue backend |
| [Celery](https://docs.celeryq.dev/) | 5.x | Async task worker |

**Why Redis + Celery?**  
Rate limiting state needs to be shared across bot worker processes. Redis is the standard. Celery handles deferred tasks (e.g. subscription expiry checks, email triggers).

---

## Payments

| Technology | Role |
|---|---|
| [Stripe](https://stripe.com/) | Checkout sessions, subscription management, customer portal, webhooks |

**Why Stripe?**  
Industry standard. Handles the full subscription lifecycle: trial, active, past_due, cancelled. Customer portal lets users self-manage without you writing UI. Webhook-driven so your DB stays in sync automatically.

---

## Infrastructure

| Technology | Role |
|---|---|
| [Docker](https://www.docker.com/) | Containerization |
| [Docker Compose](https://docs.docker.com/compose/) | Multi-service orchestration (dev + prod) |
| [nginx](https://nginx.org/) | TLS termination, reverse proxy, webhook routing |
| Systemd | Process supervision on bare-metal VPS |

**Why Docker Compose?**  
One command (`docker compose up`) starts the entire stack: bot, API, worker, DB, Redis, nginx. The same compose file works locally and on a $6/month VPS.

---

## Testing

| Technology | Role |
|---|---|
| [pytest](https://pytest.org/) | Test runner |
| [pytest-asyncio](https://pypi.org/project/pytest-asyncio/) | Async test support |
| [httpx](https://www.python-httpx.org/) | FastAPI test client |

100+ tests cover: auth flow, Stripe webhook handling, rate limit enforcement, plan gating middleware, and deployment smoke tests.

---

*Full dependency list with pinned versions is in `requirements.txt` and `pyproject.toml` — included with purchase.*

→ **[Get access on Gumroad](https://jankodur.gumroad.com)**
