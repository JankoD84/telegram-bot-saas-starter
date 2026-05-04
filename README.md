# Telegram Bot SaaS Starter Kit

> Production-ready Python framework for building monetized Telegram bots.
> Skip 3 weeks of setup. Start charging on day one.

**Built with:** Python · FastAPI · PostgreSQL · Stripe · Docker · aiogram

---

## The Problem

Every time you build a Telegram bot that earns money, you waste the first 3–4 weeks on:
- Auth (who is this user? are they paid?)
- Stripe integration (checkout, webhooks, subscription lifecycle)
- Database with migrations (users, subscriptions, audit logs)
- Rate limiting (free vs premium enforcement)
- Docker + nginx production setup
- Telegram webhook vs polling decision

None of this is your product. None of this earns you money.

**This kit is that infrastructure. Done.**

---

## What's Inside

### Core Framework (`src/`)
- Multi-tenant user management
- Stripe subscription billing (checkout, webhooks, portal)
- Plan enforcement middleware (free/premium gating)
- Rate limiting per user tier
- Admin commands and user management
- Plugin loader for domain-specific extensions

### Example Implementation (`examples/qa_coach/`)
A complete, production-ready QA coaching bot built on the framework.
Shows you exactly how to extend the framework for your domain.

### Deployment (`deploy/`)
- Docker Compose (dev + prod configs)
- nginx reverse proxy config
- Systemd service files
- `.env` templates

### Tests (`tests/`)
- 100+ tests covering critical paths
- Auth flow, billing, rate limiting, deployment smoke tests

---

## Tech Stack

| Layer | Technology |
|---|---|
| Bot | aiogram 3.x |
| API | FastAPI + Uvicorn |
| Database | PostgreSQL + SQLAlchemy async |
| Migrations | Alembic |
| Queue | Redis + Celery |
| Payments | Stripe |
| Proxy | nginx |
| Containers | Docker + Docker Compose |

Python 3.11+ required.

---

## Architecture

```
User → Telegram → aiogram Bot
                       ↓
               FastAPI Backend
                       ↓
        ┌──────────────┴──────────────┐
        ↓                             ↓
   PostgreSQL                       Redis
(users, subs,                 (rate limiting,
  audit logs)                   task queue)
                       ↓
                     Stripe
             (checkout, webhooks)
```

---

## Who This Is For

✔ Python developers building monetized Telegram bots  
✔ Indie hackers who want to ship and charge fast  
✔ Agencies building bots for multiple clients  
✔ Technical founders who want to skip infrastructure  

**NOT for:** beginners without Python/aiogram experience.  
You implement the business logic. The framework handles everything else.

---

## Pricing

| License | Price | Usage |
|---|---|---|
| Solo | $149 | 1 project, 1 developer |

👉 **[Purchase on Gumroad](https://jankodur.gumroad.com)**

After purchase you receive:
- Access to private source repository
- Setup documentation
- Email support: hello@dulvarn.com

---

## Preview

```python
# Registering a premium-gated command is this simple:
@router.message(Command("premium_feature"))
@require_subscription(plan="premium")
async def premium_feature_handler(message: Message, user: User):
    await message.answer("Welcome, premium member!")
```

---

*Built by [Dulvarn](https://www.dulvarn.com)*