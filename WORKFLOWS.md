# WORKFLOWS — Orchestration & Automation

This document describes common workflows, orchestration patterns, state transitions, and human-in-the-loop steps.

Workflow patterns

1. Create Website (user-driven)
   - User supplies high-level prompt → SiteBuilderAgent prepares spec → ContentAgent drafts content → template_renderer composes pages → preview created → human reviews → DeploymentAgent deploys to preview → on approval deploy to production.

2. Automated Content Refresh (scheduled)
   - Cron trigger → ContentAgent queries site analytics → generate updates → open pull request with changes → QA review → merge & deploy.

3. Billing Event Processing
   - Webhook from Stripe → AdminAgent validates event → DB update → notify user → generate invoice.

State Management & Idempotency

- Use immutable deployment artifacts (build IDs) and idempotent API endpoints.
- Store workflow state in a Workflows table (state machine with audit logs).

Retry & Backoff

- Use exponential backoff with jitter for transient failures. Mark retries on the workflow record.

Human Approval

- Approval tasks are surfaced in the Dashboard and via email/webhook. Approvals must include the trace_id and change summary.

Observability

- Emit events for workflow transitions. Correlate traces with trace_id for debugging.
