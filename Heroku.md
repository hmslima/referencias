**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [Heroku](#heroku)

	* [Instalação](#heroku_install)
	
	* [Configuração](#heroku_config)

	* [Banco de dados](#heroku_db)

# Introdução<span id="intro"></span>

Leia o [README](README.md).

# Heroku<span id="heroku"></span>

## Instalação<span id="heroku_install"></span>

Você precisa de duas coisas instaladas:

* Git

* [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)

## Configuração<span id="heroku_config"></span>

Na pasta do projeto a ser enviado, use o Git:

    git init
    git add .
    git commit -am "Envio"

Então você usa o Heroku:

    heroku login

<span></span>

Crie sua aplicação lá agora:

    heroku create <nome_da_aplicação>

*Aqui o próprio Heroku adiciona o repositório dele no meu Git*

Agora vincularemos o banco de dados à nossa aplicação:

    heroku addons:create heroku-postgresql:hobby-dev

Voltamos ao Git para enviar o código fonte pra lá:

    git push heroku master

Para abrir a aplicação, digite:

    heroku open

## Banco de dados<span id="heroku_db"></span>

No Heroku, entre na página do seu projeto, vá em `Settings` => `Reveal Config Vars`. Terá apenas a variável referente à URL, copie o conteúdo para um editor de textos. Vamos dizer que o conteúdo é este:

    postgres://jggfeabhnmgfas:efd77062274d012087fe8298ad920e8d87ac36cfs4f6b30f42ea69465163ac7f@ec2-53-2-2-245.compute-1.amazonaws.com:5432/daiih46kfqaxqn

Nesse caso, seu usuário será:

    jggfeabhnmgfas

A senha será:

    efd77062274d012087fe8298ad920e8d87ac36cfs4f6b30f42ea69465163ac7f

O servidor *(host)* será:

    ec2-53-2-2-245.compute-1.amazonaws.com

A porta será:

    5432

O banco de dados será:

    daiih46kfqaxqn

Olha que massa, podemos executar um arquivo SQL através do comando:

    psql -h host -p port -d dbname -U username -f datafile.sql

Que transportando para o nosso exemplo seria 

    psql -h ec2-53-2-2-245.compute-1.amazonaws.com -p 5432 -d daiih46kfqaxqn -U jggfeabhnmgfas -f datafile.sql

*Estamos assumindo aqui que o nome do arquivo SQL é `datafile.sql`*

Agora podemos criar nossas variáveis, no contexto de uma configuração de banco de dados Spring Boot, posso criar as seguintes variáveis

`JDBC_DATABASE_URL` = `jdbc:postgres://ec2-53-2-2-245.compute-1.amazonaws.com:5432/daiih46kfqaxqn`

`JDBC_DATABASE_USER` = `jggfeabhnmgfas`

`JDBC_DATABASE_PASSWORD` = `efd77062274d012087fe8298ad920e8d87ac36cfs4f6b30f42ea69465163ac7f`

Num arquivo .properties para Spring, ficaria assim:

    spring.datasource.url=${JDBC_DATABASE_URL}
    spring.datasource.user=${JDBC_DATABASE_USER}
    spring.datasource.password=${JDBC_DATABASE_PASSWORD}

Para o banco de dados, o Heroku já nos fornece uma variável, usarei o *property* do Spring Boot como exemplo:

    spring.datasource.url=${JDBC_DATASOURCE_URL}

Esse `${JDBC_DATASOURCE_URL}` já contém, além da URL, o usuário e senha.

Para adicionar dados, podemos usar o Postman

