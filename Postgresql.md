**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [PostgreSQL](#postgres)

	* [Instalação](#postgres_install)

	* [Inicialização](#postgres_start)

		* [Se você usa Linux](#postgres_start_linux)
		
		* [Se você usa Windows](#postgres_start_windows)

		* [Continuando...](#postgres_start_cont)

		* [pgadmin modo web](#postgres_start_pgadminweb)

	* [Comparação entre MySQL e PostgreSQL](#postgres_mysql)

	* [Usuários](#postgres_users)

		* [Criação de usuários](#postgres_users_create)

			* [Pelo terminal](#postgres_users_create_term)

			* [Pelo pgAdmin](#postgres_users_create_pgadmin)

		* [Lista de usuários](#postgres_users_list)

		* [Permissões dos usuários](#postgres_users_permissions)

	* [Criação de banco de dados](#postgres_db)

	* [Execução de arquivos .sql](#postgres_runfile)

	* [Conexão com o Spring](#postgres_springconnection)

# Introdução<span id="intro"></span>

Leia o [README](README.md).

Este documento é só um complemento para [SQL.md](SQL.md), apenas para criar referências para o banco de dados PostgreSQL.

# PostgreSQL<span id="postgres"></span>

## Instalação<span id="postgres_install"></span>

Durante a instalação, tenha o cuidado de instalar também o "PostgreSQL Server", que no Linux se traduz em qualquer coisa com o sufixo `-server`.

Instale também o `pgadmin` *(tenha certeza de instalar também a versão web via `phpPgAdmin`)*

## Inicialização <span id="postgres_start"></span>

### Se você usa Linux<span id="postgres_start_linux"></span>

    systemctl start postgresql

<span style="color: red;">*Se você quiser que o PostgreSQL inicie no boot do sistema*</span>

    systemctl enable postgresql

Caso você tenha acabado de instalar o PostgreSQL, você vai precisar criar um usuário.

Primeiro mude para o usuário `postgres`

    sudo su postgres

Entre no terminal do PostgreSQL:

    psql

Ou você poderia simplesmente usar o comando:

    psql -U postgres -d postgres

### Se você usa Windows<span id="postgres_start_windows"></span>

*Me referirei ao prompt de comando e Powershell como "terminal"*

No Windows, acho mais interessante fazermos tudo pelo pgAdmin *(que seria o equivalente do Workbench)*, <span style="color: red;">ESPECIALMENTE PORQUE O TERMINAL DO WINDOWS CORREMPE CARACTERES ESPECIAIS ADICIONADOS AO BANCO DE DADOS</span>.

Verifique antes se o PostgreSQL foi adicionado ao PATH do Windows. Antes de continuarmos, vamos convencionar que `#` representa a pasta onde o PostgreSQL foi instalado no Windows; por exemplo, se a pasta de instalação do meu PostgreSQL foi `C:\Program Files\PostgreSQL\14` *(no caso, foi a versão 14)*, então `#\data"` significaria `C:\Program Files\PostgreSQL\14\data"`.

OK, voltando ao PATH, tenha certeza de que a pasta `#\bin"` estja no PATH do sistema. Para testar se tudo está OK, tente rodar o comando abaixo no terminal:

    pg_ctl --version

Se você conseguir ver a versão do seu PostgreSQL, significa que está tudo funcionando OK.

Também, ainda na parte de variáveis do sistema, mas sem ser `Path` adicione a variável `PGDATA` com o valor `#\data"`, assim poderemos usar o comando `postgres`. Veja se o comando abaixo funciona:

    postgres

Para o primeiro acesso, use o comando abaixo:

    psql -U postgres -d postgres

### Continuando...<span id="postgres_start_cont"></span>

**Tenha isso em mente:** para acessar o PostgreSQL, você precisa também informar o banco de dados, não é como o MySQL em que você pode acessar o banco de dados depois, por isso que usamos o parâmetro `-d <banco_de_dados>`.

<span style="color:red;">Olha, se você vai usar o banco de dados apena spara testes, talvez seja interessante que você veja o capítulo [Conexão com o Spring](#postgres_springconnection).</span>

Vá até o capítulo [Criação de usuários](#postgres_users_create) e depois volte aqui. Fique sabendo que é importante que o usuário que você criará tenha o mesmo nome do usuário do sistema operacional onde o PostgreSQL está instalado! Por exemplo, se o nome de usuário do sistema operacional é `camila`, então o nome de usuário que você criará no PostgreSQL também tem que ser `camila`. Estamos entendidos?

Para sair do terminal do PostgreSQL, você pode usar este comando:

    \q

Para acessar o terminal do PostgreSQL com o recém criado usuário, use o comando abaixo, mas reparre que você terá que informar um banco de dados existente. 

    psql -U <nome_do_usuario> -d postgres

...não funcionará porque eu ou precisaria já está conectado como o usuário *(ususário do sistema operacional mesmo)* `admin` ou eu deveria mexer nas configurações do PostgreSQL.

Para saber qual é a porta usara pelo PostgreSQL:

    SHOW port;

### pgadmin modo web<span id="postgres_start_pgadminweb"></span>

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

#### Pelo terminal<span id="postgres_users_create_term"></span>

Para criar usuário sem senha:

    CREATE ROLE <usuário> jonathan LOGIN;

Para criar usuário com senha senha:

    CREATE USER <usuário> WITH PASSWORD '<senha>';

`CREATE ROLE` e `CREATE USER` são a mesma coisa, a diferença é que `CREATE USER` implica a adição de uma senha

Para criar usuário com senha senha e com uma permissão já definida:

    CREATE USER <usuário> WITH PASSWORD '<senha>' <permissão>;

Exemplo:

    CREATE USER thiago WITH PASSWORD '12345' CREATEDB;

#### Pelo pgAdmin<span id="postgres_users_create_pgadmin"></span>

Entrando no pgAdmin, lhe será pedido senha do usuário principal *(você definiu a senha no momento da instalação)*, haverá um painel no lado esquerdo, onde você verá o item `Servers`. Expandindo-o, você verá o nome PostgreSQL mais o número da versão do mesmo, dentro deste haverá o item `Login/Group Roles`, clique com o botão direito do mouse sobre ele e selecione `Create` => `Login/Group Role`.

O resto não exige muita explicação, só não se esqueça do que falei de pôr o mesmo nome do usuário do sistema operacional e na aba `Privileges` selecione tudo.

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

## Execução de arquivos .sql<span id="postgres_runfile"></span>

É bem simples:

    psql -h host -p port -d dbname -U username -f datafile.sql

## Conexão com o Spring<span id="postgres_springconnection"></span>

Tive problemas para conectar o banco de dados com o Spring por conta do sistema de autenticação do PostgreSQL.

Para resolver o problema, precisamos editar o arquivo `pg_hba.conf` que fica na pasta `data`.

No Linux, você pode tentar acessa o usuário do PostgreSQL...

    sudo su postgres

...para então se dirijir diretamente ao arquivo.

    cd data
    nano pg_hba.conf

Se por um acaso, você permanecer na pasta do usuário comum, você precisará pesquisar a localização da pasta do Postgres, no caso do openSUSE é `/var/lib/pgsql/`

No Windows, é mais fácil, é só ir na pasta de instalação do PostreSQL e procurar a pasta `data` *(o que não é difícil, na verdade você a configurou nas variáveis do sistema no início deste tutorial)*.

Agora vejamos o arquivo `pg_hba.conf`. Mude de...

    # TYPE  DATABASE        USER            ADDRESS                 METHOD
    
    # "local" is for Unix domain socket connections only
    local   all             all                                     peer
    # IPv4 local connections:
    host    all             all             127.0.0.1/32            ident
    # IPv6 local connections:
    host    all             all             ::1/128                 ident

*<span style="font-size: 0.8rem;">No Windows, em vez de `peer` e `ident`, pode ser que esteja `scram-sha-256` no lugar. Altere da mesma forma.</span>*

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