# CODING_STANDARDS — Kotlin / TypeScript / General

Purpose

Provide coding, testing, and repository standards to ensure maintainable and secure code.

General

- Use idiomatic Kotlin 1.9+ and TypeScript. Prefer data classes, sealed classes, and explicit types.
- Avoid nullable types unless required; prefer Result wrappers for errors.
- Document public APIs with KDoc or TSDoc.

Kotlin: Nisar AI OS rules

- Tools implement BaseTool and declare canHandle(intent: Intent) functions.
- No hidden side-effects; tools should be stateless where possible.
- Use Result.success and Result.failure to wrap outcomes.

TypeScript / Frontend

- Use strict TypeScript settings and eslint. Keep components small and testable.

Testing Strategy

- Unit tests for tool logic with 100% branch coverage on critical paths.
- Integration tests for agent orchestration with mocked external APIs.
- End-to-end tests running against a staging environment.
- CI: run lint → unit tests → integration tests → build → deploy-preview.

Security

- Secrets must never be in source. Use GitHub Secrets or environment variables.
- Run dependency scans and SCA in CI.

Code review

- Require at least one approving review and passing CI for merges.
