# Teste para Candidato a Analista Backend

## Introdução

Bem-vindo ao Teste para Candidato a Analista Backend.

O principal objetivo deste teste é avaliar sua abordagem para resolução de problemas, bem como sua capacidade de escrever código limpo, bem testado e reutilizável. Não há regras rígidas ou perguntas capciosas.

## Glossário
* **Produto** - Item cadastrado por um usuário no sistema, contendo informações como título, descrição, preço e categoria associada.
* **Categoria** - Classificação utilizada para agrupar produtos de um mesmo tipo.
* **Proprietário** - Usuário que detém os direitos sobre produtos e categorias cadastradas.

## Exercício
O objetivo do exercício é definir e implementar um serviço backend para gerenciar um catálogo de produtos em um marketplace. Após a implementação, você criará uma API REST para expor essa funcionalidade.

> **Nota:** Priorize a simplicidade e organize o projeto em módulos e pacotes.

### 1. Interface do Serviço
Defina uma interface de serviço que inclua as seguintes funcionalidades:

```javascript
interface ICatalogService {
  createProduct(productData: ProductData): Promise<Product>;
  createCategory(categoryData: CategoryData): Promise<Category>;
  associateProductToCategory(productId: string, categoryId: string): Promise<void>;
  updateProduct(productId: string, updateData: Partial<ProductData>): Promise<Product>;
  updateCategory(categoryId: string, updateData: Partial<CategoryData>): Promise<Category>;
  deleteProduct(productId: string): Promise<void>;
  deleteCategory(categoryId: string): Promise<void>;
  getCatalog(ownerId: string): Promise<Catalog>;
}
```

**Tarefa:** Implementar essa interface garantindo concorrência e não bloqueio das requisições.

### 2. Implementação do Serviço

#### Requisitos:
1. Implementar um serviço que:
   * Valide e armazene produtos e categorias.
   * Garanta que cada produto esteja associado a apenas uma categoria por vez.
   * Certifique-se de que os produtos e categorias pertencem apenas ao seu respectivo proprietário.

2. Criar um mecanismo de notificação para alterações no catálogo:
   * Sempre que um produto ou categoria for alterado, publique essa mudança no tópico **"catalog-emit"** do AWS SQS.
   * Criar um consumidor que escute mensagens sobre mudanças no catálogo de um proprietário específico.
   * O consumidor buscará o catálogo atualizado no banco de dados e o publicará em um bucket AWS S3.

### 3. API REST

**Tarefa:** Definir uma API REST para expor a funcionalidade do serviço **ICatalogService**.

#### Requisitos:
* Criar endpoints para:
  - Criar, atualizar, deletar e buscar produtos e categorias.
  - Associar produtos a categorias.
  - Obter o catálogo completo de um proprietário.
* Implementar a API usando **Express.js**.
* Garantir alta concorrência e desempenho.
* Documentar os endpoints no **Swagger**.

### Tecnologias Obrigatórias
* **MongoDB** - Banco de dados.
* **AWS SQS** - Para notificação de alterações no catálogo.
* **AWS S3** - Para armazenar o JSON atualizado do catálogo.
* **Node.js** - Backend.
* **Express.js** - Framework web.

## Instruções
1. Faça um fork do repositório.
2. Crie uma branch com seu nome completo.
3. Desenvolva a solução conforme os requisitos.
4. Envie o link do repositório com a solução completa.
5. Configure sua própria conta da AWS para os serviços necessários.
6. Atualize o **README** com instruções para rodar sua aplicação.
7. Copie o nome da sua branch no sistema GUPY e finalize o teste.

## Critérios de Avaliação

* **Conhecimento em JavaScript, Node.js e Express.js**.
* **Organização das camadas da aplicação**.
* **Boas práticas em chamadas externas**.
* **Uso adequado de variáveis de ambiente**.
* **Implementação de testes unitários**.
* **Estratégias de logging e tratamento de erros**.

Boa sorte!

