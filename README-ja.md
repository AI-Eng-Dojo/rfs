<h1 align="center">
  <img src="docs/icon.png" alt="Requests for Startups icon" width="128">
  <br>
  Requests for Startups
</h1>

<p align="center">
  <a href="README.md">English</a> |
  <a href="README-ja.md">日本語</a>
</p>

Requests for Startups は、スタートアップの機会になり得るアイデアを集める公開アイデアボードです。Y Combinator の [Requests for Startups](https://www.ycombinator.com/rfs) のように、「創業者に取り組んでほしい問題や市場」を共有する形式を参考にしています。

このリポジトリは、次のような軽量な公開フローを想定します。

1. コントリビューターが startup idea を pull request で投稿する。
2. GitHub 上でレビューし、問題設定や説明を磨く。
3. マージされた idea を GitHub Pages の元データにする。
4. 公開サイトで idea list、カテゴリ、要約、詳しい解説を表示する。

このプロジェクトは独立した非公式プロジェクトであり、Y Combinator との提携・公認・スポンサー関係はありません。

## 目的

目的は、有望な startup prompt を、長く参照できる一覧として残すことです。よい request は、創業者が市場調査、ユーザーインタビュー、初期プロトタイプに進むべきかを判断しやすくします。

各 idea では、次の問いに答えます。

- どんな痛みや緊急度の高い問題があるか。
- なぜ今なら解ける可能性が高いのか。
- 誰がその問題を強く感じ、新しいプロダクトを試す可能性があるのか。
- スタートアップが最初に何を作れるのか。
- どんな初期シグナルがあれば検証が進んだと言えるのか。
- どんなリスク、制約、未解決の問いが残っているのか。

## Idea の流れ

```text
Pull request -> review -> merge -> GitHub Pages build -> public idea page
```

このリポジトリでは `docs/` 配下の Markdown ファイルを source of truth とします。`main` にマージされると、GitHub Actions が Jekyll でビルドし、GitHub Pages に公開します。公開サイトでは次の内容を表示します。

- 全 idea の一覧
- 各 request の詳細ページ
- タグとカテゴリ
- 一覧で読みやすい短い要約
- 背景を理解するための詳しい解説
- 必要に応じた contributor や source の attribution

## 想定リポジトリ構成

```text
rfs/
├── README.md                       # 英語版概要
├── README-ja.md                    # 日本語版概要
├── AGENTS.md                       # 共有 agent workflow
├── CLAUDE.md -> AGENTS.md          # Claude 互換 symlink
├── .github/
│   ├── pull_request_template.md
│   └── workflows/pages.yml         # GitHub Pages の build / deploy
└── docs/
    ├── index.md                    # 公開される idea index
    ├── icon.png                    # site / README の icon
    └── YYYY-MM-DD-slug.md          # 1 idea につき 1 ファイル
```

最初の版は意図的にシンプルにします。コントリビューターは `docs/` 配下に 1 idea につき 1 Markdown ファイルを追加し、GitHub Pages が公開用の一覧・詳細ページを生成します。

## Idea フォーマット

pull request は 1 idea につき 1 本にします。投稿する idea には、次のセクションを含めます。

```markdown
---
idea: true
title: "Idea Title"
summary: "スタートアップ機会の短い説明。"
date: YYYY-MM-DD
tags: [ai, healthcare, devtools]
---

# Idea Title

## Summary

スタートアップ機会の短い説明。

## Problem

誰がその問題を抱えているか、今どのように発生しているか、既存手段ではなぜ不十分か。

## Why Now

最近何が変わったか。技術、規制、コスト、ユーザー行動、流通、市場構造など。

## First Product

この機会を検証するために、スタートアップが最初に作れる最小のプロダクトまたはサービス。

## Potential Users

最初にインタビューすべきユーザーまたは買い手。

## Validation

この idea の確度を上げる検証シグナル。

## Open Questions

未知の点、リスク、制約、失敗し得る理由。

## Tags

ai, healthcare, devtools, climate, robotics, fintech, enterprise など。
```

## 投稿ガイドライン

- 抽象的なトレンドではなく、具体的な startup idea を投稿する。
- ユーザー、痛み、タイミングを説明する。
- 大きすぎる市場説明より、最初に入る wedge を明確にする。
- 外部事実に依存する主張には source を添える。
- 機密情報、顧客の private data、共有権限のない素材は含めない。
- 1 pull request では 1 idea だけを扱う。
- idea は `docs/YYYY-MM-DD-slug.md` として保存し、front matter に `idea: true` を付ける。
- 採用は「公開する価値がある」という意味であり、maintainer が市場性を保証したり idea を推奨したりするものではありません。

## 編集方針

Request は野心的でありつつ、実行可能であるべきです。強い投稿には、たいてい次の要素があります。

- 高頻度または高コストな問題を持つ明確なユーザー
- その idea が今あらためて可能になった理由
- 小さなチームでも作れる first product
- 狭い wedge から大きな会社へ広がる道筋
- 読者が自分で判断できるだけの説明

GitHub Pages の公開サイトでは、まず一覧で見つけやすく、次に詳細を読み込みやすい構成にします。

## GitHub Pages

Pages サイトでは、次のページを提供します。

- `/` - 検索可能な idea index
- `/<slug>/` - 各 idea の詳細ページ
- AI、infrastructure、healthcare、enterprise、hardware、climate などの tag label
- 新着 request を追うための RSS または JSON を将来的に追加可能
- 各 idea を追加した pull request へのリンクを将来的に追加可能

`.github/workflows/pages.yml` は、`docs/**` を触る pull request で Pages build を確認し、`main` へのマージ後に deploy します。リポジトリの Pages 設定では、source を **GitHub Actions** にする必要があります。

## 参考

- Y Combinator Requests for Startups: <https://www.ycombinator.com/rfs>
- 参照確認日: 2026-06-27
