---
title: "Lição 5 - Personalizar e usar uma skill quality-checks"
description: "Explore a skill quality-checks existente, personalize o formato do relatório e use-a para validar a filtragem."
authors:
  - geektrainer
lastUpdated: 2026-09-29
---

Desenvolver software vai além de escrever código. Você já validou manualmente o funcionamento do código e usou arquivos de instruções para garantir que ele siga os padrões da equipe. E quanto a testes, lint e outras partes da integração contínua (CI)?

As **skills de agente** são adequadas para essas tarefas. Elas ajudam o Copilot a executar operações desse tipo corretamente.

Nesta lição, você vai:

- explorar a skill `quality-checks` existente.
- personalizar o formato dos resultados.
- recarregar e executar a skill.

## Cenário

A Tailspin Toys usa a skill `quality-checks` para executar testes unitários, lint e verificações de tipos. A equipe quer melhorar o relatório para facilitar a leitura dos resultados.

## Instruções, scripts e recursos

As skills de agente reúnem instruções reutilizáveis para tarefas, scripts executáveis e recursos de apoio que o agente carrega sob demanda. No mínimo, uma skill é uma pasta com um arquivo Markdown chamado `SKILL.md`. O arquivo contém frontmatter com um nome e uma descrição, uma visão geral da tarefa e orientações sobre quando a skill deve ser usada. A pasta também pode conter subpastas com scripts e outros recursos.

> [!NOTE]
> Arquivos e pastas adicionais não são necessários. A skill `quality-checks` do Tailspin Toys contém apenas `SKILL.md` porque usa os comandos existentes do projeto.

As skills podem ficar na pasta `.github/skills` do projeto para serem compartilhadas e reutilizadas pela equipe, ou na pasta de skills do usuário `~/.copilot/skills`.

## Explore a skill

Explore a skill `quality-checks` criada pela equipe Tailspin Toys para executar testes unitários, lint e verificações de tipos.

1. Volte ao Codespace. No editor do Codespaces, abra `.github/skills/quality-checks/SKILL.md`.
2. Leia `name` e `description` no início do arquivo. A descrição ajuda o Copilot a decidir quando chamar a skill.
3. Leia as instruções e observe como elas orientam o Copilot durante os testes e a execução do lint.
4. Observe que ainda não há uma seção **Results output formatting**.

## Execute a skill antes de alterá-la

As skills podem ser chamadas diretamente pelo Copilot CLI ou por linguagem natural. Peça ao Copilot que execute as três verificações da skill.

1. Volte à conversa de filtragem no modo Interactive.
2. Use este prompt:

   ```plaintext
   Run the quality-checks skill for unit tests, lint, and type checks.
   ```

3. Observe o relatório final.

## Personalize o relatório

Melhore o relatório para que informe o que foi executado, se houve sucesso e o que as ferramentas relataram.

1. Volte a `.github/skills/quality-checks/SKILL.md`.
2. Adicione esta seção ao fim do arquivo:

   ```markdown
   ## Results output formatting

   Upon completion, report each command that ran and whether it passed, failed, or was blocked. Include test counts, durations, errors, warnings, and other metrics only when the tool reports them. Identify the next action for any failure or blocker, and never describe a skipped or incomplete check as passed.
   ```

3. O arquivo será salvo automaticamente.

## Execute a skill atualizada

O Copilot CLI pode recarregar as skills editadas sem reiniciar a conversa. Execute a skill novamente e compare os relatórios.

1. Digite:

   ```plaintext
   /skills reload
   ```

2. Use exatamente o mesmo prompt de antes:

   ```plaintext
   Run the quality-checks skill for unit tests, lint, and type checks.
   ```

3. Observe o relatório final e compare-o com o primeiro.

## Resumo e próximos passos

Nesta lição, você:

- explorou a skill `quality-checks` para testes unitários, lint e verificações de tipos.
- personalizou o formato dos resultados.
- recarregou e executou a skill.

Essa alteração acompanhará a filtragem no pull request (PR) do recurso. Em seguida, você permitirá que o Copilot interaja diretamente com o site [usando o servidor MCP do Playwright][next-lesson].

## Mais exemplos de skills

Estes exemplos da comunidade são referências, não tarefas adicionais:

- [Especificação de Agent Skills][skill-spec]
- [Fluxo de contribuição: `make-repo-contribution`][contribution-example]
- [Documentos de requisitos: `prd`][prd-example]
- [Diagramas e script de exportação: `drawio`][drawio-example]
- [Testes no navegador: `webapp-testing`][browser-example]

[previous-lesson]: ../4-custom-instructions/
[next-lesson]: ../6-mcp-playwright/
[skill-spec]: https://agentskills.io/specification
[contribution-example]: https://github.com/github/awesome-copilot/tree/main/skills/make-repo-contribution
[prd-example]: https://github.com/github/awesome-copilot/tree/main/skills/prd
[drawio-example]: https://github.com/github/awesome-copilot/tree/main/skills/drawio
[browser-example]: https://github.com/github/awesome-copilot/tree/main/skills/webapp-testing
