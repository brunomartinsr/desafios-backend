# Olist - Teste para vaga de Desenvolvedor Back-end

## Introdução

Bem-vindo ao teste técnico para a vaga de Desenvolvedor Back-end na Olist! O objetivo deste desafio é avaliar suas habilidades na criação de APIs REST, modelagem de dados, boas práticas de desenvolvimento e conhecimento em tecnologias relevantes.

## Objetivo

Criar uma API REST para gerenciar uma biblioteca de livros e autores.

## Requisitos

### Importação de Autores via CSV

Criar um comando para importar um arquivo CSV contendo autores para o banco de dados. O arquivo seguirá o seguinte formato:

```
nome
Luciano Ramalho
Osvaldo Santana Neto
David Beazley
Chetan Giridhar
Brian K. Jones
J.K Rowling
```

Cada autor cadastrado no banco de dados deve conter os seguintes campos:
- ID (gerado automaticamente);
- Nome.

Os dados dos autores serão utilizados para complementar as informações dos livros cadastrados posteriormente.

### Exposição dos Dados dos Autores

Criar um endpoint que retorne uma lista paginada dos autores cadastrados. Deve ser possível realizar buscas opcionais por nome.

### CRUD de Livros

Implementar as funcionalidades de CRUD para livros, incluindo:
- Criar um livro;
- Consultar dados de um livro;
- Atualizar dados de um livro;
- Deletar um livro.

Cada livro deve conter os seguintes campos:
- ID (gerado automaticamente);
- Nome;
- Edição;
- Ano de publicação;
- Autores (um livro pode ter mais de um autor).

Para consultar um livro, deve ser possível filtrar pelos seguintes campos:
- Nome;
- Ano de publicação;
- Edição;
- Autor.

Os filtros são opcionais, permitindo a navegação por todos os dados dos livros sem necessidade de aplicação de filtros.

Para criar um livro, deve ser enviado o seguinte payload em formato JSON:

```json
{
  "name": "Nome do livro",
  "edition": "Número da edição",
  "publication_year": "Ano de publicação do livro",
  "authors": ["Lista de IDs dos autores previamente importados"]
}
```

## Requisitos Técnicos

- A aplicação deve estar funcional e ser hospedada em um serviço de deploy (recomenda-se Heroku);
- O código deve ser escrito em **Python** ou **Go**;
- No caso do uso de Python:
  - Utilizar versão >= 3.5;
  - Escolher qualquer framework web para resolver o problema;
  - Seguir o padrão **PEP-8** para estilo de código;
- No caso do uso de Go:
  - Utilizar versão >= 1.10;
  - Seguir as recomendações do **Effective Go**;
- Toda documentação e código devem estar em inglês;
- Documentação do projeto deve conter:
  - Descrição do sistema;
  - Instruções para instalação e execução;
  - Se houver uma solução em **Docker**, garantir que o projeto também funcione sem Docker;
  - Breve descrição do ambiente utilizado para desenvolvimento (sistema operacional, IDE/editor, bibliotecas, etc);
  - Documentação da API.

## Recomendações

- Escreva testes! Testes tornam o mundo melhor ❤;
- Siga os conceitos da **12 Factor-App**;
- Aplique princípios de **SOLID**;
- Utilize boas práticas de programação;
- Utilize boas práticas de uso do **Git**, com mensagens claras de commit (em inglês);
- Tenha atenção ao modelar o banco de dados;
- Cuide dos detalhes ao desenvolver a API REST;
- Divirta-se!

