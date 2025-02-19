# Desafio: API REST Simples para Gerenciamento de Notas

## Introdução
Este desafio tem como objetivo testar suas habilidades na criação de uma **API REST** utilizando **Python** com **Flask**.  
O desafio é simples e ideal para iniciantes que desejam adquirir experiência prática na construção de APIs.

---

## Objetivo
Desenvolver uma **API REST** para gerenciar uma coleção de notas, permitindo operações básicas de criação, leitura, atualização e exclusão.

---

## Requisitos

### CRUD de Notas
A API deve permitir as seguintes operações:
- Criar uma nova nota;
- Listar todas as notas;
- Atualizar uma nota existente;
- Excluir uma nota.

### Estrutura dos Dados
Cada nota deve conter os seguintes campos:
- `id`: identificador único (gerado automaticamente);
- `title`: título da nota (obrigatório);
- `content`: conteúdo da nota (obrigatório);
- `created_at`: data e hora da criação (gerado automaticamente).

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
### 2. Ative o ambiente virtual:
```bash
source venv/bin/activate  
venv\Scripts\activate      
```
### 3. Instale as dependências necessárias:
```bash
pip install flask flask-cors
```
### 4. Crie o servidor e implemente as rotas conforme os requisitos.
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