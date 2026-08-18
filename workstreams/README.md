# Workstreams

`workstreams/` は、公開済みのRFSアイデアをグリル、調査、具体化するときの
作業状態を、セッションや担当者をまたいで引き継ぐための場所です。

GitHub Pagesの公開原稿は引き続き `docs/` を正本とします。ここにある文書は
検討中の作業資料であり、確定済みの公開アイデア本文ではありません。

## 公開範囲

このリポジトリが公開されている場合、`docs/` の外に置いたファイルもGitHub上では
公開されます。個人のアセスメント回答、顧客情報、未公開の事業情報、機密情報は
保存しないでください。非公開情報が必要になった時点でprivateリポジトリへ移します。

## 推奨構成

```text
workstreams/
  YYYY-MM-DD-slug/
    README.md
    product-brief.md
    decision-log.md
    open-questions.md
    session-notes/
      README.md
      _template.md
```

## 文書の役割

- `README.md`: 現在地、同期状況、次に聞く質問、再開手順
- `product-brief.md`: 現時点のプロダクト仮説を統合したスナップショット
- `decision-log.md`: 採用した判断、理由、却下案、再検討条件
- `open-questions.md`: 未解決事項、必要な証拠、担当、次のアクション
- `session-notes/`: 各セッションの要約とチェックポイント

文書が食い違う場合、採用済みの判断は `decision-log.md`、現在の統合案は
`product-brief.md`、未解決事項は `open-questions.md` を優先します。セッションノートは
経緯を残す資料であり、それだけで採用済みの判断にはなりません。

## セッションの進め方

開始時:

1. workstreamの `README.md` を読む。
2. `decision-log.md` と `open-questions.md` を確認する。
3. 前回のセッションノートにある「次に聞く質問」から再開する。

チェックポイントまたは終了時:

1. `session-notes/_template.md` を複製し、セッションの要約を保存する。
2. 採用された判断だけを `decision-log.md` に反映する。
3. 現在の統合案を `product-brief.md` に反映する。
4. 解決済み・追加された問いを `open-questions.md` に反映する。
5. workstreamの `README.md` に現在地と「次に聞く質問」を一文で記録する。

## ハンドオフ可能の条件

- 現在のチェックポイントが書かれている。
- 最後に扱った問いと、次に聞く質問が明記されている。
- 採用済みの判断と暫定案が区別されている。
- 未解決事項に必要な証拠または次のアクションがある。
- 機密情報やprivate dataが除かれている。
- 別環境へ渡す場合は、対象コミットがremoteへpushされている。
