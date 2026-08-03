# ARCHITECTURE — Nexus Ultra Builder (Consolidated)

Source: Consolidated from Architecture.md in the repository (file: Architecture.md).

Overview

Nexus Ultra Builder is a modular AI Operating System designed to enable programmatic creation and management of websites, applications, workflows, and AI agents. The system is organized in layers:

- Client Layer: Next.js + React + TypeScript + Tailwind
- API Layer: Next.js API routes and serverless functions
- Business Logic Layer: Node.js utilities, AI adapters, authentication, and validation
- Data Layer: PostgreSQL via Prisma, optional Redis cache
- External Integrations: Payment (Stripe), AI APIs, Webhooks

Key architectural principles

- Tool-First Architecture: Business capabilities are encapsulated as tools or agents. Orchestration code only routes intents and composes tool calls.
- Separation of Concerns: Clear boundaries between orchestration, intent routing, and tool implementations.
- Deterministic Execution: All operations are traceable and idempotent where possible.

Components

- Frontend: Next.js application (marketing site, dashboard, visual site builder)
- API: Next.js API routes implementing auth, website and page management, AI endpoints, analytics, billing
- Agents: Defined orchestrators that call tools to perform tasks (see AGENTS.md)
- Tools: Reusable, stateless modules implementing business logic (lib/*)
- Database: PostgreSQL + Prisma ORM
- Cache & Queue: Optional Redis for caching and task queuing

Security & Compliance

Follow enterprise security best practices (see DEPLOYMENT.md and CODING_STANDARDS.md). Use GitHub Secrets, environment variables, least privilege principles, and secret rotation.

Traceability

Each orchestrated action must include a trace_id and produce machine-readable logs describing inputs, called tools, and outputs for auditing.

Source mapping

This document was assembled from the repository Architecture.md (file path: Architecture.md, commit OID: acf1089407e6d5c7a7a0f92e00db85bc839a9e07). For full architecture diagrams and ASCII visuals, see the original file.
