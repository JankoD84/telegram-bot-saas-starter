# Architecture Overview

High-level architecture of the Telegram Bot SaaS Starter Kit.

---

## 1. Component Diagram

```
┌─────────────────────────────────────────────────────────┐
│                        User                             │
└───────────────────────────┬─────────────────────────────┘
                            │ Telegram API
                            ▼
┌─────────────────────────────────────────────────────────┐
│                   aiogram Bot Layer                     │
│         (handlers, middleware, command routing)         │
└───────────────────────────┬─────────────────────────────┘
                            │ internal calls
                            ▼
┌─────────────────────────────────────────────────────────┐
│                  FastAPI Backend                        │
│   (Stripe webhooks, admin API, subscription logic)      │
└──────────────┬────────────────────────────┬─────────────┘
               │                            │
               ▼                            ▼
┌──────────────────────┐      ┌─────────────────────────┐
│      PostgreSQL      │      │          Redis          │
│  users, subs,        │      │  rate limiting,         │
│  audit logs          │      │  Celery task queue      │
└──────────────────────┘      └─────────────────────────┘
               │
               ▼
┌──────────────────────┐
│        Stripe        │
│  checkout sessions,  │
│  webhooks, portal    │
└──────────────────────┘
```

---

## 2. Data Flow

```
User sends command
    │
    ▼
aiogram handler receives message
    │
    ├─► Auth middleware: resolve user identity (Telegram ID → DB user)
    │
    ├─► Plan middleware: check subscription tier (free / premium)
    │
    ├─► Rate limit middleware: enforce per-tier request limits (Redis)
    │
    └─► Handler executes business logic
            │
            ├─► Reads / writes PostgreSQL via SQLAlchemy async
            │
            └─► Triggers Stripe session / webhook processing via FastAPI
```

---

## 3. Plugin System

```
src/                        ← Core framework (not modified)
│   ├── bot/                ←   aiogram router, middleware, base handlers
│   ├── billing/            ←   Stripe integration
│   ├── db/                 ←   models, migrations (Alembic)
│   └── plugins/            ←   plugin loader interface

examples/
└── qa_coach/               ← Domain-specific extension (plugin)
        ├── handlers.py     ←   registers additional aiogram routers
        ├── models.py       ←   extends DB schema
        └── config.py       ←   feature-specific settings
```

Extensions plug into the framework via the plugin loader — they never modify `src/`.

---

## 4. Deployment Topology

```
Internet
    │
    ▼
┌───────────────┐
│     nginx     │  (TLS termination, reverse proxy)
└──────┬────────┘
       │
       ├──► :8000  FastAPI (Uvicorn)
       │
       └──► Telegram Webhook endpoint

Docker Compose services:
  bot        — aiogram polling / webhook listener
  api        — FastAPI + Uvicorn
  worker     — Celery worker (async tasks)
  db         — PostgreSQL
  redis      — Redis
  nginx      — reverse proxy
```

---

## 5. Security Boundaries

- Stripe webhook signature verification on every inbound event
- Telegram user identity validated per-request via middleware
- Admin commands restricted by Telegram user ID allowlist
- Secrets managed via `.env` (never committed)

---

*Full architecture documentation, sequence diagrams, and database schema are included with purchase.*

→ **[Get access](https://jankodur.gumroad.com)**
