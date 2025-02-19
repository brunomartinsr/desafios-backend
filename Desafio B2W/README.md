# Desafio Backend BIT - SP

## Introdução

Bem-vindo ao desafio técnico de Backend BIT - SP.

O principal objetivo deste exercício é avaliar sua abordagem para resolução de problemas, bem como sua capacidade de escrever código limpo, bem testado e reutilizável. Não há regras rígidas ou perguntas complexas.

## Glossário
* **Ordem** - Identifica uma transação contendo itens e suas informações associadas.
* **Item** - Representa um produto contido dentro de uma ordem.

## Exercício

O objetivo do exercício é definir um serviço backend e fornecer uma implementação para ele. Depois disso, você criará um microsserviço que oferece uma API REST para consumir a funcionalidade do serviço.

> **Nota:** Prefira a simplicidade e implemente a solução como um único módulo, utilizando pacotes para estruturar o código.

### 1. Definição do Serviço

Dado o seguinte requisito:

#### Requisição:
```
GET http://localhost:8080/challenge-backend/item?begindate=05-10-2016&finaldate=10-10-2016
```

#### Resposta esperada:
```json
[
  {
    "name": "Impressora",
    "code": "5",
    "date": "2016-10-05T14:30:37.040Z",
    "dimension": {
      "weight": 10.5,
      "height": 10.5,
      "width": 10.5,
      "length": 10.5
    }
  },
  {
    "name": "Fifa2017",
    "code": "6",
    "date": "2016-10-06T14:30:37.040Z",
    "dimension": {
      "weight": 10.5,
      "height": 10.5,
      "width": 10.5,
      "length": 10.5
    }
  }
]
```

### 2. Implementação do Serviço

1. O serviço deve consumir uma API de pedidos externa e filtrar os resultados de acordo com os parâmetros enviados na requisição HTTP.
2. O serviço deve ser implementado de forma a suportar múltiplas requisições simultâneas sem bloqueios.
3. Deve-se garantir que o serviço seja testável e bem estruturado.
4. Utilize Java 6 ou superior (ou a linguagem Elixir, se preferir).
5. O candidato pode escolher qualquer framework para a implementação.
6. Criar um arquivo **README** explicando como rodar o projeto.

### 3. Consulta SQL

Dada a seguinte estrutura de tabela:

```sql
CREATE TABLE events (
  event_type INTEGER NOT NULL,
  value INTEGER NOT NULL,
  time TIMESTAMP NOT NULL,
  UNIQUE (event_type, time)
);
```

Escreva uma consulta SQL (MySQL) que, para cada **event_type** registrado mais de uma vez, retorne a diferença entre o penúltimo e o mais antigo **value** (em termos de tempo). A tabela deve ser ordenada por **event_type** em ordem crescente.

#### Exemplo de dados:
```sql
event_type | value | time
-----------|-------|-------------------
2          | 5     | 2015-05-09 12:42:00
4          | -42   | 2015-05-09 13:19:57
2          | 2     | 2015-05-09 14:48:30
2          | 7     | 2015-05-09 12:54:39
3          | 16    | 2015-05-09 13:19:57
3          | 20    | 2015-05-09 15:01:09
```

#### Resultado esperado:
```sql
event_type | value
-----------|------
2          | 2
3          | 0
```

Explicação:
* Para o **event_type 2**, o penúltimo valor é **7** e o mais antigo é **5**, então a diferença é **2**.
* Para o **event_type 3**, o penúltimo valor é **16** e o mais antigo também é **16**, então a diferença é **0**.

### 4. Entrega

O candidato deve:

1. Criar um diretório **task2** para armazenar a solução da consulta SQL.
2. Criar um arquivo e colocar o resultado da consulta SQL nele.
3. Criar um **fork** deste projeto e enviar um **pull request** com a solução.

**Critérios de Avaliação:**

- **Qualidade e organização do código.**
- **Atenção aos requisitos.**
- **Uso eficiente de recursos e concorrência.**
- **Capacidade de lidar com falhas de forma resiliente.**

