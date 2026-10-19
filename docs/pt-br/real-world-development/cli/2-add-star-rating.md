---
title: "Lição 2 - Adicionar avaliações por estrelas: uma melhoria rápida"
description: "Use o Copilot CLI para alterar os cartões dos jogos, revisar a mudança no navegador encaminhado e integrá-la como seu primeiro pull request."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Agora que você instalou o Copilot CLI e iniciou uma conversa, faça sua primeira alteração no projeto. Ela será pequena: os dados dos jogos já incluem avaliações por estrelas, mas os cartões da página inicial ainda não as mostram. Você pedirá ao agente que as exiba, revisará a alteração e fará o merge do seu primeiro pull request.

Nesta lição, você vai:

- iniciar uma conversa focada do Copilot em uma branch de recurso.
- pedir ao agente uma pequena alteração no projeto.
- revisar a alteração com `/diff`.
- executar o aplicativo e confirmar a alteração em um navegador encaminhado.
- abrir e fazer merge do primeiro pull request.

## Cenário

Cada jogo no Tailspin Toys pode ter uma avaliação por estrelas, que já aparece na página de detalhes. Os cartões da página inicial mostram apenas o título, a categoria, a editora e a descrição. Como exercício inicial, peça ao agente que exiba a avaliação existente em cada cartão — uma alteração pequena e independente, ideal para sua primeira sessão.

## Anatomia de uma conversa

Uma **conversa** é o espaço em que você trabalha com o Copilot CLI em uma tarefa. Diferentemente do aplicativo Copilot, uma conversa normal da CLI usa o repositório e a branch selecionados no terminal, em vez de criar uma worktree dedicada. As conversas salvas permitem retomar a discussão mais tarde, enquanto os arquivos e a branch continuam como estado normal do Git no disco.

Em uma conversa, você verá três coisas: seus prompts e as respostas do agente, a atividade do agente enquanto ele explora e edita arquivos e as alterações que você pode inspecionar com `/diff`.

## Inicie uma conversa e solicite a alteração

Inicie uma conversa para começar a implementar o recurso.

1. Volte ao Codespace.
2. Se o terminal ainda não estiver aberto, pressione <kbd>Control</kbd>+<kbd>\`</kbd> (Mac) ou <kbd>Ctrl</kbd>+<kbd>\`</kbd> (Windows/Linux).
3. Se o Copilot ainda não estiver em execução, inicie-o com o comando a seguir:

   ```bash
   copilot --yolo
   ```

4. Inicie uma nova sessão com o comando de barra `/new` e pressione <kbd>Enter</kbd>.
5. Use este prompt para solicitar a alteração:

   ```plaintext
   Show each game's starRating out of 5 in the game cards on the list page. If the rating is null, show "No rating yet". Keep the card layout as it is, add tests, and run the relevant checks.
   ```

O Copilot explora o projeto, localiza os arquivos usados para exibir os detalhes dos jogos e cria o código necessário. Agora você adicionou um recurso com o Copilot CLI.

## Revise o diff

Revise todas as alterações geradas por inteligência artificial (IA) antes de fazer merge, mesmo as pequenas. Use o Copilot CLI para inspecionar as mudanças.

1. Digite `/diff` e inspecione cada arquivo alterado.
2. Confirme que o cartão do jogo exibe a avaliação numérica quando disponível e `No rating yet` quando `starRating` for `null`.
3. Confirme que os testes cobrem os dois casos.
4. Revise os resultados das verificações executadas pelo Copilot e peça que ele corrija as falhas.
5. Quando terminar a revisão, pressione <kbd>Esc</kbd> para sair da tela de diff.

> [!NOTE]
> Como todas as ferramentas de IA generativa, o Copilot é probabilístico, e não determinístico, portanto o código exato pode variar. Revise o comportamento em vez de esperar uma implementação específica.

## Verifique as alterações

Não basta ler o código e presumir que funciona. Peça ao Copilot que inicie o site para que você possa examinar a interface atualizada no navegador encaminhado pelo Codespaces.

1. Peça ao Copilot para iniciar o aplicativo:

   ```plaintext
   Start the app so I can inspect the star-rating change in my browser. Tell me the URL and leave the server running.
   ```

2. Quando o Codespaces indicar que a porta `4321` está disponível, selecione **Open in Browser**.
3. Confirme que os cartões dos jogos exibem as avaliações de zero a cinco.
4. Volte ao Copilot e peça que pare o servidor iniciado:

   ```plaintext
   Stop the development server you started.
   ```

## Abra e faça merge do primeiro pull request

Agora que você criou o recurso, abra um pull request (PR) para integrar o novo código ao projeto.

1. Peça ao agente padrão para fazer commit da alteração:

   ```plaintext
   Commit the reviewed star-rating changes with an appropriate commit message.
   ```

2. Digite `/pr create`. Ao criar o PR, o Copilot CLI envia o commit existente e exibe o endereço da Web (URL) do PR.
3. Abra o PR mantendo pressionada a tecla <kbd>Command</kbd> (Mac) ou <kbd>Ctrl</kbd> (Windows/Linux) e selecionando a URL exibida pelo Copilot CLI.
4. Revise os arquivos alterados e as verificações.
5. Quando estiver tudo pronto, selecione **Merge pull request** e confirme o merge.
6. Volte ao Codespace e saia do Copilot CLI com `/exit`.
7. Atualize sua `main` local:

   ```bash
   git checkout main
   git pull
   ```

## Resumo e próximos passos

Você concluiu sua primeira alteração com o GitHub Copilot CLI! Nesta lição, você:

- iniciou uma conversa focada do Copilot em uma branch de recurso.
- orientou o agente a fazer uma pequena alteração nos cartões dos jogos.
- revisou a alteração com `/diff`.
- executou o aplicativo para confirmar a avaliação por estrelas em um navegador encaminhado.
- abriu e fez merge do primeiro pull request.

Em seguida, você [começará pela issue de filtragem e usará os modos Plan e Autopilot][next-lesson] para criar um recurso maior.

## Recursos

- [Sobre o GitHub Copilot CLI][about-copilot-cli]
- [Referência de comandos do Copilot CLI][cli-reference]

[previous-lesson]: ../1-install-copilot-cli/
[next-lesson]: ../3-agent-modes/
[about-copilot-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
