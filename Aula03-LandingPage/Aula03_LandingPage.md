# Relatório de Configuração, Customização e Deploy de Landing Page
**Aluno:** Giovanni Camargo Maruccio
**Curso:**  Análise e Desenvolvimento de Sistemas
**Instituição:** FATEC Sorocaba

## 1. Objetivo 
Este documento detalha o processo de clonagem derepositório, configuração de ambiente local, customização de interface, controle de versão e deploy contínuo de uma Landing Page baseada em um template React.

* **Repositório (GitHub):** [https://github.com/GMaruccio/Aula03LandingPage]

* **Repositório Original:** [https://github.com/dunky11/react-saas-template]

* **Projeto em Produção (Vercel):** [https://aula03-landing-page.vercel.app/]

## 2. Preparação do Ambiente Local e Resolução de Conflitos
A atividade foi iniciada a partir da clonagem de um repositório existente. A instalação das dependências foi realizada via terminal utilizando o Node.js.

Comando executado: ``npm install``

Resolução de Conflitos:
Durante a inicialização do servidor local (npm start), foi identificado um erro de compatibilidade de dependências (Error: No such module: http_parser). O erro ocorreu porque a versão do react-scripts utilizada no template legava funções incompatíveis com a versão atual do Node.js (v24.19.0) instalada no ambiente de desenvolvimento. O problema foi resolvido alinhando a versão do ambiente de execução (Node.js) com os requisitos do projeto.

Comando executado: ``npm install react-scripts@latest``

## 3. Customização da Interface
 A principal alteração realizada focou na identidade visual da aplicação.

Alteração efetuada: A paleta de cores original, que utilizava tons de vermelho e roxo como cores primárias e secundárias, foi refatorada. As variáveis de estilo foram reescritas para implementar uma nova identidade baseada em um novo tom de vermelho combinado com azul.

## 4. Controle de Versão e Gestão de Repositório
Como o projeto foi originado de um clone, o diretório continha todo o histórico de commits dos desenvolvedores anteriores (arquitetura legada de 2022). Para fins de organização acadêmica e autoria, o histórico foi resetado para a criação de uma nova linhagem de versionamento limpa.

Os comandos executados no PowerShell foram:

``Remove-Item -Recurse -Force .git`` (Exclusão da árvore de versionamento antiga).

``git init`` (Inicialização de um repositório limpo, sem histórico de commits antigos).

``git add . ``

``git commit ``

``git branch -M main e git remote add origin https://github.com/GMaruccio/Aula03LandingPage`` (Definição da branch principal e vínculo com o repositório remoto).

``git push -u origin main .``

## 5. Deploy Contínuo (CI/CD) na Vercel
A etapa final consistiu em colocar a aplicação em ambiente de produção através da plataforma Vercel, integrada diretamente ao repositório do GitHub.

Para evitar que o erro de build (http_parser) ocorrido no ambiente local se repetisse nos servidores da Vercel, foi necessário realizar um ajuste prévio nas configurações de infraestrutura do deploy:

Em Settings > General, a versão do Node.js foi fixada em 18.x para garantir total compatibilidade com os scripts de build do projeto.

Após essa configuração, o processo de Build e Deployment ocorreu com sucesso.
