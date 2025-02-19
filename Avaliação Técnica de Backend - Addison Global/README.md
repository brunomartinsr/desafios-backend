# Avaliação Técnica de Backend - Addison Global

## Introdução

Bem-vindo ao teste técnico de Backend da Addison Global.

O principal objetivo deste exercício é avaliar sua abordagem para a resolução de problemas, bem como sua capacidade de escrever código limpo, bem testado e reutilizável. Não há regras rígidas nem perguntas pegadinhas.

> **Nota:** Embora alguns trechos de código estejam escritos em Scala, o exercício pode ser desenvolvido em Java.

## Glossário

- **Credenciais** - Um par de _nome de usuário_ e _senha_ usado para autenticar um cliente.
- **Usuário** - Identifica um cliente no sistema. Para simplificação, contém apenas um _userId_, que corresponde ao nome de usuário do cliente.
- **UserToken** - Token concedido a um usuário para realizar operações no sistema. É a concatenação do _userId_ e do horário atual. Exemplo: `user123_2017-01-01T10:00:00.000`.

### Exemplo de Implementação:

```scala
case class Credentials(username: String, password: String)
case class User(userId: String)
case class UserToken(token: String)
```

## Exercício

O objetivo do exercício é melhorar a definição de um serviço/módulo de backend e fornecer uma implementação para ele. Depois disso, você criará um microsserviço que expõe uma API REST para consumir a funcionalidade do serviço/módulo.

> **Nota:** Priorize a simplicidade, desenvolvendo a solução como um único módulo e utilizando pacotes para organizar o código.

### 1. Interface do Serviço

Dadas estas definições síncronas e assíncronas do `TokenService`:

```scala
trait SyncTokenService {
  protected def authenticate(credentials: Credentials): User
  protected def issueToken(user: User): UserToken

  def requestToken(credentials: Credentials): UserToken = ???
}

import scala.concurrent.Future

trait AsyncTokenService {
  protected def authenticate(credentials: Credentials): Future[User]
  protected def issueToken(user: User): Future[UserToken]

  def requestToken(credentials: Credentials): Future[UserToken] = ???
}
```

**Tarefa:**
Forneça as implementações do método `requestToken`, utilizando `authenticate` e `issueToken`. Assim, quem implementar o serviço precisará apenas definir `authenticate` e `issueToken`.

> **Nota:** O `scala.concurrent.Future` não é equivalente ao `java.util.concurrent.Future` em Java. O `Future` em Scala é composável. Se estiver desenvolvendo em Java, utilize `CompletionStage` ou `CompletableFuture`.

### 2. Implementação do Serviço

Forneça uma implementação para a seguinte API, que difere da projetada na seção anterior:

```scala
trait SimpleAsyncTokenService {
   def requestToken(credentials: Credentials): Future[UserToken]
}
```

> **Nota:** Se estiver utilizando Java, prefira `CompletionStage` ou `CompletableFuture`.

### Requisitos e Diretrizes

Recomendamos o uso de um modelo baseado em atores, como [Akka](https://akka.io/), mas isso não é obrigatório. Você pode utilizar frameworks como [Spring](https://spring.io/) ou outro de sua escolha.

1. **Autenticação do Usuário**
   - Validar as **Credenciais** e retornar um **Usuário**.
   - A resposta será retornada com um atraso aleatório entre 0 e 5000 ms.
   - O usuário será autenticado apenas se a senha corresponder ao nome de usuário em maiúsculas.
   - O `userId` será o mesmo `username` fornecido.

2. **Geração de Token**
   - Retornar um **UserToken** para um **Usuário**.
   - A resposta será retornada com um atraso aleatório entre 0 e 5000 ms.
   - Se o `userId` começar com "A", a chamada falhará.
   - O `token` será a concatenação do `userId` com a data/hora atual em UTC (`yyyy-MM-dd'T'HH:mm:ssZ`).

3. **Implementação da `requestToken`**
   - Encapsular a lógica em um serviço/módulo.
   - Utilizar os serviços de autenticação e geração de token previamente definidos.
   - Primeiro, validar as credenciais e obter um **Usuário**.
   - Depois, obter um **UserToken**.
   - Retornar o **UserToken** ao chamador original.

### 3. API REST

**Tarefa:**
Defina uma API REST simples para expor a funcionalidade da interface `SimpleAsyncTokenService`.

> **Nota:** Preferimos o uso do [Akka HTTP](https://doc.akka.io/docs/akka-http/current/java/http/), mas você pode utilizar [Spring Boot](https://spring.io/projects/spring-boot) ou outra tecnologia.

### Critérios de Avaliação

- **Simplicidade** - Não complique desnecessariamente.
- **Modelo de Threading e APIs Não Bloqueantes** - Uso eficiente dos recursos.
- **Concorrência** - Como requisições são tratadas para maximizar a performance.
- **Testes** - Estratégia para garantir alta cobertura de testes.
- **Tolerância a Falhas** - Como o sistema lida com falhas.

## Entregáveis

- **Código-Fonte**: Pode ser enviado via:
  - Um arquivo `.zip` contendo o projeto completo (exceto binários e logs).
  - Um repositório privado acessível (GitHub ou Bitbucket).

- **Documentação e Instruções**:
  - Um `README.md` explicando suas decisões e tecnologias escolhidas.
  - Instruções para executar sua solução em um ambiente Linux.

> **Dica:** Prefira código autoexplicativo a não uma documentação extensa.