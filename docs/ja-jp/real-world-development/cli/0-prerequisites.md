---
title: "レッスン 0 - 前提条件"
description: "Tailspin Toys のコピーを作成し、Copilot CLI ワークショップ用の GitHub Codespace を準備します。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Copilot CLI のレッスンを始める前に、必要な準備を整えます。Tailspin Toys リポジトリの自分用コピーを作成し、次のレッスンで統合ターミナルから Copilot CLI をインストールして実行するための [Codespace][codespaces] を立ち上げます。

このレッスンでは、次のことを行います。

- テンプレートから Tailspin Toys プロジェクトのコピーを作成します。
- Codespace を作成し、プロジェクトの準備ができたことを確認します。

## ラボ用リポジトリを設定する

ワークショップでは、Tailspin Toys プロジェクトの自分用コピーを使います。[テンプレートリポジトリ][tailspin-template]から作成してください。新しいリポジトリにはラボに必要なすべてのファイルが含まれています。

1. 新しいブラウザー ウィンドウで [Tailspin Toys テンプレート][tailspin-template]に移動します。
2. **Use this template** を選択し、次に **Create a new repository** を選択して、自分用のコピーを作成します。
3. GitHub または Microsoft が主催するイベントに参加している場合は、メンターの指示に従ってください。それ以外の場合は、GitHub Copilot にアクセスできる organization に新しいリポジトリを作成します。
4. 作成したリポジトリのパス（`organization-or-user-name/repository-name`）を控えておきます。ワークショップで後から参照します。

> [!NOTE]
> テンプレートからリポジトリを作成すると、GitHub issue のバックログが自動的に作成されます。ワークショップ全体でこれらの issue を使うため、自分で作成する必要はありません。

新しいワークショップテンプレートのコピーを使ってください。テンプレートにはリポジトリの指示、アプリケーションコード、テスト、`quality-checks` スキル、バックログが含まれます。古いコピーを使う場合は、必要なファイルがそろっていることをファシリテーターに確認してください。

## Codespace を作成する

[Codespace][codespaces] を使ってワークショップを進めます。GitHub Codespaces は、ブラウザーでコードを作成、実行、デバッグできるクラウド開発環境です。複数のプログラミング言語、拡張機能、ツールに対応するエディターを備えています。

1. 作成したリポジトリに移動します。
2. **Code** を選択します。
3. **Codespaces** タブを選択し、**Create codespace on main** を選択します。
4. Codespace のセットアップが完了するまで待ちます。テンプレートによって、プロジェクトの依存関係、Playwright Chromium、ローカルデータベースがインストールされます。
5. **Do you trust the authors of the files in this folder?** と表示された場合は、**Trust Folder & Continue** を選択します。
6. リポジトリのルートでターミナルを開き、アプリケーションを起動します。

   ```bash
   npm run dev
   ```

7. Codespaces でポート `4321` が使用可能になったら、**Open in Browser** を選択し、Tailspin Toys サイトが表示されることを確認します。
8. ターミナルに戻り、<kbd>Ctrl</kbd>+<kbd>C</kbd> で開発サーバーを停止します。

## まとめと次のステップ

このレッスンでは、次のことを行いました。

- テンプレートから Tailspin Toys プロジェクトのコピーを作成しました。
- Codespace を作成し、プロジェクトの準備ができたことを確認しました。

次は、Codespace に [GitHub Copilot CLI をインストール][next-lesson]し、GitHub アカウントで認証します。

## リソース

- [GitHub Codespaces の概要][codespaces]
- [テンプレートからリポジトリを作成する][template-repository]
- [Codespaces クイックスタート][codespaces-quickstart]

[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[next-lesson]: ../1-install-copilot-cli/
[codespaces]: https://github.com/features/codespaces
