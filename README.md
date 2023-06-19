# RFC: Adição de Notificação por E-mail para Novas Tarefas Atribuídas

**Autor:** Heitor Augusto Lima da Silva

**Data:** 19/06/2023

## Resumo

O objetivo deste RFC é propor a adição de uma funcionalidade de notificação por e-mail quando uma nova tarefa é atribuída a um usuário no sistema de gerenciamento de tarefas. Isso ajudará a garantir que os usuários estejam cientes de novas tarefas atribuídas a eles e permitirá uma melhor comunicação e acompanhamento das atividades.



## Motivação

Atualmente, o sistema de gerenciamento de tarefas não possui um mecanismo de notificação por e-mail para informar os usuários sobre novas tarefas atribuídas a eles. Isso resulta em uma comunicação menos eficiente e pode levar a atrasos no cumprimento das tarefas. Ao adicionar essa funcionalidade, podemos melhorar a colaboração e garantir que todos estejam atualizados sobre suas responsabilidades.



## Detalhes da Implementação

Ao criar uma nova tarefa no sistema, será adicionada uma opção para atribuir a tarefa a um usuário específico.
Após a atribuição da tarefa, o sistema enviará automaticamente um e-mail de notificação para o usuário informando sobre a nova tarefa atribuída a ele.
O e-mail de notificação conterá detalhes relevantes da tarefa, como título, descrição, prazo e outros campos relevantes.
O conteúdo e o formato do e-mail de notificação serão definidos posteriormente, após discussões adicionais com a equipe de design e experiência do usuário.



## Impactos Potenciais

Será necessário integrar o sistema de gerenciamento de tarefas com um serviço de envio de e-mails, como o SendGrid ou SMTP.
Será necessário configurar as credenciais de e-mail para o serviço escolhido no ambiente de produção.
Pode haver impacto na carga do servidor de e-mail se houver um grande número de tarefas atribuídas simultaneamente. Esse aspecto precisa ser monitorado e otimizado, se necessário.



## Considerações Alternativas

Uma alternativa à notificação por e-mail seria a adição de notificações internas dentro do próprio sistema de gerenciamento de tarefas. No entanto, essa abordagem pode ser menos eficaz, pois os usuários podem não verificar as notificações internas com a mesma frequência que verificam seus e-mails.



## Seção Técnica

### Arquitetura de Software

A funcionalidade proposta será implementada como um microserviço separado no sistema existente de gerenciamento de tarefas. Ele se comunicará com outros componentes por meio de APIs RESTful. O microserviço será desenvolvido utilizando a arquitetura baseada em contêineres, com o uso do Docker.



### Tecnologias Envolvidas

A implementação utilizará as seguintes tecnologias e ferramentas:

Linguagem de programação: Python
Framework web: Django
Banco de dados: PostgreSQL
Serviço de envio de e-mails: SendGrid
Contêinerização: Docker
Orquestração de contêineres: Docker Compose



### Requisitos de Hardware e Software

Para o correto funcionamento da funcionalidade proposta, os requisitos de hardware e software serão:

Servidor com pelo menos 2 CPU e 4 GB de RAM
Sistema operacional: Linux (Ubuntu 20.04 LTS)
Docker Engine instalado (versão 20.10 ou superior)
Docker Compose instalado (versão 1.29 ou superior)
Python 3.8 instalado



### Fluxo de Dados

Quando uma nova tarefa é atribuída a um usuário, o fluxo de dados seguirá a seguinte sequência:

O microserviço receberá uma requisição HTTP contendo os detalhes da tarefa e o usuário atribuído.
O microserviço salvará a tarefa no banco de dados PostgreSQL.
Será realizada uma consulta ao banco de dados para obter as informações completas da tarefa.
Utilizando o serviço SendGrid, um e-mail de notificação será enviado para o usuário atribuído contendo os detalhes da tarefa.
Integrações Externas
Será necessário configurar as credenciais do serviço SendGrid no ambiente de produção para permitir o envio de e-mails de notificação. As informações de autenticação serão armazenadas em variáveis de ambiente protegidas.

### Segurança

A autenticação no microserviço será feita utilizando tokens JWT (JSON Web Tokens). As requisições de entrada serão validadas e autorizadas antes de serem processadas. Os dados sensíveis, como senhas de e-mail, serão armazenados de forma segura, utilizando-se de técnicas de criptografia.



### Testes e Qualidade de Software

A implementação da funcionalidade será acompanhada por testes unitários automatizados para garantir a qualidade do código. Além disso, serão realizados testes de integração e testes de carga para validar a robustez do sistema. Será utilizado o framework de testes pytest.


## Conclusão

A adição de notificação por e-mail para novas tarefas atribuídas é uma melhoria importante para o sistema de gerenciamento de tarefas, permitindo uma melhor comunicação e acompanhamento das atividades. Com essa funcionalidade, os usuários serão prontamente informados sobre as tarefas atribuídas a eles, garantindo uma colaboração mais eficiente.
