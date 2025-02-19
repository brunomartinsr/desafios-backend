# Teste Back End 2019

## Introdução

Bem-vindo ao teste técnico de Backend da DIN DIGITAL.

O principal objetivo deste exercício é avaliar sua abordagem para resolver problemas, assim como sua habilidade de escrever código limpo, bem testado e reutilizável. Não há regras rígidas ou perguntas pegadinhas.

## Glossário
* **Ambiente** - O sistema deve ser configurado utilizando Docker como ambiente local (Laradock), incluindo Laravel 5.8.
* **Autenticação** - Deve ser implementada utilizando JWT.
* **CRUD** - Implementação de operações básicas de criação, leitura, atualização e exclusão.

## Exercício
O objetivo do exercício é definir e implementar uma mini API REST utilizando Laravel como framework PHP, JWT para autenticação e um CRUD simples.

> **Nota:** Favoreça a simplicidade, estruturando o código em um único módulo e utilizando pacotes para organizá-lo.

### 1. Configuração do Ambiente

#### Requisitos de Software
- Algum terminal de comandos
- Docker
- Docker-compose

#### Comando para Configuração Automática do Ambiente
Copie o bloco de comandos abaixo e cole em um terminal dentro da sua pasta de projetos. **Observação:** Este comando inclui o próprio git clone. Ao final, você terá um ambiente LAMP com Laravel 5.8 pronto para uso dentro da pasta **site**.

```bash
echo -e "\033[1;92m Clonando...\033[m" &&\
git clone git@github.com:dindigital/teste-back-end-2019.git &&\
echo -e "\033[1;92m Entrando na pasta do repositório clonado...\033[m" &&\
cd teste-back-end-2019 &&\
echo -e "\033[1;92m Entrando na pasta docker...\033[m" &&\
cd docker &&\
echo -e "\033[1;92m Buildando o docker...\033[m" &&\
docker-compose build &&\
echo -e "\033[1;92m Parando possíveis dockers abertos...\033[m" &&\
docker stop $(docker ps -a -q) &&\
echo -e "\033[1;92m Ligando o docker...\033[m" &&\
docker-compose up -d &&\
echo -e "\033[1;92m Criando arquivo .env...\033[m" &&\
ln -s ../site/.env.example ../site/.env &&\
echo -e "\033[1;92m Composer install...\033[m" &&\
docker-compose exec --user=laradock workspace sh -c "cd /var/www/site && composer -vvv install --no-scripts" &&\
while ! docker-compose exec mysql mysqladmin --user=root --password=root --host "127.0.0.1" ping --silent &> /dev/null ; do
    echo "Waiting for database connection..."
    sleep 2
done
echo -e "\033[1;92m Acesso Site: http://localhost\033[m"
python -m webbrowser "http://localhost" > /dev/null 2>&1
```

### 2. Desenvolvimento

#### Requisitos
- Utilizar **Postman** para testar as rotas. Documentação: [Postman Docs](https://documenter.getpostman.com/view/2284246/SVmzvcZv?version=latest#intro)
- Utilizar a biblioteca **Laravel Responder** para formatação de respostas.
- Utilizar a biblioteca **JWT 1.0.0-rc.4.1** para autenticação.

#### Implementação
1. O ambiente docker deve estar funcionando corretamente.
2. Ao abrir a collection do Postman, devem existir 4 rotas de **autenticação**, seguindo os exemplos de input/output especificados na documentação.
3. Desenvolver essas rotas para que os resultados exibidos no Postman correspondam à documentação.
4. Criar 4 rotas privadas para operações CRUD:
   - Criar um recurso
   - Listar recursos
   - Atualizar um recurso
   - Excluir um recurso

### 3. Avaliação
Os seguintes aspectos serão analisados:

- **Funcionamento do ambiente Docker**
- **Implementação correta das rotas de autenticação** conforme a documentação do Postman
- **Criação e funcionamento das rotas privadas CRUD**
- **Boa estruturação do código e uso adequado de pacotes**
- **Testes** para garantir o funcionamento das rotas e dos serviços

## Entrega

- **Código-Fonte:**
  - Um arquivo **.zip** contendo o projeto completo (excluindo binários e logs), ou
  - Um link para um repositório privado acessível com o seu trabalho (Bitbucket permite repositórios privados gratuitamente).

- **Documentação / Instruções:**
  - Um arquivo **README.md** explicando os pressupostos e decisões feitas durante a solução do problema, incluindo as escolhas de tecnologia e bibliotecas utilizadas.
  - Instruções para rodar o sistema e os testes em um ambiente Linux.

> **Nota:** Não é necessário escrever uma tese, apenas algumas linhas explicativas são suficientes. Priorize um código autodescritivo.