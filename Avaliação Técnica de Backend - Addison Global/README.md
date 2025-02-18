Avaliação Técnica de Backend - Addison Global
Introdução
Bem-vindo ao teste técnico de Backend da Addison Global.

O principal objetivo deste exercício é avaliar sua abordagem para a resolução de problemas, bem como sua capacidade de escrever código limpo, bem testado e reutilizável. Não há regras rígidas nem perguntas pegadinhas.

Nota: Embora alguns trechos de código estejam escritos em Scala, o exercício pode ser desenvolvido em Java.

Glossário
Credenciais – Um par de nome de usuário e senha usado para autenticar um cliente.
Usuário – Identifica um cliente no sistema. Para simplificação, contém apenas um userId, que corresponde ao nome de usuário do cliente.
UserToken – Token concedido a um usuário para realizar operações no sistema. É a concatenação do userId e do horário atual. Exemplo: user123_2017-01-01T10:00:00.000.
Exemplo de Implementação:

scala
Copiar
Editar
case class Credentials(username: String, password: String)
case class User(userId: String)
case class UserToken(token: String)
Exercício
O objetivo do exercício é melhorar a definição de um serviço/módulo de backend e fornecer uma implementação para ele. Depois disso, você criará um microsserviço que expõe uma API REST para consumir a funcionalidade do serviço/módulo.

Nota: Priorize a simplicidade, desenvolvendo a solução como um único módulo e utilizando pacotes para organizar o código.

1. Interface do Serviço
Dadas estas definições síncronas e assíncronas do TokenService:

scala
Copiar
Editar
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
Tarefa
Forneça as implementações do método requestToken, utilizando authenticate e issueToken. Assim, quem implementar o serviço precisará apenas definir authenticate e issueToken.

Nota: O scala.concurrent.Future não é equivalente ao java.util.concurrent.Future em Java. O Future em Scala é composável, então, ao desenvolver a solução em Java, sinta-se à vontade para alterar a assinatura para uma alternativa mais apropriada, como java.util.concurrent.CompletionStage ou java.util.concurrent.CompletableFuture.

2. Implementação do Serviço
Forneça uma implementação para a seguinte API, que difere da projetada na seção anterior:

scala
Copiar
Editar
trait SimpleAsyncTokenService {
   def requestToken(credentials: Credentials): Future[UserToken]
}
Nota: O scala.concurrent.Future não é equivalente ao java.util.concurrent.Future em Java. Caso utilize Java, prefira CompletionStage ou CompletableFuture.

Requisitos e Diretrizes
Recomendamos o uso de um modelo baseado em atores como o Akka, mas não é obrigatório. Você pode usar outros frameworks, como Spring ou qualquer outro de sua escolha.
Implemente um Ator/Serviço/Módulo que:
Valide as credenciais e retorne uma instância de User.
O retorno do User deve ter um atraso aleatório entre 0 e 5000 milissegundos.
A validação é bem-sucedida se a senha for igual ao nome de usuário em letras maiúsculas. Caso contrário, a validação falha. Exemplos:
username: house, password: HOUSE → Válido
username: house, password: House → Inválido
O userId do usuário retornado será o próprio nome de usuário.
Esse fluxo deve estar encapsulado em um serviço/ator separado.

Implemente outro Ator/Serviço/Módulo que:
Retorne um UserToken para um User.
O retorno do UserToken deve ter um atraso aleatório entre 0 e 5000 milissegundos.
Se o userId começar com "A", a solicitação falha.
O token será a concatenação do userId e da data/hora atual em UTC: yyyy-MM-dd'T'HH:mm:ssZ.
Exemplo: username: house → house_2017-01-01T10:00:00Z
Esse fluxo também deve estar encapsulado em um serviço/ator separado.

Implemente a função requestToken da interface SimpleAsyncTokenService, garantindo que:
O fluxo seja encapsulado em um serviço/ator próprio.
O serviço utilize os atores/módulos criados anteriormente para:
Autenticar o usuário com as credenciais fornecidas.
Gerar um token para o usuário autenticado.
Retornar o UserToken para o solicitante original.
Avaliação
O foco da avaliação será na modelagem do sistema de atores (ou na orquestração do serviço) e nos seguintes aspectos:

✅ Simplicidade – Evite soluções complexas desnecessárias.
✅ Modelo de Threading e APIs Não Bloqueantes – Como a solução maximiza o uso dos recursos disponíveis.
✅ Concorrência – Como as solicitações simultâneas são tratadas para maximizar o desempenho.
✅ Testes – Cobertura e qualidade dos testes desenvolvidos.
✅ Tolerância a Falhas – Como o sistema lida e reage a falhas isoladas.

⚠️ Pontos Importantes

O sistema deve suportar múltiplas solicitações concorrentes.
O fato de uma computação levar 5 segundos não deve bloquear outras execuções.
Modelagem e tratamento de falhas são essenciais.
3. API REST
Tarefa
Defina uma API REST para expor a funcionalidade do SimpleAsyncTokenService.

Frameworks recomendados:

Preferimos Akka HTTP, mas você pode usar http4s, Play Framework ou Spring Boot.
Avaliação
Estrutura e completude da API.
Qualidade e cobertura dos testes.
Entrega
A entrega deve conter:

📌 Código-fonte:

Você pode enviar o código de duas maneiras:
Um arquivo ZIP contendo todo o projeto (evite incluir binários, logs, etc.).
Um repositório privado acessível (por exemplo, GitHub ou Bitbucket).
📌 Documentação/Instruções:

Inclua um Readme.md com:
Suas suposições e decisões durante o desenvolvimento.
Tecnologias e bibliotecas escolhidas.
Instruções para rodar o projeto e os testes em um ambiente Linux.
Nota: Não precisa ser um relatório extenso. Código autoexplicativo é preferível!