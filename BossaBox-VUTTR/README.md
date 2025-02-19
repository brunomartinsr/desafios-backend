# VUTTR - Backend

## Introdução

Bem-vindo ao desafio de desenvolvimento backend para a aplicação VUTTR (Very Useful Tools to Remember).

O principal objetivo deste exercício é avaliar sua abordagem para resolver problemas, bem como sua capacidade de escrever código limpo, bem testado e reutilizável. Não há regras rígidas ou pegadinhas.

## Glossário
* **Ferramentas** - Recurso armazenado no sistema contendo _id_, _título_, _link_, _descrição_ e _tags_.
* **API** - Interface de comunicação que permite a gestão das ferramentas.
* **Banco de Dados** - Meio de persistência das ferramentas cadastradas.

## Exercício
O objetivo do exercício é projetar e implementar um serviço backend e disponibilizá-lo por meio de uma API REST.

> **Nota:** Priorize a simplicidade. Estruture o projeto em um único módulo e utilize pacotes para organizar o código.

### 1. Interface do Serviço

Defina uma interface para gestão das ferramentas, incluindo as seguintes operações:

```java
public interface IToolService {

    List<Tool> getAllTools();
    
    Tool addTool(Tool tool);
    
    void deleteTool(int id);
}
```

**Tarefa:** Implemente a interface para fornecer funcionalidades completas de CRUD para as ferramentas.

### 2. Implementação do Serviço

Forneça uma implementação para a interface `IToolService`, garantindo que:

1. As ferramentas sejam armazenadas e recuperadas de um banco de dados.
2. O serviço suporte operações assíncronas.
3. Cada ferramenta possua os seguintes atributos:
   * `id`: identificador único.
   * `title`: nome da ferramenta.
   * `link`: URL da ferramenta.
   * `description`: descrição breve.
   * `tags`: lista de palavras-chave.
4. Os dados sejam persistidos em um banco de dados real.

**Diretrizes:**
- Utilize um banco de dados relacional ou NoSQL.
- O serviço deve ser projetado para lidar com acessos concorrentes.
- A implementação deve ser modular para facilitar a manutenção e expansão.

### 3. API REST

**Tarefa:** Defina uma API REST para expor a funcionalidade do `IToolService`. A API deve responder na porta `3000` e incluir:

1. **Listagem de Ferramentas**
   * `GET /tools`
   * Retorna todas as ferramentas cadastradas.

2. **Adicionação de uma nova Ferramenta**
   * `POST /tools`
   * Adiciona uma nova ferramenta ao banco de dados.

3. **Remoção de uma Ferramenta**
   * `DELETE /tools/{id}`
   * Remove uma ferramenta pelo seu ID.

**Exemplo de resposta:**

```json
[
    {
        "id": 1,
        "title": "Notion",
        "link": "https://notion.so",
        "description": "Ferramenta completa para organizar equipes e ideias.",
        "tags": ["organization", "planning", "collaboration"]
    }
]
```

### 4. Entrega

**Código-fonte:**
- Forneça o projeto em um repositório acessível ou um arquivo zip contendo o código.

**Documentação:**
- Inclua um `README.md` com instruções de instalação e execução.
- Utilize **Swagger** ou **API Blueprint** para documentar a API.

### 5. Avaliação

Os seguintes critérios serão considerados:

- **Simplicidade:** Evite soluções excessivamente complexas.
- **Desempenho e Concorrência:** A API deve suportar acessos simultâneos.
- **Testes:** Forneça testes automatizados.
- **Tolerância a Falhas:** O sistema deve ser capaz de lidar com erros.
- **Autenticação e Autorização:** O uso de **OAuth** ou **JWT** é um diferencial.

> **Nota:** O desafio não é sobre frameworks ou bibliotecas específicas, mas sim sobre boas práticas de desenvolvimento backend.

