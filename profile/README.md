# Talkeo

> Native AI tutoring across the surfaces where language friction actually happens.

Talkeo is an AI-first language tutor. The native apps (Mac, Windows) consume the Talkeo Cloud backend for text selection actions, voice practice with Leo, and structured learning from your captured vocabulary.

Two ways to use Talkeo:

- **Self-hosted:** free, open source, bring your own provider keys.
- **Managed:** Talkeo is your provider for everything (database, LLMs, voice, hosting). Zero config, paid.

## Repositories

| Repo | What | Status |
|------|------|--------|
| [`talkeo`](https://github.com/talkeo-ai/talkeo) | Backend API (FastAPI, provider-agnostic) | Active (Phase A) |
| [`mac`](https://github.com/talkeo-ai/mac) | Talkeo for Mac (Swift, SwiftUI, AppKit) | Active (Phase A) |
| [`windows`](https://github.com/talkeo-ai/windows) | Talkeo for Windows (C# / .NET 8, Windows App SDK) | Active (Phase A) |
| [`infra`](https://github.com/talkeo-ai/infra) | Infrastructure as Code (Terraform, AWS) | Active (Phase B.1) |
| [`agents`](https://github.com/talkeo-ai/agents) | Multi-agent orchestration + eval harness | Planned (Phase C) |
| [`mcp`](https://github.com/talkeo-ai/mcp) | MCP server (Claude Desktop, Cursor, etc.) | Planned (Phase C) |
| [`web`](https://github.com/talkeo-ai/web) | Web frontend (Next.js) | Planned (Phase E) |
| [`mobile`](https://github.com/talkeo-ai/mobile) | Mobile app (iOS / Android) | Planned (Phase E) |

See the [ROADMAP](./ROADMAP.md) for phase details and the [backend architecture](https://github.com/talkeo-ai/talkeo/blob/main/docs/architecture.md) for the technical design.

## Tech stack

* **Backend.** Python, FastAPI, PostgreSQL with pgvector, Redis.
* **Native clients.** Swift (Mac), C# / .NET 8 (Windows). Future: TypeScript (web), native or React Native (mobile).
* **Infra.** AWS (ECS Fargate, RDS, S3, CloudFront, CloudWatch), Terraform.
* **Voice.** Leo, the tutor agent. WebRTC streaming.
* **Agents.** Multi-agent orchestration, RAG over user-captured selections, eval harness.

Each app lives in its own repo with its own toolchain. Clients consume the backend via OpenAPI — no shared source code between repos.

## Status

Active development. The backend (`talkeo`) is being rewritten with production patterns and will migrate to AWS in Phase B.1. The Mac app MVP (TalkeoSelect popup mode) is shipping incrementally. Windows is contributor-driven with an active first PR.

## License

MIT for public repositories.
