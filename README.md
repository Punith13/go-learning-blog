# Go Journey

A static daily Go learning journal for experienced TypeScript/Node.js developers. Built with **Astro 7**, Markdown, and Vercel. The curriculum develops one job-processing service across lessons.

## Run locally

Requires Node.js 22.23.4+ (or newer).

```sh
npm ci
npm run dev
npm run build
```

Visit http://localhost:4321. The index is at `/`, the searchable curriculum at `/blog/`, and lessons at `/blog/day-001/` and onward.

## Add a lesson

Add `src/content/blog/day-NNN.md` with these frontmatter fields:

```yaml
---
title: "Day 7 — An HTTP handler"
description: "A one-sentence summary"
pubDate: "2026-11-28"
---
```

The index, homepage and previous/next navigation automatically pick up files whose name matches `day-NNN`.

Keep each lesson roughly 20–30 minutes, including a focused explanation, runnable or starter code, an exercise, acceptance criteria, a hint, and a stretch goal. Don't claim exercises were completed without evidence.

## Deployment

Vercel is connected to GitHub. Merging to `main` triggers production deployment; a pull request can receive a preview.

## Automation plan (not enabled yet)

The daily content generator needs a model provider and a safe publishing policy. Proposed workflow: scheduled GitHub Action -> read curriculum and feedback -> generate Markdown -> validate code in a temporary Go module -> open a PR -> merge after review -> Vercel deploys.

Do **not** add an unattended scheduled generator until provider credentials, cost limits, validation and GitHub write permissions are configured. Local Ollama requires a reachable self-hosted runner; hosted models require an API integration. GitHub Actions cannot directly read private ChatGPT conversation history, so progress must be recorded in the repository or an explicitly connected data source.

The included `site-check.yml` runs the static build for PRs and pushes. It does not run an AI agent.
