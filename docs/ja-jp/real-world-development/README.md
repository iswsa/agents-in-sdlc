---
slug: ja-jp/real-world-development
title: "実践的な開発"
authors:
  - geektrainer
lastUpdated: 2026-09-16
---

現実的なシナリオ、完全なアプリケーション、共有バックログを使って、ソフトウェア開発ライフサイクル全体で GitHub Copilot を活用します。変更の計画、コードの作成、動作のテスト、pull request のレビュー、エージェントを使った作業管理を反復しながら進めます。

## シナリオ

ボードゲームのクラウドファンディングを提供する架空の会社 Tailspin Toys に、新しい開発者として参加します。チームのバックログは GitHub issue として登録済みで、すぐに取り組めます。フィルターやページネーションなどの機能に加えて、アクセシビリティやコーディング規約などの品質改善も含まれています。

## 環境を選択する

GitHub Copilot は、開発者が作業する環境で利用できます。開発方法に合った環境を選択してください。各ワークショップには個別のセットアップがあり、共通の Tailspin Toys シナリオを使います。

### [GitHub Copilot CLI][cli]

ターミナルでエージェント型アシスタントを使います。Plan モードと Autopilot モード、指示、スキル、カスタムエージェント、Playwright MCP、Agent Merge、実用的な slash command を活用します。

### [GitHub Copilot app][app]

デスクトップアプリでエージェントセッションを並行して実行し、セッションモードを切り替え、キャンバスを共同編集し、GitHub issue と pull request を管理します。

### [GitHub Copilot cloud agent][cloud]

GitHub issue を非同期エージェントに割り当て、作業を案内し、進行状況を監視して、作成された pull request をレビューします。

### [Visual Studio Code][vscode]

Visual Studio Code と GitHub Codespaces で GitHub Copilot を使います。エディターを離れずに、Copilot Chat のエージェントモード、MCP サーバー、カスタムエージェントを活用します。

[cli]: cli/
[app]: app/
[cloud]: cloud/
[vscode]: vscode/
