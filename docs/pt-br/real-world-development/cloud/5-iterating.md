---
title: "Exercício 5 - Iterar sobre o trabalho do GitHub Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Lição anterior: Gerenciar agentes][previous-lesson] |
|:--|

## Revise o trabalho

Ao longo deste workshop, você trabalhou com o GitHub Copilot em várias tarefas para melhorar a experiência do usuário e adicionar funcionalidades. Você pediu ao Copilot que documentasse o código, criasse um recurso de jogos relacionados para a equipe de design iterar e implementasse recursos de acessibilidade, incluindo controles para alternar entre os modos de alto contraste e claro. Explore as alterações no código e, se necessário, dê feedback ao Copilot para aprimorar o trabalho.

### Cenário

Como já destacamos, os fundamentos de design de software e DevOps não mudam com a chegada da inteligência artificial (IA) generativa. Sempre queremos revisar o código gerado e seguir o processo normal de DevOps. Revise as sugestões do GitHub Copilot para a documentação, os jogos relacionados e os recursos de acessibilidade antes de habilitar a revisão para o restante da equipe.

## Segurança e agente de nuvem do GitHub Copilot

Como o agente de nuvem do Copilot executa tarefas de forma assíncrona e sem supervisão, há restrições de segurança para manter o ambiente protegido:

- O Copilot tem acesso de leitura ao repositório e acesso de gravação **somente** à branch que usará para o código.
- O agente de nuvem é executado no GitHub Actions, que cria um ambiente temporário separado para o trabalho.
- Todos os fluxos de trabalho do GitHub Actions precisam de aprovação humana antes da execução.
- [O acesso a recursos externos é limitado por padrão](https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-firewall), incluindo o acesso a servidores do Model Context Protocol (MCP).

## Revise a documentação gerada

Comece pelo primeiro pull request (PR) criado pelo agente de nuvem do GitHub Copilot: a adição de documentação ao código. Você usará a interface padrão de PR do GitHub.com.

> [!NOTE]
> Ao abrir o PR, talvez você veja um aviso de que o GitHub Copilot está bloqueado por um firewall. Isso é **esperado**, pois o acesso do Copilot a recursos externos, incluindo chamadas a servidores MCP externos, é limitado por padrão. Se quiser, você pode [personalizar ou desabilitar o firewall do agente de nuvem do Copilot][agent-firewall].

1. Volte ao repositório no github.com.
2. Selecione **Pull Requests** para abrir a lista de pull requests.
3. Abra o PR com um título semelhante a **Add missing documentation** ou outro título mais descritivo.

> [!NOTE]
> Se o Copilot ainda estiver trabalhando na tarefa, o pull request terá a indicação **[WIP]**. Nesse caso, aguarde a conclusão do trabalho. Isso pode levar alguns minutos; aproveite para fazer uma pausa ou refletir sobre o que aprendeu até aqui.

4. Quando o pull request estiver pronto, selecione a guia **Files changed** e revise as alterações.

   ![Guia Files changed](../../../_images/shared-pr-files-changed.png)

5. Explore o código atualizado, que inclui os novos comentários TSDoc e outra documentação. As alterações exatas variam.

   Procure comentários de documentação do TypeScript (TSDoc), convenções de TypeScript e cabeçalhos de comentário. Eles são resultado dos arquivos de instruções personalizados que você revisou no início do Exercício 2.

6. Depois de revisar as atualizações, volte à guia **Conversation** e role para baixo.
7. Procure um indicador de fluxos de trabalho aguardando aprovação.
8. Se algum fluxo estiver aguardando aprovação, selecione **Approve and run workflows**.

   ![Aprovar e executar fluxos de trabalho](../../../_images/shared-approve-workflows.png)

9. Os fluxos de trabalho deverão aparecer na seção de verificações do pull request. Se tudo correr bem, as verificações do projeto para o aplicativo Astro deverão ser aprovadas. Isso pode levar alguns minutos.

## Solicite alterações ao GitHub Copilot

Trabalhar com o Copilot em um pull request não é uma via de mão única. Você também pode mencioná-lo em comentários do PR ou em comentários associados a linhas de código. O Copilot verá esses comentários e iniciará outra sessão para atendê-los. Como os resultados não são determinísticos, não há um texto único que sirva para todas as solicitações. Você pode pedir, por exemplo:

- adicionar cabeçalhos de comentário no início de cada arquivo com uma breve descrição da finalidade.
- adicionar comentários TSDoc a arquivos TypeScript e Astro.
- criar um README que descreva a estrutura do aplicativo Astro.

1. Adicione um comentário pedindo uma alteração na documentação gerada e mencione **@copilot**, como faria com qualquer pessoa da equipe. Use uma das ideias acima ou outra sugestão para a documentação do código.
2. Selecione **View Session** para acompanhar o trabalho do Copilot. Observe como ele inicia uma nova sessão para fazer as atualizações.
3. Selecione **Back to pull request** para voltar ao PR.

   ![Voltar ao pull request](../../../_images/ex7-back-to-pr.png)

4. Quando o Copilot concluir as alterações, deverá aparecer um novo commit no pull request.
5. Selecione a guia **Files changed** para revisar as alterações.

Continue iterando até ficar satisfeito. Depois, você poderá marcar o PR como pronto para revisão e fazer merge na branch principal.

![Marcar o PR como pronto para revisão](../../../_images/ex7-ready-for-review.png)

## Revise o recurso de jogos relacionados

Volte ao PR criado pelo Copilot para resolver a issue sobre a exibição de jogos relacionados na página de detalhes.

1. Volte ao repositório no GitHub.com.
2. Selecione a guia **Pull Requests**.
3. Selecione o PR com um título semelhante a **Show related games on the game details page** ou outro título mais descritivo.
4. Selecione a guia **Files changed** para revisar o código gerado.
5. Depois de revisar as atualizações, volte à guia **Conversation** e role para baixo.
6. Procure um indicador de fluxos de trabalho aguardando aprovação.
7. Se algum fluxo estiver aguardando aprovação, selecione **Approve and run workflows**.

   ![Aprovar e executar fluxos de trabalho](../../../_images/shared-approve-workflows.png)

8. Os fluxos de trabalho deverão aparecer na seção de verificações do PR. Se tudo correr bem, as verificações do projeto para o aplicativo Astro deverão ser aprovadas. Isso pode levar alguns minutos.
9. **Opcional:** alterne para essa branch no Codespace para testar manualmente o recurso de jogos relacionados. Acesse o Codespace, abra o terminal e execute os comandos a seguir, substituindo `<branch-name>` pelo nome da branch criada pelo Copilot, por exemplo, `copilot/fix-8`:

   ```bash
   git fetch origin
   git checkout <branch-name>
   ```

O Copilot criou o recurso de jogos relacionados. Como antes, você pode iterar e pedir atualizações ao agente de nuvem, por exemplo, para ajustar a quantidade de jogos relacionados exibidos ou adicionar cabeçalhos de comentário e comentários TSDoc. Lembre-se de que essa tarefa foi atribuída **antes** da atualização das instruções personalizadas. Para pedir alterações, adicione um comentário na guia **Conversation**; o Copilot o verá e iniciará uma nova sessão.

## Revise os recursos de acessibilidade

Por fim, revise os recursos de acessibilidade implementados pelo agente personalizado de acessibilidade. Este PR deve incluir o modo de alto contraste atribuído no Exercício 3 e o modo claro solicitado no painel de controle no Exercício 4.

1. Volte ao repositório no GitHub.com.
2. Selecione a guia **Pull Requests**.
3. Selecione o PR com um título semelhante a **Add high contrast mode to website** ou outro título mais descritivo.

> [!NOTE]
> Se o Copilot ainda estiver trabalhando na tarefa, o pull request terá a indicação **[WIP]**. Nesse caso, aguarde a conclusão do trabalho, que pode levar alguns minutos.

4. Selecione a guia **Files changed** para revisar o código gerado.
5. Revise a implementação, prestando atenção especial a:
   - componentes de interface para alternar entre os modos.
   - uso do armazenamento local para salvar as preferências do usuário.
   - alterações de folhas de estilo em cascata (CSS) para os modos de alto contraste e claro.
   - atributos de Accessible Rich Internet Applications (ARIA), como rótulos e navegação por teclado.
   - código JavaScript/TypeScript que gerencia a alternância dos modos.
6. Depois de revisar as atualizações, volte à guia **Conversation** e role para baixo.
7. Procure um indicador de fluxos de trabalho aguardando aprovação.
8. Se algum fluxo estiver aguardando aprovação, selecione **Approve and run workflows**.

   ![Aprovar e executar fluxos de trabalho](../../../_images/shared-approve-workflows.png)

9. Os fluxos de trabalho deverão aparecer na seção de verificações do PR. Se tudo correr bem, as verificações do projeto para o aplicativo Astro deverão ser aprovadas. Isso pode levar alguns minutos.
10. **Opcional:** alterne para essa branch no Codespace para testar manualmente os recursos de acessibilidade. Acesse o Codespace, abra o terminal e execute os comandos a seguir, substituindo `<branch-name>` pelo nome da branch criada pelo Copilot:

    ```bash
    git fetch origin
    git checkout <branch-name>
    ```

    Depois, inicie o aplicativo e teste os controles dos modos de alto contraste e claro no navegador. Confirme que funcionam como esperado e que a preferência continua salva após recarregar a página.

Observe como o agente personalizado de acessibilidade ajudou o Copilot a implementar esses recursos de acordo com as práticas recomendadas de acessibilidade. Se notar problemas ou oportunidades de melhoria, mencione **@copilot** em um comentário para pedir uma atualização, como fez nos PRs anteriores.

## Exercício opcional: continue delegando

O agente de nuvem funciona melhor quando você pode delegar itens reais do backlog e se concentrar em outra atividade. Para desenvolver esse hábito, crie outras issues no repositório e atribua-as ao Copilot. Algumas ideias:

- criar um formulário de interesse de apoiadores na página de detalhes do jogo.
- implementar paginação na página de lista de jogos.
- adicionar validação de entrada e tratamento de erros aos helpers de acesso a dados.

## Resumo

Você concluiu o percurso do agente de nuvem. Ao longo destas lições, você:

- **inspecionou os arquivos de instruções personalizados do repositório** para observar mais tarde o efeito deles no resultado do agente de nuvem.
- **atribuiu issues ao agente de nuvem do Copilot** e acompanhou a configuração do ambiente, o planejamento e a execução assíncrona.
- **criou e usou um agente personalizado** para acessibilidade, adicionando modos de alto contraste e claro.
- **usou a página de agentes do Copilot como painel de controle** para monitorar e orientar a sessão de acessibilidade em andamento.
- **revisou os pull requests do agente de nuvem e iterou sobre eles**, mencionando `@copilot` para pedir alterações e aprovando fluxos de trabalho.

## Revisão e próximos passos

Você concluiu o percurso do agente de nuvem. Para continuar explorando, os outros percursos complementam o que você praticou:

- 🖥️ **[Percurso do VS Code](../../vscode/)** — explore o modo de agente do Copilot Chat e a integração com MCP diretamente no IDE.
- 💻 **[Percurso da CLI](../../cli/)** — entregue duas alterações revisadas pelo terminal usando Plan e Autopilot, skills de agente, um agente personalizado de QA, Playwright MCP, Agent Merge e uma ponte opcional `/delegate` para o agente de nuvem.

No seu próprio repositório, experimente estas ideias:

- atribuir ao agente de nuvem uma issue de refatoração ou cobertura de testes.
- criar um agente personalizado para outro domínio.
- configurar `copilot-setup-steps.yml` para outra pilha de tecnologias.

## Recursos

- [GitHub Copilot][github-copilot]
- [Sobre os agentes do Copilot][copilot-agents]
- [Atribuir issues do GitHub ao Copilot][assign-issue]
- [Práticas recomendadas para o fluxo de configuração do agente de nuvem do Copilot][cloud-agent-best-practices]
- [Configurar o firewall do agente de nuvem do Copilot][agent-firewall]

---

| [← Lição anterior: Gerenciar agentes][previous-lesson] |
|:--|

[github-copilot]: https://github.com/features/copilot
[cloud-agent-overview]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[setup-workflow]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-agent-best-practices]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[agent-firewall]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-firewall
[previous-lesson]: ../4-managing-agents/
