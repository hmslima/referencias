**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [PostgreSQL](#postgres)

	* [Instalação](#postgres_install)

	* [Inicialização](#postgres_start)

		* [Linux](#postgres_start_linux)

	* [Comparação entre MySQL e PostgreSQL](#postgres_mysql)

	* [Usuários](#postgres_users)

		* [Criação de usuários](#postgres_users_create)

		* [Lista de usuários](#postgres_users_list)

		* [Permissões dos usuários](#postgres_users_permissions)

	* [Criação de banco de dados](#postgres_db)

	* [Conexão com o Spring](#postgres_springconnection)

# Introdução<span id="intro"></span>

Leia o [README](README.md).

Este documento é só um complemento para [SQL.md](SQL.md), apenas para criar referências para o banco de dados PostgreSQL.

# PostgreSQL<span id="postgres"></span>

## Instalação<span id="postgres_install"></span>

Durante a instalação, tenha o cuidado de instalar também o "PostgreSQL Server", que no Linux se traduz em qualquer coisa com o sufixo `-server`.

Instale também o `pgadmin` *(tenha certeza de instalar também a versão web via `phpPgAdmin`)*

## Inicialização <span id="postgres_start"></span>

### Linux <span id="postgres_start_linux"></span>

    systemctl start postgresql

<span style="color: red;">*Se você quiser que o PostgreSQL inicie no boot do sistema*</span>

    systemctl enable postgresql

Caso você tenha acabado de instalar o PostgreSQL, você vai precisar criar um usuário.

<span style="color:red;">Olha, se você vai usar o banco de dados apena spara testes, talvez seja interessante que você veja o capítulo [Conexão com o Spring](#postgres_springconnection).</span>

Primeiro mude para o usuário `postgres`

    sudo su postgres

Entre no terminal do PostgreSQL:

    psql

Para criar usuário sem senha:

    CREATE ROLE <usuário> jonathan LOGIN;

Para criar usuário com senha senha:

    CREATE USER <usuário> WITH PASSWORD '<senha>';

`CREATE ROLE` e `CREATE USER` são a mesma coisa, a diferença é que `CREATE USER` implica a adição de uma senha

OK, vamos criar o usuário que pode gerenciar bancos de dados:

<span style="color: red;">*Repare que no comando abaixo eu não coloquei o nome do usuário, isso é porque é interessante que você ponha o mesmo nome do usuário do sistema operacional que você está usando*</span>

    CREATE USER <nome_do_usuario> WITH PASSWORD '12345' CREATEDB;

Para sair do terminal do PostgreSQL, você pode usar este comando:

    \q

Para acessar o terminal do PostgreSQL com o recém criado usuário, use o comando abaixo, mas reparre que você terá que informar um banco de dados existente. 

    psql -U <nome_do_usuario> -d postgres

...não funcionará porque eu ou precisaria já está conectado como o usuário *(ususário do sistema operacional mesmo)* `admin` ou eu deveria mexer nas configurações do PostgreSQL.

Para saber qual é a porta usara pelo PostgreSQL:

    SHOW port;

### pgadmin modo web <span id="postgres_start_pgadminweb"></span>

Acesse a página [http://localhost:61886/browser](http://localhost:61886/browser)

## Comparação entre MySQL e PostgreSQL<span id="postgres_mysql"></span>

| MySQL           | PostgreSQL  |
| --------------- | ----------- |
| show databases; | \l          |
| show tables;    | \dt         |
| use database;   | \c database |
| exit;           | \q          |

## Usuários<span id="postgres_users"></span>

### Criação de usuários<span id="postgres_users_create"></span>

Já ensinei como criar usuários, isto aqui é só uma recapitulação. Bom, se certifique de usar um usuário com permissão para criar outros usuários:

Para criar usuário sem senha:

    CREATE ROLE <usuário> jonathan LOGIN;

Para criar usuário com senha senha:

    CREATE USER <usuário> WITH PASSWORD '<senha>';

`CREATE ROLE` e `CREATE USER` são a mesma coisa, a diferença é que `CREATE USER` implica a adição de uma senha

Para criar usuário com senha senha e com uma permissão já definida:

    CREATE USER <usuário> WITH PASSWORD '<senha>' <permissão>;

Exemplo:

    CREATE USER thiago WITH PASSWORD '12345' CREATEDB;

### Lista de usuários<span id="postgres_users_list"></span>

    SELECT * FROM pg_user;

### Permissões usuários<span id="postgres_users_permissions"></span>

Para listar as permissões atuais dos usuários:

    \du

Para alterar as permissões:

    ALTER USER <usuário> WITH OPTION1 OPTION2 OPTION3;

Algumas dessas opções podem ser `CREATEDB`, `CREATEROLE`, `CREATEUSER`, e até mesmo `SUPERUSER`.

Exemplo:

    ALTER USER mariana WITH CREATEDB;


## Criação de banco de dados<span id="postgres_db"></span>

Vamos dizer que quero criar o banco de dados `estudo`:

    CREATE DATABASE estudo;
    \c estudo

## Conexão com o Spring<span id="postgres_springconnection"></span>

Tive problemas para conectar o banco de dados com o Spring por conta do sistema de autenticação do PostgreSQL.

Para resolver o problema, acesse o usuário do PostgreSQL

    sudo su postgres

Então se dirija para a o arquivo `data/`

    cd data
    nano pg_hba.conf

Se por um acaso, você permanecer na pasta do usuário comum, você precisará pesquisar a localização da pasta do Postgres, no caso do openSUSE é `/var/lib/pgsql/`

Afora vejamos o arquivo `pg_hba.conf`. Mude de...

    # TYPE  DATABASE        USER            ADDRESS                 METHOD
    
    # "local" is for Unix domain socket connections only
    local   all             all                                     peer
    # IPv4 local connections:
    host    all             all             127.0.0.1/32            ident
    # IPv6 local connections:
    host    all             all             ::1/128                 ident

...para:

    # TYPE  DATABASE        USER            ADDRESS                 METHOD
    
    # "local" is for Unix domain socket connections only
    local   all             all                                     password
    # IPv4 local connections:
    host    all             all             127.0.0.1/32            password
    # IPv6 local connections:
    host    all             all             ::1/128                 password

<span style="color: red;">**Não se esqueça de reiniciar o servidor!**</span>

No arquivo `application.properties`, na parte de URL, você referencia o PostgreSQL desse jeito:

    spring.datasource.url=jdbc:postgresql://localhost:5432/teste

No caso da linha acima, estaríamos usando um banco de dados de nome `teste` que estaria rodando na porta 5432.