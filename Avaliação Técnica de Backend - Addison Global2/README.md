# Avaliação Técnica de Backend - Addison Global

## Introdução

Bem-vindo ao teste técnico de backend da Addison Global.

O principal objetivo deste exercício é avaliar sua abordagem para resolução de problemas, além da sua capacidade de escrever código limpo, bem testado e reutilizável. Não há regras rígidas ou pegadinhas.

## Glossário

* **Credenciais** - Uma tupla de _nome de usuário_ e _senha_ usada para autenticar um cliente.
* **Usuário** - Identifica um cliente dentro do sistema. Para simplificação, contém apenas um _userId_, que corresponde ao _nome de usuário_ do cliente.
* **Token de Usuário** - Um token concedido a um usuário para permitir operações no sistema. O token é a concatenação do _userId_ e do horário atual. Exemplo: `user123_2017-01-01T10:00:00.000`.

## Exemplo de Implementação

```java
public class Credentials {
    private String username;
    private String password;

    public String getUsername(){
        return username;
    }

    public String getPassword(){
        return password;
    }
}

public class User {
    private String userId;

    public String getUserId(){
        return userId;
    }
}

public class UserToken {
    private String token;

    public String getToken(){
        return token;
    }
}
```

## Exercício

O objetivo do exercício é aprimorar a definição de um serviço/módulo de backend e fornecer uma implementação para ele. Depois disso, você criará um microsserviço que disponibilizará uma API REST para consumir a funcionalidade do serviço/módulo.

> **Observação:** Busque a simplicidade. Desenvolva a solução como um único módulo e use pacotes para estruturá-la.

### 1. Interface do Serviço

Abaixo estão as definições de serviços síncronos e assíncronos do _TokenService_:

```java
public interface ISyncTokenService {
    User authenticate(Credentials credentials);
    UserToken requestToken(User user);
    
    default UserToken issueToken(Credentials credentials) {
        throw new NotImplementedException(); //TODO: Implementar
    }
}
```

```java
public interface IAsyncTokenService {
    CompletableFuture<User> authenticate(Credentials credentials);
    CompletableFuture<UserToken> requestToken(User user);
    
    default Future<UserToken> issueToken(Credentials credentials) {
        throw new NotImplementedException(); //TODO: Implementar
    }
}
```

#### **Tarefa:**
Fornecer as implementações do método `issueToken`, usando `authenticate` e `requestToken`. Dessa forma, quem implementar o serviço só precisará definir esses dois métodos.

### 2. Implementação do Serviço

Fornecer uma implementação para a seguinte API, que é diferente da anterior:

```java
public interface ISimpleAsyncTokenService {
  default CompletableFuture<UserToken> issueToken(Credentials credentials) {
    throw new NotImplementedException(); //TODO: Implementar
  }
}
```

#### **Requisitos da Tarefa:**

Preferimos que você utilize um modelo baseado em atores, como o [Akka](https://akka.io/), mas não é obrigatório. Outras tecnologias, como [Spring](https://spring.io/), podem ser utilizadas.

Você precisará implementar três serviços/módulos diferentes:

#### 1. **Serviço para Autenticação do Usuário**
* Valida as **credenciais** e retorna um objeto **User**.
* A resposta deve ter um atraso aleatório entre **0 e 5000 milissegundos**.
* A validação é bem-sucedida se a senha corresponder ao nome de usuário em **letras maiúsculas**, caso contrário, falha.
  * Exemplo:
    * username: `house`, password: `HOUSE` => **Credenciais válidas**
    * username: `house`, password: `House` => **Credenciais inválidas**
* O `userId` do usuário será o **nome de usuário** informado.

#### 2. **Serviço para Geração do Token de Usuário**
* Retorna um **UserToken** para um determinado **User**.
* O token deve ser retornado com um atraso aleatório entre **0 e 5000 milissegundos**.
* Se o **userId** começar com a letra **"A"**, a chamada falhará.
* O formato do **token** deve ser a concatenação do `userId` com a data e hora atual no formato `yyyy-MM-dd'T'HH:mm:ssZ`.
  * Exemplo:
    * username: `house` => `house_2017-01-01T10:00:00Z`

#### 3. **Serviço para Emissão de Tokens**
* Deve utilizar os dois serviços anteriores para:
  * Autenticar o usuário com as credenciais fornecidas.
  * Gerar um token após a autenticação bem-sucedida.
* Deve retornar o **UserToken** para o solicitante original.

### 3. API REST

#### **Tarefa:**
Definir uma API REST simples para expor a funcionalidade do **SimpleAsyncTokenService**.

> **Nota:** Preferimos o uso do [Akka HTTP](https://doc.akka.io/docs/akka-http/current/java/http/), mas você pode usar outras opções como [Spring Boot](https://projects.spring.io/spring-boot/).

### Entregáveis

* **Código Fonte:**
  * Um arquivo ZIP contendo o projeto.
  * Ou um repositório privado acessível com seu trabalho.
* **Documentação:**
  * Um `README.md` explicando decisões e tecnologias escolhidas.
  * Instruções para rodar a solução em ambiente Linux.
  
> **Nota:** Favor código autoexplicativo ao invés de documentação extensa.

