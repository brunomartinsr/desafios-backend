# FCamara - Teste para vaga de Desenvolvedor Node.js/React.js

## Introdução

Bem-vindo ao teste técnico para a vaga de Desenvolvedor Node.js/React.js na FCamara! O objetivo deste desafio é avaliar suas habilidades na criação de sistemas web, manipulação de banco de dados, boas práticas de desenvolvimento e conhecimento em tecnologias relevantes.

## Objetivo

Criar um sistema de controle de aluguel de livros em uma biblioteca.

## Requisitos

### Cadastro de Pessoa
Criar um cadastro de pessoa com os seguintes campos:
- Nome;
- CPF;
- Data de nascimento;
- Endereço completo.

> **Todos os campos são de preenchimento obrigatório.**

### Cadastro de Livro
Criar um cadastro de livro com os seguintes campos:
- Título;
- Autor;
- ISBN;
- Código da cópia.

> **Todos os campos são de preenchimento obrigatório.**

### Funcionalidades
- CRUD de pessoas;
- CRUD de livros;
- CRUD de cópias;
- Controle de aluguel de livros.

### Requisitos técnicos
- Persistência utilizando um banco de dados relacional open source (**MySQL, PostgreSQL, Firebird, etc.**);
- API RESTful com retorno em **JSON**;
- Implementação de **autenticação JWT**;
- Front-end responsivo (compatível com **desktop e celular**);
- Deve conter pelo menos:
  - Uma **tela modal**;
  - Um **menu lateral expansível**;
  - **Não utilizar Bootstrap e jQuery**;
- Implementação de relatórios:
  - Listar o título dos **3 livros com mais atrasos na devolução por mês** ao longo do ano;
  - Listar o título dos **3 livros mais alugados por cidade** ao longo do ano;
  - **Restrição:** Se uma pessoa atrasar a devolução **mais de 2 vezes**, ela não poderá alugar mais livros.
- Criar um **README** descrevendo:
  - Tecnologias utilizadas;
  - Chamadas dos serviços;
  - Configurações necessárias para executar a aplicação.

## Submissão

Crie um **fork** deste teste para acompanharmos o seu desenvolvimento através dos seus commits.

## Agradecimento

Agradecemos sua participação no teste. Boa sorte! 😄