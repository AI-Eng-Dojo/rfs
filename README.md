<h1 align="center">
  <img src="docs/icon.png" alt="Requests for Startups icon" width="128">
  <br>
  Requests for Startups
</h1>

<p align="center">
  <a href="README.md">English</a> |
  <a href="README-ja.md">日本語</a>
</p>

Requests for Startups is a public idea board for startup opportunities. It is inspired by Y Combinator's [Requests for Startups](https://www.ycombinator.com/rfs), where people share problems and markets they want founders to tackle.

This repository is intended to work as a lightweight publishing flow:

1. Contributors submit startup ideas as pull requests.
2. Reviewers discuss and refine the idea in GitHub.
3. Merged ideas become source content for GitHub Pages.
4. The published site shows an idea list, categories, summaries, and deeper explanations.

This is an independent project and is not affiliated with, endorsed by, or sponsored by Y Combinator.

## Goal

The goal is to turn promising startup prompts into a durable, browsable backlog. A good request should make it easier for a founder to decide whether to investigate a market, talk to users, or build an early prototype.

Each idea should answer:

- What painful or urgent problem exists?
- Why is now a good time to solve it?
- Who feels the problem strongly enough to try a new product?
- What could a startup build first?
- What would count as early validation?
- What risks, constraints, or open questions remain?

## How Ideas Flow

```text
Pull request -> review -> merge -> GitHub Pages build -> public idea page
```

The repository treats Markdown files under `docs/` as the source of truth. GitHub Actions builds those files with Jekyll and publishes the result to GitHub Pages after changes are merged to `main`. The published site renders:

- an index of all ideas
- detail pages for each request
- tags and categories
- short summaries for scanning
- longer explanations for founders who want more context
- contributor and source attribution where appropriate

## Proposed Repository Shape

```text
rfs/
├── README.md                       # English overview
├── README-ja.md                    # Japanese overview
├── AGENTS.md                       # Shared agent workflow
├── CLAUDE.md -> AGENTS.md          # Claude-compatible symlink
├── .github/
│   ├── pull_request_template.md
│   └── workflows/pages.yml         # Builds and deploys GitHub Pages
└── docs/
    ├── index.md                    # Published idea index
    ├── icon.png                    # Site and README icon
    └── YYYY-MM-DD-slug.md          # One idea per file
```

The first version stays intentionally simple: contributors add one Markdown file per idea under `docs/`, and GitHub Pages renders the public index and detail pages.

## Idea Format

Use one pull request per idea. A submitted idea should include these sections:

```markdown
---
idea: true
title: "Idea Title"
summary: "A short description of the startup opportunity."
date: YYYY-MM-DD
tags: [ai, healthcare, devtools]
---

# Idea Title

## Summary

A short description of the startup opportunity.

## Problem

Who has the problem, how it appears today, and why existing options are not enough.

## Why Now

What changed recently: technology, regulation, cost curves, user behavior, distribution, or market structure.

## First Product

The smallest useful product or service a startup could build to test the opportunity.

## Potential Users

The first users or buyers to interview.

## Validation

Signals that would make the idea more credible.

## Open Questions

Unknowns, risks, hard constraints, or reasons the idea may fail.

## Tags

ai, healthcare, devtools, climate, robotics, fintech, enterprise, etc.
```

## Contribution Guidelines

- Submit concrete startup ideas, not generic trend summaries.
- Explain the user, the pain, and the timing.
- Prefer specific wedges over huge abstract markets.
- Include sources when the claim depends on outside facts.
- Do not include confidential information, private customer data, or material you do not have rights to share.
- Keep each pull request focused on one idea.
- Store the idea as `docs/YYYY-MM-DD-slug.md` with `idea: true` in the front matter.
- Acceptance means the idea is useful to publish; it does not mean the maintainers endorse the market or guarantee the idea will work.

## Editorial Principles

Requests should be ambitious but actionable. The strongest entries usually have:

- a clear user with an expensive or frequent problem
- a recent shift that makes the idea newly possible
- a first product that can be built by a small team
- a path from narrow wedge to larger company
- enough explanation for readers to form their own view

The published Pages site should make the ideas easy to scan first and easy to study second.

## GitHub Pages

The Pages site provides:

- `/` - a searchable idea index
- `/<slug>/` - a detail page for each idea
- tag labels for categories such as AI, infrastructure, healthcare, enterprise, hardware, and climate
- future room for RSS or JSON output for people who want to follow new requests
- future room for links back to the pull request that introduced each idea

The workflow in `.github/workflows/pages.yml` builds Pages on pull requests that touch `docs/**` and deploys after the changes are merged to `main`. Repository Pages settings must use **GitHub Actions** as the Pages source.

## Reference

- Y Combinator Requests for Startups: <https://www.ycombinator.com/rfs>
- Reference checked: 2026-06-27
