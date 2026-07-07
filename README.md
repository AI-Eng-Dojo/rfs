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

Each idea is submitted through one pull request and published as paired English and Japanese Markdown files under `docs/`. When the pull request is merged into `main`, GitHub Actions builds and publishes the idea list with GitHub Pages.

## How It Works

1. Create one English Markdown file and one Japanese Markdown file for one idea.
2. Open a pull request.
3. Review the idea and its risks.
4. Merge into `main`.
5. GitHub Pages updates the public idea list.

## Idea File

Create paired files like `docs/YYYY-MM-DD-slug.md` and `docs/YYYY-MM-DD-slug-ja.md`.

English file:

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

Japanese file:

```markdown
---
idea: true
title: "アイデア名"
summary: "アイデアの短い説明。"
date: YYYY-MM-DD
tags: [ai, devtools]
lang: ja
translation_key: YYYY-MM-DD-slug
alternate_url: /YYYY-MM-DD-slug.html
---

# アイデア名

## 概要

## 課題

## なぜ今か

## 最初のプロダクト

## 想定ユーザー

## 検証

## 未解決の問い
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
- Keep `translation_key` identical across the English and Japanese files.
- Use the pull request template, including the Red Team Review checklist.
- Include sources for factual claims when needed.
- Do not include confidential information or private customer data.
- Do not include raw HTML, scripts, iframes, or embedded remote content.
- Repository Pages settings should use **GitHub Actions** as the source.
- The root Pages URL uses browser language and timezone to send likely Japanese visitors to `index-ja.html`; users can still choose English from the language switch.
