# Exercício de Backend - Pokéfight

## Introdução

Bem-vindo ao exercício técnico de backend da Brainn.

O principal objetivo deste exercício é avaliar sua abordagem para a resolução de problemas, bem como sua habilidade em escrever código limpo, bem testado e reutilizável. Não há regras rígidas ou perguntas pegadinhas.

## Glossário
* **Batalha** - Representa um confronto entre dois Pokémons.
* **Pokémon** - Criatura que participa da batalha.
* **Resultado da batalha** - Determina qual Pokémon saiu vitorioso e quais foram os participantes.

## Exercício

O objetivo do exercício é melhorar a definição de um serviço/backend e fornecer uma implementação para ele. Após isso, você deverá criar um microsserviço que disponibilize uma API REST para consumir as funcionalidades do serviço.
> **Nota:** Prefira simplicidade, codifique a solução como um único módulo e utilize pacotes para estruturá-lo.

### 1. Interface do Serviço

Dadas estas definições síncronas e assíncronas do **BattleService**:

```java
public interface ISyncBattleService {

    Battle createBattle(Pokemon pokemon1, Pokemon pokemon2);

    BattleResult getBattleResult(Battle battle);

    default BattleResult executeBattle(Pokemon pokemon1, Pokemon pokemon2) {
        throw new NotImplementedException(); //TODO: Implementar isso
    }
}
```

```java
public interface IAsyncBattleService {

    CompletableFuture<Battle> createBattle(Pokemon pokemon1, Pokemon pokemon2);

    CompletableFuture<BattleResult> getBattleResult(Battle battle);

    default Future<BattleResult> executeBattle(Pokemon pokemon1, Pokemon pokemon2) {
        throw new NotImplementedException(); //TODO: Implementar isso
    }
}
```

**Tarefa:** Fornecer ambas as implementações do método *executeBattle* utilizando *createBattle* e *getBattleResult*. Dessa forma, quem implementar o serviço precisará apenas implementar *createBattle* e *getBattleResult*.

### 2. Implementação do Serviço

Fornecer uma implementação para a seguinte API, que **é diferente** da definida anteriormente:

```java
public interface ISimpleAsyncBattleService {

  default CompletableFuture<BattleResult> executeBattle(Pokemon pokemon1, Pokemon pokemon2) {
    throw new NotImplementedException(); //TODO: Implementar isso
  }
}
```

**Requisitos e diretrizes da tarefa:**

Preferimos que você utilize um modelo baseado em **atores**, como o [Akka](https://akka.io/), mas não é obrigatório. Você pode utilizar outros frameworks, como [Spring](https://spring.io/) ou qualquer outro de sua escolha.

1. Implementar um **Actor/Service/Module** que:
   * Consulta informações dos Pokémons na [PokéAPI](https://pokeapi.co/).
   * A batalha deve ser gerada e armazenada em um banco de dados para consultas futuras.
   * A decisão do vitorioso pode ser feita de forma randômica.

2. Implementar outro **Actor/Service/Module** que:
   * Retorna o resultado de uma batalha previamente armazenada.
   * Este serviço deve garantir concorrência adequada para suportar várias requisições simultâneas.

3. Implementar a função *executeBattle* de **ISimpleAsyncBattleService**, garantindo que:
   * A batalha é registrada e processada corretamente.
   * O vitorioso é determinado e salvo no banco de dados.
   * A resposta da batalha é retornada corretamente ao chamador original.

**Notas de avaliação:**

Queremos ver como você estrutura o sistema e lida com aspectos como:
* **Simplicidade** - Evite soluções excessivamente complexas.
* **Modelo de threading e APIs não bloqueantes** - Como você otimiza o uso dos recursos disponíveis.
* **Concorrência** - Como as requisições são tratadas para maximizar o desempenho.
* **Testes** - Como você projeta os testes para garantir boa cobertura.
* **Tolerância a falhas** - Como o sistema lida e reage a falhas.

> **Importante:**
> * O sistema deve suportar várias requisições simultâneas sem bloqueios.
> * Falhas e exceções devem ser tratadas adequadamente.

### 3. API REST

**Tarefa:** Definir uma API REST para expor a funcionalidade do **ISimpleAsyncBattleService**.

Para sua implementação, preferimos que você utilize [Akka HTTP](https://doc.akka.io/docs/akka-http/current/java/http/), mas frameworks como [Spring Boot](https://projects.spring.io/spring-boot/) também são aceitos.

**Notas de avaliação:**

Nosso foco é na estrutura e completude da API, bem como em seus testes.

## Entrega

* **Código-Fonte** - Envie de uma das seguintes formas:
    * Um arquivo ZIP contendo o projeto completo. Evite incluir binários e logs.
    * Um repositório privado acessível (GitHub, Bitbucket, etc.).

* **Documentação e Instruções** - Inclua um arquivo `README.md` contendo:
    * Suas suposições e decisões ao resolver o problema.
    * Justificativa para escolha das tecnologias e bibliotecas utilizadas.
    * Instruções para executar o código e os testes em um ambiente Linux.

> **Nota:** A documentação não precisa ser extensa, prefira código autoexplicativo.

