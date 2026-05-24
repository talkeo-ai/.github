# Talkeo

> Native AI tutoring across the surfaces where language friction actually happens.

Talkeo is an AI-first language tutor. The native apps (Mac, Windows) consume the Talkeo Cloud backend for text selection actions, voice practice with Leo, and structured learning from your captured vocabulary.

Two ways to use Talkeo:

- **Self-hosted:** free, open source, bring your own provider keys.
- **Managed:** Talkeo is your provider for everything (database, LLMs, voice, hosting). Zero config, paid.

## Repositories

| Repo | What |
|------|------|
| [`talkeo`](https://github.com/talkeo-ai/talkeo) | Backend monorepo (FastAPI + Next.js + React Native) |
| [`mac`](https://github.com/talkeo-ai/mac) | Talkeo for Mac (Swift, SwiftUI, AppKit) |
| [`windows`](https://github.com/talkeo-ai/windows) | Talkeo for Windows (C# + WinUI 3, planned) |
| [`infra`](https://github.com/talkeo-ai/infra) | Infrastructure as code (Terraform / CDK + AWS) |
| [`agents`](https://github.com/talkeo-ai/agents) | Multi-agent orchestration and eval harness |
| [`mcp`](https://github.com/talkeo-ai/mcp) | MCP server, consumable from Claude Desktop, Cursor, and other agent clients |

## Tech stack

* **Backend.** Python, FastAPI, PostgreSQL with pgvector, Redis.
* **Frontend.** TypeScript, Next.js, Swift, C#.
* **Infra.** AWS (ECS Fargate, RDS, S3, CloudFront, CloudWatch), Terraform / CDK.
* **Voice.** Leo, the tutor agent. WebRTC streaming.
* **Agents.** Multi-agent orchestration, RAG over user-captured selections, eval harness.

## Status

Active development. The backend is being rewritten with production patterns and migrated to AWS. The Mac app MVP (TalkeoSelect popup mode) is shipping incrementally. Windows is planned, contributor-driven.

## License

MIT for public repositories.
