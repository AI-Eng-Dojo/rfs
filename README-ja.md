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

アイデアは 1 件 1 pull request で投稿し、`docs/` 配下に英語版と日本語版の Markdown ペアとして保存します。pull request が `main` にマージされると、GitHub Actions が GitHub Pages をビルドし、公開アイデア一覧を更新します。

## 流れ

1. 1 アイデアにつき英語版と日本語版の Markdown ファイルを作る。
2. pull request を作成する。
3. アイデアとリスクをレビューする。
4. `main` にマージする。
5. GitHub Pages の公開一覧が更新される。

## アイデアファイル

`docs/YYYY-MM-DD-slug.md` と `docs/YYYY-MM-DD-slug-ja.md` のようなファイルペアを作成します。

英語ファイル:

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
credit_name: "Contributor Name"
credit_url: "https://github.com/contributor"
source_pr: 123
votes: 0
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

日本語ファイル:

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
credit_name: "Contributor Name"
credit_url: "https://github.com/contributor"
source_pr: 123
votes: 0
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

## 構成

```text
docs/
  index.md                 # 英語の公開アイデア一覧
  index-ja.md              # 日本語の公開アイデア一覧
  YYYY-MM-DD-slug.md       # 英語のアイデアファイル
  YYYY-MM-DD-slug-ja.md    # 対応する日本語のアイデアファイル
.github/
  pull_request_template.md
  workflows/pages.yml
AGENTS.md
CLAUDE.md -> AGENTS.md
```

## メモ

- pull request は 1 idea につき 1 本にする。
- アイデア公開時は英語版と日本語版の docs を両方追加し、`alternate_url` で相互リンクする。
- 英語版と日本語版の `translation_key` は同じ値にする。
- `credit_name`, `credit_url`, `source_pr`, `votes` を追加し、サイト上で発想主と投票の初期値を表示できるようにする。PR番号が発行されるまでは `source_pr: pending` を使い、完了前に番号へ差し替える。
- 現在の投票UIは静的サイト向けで、`localStorage` により 1 アイデアにつき 1 ブラウザ 1 日 1 回まで投票でき、件数は端末内の値として表示する。
- pull request template の Red Team Review checklist も埋める。
- 事実に依存する主張には、必要に応じて source を付ける。
- 機密情報や顧客の private data は含めない。
- raw HTML、script、iframe、外部埋め込みコンテンツは含めない。
- リポジトリの Pages 設定では、source を **GitHub Actions** にする。
- Pages のルートURLは、ブラウザ言語またはタイムゾーンから日本語利用者と判断した場合に `index-ja.html` を表示する。言語切り替えから英語も選択できる。
