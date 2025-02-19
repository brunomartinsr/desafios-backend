# FCamara - Teste para vaga de Desenvolvedor Back-end

## Introdução

Bem-vindo ao teste técnico para a vaga de Desenvolvedor Back-end na FCamara! O objetivo deste desafio é avaliar suas habilidades na criação de APIs REST, modelagem de dados, boas práticas de desenvolvimento e conhecimento em tecnologias relevantes.

## Objetivo

Criar uma API REST para gerenciar um estacionamento de carros e motos.

## Requisitos

### Cadastro de estabelecimento
Criar um cadastro da empresa com os seguintes campos:
- Nome;
- CNPJ;
- Endereço;
- Telefone;
- Quantidade de vagas para motos;
- Quantidade de vagas para carros.

> **Todos os campos são de preenchimento obrigatório.**

### Cadastro de veículos
Criar um cadastro de veículos com os seguintes campos:
- Marca;
- Modelo;
- Cor;
- Placa;
- Tipo (carro ou moto).

> **Todos os campos são de preenchimento obrigatório.**

### Funcionalidades
- CRUD de estabelecimentos;
- CRUD de veículos;
- Controle de entrada e saída de veículos.

### Requisitos técnicos
- Modelagem de dados;
- O retorno deverá ser em formato **JSON** e **XML**;
- Requisições **GET, POST, PUT e DELETE**, conforme as melhores práticas;
- A persistência dos dados pode ser realizada da maneira que preferir;
- Criar um **README** descrevendo as tecnologias utilizadas, chamadas dos serviços e configurações necessárias para executar a aplicação.

### Ganha mais pontos
- Desenvolver utilizando **TDD**;
- Criar uma API de relatório:
  - Sumário da quantidade de entradas e saídas;
  - Sumário da quantidade de entradas e saídas de veículos por hora.
- Criar uma solução de **autenticação**.

## Questionário para Avaliação de Competências

### 1. GraphQL (Implementação BFF - Backend For Frontend)

#### Implementação
Crie um BFF com **GraphQL** localmente para permitir as operações de CRUD e controle de entrada e saída de veículos. O BFF deve expor as operações e lidar com as interações entre o front-end e o back-end.

#### Disponibilização
Disponibilize o projeto publicamente no **GitHub**, com um link no **README** para o repositório.

#### Documentação
Explique no **README** os benefícios de usar **GraphQL** no contexto do projeto, descrevendo também como configurar e rodar o **BFF** localmente.

#### Perguntas
- **Pergunta 1:** Explique o que é o **GraphQL** e como ele se diferencia de uma API REST tradicional.
- **Pergunta 2:** Descreva como você implementaria o uso do **GraphQL** como **BFF** neste projeto de gerenciamento de estacionamento. Forneça exemplos práticos.
- **Pergunta 3:** Quais são os benefícios de utilizar **GraphQL** em relação à flexibilidade das consultas? Cite possíveis desafios ao utilizá-lo.

### 2. Banco de Dados (Nível Básico)
- **Pergunta 1:** Explique os principais conceitos de um banco de dados relacional, como **tabelas, chaves primárias e estrangeiras**.
- **Pergunta 2:** No contexto de uma aplicação de gerenciamento de estacionamento, como você organizaria a modelagem de dados para suportar as funcionalidades de controle de entrada e saída de veículos?
- **Pergunta 3:** Quais seriam as vantagens e desvantagens de utilizar um **banco de dados NoSQL** neste projeto?

### 3. Agilidade (Nível Básico)
- **Pergunta 1:** Explique o conceito de **metodologias ágeis** e como elas impactam o desenvolvimento de software.
- **Pergunta 2:** No desenvolvimento deste projeto, como você aplicaria princípios ágeis para garantir entregas contínuas e com qualidade?
- **Pergunta 3:** Qual a importância da **comunicação entre as equipes** em um ambiente ágil? Dê exemplos de boas práticas.

### 4. DevOps (Nível Básico)
- **Pergunta 1:** O que é **DevOps** e qual a sua importância para o ciclo de vida de uma aplicação?
- **Pergunta 2:** Descreva como você integraria práticas de **DevOps** no desenvolvimento desta aplicação de estacionamento. Inclua exemplos de **CI/CD**.
- **Pergunta 3:** Cite as ferramentas que você usaria para automatizar o processo de **deploy** e monitoramento da aplicação.

## Submissão

Crie um **fork** deste teste para acompanharmos o seu desenvolvimento através dos seus commits.

## Agradecimento

Agradecemos sua participação no teste. Boa sorte! 😄

---

## Sobre a FCamara 🚀

"Queremos ser como uma árvore, crescer um pouco todos os dias e tentar tocar o céu, sem perder a solidez de nossas raízes."

Saiba mais: [www.fcamara.com.br](https://www.fcamara.com.br)

