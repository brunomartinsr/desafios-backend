# Desafio: API REST Simples para Gerenciamento de Tarefas

## Introdução
Este desafio tem como objetivo testar suas habilidades na criação de uma **API REST** usando **Node.js**.  
O desafio é simples e ideal para quem está começando a trabalhar com **desenvolvimento backend** e criação de **APIs**.

---

## Objetivo
Criar uma **API REST** para gerenciar uma lista de tarefas, permitindo operações básicas como:

- [ ] Criar uma nova tarefa
- [ ] Listar todas as tarefas
- [ ] Atualizar uma tarefa existente
- [ ] Excluir uma tarefa

---

## Requisitos

### CRUD de Tarefas
A API deve permitir as seguintes operações:

- Criar uma tarefa
- Listar todas as tarefas
- Atualizar uma tarefa existente
- Excluir uma tarefa

### Estrutura dos Dados
Cada tarefa deve conter os seguintes campos:

| Campo        | Tipo      | Obrigatório | Descrição |
|-------------|----------|-------------|------------|
| `id`        | integer  | Sim         | Gerado automaticamente |
| `title`     | string   | Sim         | Título da tarefa |
| `description` | string | Não         | Descrição opcional da tarefa |
| `completed` | boolean  | Sim         | Indica se a tarefa foi concluída *(default: false)* |
| `created_at` | datetime | Sim        | Data e hora da criação |

### Formato das Requisições e Respostas
> **A API deve aceitar e responder em formato JSON**.

---

## Tecnologias Obrigatórias
- **Node.js** com **Express.js**  

---

## Instruções para Implementação

### 1. Inicialize um projeto Node.js:
```bash
npm init -y
```

2. Instale as dependências necessárias:
```bash
npm install express cors
```

### 3. Crie o servidor e implemente as rotas conforme os requisitos.
### Extras (Opcional)
-Implementar persistência de dados usando SQLite ou MongoDB
-Adicionar validações para garantir que os campos obrigatórios sejam preenchidos
-Criar uma documentação da API usando Swagger

### Requisitos Técnicos
-O código deve seguir boas práticas de organização e estilo
-O projeto deve conter um README com instruções de instalação e uso
-Recomendado o uso de ES Modules ("type": "module" no package.json)
-Opcionalmente, hospedar a API em um serviço gratuito como Render ou Railway

### Recursos Úteis
-Documentação Express.js
-JSON Placeholder (Exemplo de API)