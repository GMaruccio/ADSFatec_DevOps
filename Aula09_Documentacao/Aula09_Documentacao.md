# Relatório — Aula 09 de DevOps

## 1. Como foi a aula

Na Aula 09 de DevOps, o foco foi a **documentação de projetos de software**. Foi trabalhada a importância de registrar de forma clara o propósito de uma aplicação, o problema que ela busca resolver, seu escopo, seus requisitos e os detalhes técnicos necessários para compreender e executar o sistema.

A documentação também deve apresentar as tecnologias utilizadas, a arquitetura da aplicação e a organização de seus principais componentes. Outro ponto importante é manter um arquivo `README.md` atualizado no repositório, com informações práticas para que outras pessoas consigam instalar, configurar, executar e testar o projeto.

## 2. Proposta de atividade

A atividade solicitada consistiu em escolher um projeto de software e elaborar sua documentação. O documento deveria apresentar:

- **Objetivo e problema:** explicar a finalidade do sistema e qual necessidade ele pretende atender.
- **Escopo:** delimitar o que faz parte do projeto e o que não está contemplado.
- **Requisitos:** descrever os principais requisitos funcionais e não funcionais.
- **Tecnologias e arquitetura:** apresentar as ferramentas utilizadas, a arquitetura da aplicação e a função de seus principais componentes.
- **Instruções de uso:** documentar os pré-requisitos e os procedimentos de instalação, configuração e execução.
- **Informações técnicas adicionais:** quando aplicável, explicar as APIs, o banco de dados, as variáveis de configuração, os testes e o processo de deploy.

Por fim, foi solicitado criar ou atualizar o `README.md` do repositório no GitHub, reunindo essas informações em um único lugar.

Link do Repositório: https://github.com/GMaruccio/Controle-De-Presenca

## 3. Projeto documentado

Para realizar a atividade, utilizei o projeto **Controle de Presença — ESP32 + Node-RED + MySQL**. O sistema tem como objetivo automatizar o registro de presença dos alunos em sala de aula. Em vez de realizar a chamada manualmente, o aluno informa seu RA em um teclado matricial conectado a um ESP32. O dispositivo envia essa informação por uma requisição HTTP para o Node-RED, que verifica se o aluno está cadastrado no banco de dados MySQL e registra sua presença.

Depois do registro, as informações são disponibilizadas em um dashboard web, permitindo que o professor acompanhe os dados da turma. O painel apresenta indicadores como total de matriculados, presentes e ausentes, última entrada, percentual de presença e lista dos alunos que registraram presença no dia. A atualização ocorre automaticamente a cada cinco segundos.

### 3.1 Tecnologias utilizadas

O projeto integra diferentes tecnologias, cada uma responsável por uma parte do funcionamento:

- **ESP32:** microcontrolador responsável por receber os dados digitados e realizar a comunicação Wi-Fi.
- **Teclado matricial 4x4:** utilizado pelo aluno para informar o RA.
- **C++ com Arduino framework:** linguagem e framework utilizados no firmware do ESP32.
- **PlatformIO:** ferramenta utilizada para configurar e compilar o firmware.
- **Wokwi:** simulador utilizado para representar o circuito e testar o funcionamento do dispositivo.
- **Node-RED:** responsável pela API HTTP, pelas regras de validação e pela integração com o banco de dados.
- **MySQL:** banco de dados utilizado para armazenar os alunos e os registros de presença.
- **Node-RED Dashboard 2.0:** utilizado para apresentar os indicadores e a lista de presença em uma interface web.

### 3.2 Arquitetura e componentes

A arquitetura foi organizada em três partes principais: dispositivo, servidor e banco de dados.

O **dispositivo** é formado pelo teclado matricial e pelo ESP32. O firmware lê os dígitos informados pelo aluno. A tecla `#` confirma o RA e inicia o envio, enquanto a tecla `*` apaga o valor digitado.

No **servidor**, o Node-RED recebe o RA por meio do endpoint `POST /presenca`, valida a informação, consulta o cadastro do aluno e registra a presença quando encontra um RA válido. O próprio Node-RED também executa as consultas necessárias para alimentar o dashboard.

Na camada de **dados**, o MySQL mantém as tabelas `alunos` e `presencas`. A primeira armazena os dados dos estudantes, enquanto a segunda registra o aluno e a data e hora de cada presença.

O fluxo principal funciona da seguinte maneira: o aluno digita o RA, o ESP32 envia os dados ao Node-RED, o servidor consulta o MySQL, registra a presença e retorna uma resposta ao dispositivo. O dashboard consulta os dados periodicamente e atualiza as informações exibidas ao professor.

### 3.3 Requisitos documentados

A documentação apresenta requisitos funcionais e não funcionais. Entre os funcionais, estão a leitura do RA pelo teclado, o envio da informação por HTTP, a validação do aluno, o registro da presença no banco e a atualização automática do dashboard.

Entre os requisitos não funcionais, foram descritos aspectos de desempenho, usabilidade, portabilidade, interoperabilidade, manutenibilidade, compatibilidade, segurança e confiabilidade. O README também identifica quais requisitos estão atendidos, parcialmente atendidos ou ainda não implementados.

## 4. Documentação do README.md

A principal entrega da atividade foi a elaboração de um README detalhado para o repositório. O arquivo foi organizado em seções para facilitar a consulta e permitir que outra pessoa compreenda o projeto e consiga reproduzir sua execução.

Além da visão geral, dos requisitos, das tecnologias e da arquitetura, o README documenta:

- **Estrutura do repositório:** localização dos arquivos do firmware, do fluxo do Node-RED, do banco de dados e do circuito do Wokwi.
- **Pré-requisitos:** ferramentas e versões necessárias, como Node.js, Node-RED, MySQL, VS Code, PlatformIO e Wokwi.
- **Instalação e configuração:** instruções para clonar o repositório, preparar o banco, instalar as dependências do Node-RED, importar o fluxo e configurar o ESP32.
- **Execução:** orientações para iniciar o servidor, compilar o firmware e utilizar o projeto tanto no Wokwi quanto em um ESP32 físico.
- **API:** documentação do endpoint `POST /presenca`, com exemplo de requisição e possíveis respostas HTTP.
- **Banco de dados:** descrição das tabelas `alunos` e `presencas`, seus campos e as consultas utilizadas pelo sistema.
- **Variáveis de configuração:** indicação dos parâmetros de Wi-Fi, endereço da API, pinos do teclado, conexão com o MySQL e intervalo de atualização do dashboard.
- **Testes:** procedimentos manuais para verificar a API, o registro no banco, o dashboard e o firmware.
- **Deploy:** recomendações para disponibilizar o Node-RED e o banco em um servidor e preparar o dispositivo para o ambiente de uso.

O README também registra limitações conhecidas e possíveis melhorias. Entre elas estão a ausência de autenticação e HTTPS, a possibilidade de registros duplicados no mesmo dia, a necessidade de melhorar o tratamento de alguns erros e a falta de testes automatizados no repositório. Essas observações ajudam a deixar claro o estado atual do projeto, sem apresentar funcionalidades planejadas como se já estivessem implementadas.

## 5. Considerações finais

A atividade permitiu aplicar os conceitos de documentação de software em um projeto que integra hardware, firmware, comunicação HTTP, processamento de dados e interface web. Ao organizar essas informações no README, o projeto passou a ter uma descrição mais completa de seu funcionamento e instruções que facilitam sua instalação, configuração, execução e análise.

Além de explicar o que o sistema faz, a documentação registra suas tecnologias, arquitetura, requisitos e limitações. Dessa forma, o trabalho reforçou a importância de manter a documentação junto ao código-fonte, contribuindo para a compreensão, manutenção e continuidade do desenvolvimento do projeto.
