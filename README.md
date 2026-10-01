# Amantu Khan — Backend, DevOps & AI Engineer

I'm **Amantu Khan**, a **backend, DevOps and AI engineer**. I build AI-integrated backends, multi-tenant SaaS platforms and messaging infrastructure for WhatsApp, TikTok, Meta and SMS, and I self-host on Docker by default. I mostly work in **Python, FastAPI, Node.js, TypeScript, Next.js and SvelteKit**. I also make commercial **FiveM / Lua scripts** for QBCore, ESX and standalone GTA V roleplay servers, and open-source desktop tools in **Rust, Tauri and .NET**.

**[GitHub](https://github.com/amantu-qbit)** · **[Email](mailto:amantu.khan2013@gmail.com)** · **[Open-source projects](#open-source-projects)** · **[Tech stack](#tech-stack)**

> Trying to be better, always trying to help and improve.

## Contents

- [What I do](#what-i-do)
- [Selected work](#selected-work)
- [Open-source projects](#open-source-projects)
- [FiveM and Lua scripts](#fivem-and-lua-scripts)
- [Tech stack](#tech-stack)
- [How I architect AI backends](#how-i-architect-ai-backends)
- [Contact](#contact)

## What I do

### AI systems and LLM engineering

Production **LLM pipelines**, **retrieval-augmented generation (RAG)** and **conversational AI agents** on OpenAI, Anthropic Claude and Google Gemini, with streaming, caching and guardrails.

### Multi-tenant SaaS backends

Commercial **multi-tenant APIs** with billing, webhooks and job queues, built on FastAPI, Node.js and PostgreSQL.

### Messaging infrastructure

**WhatsApp Cloud API**, TikTok, Meta and **SMS** integrations: inbound webhooks and high-volume outbound messaging via Twilio and BullMQ queues.

### DevOps and self-hosting

**Dockerized, self-hosted** deployments with CI/CD, observability and backups set up from day one, using Coolify, Traefik, GitHub Actions, Grafana, Loki, Prometheus and Sentry.

## Selected work

### SalesLeon — multi-tenant AI commerce platform

Conversational AI for orders, customer service and business automation across **WhatsApp, TikTok, Facebook and the web**. One backend serves many brands.

**Stack:** Python 3.12, FastAPI, OpenAI, Claude, Gemini, multi-tenant architecture.

### AmirusSMS — bulk SMS messaging platform

SMS infrastructure for operators at scale, covering campaigns, provider failover, queueing and delivery analytics. It's a Dockerized monorepo.

**Stack:** Next.js, Node.js, Docker, Twilio.

### Amirus Studio — software studio website and brand system

Built with **SvelteKit 2** and **Svelte 5 runes**. A runtime theme engine swaps accent palettes and logo variants without a rebuild, and the styling is pure CSS with no UI framework.

**Stack:** SvelteKit 2, Svelte 5, Vite 6, CSS.

### Game Account Manager — credential and inventory web app

A web app for managing and sharing game accounts: credentials, in-game state, skins, battle passes and ban status, all with an audit trail.

**Stack:** Next.js, TypeScript, PostgreSQL.

## Open-source projects

### [Palworld Server Manager](https://github.com/amantu-qbit/palworld-server-manager)

A modern, open-source **desktop control panel for Palworld dedicated servers**. It has a real-time dashboard (server FPS, uptime, players online, frame time), a live world map of players and Pals, player management (kick, ban, unban), a command console, trend graphs and a settings editor. An optional **Server+ Bridge**, written in **Rust**, adds save-file tools for characters, storage and guilds. They need no mods and back up before every change.

**Stack:** Tauri v2, React 18, TypeScript, Rust · MIT license · Windows.

### [LingoLens](https://github.com/amantu-qbit/LingoLens)

A transparent, **on-device screen-translation overlay for Windows**. It finds Chinese text in any window, region or monitor with on-device OCR (PP-OCRv5 or Windows OCR) and draws the English translation right where the original sits. New text is translated in about 35–85 ms, and repeated lines come from translation memory in under 5 ms. It runs on NVIDIA, AMD and Intel GPUs or on the CPU alone, fully offline.

**Stack:** .NET 10, C#, WPF, ONNX Runtime (DirectML) · MIT license.

### [Discord All-in-One Bot](https://github.com/amantu-qbit/discord-server-stats-bot)

A **Discord bot** that combines live server statistics (CPU, RAM and disk, with charts), moderation tools, music playback and a web control panel.

**Stack:** Node.js, discord.js 14, Express, Socket.IO, Chart.js.

I've also shipped QBCore resource forks, NPWD (TypeScript) work, GTA V audio-occlusion tools and FiveM Loki logging setups.

## FiveM and Lua scripts

A commercial **FiveM / FXServer Lua script** catalog sold on **Tebex**. Every script works on **QBCore, ESX and standalone** servers through a shared `fsh-lib` bridge, so one codebase runs on any server stack.

- **fsh-lib** — the core bridge for framework, inventory, UI, dispatch, phone, MDT, garage and keys. It auto-detects QBCore, ESX or standalone and supports 9+ inventory systems, with a Svelte NUI.
- **FSH-Crafting** — skill-check crafting with XP and levelling, placeable benches, nonce-based anti-replay and oxmysql persistence.
- **FSH-Weapontuner** — per-weapon damage, recoil and spread tuning with a React admin UI, presets and an audit log.
- **FSH-Drug-Scale** — a placeable drug-breakdown scale with risk and reputation. Standalone, with zero dependencies.
- **fsh-moneywash** — money-laundering machines with wear, part durability and placeable props.
- **FSH-Plug** — phone-booth supplier encounters with trust and heat, plus an audio abstraction over four backends.
- **FSH-Trapper** — street drug sales with an employee system and vehicle buyer spawns.
- **FSH-Car-Stash** — hidden vehicle stashes with key-script integration and persistent per-vehicle oxmysql storage.

## Tech stack

| Area | Technologies |
| --- | --- |
| Languages | Python, TypeScript, JavaScript, Go, Rust, C#, Lua |
| Backend and data | FastAPI, Node.js, Pydantic, PostgreSQL, Redis, MongoDB, Prisma, Drizzle, BullMQ |
| AI and LLMs | OpenAI, Anthropic Claude, Google Gemini, LangChain, RAG |
| Messaging and payments | WhatsApp Cloud API, Meta Graph API, TikTok, Twilio, Stripe, Discord, Socket.IO, SMTP, webhooks |
| DevOps and observability | Docker, Coolify, Traefik, Nginx, Linux, Bash, GitHub Actions, Cloudflare, Vercel, Grafana, Loki, Prometheus, Sentry |
| Frontend | Next.js, React, Svelte 5, SvelteKit, Vue, Vite, Tailwind CSS, shadcn/ui, TanStack Query, Zustand |
| Desktop | Tauri v2, .NET 10, WPF |
| Game development | FiveM, QBCore, ESX, Lua 5.4, Tebex |

## How I architect AI backends

This is a typical **multi-tenant AI backend**. Tenants are isolated at every layer, LLM calls go through a policy gate, and messages fan out to channels through a durable queue.

1. A **client or messaging channel** calls the **API gateway**.
2. A **tenant router** sends each request to tenant-isolated **PostgreSQL** (row-level security), **Stripe billing**, the **LLM orchestrator** or the job queue.
3. The **LLM orchestrator** routes model calls to **OpenAI, Anthropic or Gemini**, depending on policy.
4. A **durable queue** handles **webhook dispatch** and **provider fan-out** (WhatsApp, SMS and more).
5. **Observability** (logs, metrics, traces) covers the gateway, router, orchestrator and queue.

## Contact

Need a backend, an AI integration, messaging infrastructure or a FiveM script? Email me at **[amantu.khan2013@gmail.com](mailto:amantu.khan2013@gmail.com)** or find me on **[GitHub @amantu-qbit](https://github.com/amantu-qbit)**.
