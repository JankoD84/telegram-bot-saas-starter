# Repository Context

## What this repository is

`telegram-bot-saas-starter` is a Telegram Bot SaaS starter-kit repository. Current tracked documentation positions it as a Python framework for monetized Telegram bots with reusable infrastructure for authentication, subscriptions, rate limiting, deployment, and extension through bot-specific plugins/examples.

## Primary stack from repository documentation

- Python 3.11+
- aiogram 3.x
- FastAPI / Uvicorn
- PostgreSQL with SQLAlchemy async and Alembic
- Redis and Celery
- Stripe subscriptions, checkout, webhooks, and customer portal
- Docker Compose, nginx, and systemd deployment patterns
- pytest-oriented testing guidance in product docs

## High-level architecture

- Bot layer receives Telegram commands through aiogram handlers and middleware.
- FastAPI backend handles Stripe webhooks, admin API, and subscription logic.
- PostgreSQL stores users, subscriptions, and audit logs.
- Redis supports rate limiting and Celery task queues.
- Plugin/extension guidance separates reusable framework code from domain-specific bot behavior.

## Ownership

This repository owns the starter-kit governance, product documentation, and any source/runtime files committed here for the Telegram Bot SaaS kit.

It does not own external Telegram Bot API state, Stripe dashboard state, buyer production infrastructure, DNS/TLS state, or unrelated Dulvarn platform decisions.

## Important external dependencies

- Telegram Bot API and BotFather-issued tokens
- Stripe products, subscriptions, checkout, webhooks, and customer portal
- PostgreSQL and Redis in production-like deployments
- Docker/nginx/VPS deployment environment
