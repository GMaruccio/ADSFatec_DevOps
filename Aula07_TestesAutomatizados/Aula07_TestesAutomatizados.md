# Relatório — Aula 07 de DevOps

## Conteudo 

Na Aula 07 de DevOps, o conteúdo foi voltado aos **testes automatizados** e à sua importância no desenvolvimento de software. Foram abordidos conceitos relacionados à validação do funcionamento de uma aplicação, à identificação de erros e à melhoria da qualidade do código.

A aula apresentou três categorias de testes: **unitários**, que verificam partes isoladas do sistema; **testes de integração**, que avaliam se diferentes componentes funcionam corretamente em conjunto; e **testes de performance**, que analisam o comportamento da aplicação em condições de carga, considerando aspectos como tempo de resposta e quantidade de requisições suportadas.

Também foi trabalhado o conceito de **Integração Contínua (CI)**, utilizando o GitHub Actions. Com uma pipeline configurada em um arquivo YAML, é possível automatizar etapas como a instalação de dependências e a execução dos testes sempre que novas alterações são enviadas ao repositório.

## Proposta da atividade

A proposta foi desenvolver um novo projeto que reunisse os três tipos de testes automatizados — unitário, integração e performance — organizados de maneira independente. Dessa forma, cada conjunto de testes deveria possuir seu próprio comando de execução e permitir que seus resultados fossem analisados separadamente.

Além disso, a atividade solicitou a criação de uma pipeline de Integração Contínua por meio de um arquivo `.yml` no GitHub Actions. Essa pipeline deveria ser acionada automaticamente a cada `push` na branch `main`, instalar as dependências do projeto, executar os três tipos de teste e apresentar os resultados obtidos.

## Projeto desenvolvido

Para colocar os conceitos da aula em prática, desenvolvi uma aplicação simples de **gerenciamento de fichas de personagens de RPG**, baseada em um CRUD. Nela, é possível criar, visualizar, editar e excluir fichas de personagens de D&D 5e, com informações básicas como nome, classe, raça, nível e atributos.

A aplicação foi construída com **Node.js e Express**. Sua finalidade principal não era desenvolver um sistema completo de RPG, mas servir como objeto de estudo para aplicar e demonstrar os conceitos de testes automatizados e Integração Contínua.

O projeto conta com três conjuntos de testes independentes:

- **Testes unitários:** verificam funções e regras isoladas, como cálculos de modificadores, pontos de vida e operações de armazenamento.
- **Testes de integração:** verificam o funcionamento conjunto da API, das rotas e do armazenamento, incluindo as operações do CRUD.
- **Testes de performance:** simulam requisições à aplicação para avaliar métricas como latência, vazão e ocorrência de erros.

Por fim, configurei uma pipeline no **GitHub Actions** para executar automaticamente os testes a cada envio de código para a branch `main`. A pipeline instala as dependências, executa cada conjunto de testes, gera um resumo dos resultados e disponibiliza os relatórios como artefatos da execução. Assim, é possível acompanhar se as alterações realizadas mantêm o funcionamento esperado do sistema.

## Links do projeto

- **Repositório no GitHub:** https://github.com/GMaruccio/RPG-Sheet_Manager
- **Aplicação publicada no Vercel:** https://rpg-sheet-maker.vercel.app/
