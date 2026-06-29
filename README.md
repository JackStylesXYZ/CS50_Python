# CS50_Python

## Project Goal

This repository tracks my CS50 Python journey while building a real, public-facing project.

The purpose is to:
- Sharpen Python fundamentals through hands-on work.
- Build a clean, maintainable application using modern practices.
- Demonstrate practical skills publicly (backend, APIs, realtime data, Docker, and databases).

## Product Vision

Build a simple crypto market web app where a user can:
- Register, log in, and stay in a session.
- Search and select trading pairs/symbols (for example, Binance pairs).
- Click a `Fetch Data` button to retrieve REST market data.
- Enable a live mode to receive WebSocket updates (price, spread, and order book data).
- Save favorite symbols to a personal dashboard.

## Why Docker

The project runs in Docker to keep development isolated and reproducible.

Benefits:
- Consistent environment across machines.
- Clear service boundaries.
- Easy onboarding and demo setup for reviewers.

## Initial Scope (MVP)

Keep the first version intentionally simple:
- Auth + session-based login.
- Symbol list and symbol search/select.
- REST fetch for selected symbol and display key data.
- Live WebSocket stream for selected symbol.
- Basic user dashboard with favorites.

## Planned Architecture

Start simple, then split services only when needed.

Initial service layout:
- `api`: FastAPI app for auth, sessions, market endpoints, and websocket relay.
- `db`: PostgreSQL for users and favorites.
- `web`: Simple UI pages (templates + light JavaScript).

Possible later service:
- `analytics-worker`: pandas/technical indicators (RSI, EMA) when analytics grows.

## Database Plan

Core tables:
- `users` (`id`, `email`, `password_hash`, `created_at`)
- `favorites` (`id`, `user_id`, `symbol`, `created_at`)

Rules:
- `email` is unique.
- (`user_id`, `symbol`) is unique to prevent duplicate favorites.

## Feature Roadmap

### Phase 1 - Core App
- Project scaffold, Docker setup, and database wiring.
- Registration, login, logout, and sessions.
- Symbol selection and REST fetch flow.

### Phase 2 - Realtime
- WebSocket streaming for selected symbol.
- Live UI updates for price, bid/ask, spread, and basic order book.
- Reconnect and resilience handling.

### Phase 3 - Dashboard
- User dashboard with favorite symbols.
- Quick navigation between dashboard, market, and live pages.
- Basic account/settings placeholders.

### Phase 4 - Technical Indicators
- Add RSI/EMA endpoints and UI cards.
- Use pandas + a technical analysis library.
- Move heavy analysis to a separate worker service if needed.

## Design Principles

- Keep it simple and readable first.
- Prefer DRY and maintainable patterns.
- Add complexity only when there is a clear reason.
- Build in small, testable milestones.

## Success Criteria

This project is successful when:
- A user can sign in, choose a symbol, fetch REST data, and watch live updates.
- Favorites persist in the database and appear on the dashboard.
- The full app runs reproducibly with Docker.
- The codebase remains clean and understandable as features are added.

---

*Footnote: If time allows after the core Dockerized application is complete, infrastructure as code (IaC) using Terraform may be added as a follow-on phase for AWS deployment.*