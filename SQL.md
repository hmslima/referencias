# Índice

* [Introdução](#intro)

	* [O básico do básico](#intro_basico)

* [Banco de dados SQL](#sql)

	* [Instalação no Windows](#sql_instWindows)

	* [Instalação no Linux](#sql_instLinux)

	* [Como iniciar o servidor](#sql_iniciar)

		* [Se você usa Windows](#sql_iniciar_windows)

		* [Se você usa Linux](#sql_iniciar_linux)

	* [Configuração de senha](#sql_configSenha)

	* [Como abrir prompt do MySQL](#sql_prompt)

	* [Configuração de usuário](#sql_configUsuario)

	* [Comandos básicos](#sql_comandosBasicos)

		* [Bancos de dados](#sql_comandosBasicos_banco)

		* [Criação de tabelas](#sql_comandosBasicos_criarTabelas)
		
		* [Inserção de dados em tabelas](#sql_comandosBasicos_inserirDadosTabelas)

		* [Comando WHERE](#sql_comandosBasicos_where)

		* [Descrição de tabelas](#sql_comandosBasicos_descreverTabelas)

		* [Atualização de tabelas](#sql_comandosBasicos_atualizarTabelas)

		* [Deleção de tabelas](#sql_comandosBasicos_deletarTabelas)

		* [Alteração de tabelas](#sql_comandosBasicos_alterarTabelas)

		* [NULL e NOT NULL](#sql_comandosBasicos_null)

		* [AUTO_INCREMENT](#sql_comandosBasicos_autoincrement)

		* [PRIMARY KEY](#sql_comandosBasicos_primarykey)

		* [Antes de prosseguirmos!](#sql_comandosBasicos_antesdeprosseguirpkjoin)

		* [FOREIGN KEY](#sql_comandosBasicos_foreignkey)

		* [Comando JOIN](#sql_comandosBasicos_join)

		* [Como saber qual é a porta](#sql_comandosBasicos_porta)
</div>

# Introdução<span id="intro"></span>

Leia o [README](README.md).

# Banco de dados SQL <span id="sql"></span>

Antes de prosseguirmos para o capítulo seguinte, precisamos entender como mexer com banco de dados SQL.

Há muitos bancos de dados que usam a linguagem SQL, como o SQL Server, PostgreSQL e MySQL, mas usaremos esse último. Não se preocupe porque como todos usam o SQL, os comandos básicos são os mesmos.

## Instalação no Windows<span id="sql_instWindows"></span>

Acesse a página [deste link](https://dev.mysql.com/downloads/windows/) e baixe a versão que lhe parecer mais conveniante. O arquivo .msi menor fará o download do MySQL durante a instalação enquanto o maior instala o software mesmo quando offline.

Fica a seu critério o que selecionar durante a instalação, mas tenha certeza de pelo menos instalar o servidor.

## Instalação no Linux<span id="sql_instLinux"></span>

Use os seguintes comandos:

    sudo apt update

    sudo apt install mysql-server

Não estranhe se você ver, em algum momento, o nome "MariaDB" em vez de "MySQL". MariaDB não é nada mais e nada menos que um [fork](https://pt.wikipedia.org/wiki/Bifurca%C3%A7%C3%A3o_(desenvolvimento_de_software)) do MySQL.

## Como inciar o servidor<span id="sql_iniciar"></span>

Para iniciar o MySQL, abra o terminal.

### Se você usa Windows<span id="sql_iniciar_windows"></span>

Abra o prompt de comando e use o comando abaixo:

    mysqld start

Caso você tenha problemas, tente o comando abaixo, mas antes observe que pode ser que o endereço seja um pouco diferente, então tenha certeza onde o `mysqld` está instalado.

    "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqld"

O `mysqld` é o MySQL Server, ele gerencia o acesso ao diretório de dados do MySQL que contém banco de dados e tabelas.

Para parar o servidor, use o comando abaixo.

    mysqld stop

De novo, se você tiver problemas, tente o comando abaixo observando o endereço:

    "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqladmin" -u root shutdown

A propósito, caso a senha já tenha sido definida, o comando será:

    "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqladmin" -u root -p shutdown

*Novamente, verifique se é esse mesmo o caminho onde se encontra as pastas e arquivos do MySQL Server.*

### Se você usa Linux<span id="sql_iniciar_linux"></span>

Há três formas de (re)inciar/parar o servidor MySQL no Linux.

Abra o terminal e use o comando abaixo:

    sudo service mysqld start

Para parar o comando é:

    sudo service mysqld stop

E para reiniciar é:

    sudo service mysqld restart

Caso seu sistema não tenha o `service`, use o comando logo abaixo para iniciar:

    sudo /etc/init.d/mysqld start

Para parar é:

    sudo /etc/init.d/mysqld stop

E para reiniciar é:

    sudo /etc/init.d/mysqld restart


E a terceira forma é por meio do `systemctl`. Para iniciar, parar e reiniciar o servidor, você usa respectivamente os comandos:

    sudo systemctl start mysqld

    sudo systemctl stop mysqld

    sudo systemctl restart mysqld

<div class="espacoEntreSubcapitulos"></div>

## Configuração de senha<span id="sql_configSenha"></span>

*Antes de começarmos, precisarei que você use uma série de comandos sobre os quais comentarei brevemente, mas não se preocupe que entrerei em detalhes sobre eles mais a frente deste capítulo.*

*Outro detalhe, se durante a instalação você já definiu a senha, esse passo não é necessário, salvo se você quiser reconfigurar a senha.*

Para realizar a (re)configuração, use o comando abaixo:

    mysql_secure_installation

*Caso você use Linux, não se esqueça de por `sudo` antes!*

A primeira pergunta é sobre se você deseja usar um plug-in que verifica a força da senha. Fica a seu critério, mas como você está apenas usando o MySQL para estudo exclusivamente em seu computador, você pode dizer que não (`n`).

> VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD component?
> 
> Press y|Y for Yes, any other key for No:

A sua próxima escolha é definir a senha do usuário `root` do MySQL:

> Please set the password for root here.

Lembre-se que se você decidiu usar o plug-in, ele dirá a força da sua senha e se ela será válida ou não.

## Como abrir prompt do MySQL<span id="sql_prompt"></span>

Se você usa Windows, procure pelo **Command Line Client** do MySQL no menu. P

ra quem usa Linux, basta abrir o terminal e usar o comando abaixo:

    mysql -u root -p

O `-u root` indica que você selecionou o usuário ***root***, já o `-p` indica que você colocará a senha do usuário.

## Configuração de usuário<span id="sql_configUsuario"></span>

No *ubuntu, por exemplo, nas versões posteriores à 5.7 do MySQL, a autenticação do usuário `root` é feita por meio do plug-in `auth_socket`, em vez de uma senha; isso grarante mais proteção, mas pode complicar para o nosso lado em que queremos acessar o banco de dados através de um programa externo como phpMyAdmin.

Abra o prompt do MySQL conforme ensinado no subcapítulo anterior.

Independentemente do seu sistema operacional, verifique o sistema de autenticação do seu usuário `root` através do comandfo abaixo:

    SELECT user,authentication_string,plugin,host FROM mysql.user;

Se em `plugin` estiver `auth_socket` para `root`, você precisa mudar para `mysql_native_password` ou `caching_sha2_password`; esse último é mais seguro que o outro, entretanto o `mysql_native_password` apresenta menos problemas com aplicativos externos. Escolha qualquer um dos dois abaixo:

    ALTER USER 'root'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'password';

    ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

*Troque a palavra `password` pela senha desejada.*

Por fim, use o comando abaixo para recarregar as tabelas de permissões:

    FLUSH PRIVILEGES;

## Comandos e conceitos básicos<span id="sql_comandosBasicos"></span>

Até agora você usou os comandos de maneira cega, agora vamos entender como usar o MySQL na prática. A boa notícia é, como você vai ver,  que é uma linguagem bem fácil de aprender, é quase como a linguagem falada *em inglês*.

### Bancos de dados<span id="sql_comandosBasicos_banco"></span>

Primeiro vamos ver os bancos de dados que temos:

    SHOW DATABASES;

Você verá algo mais ou menos assim:

```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
```

Para criar um banco de dados, use o comando `CREATE DATABASE <nome>`, vamos dizer que quero criar o banco de dados chamado "teste".

    CREATE DATABASE teste;


Se você usar o comando `SHOW DATABASES;` novamente, verá nosso novo banco de dados na lista.

Para selecionar um banco de dados, use o comando `USE`, vamos selecionar o banco de dados ***mysql***:

    USE mysql;

Para ver todas as tabelas de um banco de dados, use o comando abaixo:

    SHOW TABLES;

Você verá algo mais ou menos assim:

```
+---------------------------+
| Tables_in_mysql           |
+---------------------------+
| column_stats              |
| columns_priv              |
| db                        |
| event                     |
| func                      |
| general_log               |
| global_priv               |
| gtid_slave_pos            |
| help_category             |
| help_keyword              |
| help_relation             |
| help_topic                |
| index_stats               |
| innodb_index_stats        |
| innodb_table_stats        |
| plugin                    |
| proc                      |
| procs_priv                |
| proxies_priv              |
| roles_mapping             |
| servers                   |
| slow_log                  |
| table_stats               |
| tables_priv               |
| time_zone                 |
| time_zone_leap_second     |
| time_zone_name            |
| time_zone_transition      |
| time_zone_transition_type |
| transaction_registry      |
| user                      |
+---------------------------+
```

Ok, vamos ver o banco de dados que criamos, para trocar basta usar o comando `USE`:

    USE teste;

Se você usar o comando `SHOW TABLES;`, o sistema dirá que não há tabelas no banco de dados recém criado, o que é natural, afinal acabamos de criá-lo. 

### Criação de tabelas<span id="sql_comandosBasicos_criarTabelas"></span>

Vamos criar uma tabela:

    CREATE TABLE funcionarios (Id int, Nome varchar(255), Sobrenome varchar(255), Genero char(1), email varchar(255), Salario float(7,2));

A propósito, eu poderia escrever o comando em linhas separadas *(dando enter mesmo em cada parte, como exibido logo abaixo)*, isso porque o MySQL só percebe o fim do comando quando inserimos o ponto e vírgula(`;`).

```
CREATE TABLE funcionarios
(Id int,
Nome varchar(255),
Sobrenome varchar(255),
Genero char(1),
email varchar(255),
Salario float(7,2)
);
```

Usamos o comando `CREATE TABLE` para criar uma tabela chamada "funcionarios". Dentro de `();` colocamos as variáveis, cada uma com seu nome e seu respectivo tipo. Observe também que cada variável tem um número, ele determina a quantidade de espaço disponível para caracteres ou dígitos.

Não mostrarei todos, explicarei apenas os do exemplo que são os mais usados:

 
| **TIPO**   |      **DESCRIÇÃO**      |
|----------|:-------------:|
| **int** |  Número inteiro que pode variar de -2147483648 a 2147483647 |
| **char()** |  Caracteres de tamanho *in*variável, ou seja, se defino o tamanho como 4, só posso ter nomes como "João" ou "Iara", não como "Mariana" ou "Téo". O tamanho pode varia de 0 a 255. |
| **varchar()** |  Caracteres de tamanho variável, ou seja, posso ter "João", "Mariana", "Liana", ect. O tamanho pode varia de 0 a 65535. |
| **float(,)** |  Ponto flutuante, o primeiro parâmetro indica a quantidade total de dígitos aceitos e o segundo parâmetro indica a quantidade total de dígitas aceitas após a vírgula. O tamanho pode varia de 0 a 65535. |

Como eu havia dito, há mais formatos. Se, por exemplo, eu quisesse adicionar o texto de um blog, talvez eu precisasse de uma variável do tipo texto mais parruda como `text` ou uma de suas variações.

Pesquise por outros formatos para ver quais serão úteis para você.

### Inserção de dados em tabelas<span id="sql_comandosBasicos_inserirDadosTabelas"></span>

Vamos povoar a nossa tabela:

    INSERT INTO funcionarios (Nome, Id, Sobrenome, email, Genero, Salario) VALUES ("Marcos", 1, "Freitas", "marcos@gmail.com", "M", "3000.50");

Usei o comando `INSERT INTO` numa tabela tal para (determinadas variáveis) com os seus (respectivos valores).

Para ver o conteúdo da tabela:

    SELECT * FROM funcionarios;

De um modo geral, o asterisco normalmente `*` significa "todos", não só no SQL, como também em outros meios. Veja como o SQL é simples de entender, tente traduzir o comando acima para português:

**select** * ***from*** funcionarios = **selecione** todos ***da tabela*** funcionarios

A propósito, reparou que a ordem das variáveis que inseri não segue a ordem de apresentação da tabela. Não teve problema porque quando defini os nomes das variáveis no meu comando `INSERT INTO`, segui a mesma ordem no momento que defini os valores.

Vamos fazer uma nova inserção, mas de uma forma mais resumida.

    INSERT INTO funcionarios VALUES(2, "Mariana", "Cardoso", "F", "mariana@terra.com.br", 4000.00);

Não precisei dizer os nomes das variáveis, mas precisei seguir a ordem correta.

Voltando ao comando `INSERT`, podemos selecionar colunas em específico. Teste o comando abaixo:

    SELECT Nome, Salario FROM funcionarios;

Massa, né? Bom, agora vamos inserir uma entrada incompleta.

    INSERT INTO funcionarios (Id, Nome) VALUES (2, "Laura");

Se você usar o comando `SELECT * FROM funcionarios;`, verá o seguinte:

```
+------+---------+-----------+--------+----------------------+---------+
| Id   | Nome    | Sobrenome | Genero | email                | Salario |
+------+---------+-----------+--------+----------------------+---------+
|    1 | Marcos  | Freitas   | M      | marcos@gmail.com     | 3000.50 |
|    2 | Mariana | Cardoso   | F      | mariana@terra.com.br | 4000.00 |
|    2 | Laura   | NULL      | NULL   | NULL                 |    NULL |
+------+---------+-----------+--------+----------------------+---------+
```

### Comando WHERE<span id="sql_comandosBasicos_where"></span>

Para testar esse comando, é interessante que adicionemos mais dados à nossa tabela:

    INSERT INTO funcionarios VALUES(4, "Thiago", "Silva", "M", "thiago@bol.com.br", 5000.00);
    INSERT INTO funcionarios VALUES(5, "Tião", "Trovão", "M", "danadinha@gmail.com.br", 2000.00);
    INSERT INTO funcionarios VALUES(6, "Iara", "Schmidt", "F", "schmidt@gmail.com.br", 4500.00);

A tabela ficou assim:

    +------+---------+-----------+--------+------------------------+---------+
    | Id   | Nome    | Sobrenome | Genero | email                  | Salario |
    +------+---------+-----------+--------+------------------------+---------+
    |    1 | Marcos  | Freitas   | M      | marcos@gmail.com       | 3000.50 |
    |    2 | Mariana | Cardoso   | F      | mariana@terra.com.br   | 4000.00 |
    |    2 | Laura   | NULL      | NULL   | NULL                   |    NULL |
    |    4 | Thiago  | Silva     | M      | thiago@bol.com.br      | 5000.00 |
    |    5 | Tião    | Trovão    | M      | danadinha@gmail.com.br | 2000.00 |
    |    6 | Iara    | Schmidt   | F      | schmidt@gmail.com.br   | 4500.00 |
    +------+---------+-----------+--------+------------------------+---------+

Vamos dizer que queremos listar apenas os funcionários do sexo feminino:

    SELECT * FROM funcionarios WHERE Genero="F";

Selecione todas as colunas de `funcionarios` onde `Genero` é igual a "F". Neste caso, Laura não aparecerá porque o Genero dela está como `NULL`. Veremos mais sobre `Null` adiante.

Outro exemplo:

    SELECT * FROM funcionarios WHERE Genero="M" AND Salario >= 3000;

Selecione todas as colunas de `funcionarios` onde `Genero` é igual a "M" e Salario seja igual ou maior que 3000.

### Descrição de tabelas<span id="sql_comandosBasicos_descreverTabelas"></span>

Para verificar a descrição ténica de uma tabela, use o comando `DESCRIBE`:

    DESCRIBE funcionarios;

Resultado:

    +-----------+--------------+------+-----+---------+-------+
    | Field     | Type         | Null | Key | Default | Extra |
    +-----------+--------------+------+-----+---------+-------+
    | Id        | int(11)      | YES  |     | NULL    |       |
    | Nome      | varchar(255) | YES  |     | NULL    |       |
    | Sobrenome | varchar(255) | YES  |     | NULL    |       |
    | Genero    | char(1)      | YES  |     | NULL    |       |
    | email     | varchar(255) | YES  |     | NULL    |       |
    | Salario   | float(7,2)   | YES  |     | NULL    |       |
    +-----------+--------------+------+-----+---------+-------+

### Atualização de tabelas<span id="sql_comandosBasicos_atualizarTabelas"></span>

Além da tabela possuir valores nulos, a contagem do Id está errada, era para Laura ter o `Id` 3, mas a falta de configurações permitiu que um erro como esse ocorresse. Na verdade, é chato ficar definindo esse Id na mão... Mas vamos tentar corrigir os dados de Laura.

A estrutura do comando para atualizar uma tabela é o seguinte:

    UPDATE <nome_da_tabela>
    SET <coluna1> = <valor1>, <coluna2> = <valor2>, ...
    WHERE <condição>;

Vejamos o comando em ação:

    UPDATE funcionarios SET Id=3, Sobrenome="Ferreira", Genero="F", email="laura@hotmail.com", Salario=2500.00 WHERE Nome="Laura";

Atualize a tabela `funcionario` definindo a coluna `Id` para 3, a coluna `Sobrenome` para "Ferreira" e a coluna `Genero` para "F" na(s) linha(s) onde a coluna `Nome` tem o valor "Laura".

### Deleção de tabelas<span id="sql_comandosBasicos_deletarTabelas"></span>

Nós poderíamos deletar a tabela `funcionarios` com o comando abaixo...

    DROP TABLE funcionarios; 

...e simplesmente criar uma nova. Mas e se a tabela que estivéssemos lidando já estivesse sendo usada em produção com centenas, milhares ou milhões de dados? Recriar tudo do zero não seria viável.

### Alteração de tabelas<span id="sql_comandosBasicos_alterarTabelas"></span>

#### Como adicionar uma coluna:

    ALTER TABLE <nome_da_tabela>
    ADD <nome_da_coluna> <tipo_da_coluna>; 

#### Como deletar uma coluna:

    ALTER TABLE <nome_da_tabela>
    DROP COLUMN <nome_da_coluna>;

#### Como modificar uma coluna:

Esse requer um pouco mais de atenção, pois o comando variará a depender to tipo de banco de dados e sua versão:

**SQL / MySQL/Oracle 10G ou versões mais novas**

    ALTER TABLE <nome_da_tabela>
    MODIFY <nome_da_coluna> <tipo_da_coluna>;

Tentaremos modificar a tabela, vamos começar com o `Id`.

**Versões do MySQL/Oracle antes da versão 10G**

    ALTER TABLE <nome_da_tabela>
    MODIFY COLUMN <nome_da_coluna> <tipo_da_coluna>;

**SQL Server / Microsoft Access**

    ALTER TABLE <nome_da_tabela>
    ALTER COLUMN <nome_da_coluna> <tipo_da_coluna>; 

#### Mão na massa!

*Olha, vou adicionar uma enxurrada de novos conceitos aqui que só explicarei nos próximos capítulos, então não se preocupe porque explicarei tudo.*

O nome e o tipo do Id está correto, mas queremos adicionar uma característica a mais *(duas, na verdade)*. Mas antes precisamos criar duas novas colunas:

    ALTER TABLE funcionarios ADD Departamento varchar(255) NOT NULL;
    ALTER TABLE funcionarios ADD PRIMARY KEY (Id);

*De novo, explicarei o que é esse `ADD PRIMARY KEY (Id)` mais para frente. E adicionei essa coluna Departamento meramente por uma questão de organização*

Agora a alteração da coluna Id.

    ALTER TABLE funcionarios MODIFY Id int NOT NULL AUTO_INCREMENT;

Para o resto, apenas adicionaremos a restrição `NOT NULL`.

    ALTER TABLE funcionarios MODIFY Nome varchar(255) NOT NULL;
    ALTER TABLE funcionarios MODIFY Sobrenome varchar(255) NOT NULL;
    ALTER TABLE funcionarios MODIFY Genero char(1) NOT NULL;
    ALTER TABLE funcionarios MODIFY email varchar(255) NOT NULL;
    ALTER TABLE funcionarios MODIFY Salario float(7,2) NOT NULL;

Todas as alterações que queríamos fazer já foram realizadas. Se fossemos recriar essa tabela com essas novas atribuições, o comando seria assim:

```
CREATE TABLE funcionarios
(Id int NOT NULL AUTO_INCREMENT,
Nome varchar(255) NOT NULL,
Sobrenome varchar(255) NOT NULL,
Genero char(1) NOT NULL,
email varchar(255) NOT NULL,
Salario float(7,2) NOT NULL,
Departamento varchar(255) NOT NULL,
PRIMARY KEY (Id)
);
```

### NULL e NOT NULL<span id="sql_comandosBasicos_null"></span>

Por padrão, as colunas podem não receber nenhum valor, ficando como `NULL`. Mas normalmente queremos que, ao adicionar novos dados, nenhuma coluna fique vazia, então adicionamos a restrição `NOT NULL` que obriga a adição de dados naquela nova linha da coluna.

O `NOT NULL` indica que você não pode adicionar uma entrada na tabela sem definir um valor para aquela variável em específico.

### AUTO_INCREMENT<span id="sql_comandosBasicos_autoincrement"></span>

O `AUTO_INCREMENT` indica que um valor será somado a cada adição sem que precisamos fazer isso manualmente. Veja só:

    INSERT INTO funcionarios (Nome, Id, Sobrenome, email, Genero, Salario, Departamento) VALUES ("Marcos", Null, "Freitas", "marcos@gmail.com", "M", "3000.50", "Financeiro");

Pude definir o **Id** como *Null* porque a tabela tem a função de auto incrementar os valores. 

### PRIMARY KEY<span id="sql_comandosBasicos_primarykey"></span>

A **PRIMARY KEY ()** define que o valor a que ela se refere *(no caso, Id)* tenha sempre um valor único. Esse recurso é normalmente usado com IDs.

#### MySQL

```
CREATE TABLE funcionarios
(Id int NOT NULL AUTO_INCREMENT,
Nome varchar(255) NOT NULL,
Sobrenome varchar(255) NOT NULL,
Genero char(1) NOT NULL,
email varchar(255) NOT NULL,
Salario float(7,2) NOT NULL,
Departamento varchar(255) NOT NULL,
PRIMARY KEY (Id)
);
```

#### SQL Server, Microsoft Access, Oracle

```
CREATE TABLE funcionarios
(Id int NOT NULL PRIMARY KEY AUTO_INCREMENT,
Nome varchar(255) NOT NULL,
Sobrenome varchar(255) NOT NULL,
Genero char(1) NOT NULL,
email varchar(255) NOT NULL,
Salario float(7,2) NOT NULL,
Departamento varchar(255) NOT NULL,
);
```

<div class="espacoEntreSubcapitulos"></div>

### Antes de prosseguirmos!<span id="sql_comandosBasicos_antesdeprosseguirpkjoin"></span>

Para prosseguirmos, vamos completar nossa tabela, insira os seguintes dados:

    INSERT INTO funcionarios VALUES(Null, "Mariana", "Cardoso", "F", "mariana@terra.com.br", 4000.00, "Financeiro");
    INSERT INTO funcionarios VALUES(Null, "Thiago", "Silva", "M", "thiago@terra.com.br", 1500.00, "TI");
    INSERT INTO funcionarios VALUES(Null, "Tião", "Trovão", "M", "danadinha@gmail.com.br", 2000.00, "TI");
    INSERT INTO funcionarios VALUES(Null, "Iara", "Schmidt", "F", "schmidt@gmail.com.br", 4500.00, "Financeiro");
    INSERT INTO funcionarios VALUES(Null, "Patrícia", "Oliveira", "F", "patioliveira@gmail.com.br", 8000.00, "Financeiro");
    INSERT INTO funcionarios VALUES(Null, "Railton", "Carneiro", "M", "rai@hotmail.com.br", 3000.00, "TI");
    INSERT INTO funcionarios VALUES(Null, "Pedro", "dos Santos", "M", "pedrao@hotmail.com.br", 12000.00, "TI");


### FOREIGN KEY<span id="sql_comandosBasicos_foreignkey"></span>

Uma FOREIGN KEY nada mais nada menos que um meio de garantir que o valor referenciado por uma tabela realmente exista na outra.

A declaração pode varia a depender do sistema de banco de dados:

#### MySQL

```
CREATE TABLE Ordens (
    OrdemID int NOT NULL AUTO_INCREMENT,
    OrdemNumero int NOT NULL,
    FuncionarioID int,
    PRIMARY KEY (OrdemID),
    FOREIGN KEY (FuncionarioID) REFERENCES funcionarios(Id)
);
```

#### SQL Server / Oracle / Microsoft Access

```
CREATE TABLE Ordens (
    OrdemID int NOT NULL PRIMARY KEY AUTO_INCREMENT,
    OrdemNumero int NOT NULL,
    FuncionarioID int FOREIGN KEY REFERENCES funcionarios(Id)
);
```

#### Continuando com nossas tabelas

Vamos criar uma nova tabela para testar o chaves estrangeiras:

```
CREATE TABLE Ordens (
    OrdemID int NOT NULL AUTO_INCREMENT,
    OrdemNumero int NOT NULL,
    FuncionarioID int,
    PRIMARY KEY (OrdemID),
    FOREIGN KEY (FuncionarioID) REFERENCES funcionarios(Id)
);
```

Os itens de Ordens:

    INSERT INTO Ordens VALUES(Null, 1523, 2);
    INSERT INTO Ordens VALUES(Null, 5004, 2);
    INSERT INTO Ordens VALUES(Null, 8002, 4);
    INSERT INTO Ordens VALUES(Null, 6066, 1);
    INSERT INTO Ordens VALUES(Null, 1000, 3);

Aqui eu tenho a certeza que `FuncionarioID` de **Ordens** sempre referenciará a uma `Id` de **funcionarios** que realmente exista.

### Comando JOIN<span id="sql_comandosBasicos_join"></span>

Vamos criar uma nova tabela para testar o comando JOIN.

```
CREATE TABLE extra
(Nome varchar(255),
Endereco varchar(300),
Idade int,
EstadoCivil varchar(50)
);
```

Os itens de extra:

    INSERT INTO extra VALUES("Marcos", "Rua B, 1104, Pinheiros", 32, "Casado");
    INSERT INTO extra VALUES("Mariana", "Rua B, 1104, Pinheiros", 28, "Casado");
    INSERT INTO extra VALUES("Thiago", "Rua Augusta, 256, Centro", 25, "Solteiro");
    INSERT INTO extra VALUES("Tião", "Rua dos Chanéis, 581, Indianópolis", 50, "Solteiro");
    INSERT INTO extra VALUES("Iara", "Rua América, 512, Torres", 42, "Solteiro");
    INSERT INTO extra VALUES("Lourival", "Rua Rio de Janeiro, 12, ----", 28, "Casado");
    INSERT INTO extra VALUES("Taiara", "Rua Augusta, 208, Centro", 21, "Solteiro");

Através do comando `JOIN`, podemos cruzar os dados de duas tabelas:

    SELECT extra.Nome, extra.Endereco, extra.Idade, extra.EstadoCivil
    FROM extra JOIN funcionarios
    ON funcionarios.Nome = extra.Nome;

Eis o resultado:
```
+---------+--------------------------------------+-------+-------------+
| Nome    | Endereco                             | Idade | EstadoCivil |
+---------+--------------------------------------+-------+-------------+
| Marcos  | Rua B, 1104, Pinheiros               |    32 | Casado      |
| Mariana | Rua B, 1104, Pinheiros               |    28 | Casado      |
| Thiago  | Rua Augusta, 256, Centro             |    25 | Solteiro    |
| Tião    | Rua dos Chanéis, 581, Indianópolis   |    50 | Solteiro    |
| Iara    | Rua América, 512, Torres             |    42 | Solteiro    |
+---------+--------------------------------------+-------+-------------+
```
Apenas 5 pessoas foram retornadas porque só há esses 5 em comum. A propósito, eu poderia escrever o comando desta forma também:
```
SELECT e.Nome, e.Endereco, e.Idade, e.EstadoCivil
FROM extra e JOIN funcionarios f
ON f.Nome = e.Nome;
```

Se eu quisesse incluir todos os itens da primeira tabela, eu usaria `LEFT JOIN`:

```
SELECT e.Nome, e.Endereco, e.Idade, e.EstadoCivil
FROM extra e LEFT JOIN funcionarios f
ON f.Nome = e.Nome;
```

### Como saber qual é a porta<span id="sql_comandosBasicos_porta"></span>

Use o comando abaixo:

    SHOW GLOBAL VARIABLES LIKE 'PORT';

<div class="espacoEntreCapitulos"></div>






</div> <!-- Fim do container -->