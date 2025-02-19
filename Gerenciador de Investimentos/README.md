# Teste Técnico de Backend

## Introdução

Bem-vindo ao teste técnico de Backend.

O objetivo principal deste exercício é avaliar sua abordagem para a resolução de problemas, bem como sua capacidade de escrever código limpo, bem testado e reutilizável. Não há regras rígidas ou perguntas complicadas.

## Glossário
* Investimento - Representa um investimento realizado por um cliente, contendo o proprietário, data de criação e valor investido.
* Ganho - Representa o lucro acumulado de um investimento, calculado mensalmente com juros compostos.
* Retirada - Processo de resgatar o valor investido junto com os ganhos, considerando a tributação aplicável.

## Exercício
O objetivo do exercício é definir e implementar um serviço de backend para gerenciar investimentos. Após essa implementação, você criará um microsserviço que oferece uma API REST para consumir essa funcionalidade.

> **Nota:** Priorize a simplicidade e estruture o código em um único módulo utilizando pacotes apropriados.

### 1. Interface do Serviço
Dado a seguinte definição para o serviço de investimentos:

```java
public interface IInvestimentoService {

    Investimento criarInvestimento(InvestimentoDados dados);

    InvestimentoVisualizar visualizarInvestimento(String id);

    void retirarInvestimento(String id);
}
```

**Tarefa:** Implemente a interface acima garantindo as seguintes regras de negócio:

1. A criação de um investimento deve conter:
   * Proprietário
   * Data de criação (hoje ou no passado)
   * Valor investido (deve ser positivo)

2. A visualização de um investimento deve retornar:
   * Valor inicial
   * Saldo esperado (valor investido + ganhos)
   * Se o investimento já foi retirado, o saldo deve refletir apenas os ganhos

3. A retirada de um investimento deve considerar:
   * O resgate será sempre do valor total (parcial não é permitido)
   * Pode ocorrer hoje ou no passado, mas não no futuro e nem antes da criação
   * Tributação será aplicada ao lucro antes do valor final ser exibido

### 2. Cálculo de Ganhos
O investimento pagará 0.52% ao mês na mesma data da criação.

* Os ganhos devem ser compostos, ou seja, cada período (mês) os ganhos acumulados serão incorporados ao saldo.

### 3. Tributação
Ao realizar uma retirada, a tributação será aplicada apenas sobre o lucro obtido:

* Se tiver menos de 1 ano, a alíquota é 22,5%
* Entre 1 e 2 anos, a alíquota é 18,5%
* Acima de 2 anos, a alíquota é 15%

### 4. API REST

**Tarefa:** Defina uma API REST para oferecer a funcionalidade do serviço de investimentos implementado.

* Utilize um framework como [Spring Boot](https://spring.io/) ou similar.
* A API deve incluir:
   * Rota para criar um investimento
   * Rota para visualizar um investimento
   * Rota para retirar um investimento
   * Paginação na listagem de investimentos de um usuário

## Entregáveis

### Código-Fonte
O projeto deve ser disponibilizado no GitHub seguindo estas etapas:

1. Fork deste repositório.
2. Criar um branch "development" e realizar os commits nele.
3. Incluir um README explicando:
   * Instruções de build e execução
   * Bibliotecas utilizadas e suas finalidades
   * Link para a documentação da API
4. Criar um pull request quando finalizar o desafio.

> **Nota:** Prefira código autoexplicativo ao invés de documentação extensa.

