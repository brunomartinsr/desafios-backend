# API REST Simples para Gerenciamento de Contatos

## Introdução
Este desafio tem como objetivo testar suas habilidades na criação de uma API REST utilizando **Node.js** com **Express.js**. O desafio é simples e ideal para quem está começando a trabalhar com desenvolvimento backend e na construção de APIs.

---

## Objetivo
Desenvolver uma API REST para gerenciar uma lista de contatos, permitindo operações básicas de criação, leitura, atualização e exclusão de registros.

---

## Requisitos

### CRUD de Contatos
A API deve permitir as seguintes operações:
- Criar um novo contato;
- Listar todos os contatos;
- Atualizar um contato existente;
- Excluir um contato.

### Estrutura dos Dados
Cada contato deve conter os seguintes campos:
- `id`: identificador único (gerado automaticamente);
- `name`: nome do contato (obrigatório);
- `email`: email do contato (obrigatório);
- `phone`: telefone do contato (obrigatório);
- `address`: endereço (opcional).

### Formato das Requisições e Respostas
> **A API deve aceitar e retornar dados no formato JSON.**

---

## Tecnologias Obrigatórias
- **Node.js** com **Express.js**

---

## Instruções para Implementação
1. Inicialize um projeto Node.js:
```bash
npm init -y
```
Instale as dependências necessárias:
```bash
npm install express cors
```
## Implemente as rotas para as operações CRUD conforme os requisitos.
### Extras (Opcional)
-Implementar persistência de dados utilizando um banco de dados leve (por exemplo, SQLite ou MongoDB);
-Adicionar validações para garantir o preenchimento dos campos obrigatórios;
-Documentar a API utilizando Swagger.

### Requisitos Técnicos
-O código deve seguir boas práticas de organização e estilo;
-O projeto deve conter um README com instruções de instalação e uso;
-Recomenda-se o uso de ES Modules (definindo "type": "module" no package.json);
-Opcionalmente, hospedar a API em um serviço gratuito como Render ou Railway.

### Recursos Úteis
-Documentação Express.js
-JSON Placeholder (Exemplo de API)