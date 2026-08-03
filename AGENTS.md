# AGENTS — Agent Definitions & Responsibilities

This document defines the AI agents used by Nexus Ultra Builder, their responsibilities, inputs, outputs, and failure modes.

Agent design principles

- Agents are stateless orchestrators that map intents to Tools.
- Each agent declares: name, primary intents, allowed tools, input schema, output schema, and retry rules.
- Use deterministic prompts and include the trace_id in every call.

Primary Agents

1. SiteBuilderAgent
   - Purpose: Generate or update full websites and pages using templates, content generation, and asset integration.
   - Inputs: {website_spec: object, content_prompts: []}
   - Tools: template_renderer, ai_content_generator, storage_uploader, api_patch_tool
   - Outputs: {website_id, deploy_preview_url}

2. ContentAgent
   - Purpose: Create marketing content, blog posts, landing pages, copy for CTAs.
   - Inputs: {topic, audience, tone}
   - Tools: ai_content_generator, seo_analyzer
   - Outputs: {draft_text, seo_score}

3. DeploymentAgent
   - Purpose: Prepare build artifacts and orchestrate deployment on Vercel or Docker.
   - Inputs: {build_config, environment}
   - Tools: ci_runner, vercel_cli_adapter, docker_builder
   - Outputs: {deployment_id, url, status}

4. AdminAgent
   - Purpose: Manage user, org, billing and analytic tasks via admin APIs.
   - Inputs: {user_action, target}
   - Tools: admin_api_client
   - Outputs: {status, details}

Failure & Recovery

- On partial failure, agents should return structured errors and indicate if operation is retryable.
- For destructive actions, require an explicit human approval token.

Testing Agents

- Provide unit-level tests mocking tool responses.
- Provide end-to-end integration tests in a staging environment using ephemeral test orgs.

Source references: Master_Guide.md, Console Guide, Architecture.md
