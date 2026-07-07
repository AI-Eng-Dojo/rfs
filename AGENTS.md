# Agent Instructions

## Project

This repository is for Requests for Startups, a public idea board for startup opportunities submitted through pull requests.

The intended flow is:

```text
idea pull request -> review -> merge -> GitHub Pages -> public idea list and detail pages
```

## Current Surface

- `README.md` is the English project overview.
- `README-ja.md` is the Japanese project overview.
- `docs/` is the GitHub Pages source directory and also stores one Markdown file per published idea.
- `docs/index.md` renders the English public idea index and performs client-side locale routing for Japanese visitors.
- `docs/index-ja.md` renders the Japanese public idea index.
- `.github/workflows/pages.yml` builds Pages on pull requests and deploys on pushes to `main`.
- Keep the English and Japanese README files aligned when changing project intent, contribution flow, idea format, or GitHub Pages plans.
- Treat `.omc/` as local agent state unless the user explicitly asks to inspect or commit it.

## Content Conventions

- The Markdown content should be the source of truth for submitted startup ideas.
- Use one pull request per idea.
- Use `.github/pull_request_template.md` as the canonical checklist for idea PRs.
- Use one pull request per startup request, but publish the request as an English/Japanese file pair:
  - English: `docs/YYYY-MM-DD-slug.md`
  - Japanese: `docs/YYYY-MM-DD-slug-ja.md`
- Idea pages must include front matter with `idea: true`, `title`, `summary`, `date`, `tags`, `lang`, `translation_key`, and `alternate_url`.
- `translation_key` must match across the English and Japanese files.
- `alternate_url` must point to the paired detail page, including the leading slash.
- Idea submissions should follow the README sections in both languages: Summary, Problem, Why Now, First Product, Potential Users, Validation, Open Questions, Tags, and Sources.
- Prefer concrete startup wedges over broad market commentary.
- Include sources for factual claims that depend on external data.
- Do not add confidential information, private customer data, or material the contributor does not have rights to share.
- Do not add raw HTML, scripts, iframes, or embedded remote content to idea Markdown.

## Idea Submission Operator Workflow

When the user says they want to submit an idea, post an idea, create an RFS idea, or uses equivalent wording, run the full idea-submission workflow instead of only drafting text.

Treat these phrases as explicit submission intent:

- "アイデアが出た！"
- "アイデアが出た!"
- "アイデアが出た"
- "アイデアを思いついた"
- "アイデアを投稿したい"
- "アイデアをPRにしたい"
- "アイデアを出したい"
- "I have an idea"
- "I want to submit an idea"

1. Start PR-preparation interviewing using the pull request template sections:
   - Summary
   - Problem
   - Why Now
   - First Product
   - Potential Users
   - Validation
   - Open Questions
   - Tags
   - Sources
2. Ask only for missing information that materially affects the idea. Do not over-interview when a reasonable draft can be produced from context.
3. Draft the idea Markdown from the user's answers.
4. Perform a Red Team review before creating the branch:
   - Identify the weakest assumptions.
   - Name plausible competitors or existing substitutes when known.
   - Check whether the target user and first product are specific enough.
   - Surface regulatory, legal, safety, data, distribution, and trust risks where relevant.
   - Reject raw HTML, scripts, iframes, or embedded remote content in the Markdown.
   - Suggest concrete improvements to the idea text.
5. Apply the Red Team improvements, or clearly note any unresolved risks in the idea.
6. Create a new branch for the submission. The branch name must start with `idea/`, using a name like `idea/YYYY-MM-DD-slug`.
7. Add the paired idea files under `docs/YYYY-MM-DD-slug.md` and `docs/YYYY-MM-DD-slug-ja.md`.
8. Commit the change and push the branch.
9. Create a regular ready-for-review pull request using `.github/pull_request_template.md`.
10. Use the PR title format `[IDEA] {idea summary}`. If the idea-submission conversation with the user was in Japanese, write the summary in Japanese; otherwise write it in English.
11. Do not create draft pull requests for idea submissions unless the user explicitly asks for a draft PR.
12. In the PR body, include the completed template and the Red Team Review checklist.

Do not skip the Red Team review for idea submissions unless the user explicitly asks to bypass it.

## GitHub Pages Direction

Preserve Markdown idea files in `docs/` as the canonical source and render:

- a searchable idea index
- detail pages for each idea
- tag labels on idea cards

The root page is the English index, but it includes a small client-side locale redirect. Visitors with a Japanese browser locale or Asia/Tokyo timezone should land on `index-ja.html` unless they explicitly choose English.

The Pages workflow uses GitHub's Jekyll Pages action:

- Pull requests adding or updating Markdown files under `docs/**` run the Pages build.
- After that pull request is merged into `main`, the resulting push to `main` builds, uploads the Pages artifact, and deploys it.
- Repository Pages settings must use GitHub Actions as the source.

Document any new setup, development, build, and verification commands in this file and in the README when they become stable.

## Verification

- For documentation-only changes, run `git diff --check` and inspect the rendered Markdown structure mentally or with the available local tools.
- For Pages changes, run `git diff --check`; if Ruby/Jekyll tooling is available locally, also run a local Jekyll build against `docs/`.
- For future site or tooling changes, run the relevant format, lint, test, and build commands before reporting completion.
- If a command is added to package scripts or project tooling, prefer documenting the exact command here.

## Agent File Policy

- `AGENTS.md` is the canonical shared instruction file.
- `CLAUDE.md` should remain a symbolic link to `AGENTS.md`.
- Update `AGENTS.md` directly rather than replacing the `CLAUDE.md` symlink.
