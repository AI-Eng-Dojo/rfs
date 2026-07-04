<h1 align="center">
  <img src="docs/icon.png" alt="Requests for Startups icon" width="128">
  <br>
  Requests for Startups
</h1>

<p align="center">
  <a href="README.md">English</a> |
  <a href="README-ja.md">日本語</a>
</p>

A simple repository for collecting startup ideas through pull requests.

Each idea is stored as one Markdown file under `docs/`. When the pull request is merged into `main`, GitHub Actions builds and publishes the idea list with GitHub Pages.

## How It Works

1. Create one Markdown file for one idea.
2. Open a pull request.
3. Review the idea and its risks.
4. Merge into `main`.
5. GitHub Pages updates the public idea list.

## Idea File

Create files like `docs/YYYY-MM-DD-slug.md`.

```markdown
---
idea: true
title: "Idea Title"
summary: "A short description of the opportunity."
date: YYYY-MM-DD
tags: [ai, devtools]
lang: en
translation_key: YYYY-MM-DD-slug
alternate_url: /YYYY-MM-DD-slug-ja.html
---

# Idea Title

## Summary

## Problem

## Why Now

## First Product

## Potential Users

## Validation

## Open Questions
```

## Repository Layout

```text
docs/
  index.md                 # Public idea index in English
  index-ja.md              # Public idea index in Japanese
  YYYY-MM-DD-slug.md       # One English idea file
  YYYY-MM-DD-slug-ja.md    # Matching Japanese idea file
.github/
  pull_request_template.md
  workflows/pages.yml
AGENTS.md
CLAUDE.md -> AGENTS.md
```

## Notes

- Keep one idea per pull request.
- Add both English and Japanese docs when publishing an idea, and link them with `alternate_url`.
- Use the pull request template, including the Red Team Review checklist.
- Include sources for factual claims when needed.
- Do not include confidential information or private customer data.
- Do not include raw HTML, scripts, iframes, or embedded remote content.
- Repository Pages settings should use **GitHub Actions** as the source.
