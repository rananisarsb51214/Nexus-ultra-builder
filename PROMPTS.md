# PROMPTS — Canonical Prompts & Examples

This file contains canonical prompts to use when composing agent requests. Use these as templates and adapt with additional context.

1. Site generation (SiteBuilderAgent)

Prompt template:

"Generate a responsive marketing website for a company called {company_name}. Target audience: {audience}. Must include: hero, features, pricing, contact form. Tone: {tone}. Provide: (1) site structure JSON, (2) page content drafts, (3) asset list."

2. Blog post (ContentAgent)

Prompt template:

"Write a {word_count}-word blog post about {topic} for {audience} with SEO keywords: {keywords}. Include title, meta description, headings, and suggested images."

3. Deployment dry-run (DeploymentAgent)

"Perform a dry-run for deployment of commit {commit_sha} to environment {env}. Output: build steps, estimated duration, checks that will run, and potential breaking changes."

Prompt best practices

- Keep system instructions brief and explicit.
- Provide concrete examples of desired output schema.
- Always include trace_id in the prompt.

Appendix: example prompts adapted from Master_Guide.md and Console Guide
