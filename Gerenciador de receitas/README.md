# Desafio: API REST para Gerenciamento de Receitas

## Introdução
Este desafio tem como objetivo testar suas habilidades na criação de uma **API REST** utilizando **Python** com **Flask**. O desafio é simples e criativo, ideal para quem está começando no desenvolvimento backend e deseja construir uma API para gerenciar uma coleção de receitas.

---

## Objetivo
Desenvolver uma **API REST** para gerenciar uma coleção de receitas, permitindo operações básicas de criação, leitura, atualização e exclusão de registros. A API deve possibilitar a busca por nome, ingredientes ou categoria, facilitando a navegação e o acesso às receitas.

---

## Requisitos

### CRUD de Receitas
A API deve permitir as seguintes operações:
- Criar uma nova receita;
- Listar todas as receitas;
- Atualizar uma receita existente;
- Excluir uma receita.

### Estrutura dos Dados
Cada receita deve conter os seguintes campos:
- `id`: identificador único (gerado automaticamente);
- `name`: nome da receita (obrigatório);
- `ingredients`: lista de ingredientes (obrigatório);
- `instructions`: modo de preparo (obrigatório);
- `category`: categoria da receita (ex.: sobremesa, prato principal) (obrigatório);
- `created_at`: data e hora de criação (gerado automaticamente).

### Formato das Requisições e Respostas
> **A API deve aceitar e retornar dados no formato JSON.**

---

## Tecnologias Obrigatórias
- **Python** com **Flask**

---

## Instruções para Implementação

### 1. Inicialize um ambiente virtual:
```bash
python -m venv venv
```
Ative o ambiente:
```bash
source venv/bin/activate  
venv\Scripts\activate      
```
### 2. Instale as dependências necessárias:
```bash
pip install flask flask-cors
```
### 3. Crie o servidor e implemente as rotas conforme os requisitos.
### Extras (Opcional)
-Implementar persistência de dados utilizando SQLite ou MongoDB;
-Adicionar validações para garantir que os campos obrigatórios sejam preenchidos;
-Documentar a API utilizando Swagger.

### Requisitos Técnicos
-O código deve seguir boas práticas de organização e estilo (PEP-8);
-O projeto deve conter um README com instruções de instalação e uso;
-Opcionalmente, hospedar a API em um serviço gratuito como Heroku ou Railway.

### Recursos Úteis
-Documentação Flask
-JSONPlaceholder (Exemplo de API)