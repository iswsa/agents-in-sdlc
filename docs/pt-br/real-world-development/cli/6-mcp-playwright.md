---
title: "Lição 6 - Validar a funcionalidade com Playwright MCP"
description: "Inspecione ou configure o Playwright MCP no Copilot CLI e use-o para explorar a filtragem no navegador."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Como já vimos, desenvolver software envolve mais do que escrever código. Também precisamos trabalhar com dados e serviços externos e disponibilizar automações adicionais ao Copilot. É aí que entram os servidores do Model Context Protocol (MCP): eles ampliam o Copilot CLI com ferramentas e serviços externos.

Nesta lição, você vai:

- entender como o Copilot CLI usa o MCP.
- adicionar o servidor MCP do Playwright, caso ele ainda não esteja disponível.
- pedir ao agente que controle um navegador e explore o recurso de filtragem.

## Cenário

Testes unitários e de ponta a ponta são importantes, mas validar alterações na interface também exige interagir com ela. Você permitirá que o Copilot use o site como uma pessoa usuária para automatizar a verificação das alterações e aumentar a confiança de que elas funcionam como esperado.

## O que é o Model Context Protocol (MCP)?

O [Model Context Protocol (MCP)][mcp-blog-post] permite que agentes de inteligência artificial (IA) se comuniquem com ferramentas e serviços externos em tempo real, acessem informações atuais e executem ações em seu nome.

Os agentes acessam ferramentas e recursos por meio de um servidor MCP, que funciona como uma ponte para ferramentas e serviços externos. Cada servidor MCP representa um conjunto diferente de ferramentas e recursos disponíveis ao agente.

Alguns servidores MCP conhecidos:

- **[GitHub MCP Server][github-mcp]**: dá acesso às interfaces de programação de aplicações (APIs) para gerenciar repositórios, issues e pull requests do GitHub.
- **[Playwright MCP Server][playwright-mcp-server]**: oferece recursos de automação de navegadores com o Playwright.

Há muitos outros servidores MCP disponíveis. O GitHub mantém um [registro de MCP][mcp-registry] para facilitar a descoberta e as contribuições ao ecossistema.

> [!CAUTION]
> Trate servidores MCP como qualquer outra dependência do projeto. Antes de usar um, revise o código-fonte, verifique o publicador e considere as implicações de segurança.

## Adicione o servidor MCP do Playwright

Se o servidor MCP do Playwright ainda não estiver disponível, adicione-o para que o Copilot possa interagir com o site como uma pessoa usuária.

> [!NOTE]
> Se o Playwright MCP já estiver configurado no Copilot CLI, pule estas etapas e prossiga para a próxima seção.

1. Volte ao Codespace.
2. No Copilot CLI, abra a caixa de diálogo para adicionar um servidor MCP:

   ```plaintext
   /mcp add
   ```

3. Digite `playwright` como nome e pressione <kbd>Tab</kbd>.
4. Confirme que o tipo do servidor é **STDIO** pressionando <kbd>Enter</kbd> e depois <kbd>Tab</kbd>.
5. Cole o comando a seguir na caixa de diálogo **Command**:

   ```plaintext
   npx -y @playwright/mcp@latest --headless --no-sandbox
   ```

6. Pressione <kbd>Control</kbd>+<kbd>S</kbd> (Mac) ou <kbd>Ctrl</kbd>+<kbd>S</kbd> (Windows/Linux) para salvar o servidor MCP.
7. Pressione <kbd>Esc</kbd> para sair da caixa de diálogo MCP.

## Peça ao Copilot para explorar o recurso com o Playwright

Você já confirmou manualmente que o recurso funciona. Agora peça ao Copilot que faça o mesmo usando o servidor MCP do Playwright.

1. Use este prompt para pedir ao Copilot que valide a funcionalidade com o servidor MCP do Playwright:

   ```plaintext
   Start the app and use Playwright MCP to check filtering against the issue and our plan. Tell me what works and what doesn't, without making changes. Stop the server you started when you're done.
   ```

> [!NOTE]
> Normalmente, não é necessário pedir explicitamente ao Copilot que use o servidor MCP; ele costuma identificá-lo automaticamente. Ainda assim, indicar a ferramenta pode tornar os resultados mais consistentes.

2. Observe as etapas de interação do Copilot no navegador para confirmar que a funcionalidade funciona.
3. Leia o relatório e confirme que tudo se comporta como esperado.

O Copilot iniciará o servidor, usará o Playwright para interagir com o site, encerrará o servidor e apresentará um relatório.

## Resumo e próximos passos

Nesta lição, você:

- aprendeu o que é o Model Context Protocol (MCP) e como o Copilot CLI o usa.
- adicionou o servidor MCP do Playwright, caso ele ainda não estivesse disponível.
- pediu ao agente que controlasse um navegador e explorasse o recurso de filtragem.

Em seguida, você [criará um agente personalizado de QA][next-lesson] que combinará a skill e as ferramentas do navegador em uma função especializada.

## Recursos

- [O que é MCP e por que todo mundo está falando sobre isso?][mcp-blog-post]
- [Servidor MCP do Microsoft Playwright][playwright-mcp-server]
- [Adicionar servidores MCP ao Copilot CLI][add-mcp]

[previous-lesson]: ../5-agent-skills/
[next-lesson]: ../7-qa-agent/
[mcp-blog-post]: https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/
[playwright-mcp-server]: https://github.com/microsoft/playwright-mcp
[github-mcp]: https://github.com/github/github-mcp-server
[mcp-registry]: https://github.com/mcp
[add-mcp]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers
