# Talkeo Roadmap

This roadmap describes the public direction of the Talkeo ecosystem. It captures phases, scope, and intent — not internal commitments or dates that can shift.

## What is Talkeo

Talkeo is an open-source AI assistant ecosystem focused on language learning and text-context augmentation. The platform exposes provider-agnostic APIs (LLM, STT, TTS) and powers native apps (Mac, Windows) plus a managed Cloud experience.

**Two ways to use Talkeo:**

- **Self-hosted:** clone the public repos, bring your own provider API keys, run locally or on your own infrastructure.
- **Managed (Talkeo Cloud):** zero-config, we host everything and route to providers internally.

## Repositories

| Repo | Purpose | Status |
|---|---|---|
| [`talkeo`](https://github.com/talkeo-ai/talkeo) | Backend API + business logic + providers | Active (Phase A) |
| [`mac`](https://github.com/talkeo-ai/mac) | Mac app (Swift, native) | Active (Phase A) |
| [`windows`](https://github.com/talkeo-ai/windows) | Windows app (C# / WPF) | Active (Phase A) |
| [`infra`](https://github.com/talkeo-ai/infra) | Infrastructure as code (Terraform, AWS) | Active (Phase B.1) |
| [`agents`](https://github.com/talkeo-ai/agents) | Multi-agent orchestration + eval harness | Planned (Phase C) |
| [`mcp`](https://github.com/talkeo-ai/mcp) | MCP server (consumable from Claude Desktop / Cursor) | Planned (Phase C) |
| [`web`](https://github.com/talkeo-ai/web) | Web frontend (Next.js) | Planned (Phase E) |
| [`mobile`](https://github.com/talkeo-ai/mobile) | Mobile app (iOS / Android) | Planned (Phase E) |

Each repo holds a single concern. Apps written in different languages (Python backend, Swift Mac, C# Windows, TypeScript web, mobile native) live in separate repos with their own toolchain, CI, and release cadence. They share no source code — instead, clients consume the backend's OpenAPI spec to generate type-safe API access.

## Phases

### Phase A — Mac MVP backend

**Scope:** FastAPI backend with streaming endpoints and provider-agnostic ports, powering the Mac app's text features: translate, improve copy, capture text (OCR), and listen-to-pronunciation (one-shot TTS playback). LLM streams through the gateway; one-shot TTS through the speech abstraction. Realtime voice (STT + Leo sessions) lands in Phase B.1.

**Stack:** Python 3.12, FastAPI, Pydantic v2, async streaming SSE. Deploys to AWS (ECS). No persistence layer yet — endpoints are stateless.

**Output:** public backend repo with clean architecture foundation, Mac app using it as daily driver.

### Phase B.1 — Cloud migration

**Scope:** PostgreSQL on AWS RDS, full backend rewrite of the voice session pipeline under clean architecture, infrastructure refactor to production-grade Terraform modules (multi-env, modular, documented).

**Stack:** PostgreSQL 16, SQLAlchemy 2.0 async, Alembic migrations, AWS (VPC, ECS Fargate, ALB, ACM, S3, CloudWatch), Docker production builds, GitHub Actions CI/CD.

**Output:** Talkeo Cloud running on AWS production, Mac app connected to Cloud, architecture decision records (ADRs) public.

### Phase B.2 — Mac ↔ Cloud integration

**Scope:** authenticated user sessions, selection persistence, practice generation endpoint that builds on stored user context.

**Output:** end-to-end flow from user-selected text in any Mac app → Talkeo backend → tailored practice session.

### Phase C — Agentic + observability

**Scope:** multi-agent orchestration (Leo conversation + Tutor + Evaluator + Coach), Redis caching, RAG with pgvector, evaluation harness, observability (OpenTelemetry, structured logs, dashboards), MCP server.

**Output:** senior-level backend with multi-agent flows, full observability, public MCP server consumable from Claude Desktop and Cursor.

### Phase D — Polish + outreach

**Scope:** portfolio refresh, documentation polish, architecture writeups, additional language support, Go service taste.

### Phase E (deferred) — Web + mobile

**Scope:** web frontend rewrite, React Native mobile, both consuming the same public backend.

## Architecture

See [`talkeo/docs/architecture.md`](https://github.com/talkeo-ai/talkeo/blob/main/docs/architecture.md) for the technical architecture: layered design (Clean / Hexagonal), provider abstraction via ports & adapters (LLM through a unified gateway, speech through voice plugins), prompts as data, and bounded contexts (Session, Pedagogy, User, Learning, Director).

## Contributing

External contributions are welcome. Each repo has a `CONTRIBUTING.md` explaining the development workflow, testing strategy, and PR conventions. Issues are labeled with `good first issue` and `help wanted` where applicable.

## License

MIT for public repos.
