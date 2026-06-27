<h1 align="center">
  <img src="docs/icon.png" alt="Requests for Startups icon" width="128">
  <br>
  Requests for Startups
</h1>

<p align="center">
  <a href="README.md">English</a> |
  <a href="README-ja.md">日本語</a>
</p>

スタートアップのアイデアを pull request で集めるためのシンプルなリポジトリです。

アイデアは `docs/` 配下に 1 件 1 Markdown ファイルとして保存します。pull request が `main` にマージされると、GitHub Actions が GitHub Pages をビルドし、公開アイデア一覧を更新します。

## 流れ

1. 1 アイデアにつき 1 つの Markdown ファイルを作る。
2. pull request を作成する。
3. アイデアとリスクをレビューする。
4. `main` にマージする。
5. GitHub Pages の公開一覧が更新される。

## アイデアファイル

`docs/YYYY-MM-DD-slug.md` のようなファイルを作成します。

```markdown
---
idea: true
title: "Idea Title"
summary: "アイデアの短い説明。"
date: YYYY-MM-DD
tags: [ai, devtools]
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

## 構成

```text
docs/
  index.md              # 公開アイデア一覧
  YYYY-MM-DD-slug.md    # 1 idea につき 1 ファイル
.github/
  pull_request_template.md
  workflows/pages.yml
AGENTS.md
CLAUDE.md -> AGENTS.md
```

## メモ

- pull request は 1 idea につき 1 本にする。
- pull request template の Red Team Review checklist も埋める。
- 事実に依存する主張には、必要に応じて source を付ける。
- 機密情報や顧客の private data は含めない。
- raw HTML、script、iframe、外部埋め込みコンテンツは含めない。
- リポジトリの Pages 設定では、source を **GitHub Actions** にする。
