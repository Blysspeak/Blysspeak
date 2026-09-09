<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Blysspeak/Blysspeak/main/assets/banner-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Blysspeak/Blysspeak/main/assets/banner-light.svg">
  <img alt="Vladislav Rakhmanov, backend engineer for the part of a system where money moves" src="https://raw.githubusercontent.com/Blysspeak/Blysspeak/main/assets/banner-light.svg" width="100%">
</picture>

<br><br>

[![Telegram](https://img.shields.io/badge/Telegram-%40blysspeak-26A5E4?style=flat-square&logo=telegram&logoColor=white)](https://t.me/blysspeak)
[![Email](https://img.shields.io/badge/blysspeak%40nexalix.io-1F6FEB?style=flat-square&logo=minutemailer&logoColor=white)](mailto:blysspeak@nexalix.io)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-blysspeak-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/blysspeak)
[![Nexalix Labs](https://img.shields.io/badge/nexalix.io-0B0D10?style=flat-square&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAzMiAzMiI+PHBhdGggZD0iTTkgOSBMMjMgMTEgTDEzIDIzIFoiIHN0cm9rZT0iI0Y1RjdGQSIgc3Ryb2tlLXdpZHRoPSIxLjkiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIgZmlsbD0ibm9uZSIvPjxjaXJjbGUgY3g9IjkiIGN5PSI5IiByPSIyLjQiIGZpbGw9IiNGNUY3RkEiLz48Y2lyY2xlIGN4PSIyMyIgY3k9IjExIiByPSIyLjQiIGZpbGw9IiNGNUY3RkEiLz48Y2lyY2xlIGN4PSIxMyIgY3k9IjIzIiByPSIyLjgiIGZpbGw9IiMwMDk4RUEiLz48L3N2Zz4=)](https://nexalix.io)

</div>

<br>

## Payments in production

What I am hired for: acquiring, subscriptions with recurring charges, balances and transaction journals, exact arithmetic on money paths, provider webhooks with protection against repeated processing. Around that: third party API integrations, background queues, bots and admin panels. I run the result in production myself.

Commercial work lives in private repositories, so the projects stay unnamed here. The numbers are counted, not estimated.

**Content generation SaaS platform**

- Acquiring built from scratch on YooKassa: a payment carries a unique idempotency key and a unique provider ID, so a repeated call cannot create a second charge.
- A separate payment event log: webhook received, duplicate ignored, signature check failed, auto renewal attempted, refund initiated, each entry keeping the status before and after.
- Ledger for the internal currency: the balance is always derived from the transaction history.
- BullMQ queue with deduplication by explicit job ID, so the same job is not queued twice.
- Deploy on merge to main with automatic rollback, OpenTelemetry and Sentry in production.
- Five months of work: 1174 commits, 128 merged pull requests, 271 releases, currently v1.50.0. 83 Prisma models, 101 migrations, 5579 tests.

**Subscription VPN service, my own product.** 14 consecutive months in production, 585 commits, five processes under pm2, 769 tests.

- Four payment providers behind a single payment layer: CryptoBot for crypto, Telegram Stars, YooKassa, bePaid. Adding a provider does not spread across the codebase.
- Recurring charges: the provider notification is verified, then handled idempotently through Redis `SET NX` with a TTL, so a redelivered webhook never extends a subscription twice.

**Currency and crypto exchange service, client project.** Amounts stored and computed as `Decimal` with up to 8 decimal places, no float on any path that touches money. 17 models, 21 unique indexes, 20 migrations, 1333 tests.

Beyond these: a browser strategy game backend with a tick based economy, and more than 20 Telegram bots and client sites since 2024, from scraping and monitoring to third party integrations, admin panels and automation.

---

## Nexalix Labs

My own product line: fraud prevention for TON and Telegram Mini Apps, plus developer tools. [nexalix.io](https://nexalix.io) · [github.com/Nexalix-Labs](https://github.com/Nexalix-Labs)

- **[ledgent](https://github.com/Nexalix-Labs/ledgent)** · public · `@nexalix/ledgent` on npm. CLI that measures the real token spend of AI agents from local Claude Code session logs. Apache-2.0, zero runtime dependencies, not a single network call.
- **[agora](https://github.com/Nexalix-Labs/agora)** · public. Spotlight style launcher for Windows on Tauri, opens on Alt+Space.
- **Guard** · private. Anti sybil and fraud detection API for Telegram Mini Apps and TON. Fastify, PostgreSQL directly through `pg` and `node-pg-migrate` with no ORM, Redis, Zod, argon2, the official TON SDK. 198 tests, and the integration suite starts real PostgreSQL and Redis in containers instead of mocks.

---

## Open source

| Repository | What it does |
| --- | --- |
| **[aurelius](https://github.com/Blysspeak/aurelius)** `Rust` | Self hosted knowledge graph for developers and AI agents: MCP server, interactive graph, auto indexing. 13 releases |
| **[timeforged](https://github.com/Blysspeak/timeforged)** `Rust` | Self hosted time tracking for developers: daemon, CLI, tray app and web dashboard. 9 releases, v0.1.0 to v0.5.4. MCP client in [timeforged-mcp](https://github.com/Blysspeak/timeforged-mcp) |
| **[beacon](https://github.com/Blysspeak/beacon)** `Rust` | Daemon that watches CI/CD after a git push: Telegram alerts, Waybar widget, Claude Code integration. 3 releases |
| **[rvnc](https://github.com/Blysspeak/rvnc)** `Rust` | An Android phone as a second monitor over USB: GPU accelerated H.264 streaming through VAAPI |

These are tools I run myself, on Axum, sqlx, ratatui and egui. Rust is a hobby and an OSS playground, not my commercial stack.

<div align="center">
  <a href="https://github.com/Blysspeak/timeforged">
    <img alt="Coding time this year, tracked by my own TimeForged daemon" src="https://timeforged.nexalix.io/api/v1/card/blysspeak" width="100%">
  </a>
</div>

<sub>Live from my own instance: the daemon watches file changes and Claude Code hooks, the card is rendered server side by TimeForged itself.</sub>

---

## Stack

| | |
| --- | --- |
| **Language and runtime** | TypeScript, Node.js, Bun |
| **HTTP and realtime** | Fastify, Express, NestJS, Hono, socket.io |
| **Data** | PostgreSQL, Prisma, SQLite. Schemas, migrations, transactions, unique indexes |
| **Queues and cache** | BullMQ, Redis (ioredis), node-cron |
| **Validation and tests** | Zod, Vitest |
| **Production** | Linux VPS, pm2, nginx, GitHub Actions, Docker |
| **Observability** | OpenTelemetry, Sentry, pino, winston |
| **Client side** | React, Vue, Vite, Tailwind, Astro, Telegram Mini Apps, Tauri |
| **Integrations** | grammy, Telegraf, Puppeteer, MCP servers |

## How I work

I confirm the cause with a log or a measurement before fixing anything, and I look for every cause, not the first one. "Done" means the tests and a live scenario were run. Changes are surgical and go through a branch and a pull request, so a rollback is one command.

## Background

In development since 2021. Almost four years at EPAM Systems in Minsk, from 2021 to 2024: joined as a student intern in my third year at BSUIR, faculty of computer systems and networks, and grew into a senior backend developer on Node.js and TypeScript. Since 2024 I build my own products and take on client work as the founder of Nexalix Labs.

58 of my 72 repositories are private, so the contribution graph below shows a small share of the actual work.

---

<div align="center">

**Open to backend work on payments, billing, integrations and production support.**

Telegram [@blysspeak](https://t.me/blysspeak) is the fastest channel.<br>
`blysspeak@nexalix.io` for Nexalix Labs, `rahmanov.official@yandex.ru` for everything else.

Names of the closed projects, a code walkthrough and demos on a call.

</div>
