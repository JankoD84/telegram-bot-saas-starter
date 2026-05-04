# Quickstart Preview

> **This is a teaser of the full quickstart guide.**  
> The complete step-by-step setup documentation is included with purchase.  
> → [Get access on Gumroad](https://jankodur.gumroad.com)

---

## Prerequisites

- Python 3.11+
- Docker + Docker Compose
- A Telegram bot token (from [@BotFather](https://t.me/BotFather))
- A Stripe account (test keys are fine to start)
- A PostgreSQL instance (or use the included Docker Compose stack)

---

## Step 1 — Clone the private repository

After purchase you receive collaborator access to the private source repo.

```bash
git clone git@github.com:JankoD84/telegram-bot-starter-kit.git
cd telegram-bot-starter-kit
```

---

## Step 2 — Configure environment

```bash
cp .env.example .env
```

Open `.env` and fill in:

```env
# Telegram
BOT_TOKEN=your_bot_token_here

# Database
DATABASE_URL=postgresql+asyncpg://user:password@db:5432/botdb

# Redis
REDIS_URL=redis://redis:6379/0

# Stripe
STRIPE_SECRET_KEY=sk_test_...
STRIPE_WEBHOOK_SECRET=whsec_...
STRIPE_PRICE_ID_PREMIUM=price_...

# Admin
ADMIN_TELEGRAM_IDS=123456789
```

---

## Step 3 — Start the stack

```bash
docker compose up --build
```

Services that start:
- `db` — PostgreSQL
- `redis` — Redis
- `api` — FastAPI on port 8000
- `bot` — aiogram bot (polling mode by default)
- `worker` — Celery worker

---

## Step 4 — Run migrations

```bash
docker compose exec api alembic upgrade head
```

---

## Step 5 — Talk to your bot

Open Telegram, find your bot, and send `/start`.

The framework automatically:
1. Creates a user record in PostgreSQL
2. Assigns the `free` plan tier
3. Applies rate limiting based on tier

---

*Steps 6–12 (webhook setup, Stripe checkout flow, deploying to a VPS, enabling your first plugin) are covered in the full documentation included with purchase.*

→ **[Purchase and get the full guide](https://jankodur.gumroad.com)**
