---
title: "Lição 4 - Orientar o Copilot com instruções personalizadas"
description: "Explore as instruções do repositório, adicione um padrão de documentação e aplique-o ao código de filtragem."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

O contexto é essencial ao trabalhar com inteligência artificial (IA) generativa. Se uma tarefa precisa ser feita de uma maneira específica, forneça essa orientação ao Copilot. Os [arquivos de instruções][instruction-files] descrevem não apenas o código que você quer, mas também como ele deve ser estruturado. Agora que você implementou a filtragem, explore as instruções usadas pelo Copilot, adicione um padrão de documentação e aplique-o ao código.

Nesta lição, você vai:

- explorar como as instruções do repositório e os arquivos de instruções associados a caminhos chegam ao agente.
- atualizar o arquivo de instruções para garantir que os padrões de código sejam seguidos.
- observar o impacto dos arquivos de instruções no código.

## Cenário

Como toda boa equipe de desenvolvimento, a Tailspin Toys tem diretrizes e requisitos para as práticas de desenvolvimento. Entre eles:

- Os comentários devem explicar a intenção e as decisões não óbvias, em vez de repetir o código.
- Funções exportadas em `db/` e `src/lib/` devem documentar sua finalidade, parâmetros e valores de retorno com comentários TypeScript Documentation (TSDoc)/JavaScript Documentation (JSDoc), incluindo um argumento `db` injetável quando existir.
- Componentes Astro reutilizáveis devem documentar seus contratos `Props`, e os comentários devem continuar atualizados quando o código relacionado mudar.
- As orientações existentes de formatação e lint devem ser preservadas.

Com os arquivos de instruções, você fornecerá ao Copilot as informações necessárias para seguir essas práticas.

## Arquivos de instruções

As instruções personalizadas dão contexto e preferências ao Copilot para que ele compreenda melhor o estilo e os requisitos de código. Você pode especificar convenções de programação, bibliotecas e até os tipos de comentários desejados. É possível criar instruções para todo o repositório ou para tipos específicos de arquivo e tarefas.

Há dois tipos de arquivos de instruções:

- `.github/copilot-instructions.md`, um único arquivo enviado ao Copilot em todas as solicitações relacionadas ao repositório. Ele deve conter informações do projeto relevantes para a maioria das solicitações.
- `.github/instructions/*.instructions.md`, arquivos com diretrizes para linguagens, tipos de arquivo ou tarefas específicas.

> [!NOTE]
> O suporte a outros formatos de instrução varia conforme o ambiente. Consulte a [referência de suporte a instruções personalizadas][custom-instructions-support] antes de depender de um formato específico.

## Explore os arquivos de instruções personalizadas do projeto

O projeto inicial já inclui alguns arquivos de instruções. Explore-os antes de fazer alterações para observar o efeito que eles têm.

1. Volte ao Codespace.
2. No editor do Codespaces, e não no terminal, abra `.github/copilot-instructions.md`.
3. Explore o arquivo e observe a breve descrição do projeto e as orientações de código. Essas instruções se aplicam a todas as interações com o Copilot neste repositório.
4. Abra a pasta `.github/instructions` e explore os arquivos. Há instruções para arquivos Astro, a camada de dados Drizzle, testes e outros itens.
5. Abra `.github/instructions/unit-tests.instructions.md`. Observe o campo `applyTo` no início do arquivo, que define um glob para determinar a quais arquivos as instruções se aplicam.
6. Abra `.github/instructions/drizzle.instructions.md` e observe os links para outros arquivos de instruções e arquivos existentes do projeto. Assim, conjuntos maiores de instruções podem ser divididos em arquivos menores e reutilizáveis, com referências a exemplos.

## Atualize os arquivos de instruções para refletir as diretrizes da equipe

Os arquivos atuais são um bom começo, mas falta uma orientação. Adicione um padrão para que o Copilot gere comentários TypeScript Documentation (TSDoc) em TypeScript.

1. Em `.github/copilot-instructions.md`, localize a seção **Code formatting guidance**, que deve estar perto da linha 35.
2. Adicione o item a seguir no fim da lista:

   ```markdown
   - All new TypeScript should contain TSDocs comments for documentation purposes.
   ```

O arquivo será salvo automaticamente.

## Use a orientação atualizada

O Copilot CLI carrega as instruções do repositório quando uma conversa é iniciada. Depois de salvar as instruções, retome a conversa de filtragem para que o Copilot use a nova orientação sem perder o contexto do recurso.

1. Se a conversa de filtragem ainda estiver aberta, digite `/exit` para fechá-la. O Copilot CLI salva as conversas automaticamente.
2. Na raiz do repositório, na branch `game-filters-cli`, retome a conversa salva:

   ```bash
   copilot --resume
   ```

   Se solicitado, selecione a conversa de filtragem e confirme que a branch selecionada é `game-filters-cli`.
3. Peça ao Copilot que aplique a orientação atualizada:

   ```plaintext
   We just updated our instructions and code guidance. Can you please update the code you generated to match that guidance?
   ```

4. Digite `/diff` e revise os arquivos TypeScript alterados. Observe os novos comentários TSDoc e confirme que explicam o código corretamente.

## Resumo e próximos passos

Nesta lição, você:

- explorou como as instruções do repositório e os arquivos de instruções associados a caminhos chegam ao agente.
- atualizou o arquivo de instruções para garantir que os padrões de código sejam seguidos.
- observou o impacto dos arquivos de instruções no código.

Em seguida, você [personalizará e executará a skill reutilizável `quality-checks`][next-lesson] para garantir a execução consistente de lint e testes.

## Recursos

- [Adicionar instruções personalizadas ao Copilot CLI][instruction-files]
- [Suporte a instruções personalizadas][custom-instructions-support]
- [Práticas recomendadas para criar instruções personalizadas][instructions-best-practices]
- [Awesome Copilot — coleção de arquivos de instruções e outros recursos][awesome-copilot]

[instruction-files]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions
[instructions-best-practices]: https://docs.github.com/copilot/concepts/prompting/response-customization#writing-effective-custom-instructions
[awesome-copilot]: https://awesome-copilot.github.com/
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support
[previous-lesson]: ../3-agent-modes/
[next-lesson]: ../5-agent-skills/
