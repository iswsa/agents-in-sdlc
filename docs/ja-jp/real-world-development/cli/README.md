---
slug: ja-jp/real-world-development/cli
title: "GitHub Copilot CLI"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

**[GitHub Copilot CLI](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)** を使うと、ターミナルで GitHub Copilot をエージェント型コーディングアシスタントとして利用できます。コードベースを探索し、コードを生成し、コマンドを実行し、外部ツールに接続できます。すべてコマンドラインから行えるため、グラフィカルエディターに切り替えずに作業の流れを保てます。

このワークショップでは、Tailspin Toys の一連のワークフローに取り組みます。

1. GitHub Codespaces でプロジェクトを準備し、Copilot CLI をインストールして操作に慣れます。
2. 星評価に対象を絞った変更を加え、ブラウザーでレビューし、最初の pull request (PR) を手動でマージします。
3. フィルタリングの issue から始め、Plan モードでアプローチを定義し、Autopilot モードで構築した後、Interactive モードでレビューします。
4. リポジトリの指示を更新し、フィルタリング作業に適用します。
5. 既存の `quality-checks` スキルをカスタマイズし、プロジェクトのチェックに使います。
6. Playwright Model Context Protocol (MCP) サーバーを追加し、ブラウザーでフィルタリングを確認します。
7. 品質保証 (QA) カスタムエージェントを作成して使い、要件、カバレッジ、検証の証拠をレビューします。
8. フィルタリングの変更全体をレビューし、フィルタリング PR に Agent Merge を使います。
9. コンテキスト、モデル、共有、任意の cloud agent への委任に使える slash command を確認します。

ワークショップに集中できるよう、作成する PR は 2 つです。1 つ目は星評価、2 つ目は指示の更新、スキルの更新、QA プロファイル、テストを含むフィルタリング機能です。フィルタリングと品質改善のワークフローでは 1 つの会話とブランチを共有し、各ツールを学びながら前の作業を活用します。

## 演習

| 演習 | トピック | 説明 |
|----------|-------|-------------|
| [0. 前提条件][ex0] | セットアップ | リポジトリと Codespace を作成する |
| [1. Copilot CLI のインストール][ex1] | インストール | Copilot CLI をインストールして認証する |
| [2. 星評価の追加][ex2] | 最初の変更 | 既存の評価と null の場合の表示を追加し、最初の PR をマージする |
| [3. エージェントモード][ex3] | エージェントモード | issue から機能を計画し、Autopilot で構築して、Interactive モードでレビューする |
| [4. カスタム指示][ex4] | コンテキスト | 指示を追加し、Copilot CLI がどう従うかを確認する |
| [5. エージェントスキル][ex5] | スキル | 既存のスキルをカスタマイズして使う |
| [6. Playwright MCP によるテスト][ex6] | 外部ツール | Playwright MCP サーバーを追加し、ブラウザーで機能をテストする |
| [7. QA エージェント][ex7] | 要件とカバレッジ | 専門家のプロファイルを作成して選択し、最終検証の証拠を集める |
| [8. 機能 PR の作成とマージ][ex8] | レビューとマージ | 変更全体をレビューし、PR を作成して Agent Merge を使う |
| [9. CLI の便利な機能][ex9] | CLI 機能 | コンテキスト、モデル、共有、cloud agent への任意の委任を確認する |
| [10. 振り返り][ex10] | まとめ | 重要な概念と次のステップを確認する |
| [任意: Foundry を組み込む][foundry] | ホスト型エージェント | モデルを準備し、Backer Concierge を構築してデプロイし、Web サイトに接続する |

## 前提条件

このワークショップを始める前に、次のものを用意してください。

- [ ] 有効な **Copilot Student、Pro、Pro+、Business、Enterprise** のいずれかのプランが設定された GitHub アカウント
- [ ] リポジトリと Codespace を作成する権限
- [ ] ターミナルまたはコマンドライン操作の基本的な知識

> [!TIP]
> 有料プランを利用していない場合、認証済みの学生は [GitHub Education][callout-student-plan-education] を通じて GitHub Copilot を無料で利用できます。**Copilot Student** プランには、このワークショップで使うエージェント、MCP、コードレビュー、Copilot CLI の機能が含まれているため、すべてのハーネスを完了できます。

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> Copilot Business または Copilot Enterprise を使う場合は、管理者が Copilot CLI を有効にしていることを確認してください。

## はじめる

**[レッスン 0「前提条件」から始める →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-install-copilot-cli/
[ex2]: 2-add-star-rating/
[ex3]: 3-agent-modes/
[ex4]: 4-custom-instructions/
[ex5]: 5-agent-skills/
[ex6]: 6-mcp-playwright/
[ex7]: 7-qa-agent/
[ex8]: 8-create-pull-request/
[ex9]: 9-cli-power-tools/
[ex10]: 10-review/
[foundry]: 8-foundry-agent/
