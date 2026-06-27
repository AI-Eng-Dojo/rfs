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
- `docs/index.md` renders the public idea index.
- `.github/workflows/pages.yml` builds Pages on pull requests and deploys on pushes to `main`.
- Keep the English and Japanese README files aligned when changing project intent, contribution flow, idea format, or GitHub Pages plans.
- Treat `.omc/` as local agent state unless the user explicitly asks to inspect or commit it.

## Content Conventions

- The Markdown content should be the source of truth for submitted startup ideas.
- Use one pull request per idea.
- Use `.github/pull_request_template.md` as the canonical checklist for idea PRs.
- Use one file per startup request under `docs/`, preferably named `YYYY-MM-DD-slug.md`.
- Idea pages must include front matter with `idea: true`, `title`, `summary`, `date`, and `tags`.
- Idea submissions should follow the README sections: Summary, Problem, Why Now, First Product, Potential Users, Validation, Open Questions, and Tags.
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
6. Create a new branch for the submission, using a name like `idea/YYYY-MM-DD-slug`.
7. Add the idea file under `docs/YYYY-MM-DD-slug.md`.
8. Commit the change, push the branch, and create a pull request using `.github/pull_request_template.md`.
9. In the PR body, include the completed template and the Red Team Review checklist.

Do not skip the Red Team review for idea submissions unless the user explicitly asks to bypass it.

## GitHub Pages Direction

Preserve Markdown idea files in `docs/` as the canonical source and render:

- a searchable idea index
- detail pages for each idea
- tag labels on idea cards

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
