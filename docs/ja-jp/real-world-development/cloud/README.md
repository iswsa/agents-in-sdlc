---
slug: ja-jp/real-world-development/cloud
title: "GitHub Copilot cloud agent"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

**[GitHub Copilot cloud agent](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent)** を使うと、GitHub Copilot にクラウドで非同期に作業させることができます。GitHub で作業を割り当てると、cloud agent はバックグラウンドでリポジトリを調べ、変更を加えて pull request を作成します。その間、開発者は別の作業を続けられます。

各演習では、まず cloud agent が従うカスタム指示を追加し、GitHub issue を割り当てて実装を依頼します。カスタムエージェントを確認して利用し、エージェントのダッシュボードからセッションを監視して案内した後、作成された pull request をレビューし、結果を反復して改善します。

## 演習

| 演習 | トピック | 説明 |
|----------|-------|-------------|
| [0. 前提条件][ex0] | セットアップ | リポジトリと Codespace を作成する |
| [1. カスタム指示][ex1] | コンテキスト | cloud agent が従うカスタム指示を追加する |
| [2. Cloud agent][ex2] | 非同期エージェント | GitHub issue を Copilot cloud agent に割り当てる |
| [3. カスタムエージェント][ex3] | 専門エージェント | カスタムエージェントを確認して使用する |
| [4. エージェントの管理][ex4] | 監視 | エージェントセッションを監視して案内する |
| [5. 反復して改善する][ex5] | レビュー | PR をレビューし、Copilot の作業を反復して改善し、次のステップを選ぶ |

## 前提条件

このワークショップを始める前に、次のものを用意してください。

- [ ] 有効な **Copilot Student、Pro、Pro+、Business、Enterprise** のいずれかのプランが設定された GitHub アカウント
- [ ] アカウントまたは organization で有効になっている Copilot cloud agent

> [!TIP]
> 有料プランを利用していない場合、認証済みの学生は [GitHub Education][callout-student-plan-education] を通じて GitHub Copilot を無料で利用できます。**Copilot Student** プランには、このワークショップで使うエージェント、MCP、コードレビュー、Copilot CLI の機能が含まれています。

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> Cloud agent は Copilot Free を除く **Copilot Student、Pro、Pro+、Business、Enterprise** で利用できます。Copilot Business または Enterprise では、管理者が organization に対して有効にする必要があります。

> [!NOTE]
> このハーネスでは MCP を扱いません。Copilot で MCP サーバーを使う方法については、[CLI ハーネス][cli]または [VS Code ハーネス][vscode]を参照してください。

## はじめる

**[演習 0「前提条件」から始める →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/
[cli]: ../cli/
[vscode]: ../vscode/
