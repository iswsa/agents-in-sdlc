---
title: "レッスン 5 - quality-checks スキルをカスタマイズして使う"
description: "既存の quality-checks スキルを確認し、レポート形式をカスタマイズして、フィルタリング機能を検証します。"
authors:
  - geektrainer
lastUpdated: 2026-09-29
---

コードを書くこと以外にも、開発にはさまざまな作業があります。これまで手動でコードを検証し、指示ファイルを使って規約に従うようにしました。テスト、lint、継続的インテグレーション (CI) のほかの作業には、**エージェントスキル**が適しています。スキルを使うと、Copilot にこうした作業の実行方法を伝えられます。

このレッスンでは、次のことを行います。

- 既存の `quality-checks` スキルを確認します。
- 結果の形式をカスタマイズします。
- スキルを再読み込みして実行します。

## シナリオ

Tailspin Toys では、ユニットテスト、lint、型チェックに `quality-checks` スキルを使っています。チームは結果を読みやすくするため、レポートを改善したいと考えています。

## 指示、スクリプト、リソース

エージェントスキルには、再利用可能なタスクの指示、実行可能なスクリプト、補助リソースがまとめられており、エージェントが必要に応じて読み込みます。基本的には、スキル名のフォルダーと、その中の `SKILL.md` ファイルで構成されます。Markdown ファイルには、スキルの名前と説明を定義する frontmatter、概要、スキルを呼び出すタイミングのガイダンスが含まれます。スキルのフォルダーには、スクリプトやほかのリソースを含めることもできます。

> [!NOTE]
> スキルにほかのフォルダーやファイルを含める必要はありません。Tailspin Toys の `quality-checks` スキルは、プロジェクトの既存コマンドを使うため、`SKILL.md` のみで構成されています。

スキルは、チームで共有して再利用できるようプロジェクトの `.github/skills` フォルダーに置くか、ユーザーのスキルフォルダー `~/.copilot/skills` に置きます。

## スキルを確認する

Tailspin Toys チームがユニットテスト、lint、型チェックのために作成した `quality-checks` スキルを確認します。

1. Codespace に戻ります。Codespaces エディターで `.github/skills/quality-checks/SKILL.md` を開きます。
2. ファイルの先頭にある `name` と `description` を読みます。説明は、Copilot がスキルを呼び出すタイミングの判断に役立ちます。
3. 指示を読み、テストと lint のプロセスをどう案内するか確認します。
4. まだ **Results output formatting** セクションがないことを確認します。

## 変更前にスキルを実行する

スキルは Copilot CLI から直接呼び出すことも、自然言語で依頼することもできます。まず、3 つのチェックを実行するよう Copilot に依頼します。

1. Interactive モードのフィルタリングに関する会話に戻ります。
2. 次のプロンプトを使います。

   ```plaintext
   Run the quality-checks skill for unit tests, lint, and type checks.
   ```

3. 最後に表示されるレポートを確認します。

## レポートをカスタマイズする

実行内容、成否、ツールが報告した内容を明確に示すレポートに変更します。

1. `.github/skills/quality-checks/SKILL.md` に戻ります。
2. ファイルの末尾に次のセクションを追加します。

   ```markdown
   ## Results output formatting

   Upon completion, report each command that ran and whether it passed, failed, or was blocked. Include test counts, durations, errors, warnings, and other metrics only when the tool reports them. Identify the next action for any failure or blocker, and never describe a skipped or incomplete check as passed.
   ```

3. ファイルが自動的に保存されることを確認します。

## 更新したスキルを実行する

変更したスキルを使ってレポートを確認します。Copilot CLI では、会話を再起動せずに編集済みスキルを再読み込みできます。

1. 次のコマンドを入力します。

   ```plaintext
   /skills reload
   ```

2. 先ほどと同じプロンプトを使います。

   ```plaintext
   Run the quality-checks skill for unit tests, lint, and type checks.
   ```

3. 最後に表示されるレポートを確認し、最初のレポートと比較します。

## まとめと次のステップ

このレッスンでは、既存のエージェントスキルをカスタマイズして使用しました。次のことを行いました。

- ユニットテスト、lint、型チェック用の `quality-checks` スキルを確認しました。
- 結果の形式をカスタマイズしました。
- スキルを再読み込みして実行しました。

この変更は、フィルタリング機能の PR に含まれます。次は [Playwright MCP サーバー][next-lesson]を使って、Copilot がサイトを直接操作できるようにします。

## スキルの例

次のコミュニティ例は参考資料であり、追加の作業ではありません。

- [Agent Skills の仕様][skill-spec]
- [コントリビューション ワークフロー: `make-repo-contribution`][contribution-example]
- [要件ドキュメント: `prd`][prd-example]
- [図と同梱のエクスポートスクリプト: `drawio`][drawio-example]
- [ブラウザーテスト: `webapp-testing`][browser-example]

[previous-lesson]: ../4-custom-instructions/
[next-lesson]: ../6-mcp-playwright/
[skill-spec]: https://agentskills.io/specification
[contribution-example]: https://github.com/github/awesome-copilot/tree/main/skills/make-repo-contribution
[prd-example]: https://github.com/github/awesome-copilot/tree/main/skills/prd
[drawio-example]: https://github.com/github/awesome-copilot/tree/main/skills/drawio
[browser-example]: https://github.com/github/awesome-copilot/tree/main/skills/webapp-testing
