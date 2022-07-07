**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [MongoDB](#mongodb)

	* [Instalação e configuração](#mongodb_installconf)

		* [Windows](#mongodb_installconf_win)

	* [Porta padrão](#mongodb_port)

	* [Start](#mongodb_start)

	* [Comandos básicos](#mongodb_basic)

		* [Uso na prática](#mongodb_basic_test)

	* [Drivers](#mongodb_drivers)

# Introdução<span id="intro"></span>

Leia o [README](README.md).

Para eu não ter que me repetir, sugiro que você estude [SQL.md](SQL.md) antes. Sim, é outro tipo de banco de dados, mas ainda assim poupará nosso tempo na apresentação do MongoDB.

# MongoDB<span id="mongodb"></span>

## Instalação e configuração<span id="mongodb_installconf"></span>

Baixe o MongoDB [neste endereço](https://www.mongodb.com/try/download/community).

### Windows<span id="mongodb_installconf_win"></span>

Baixe a versão ZIP e extraia o conteúdo no local definitivo *(sugiro fortemente que seja num endereço de pasta que não tenha espaços, então evite por em `*\Arquivos de programas\*`)*. Também crie uma pasta onde serão armazenados os dados, algo como `mongodb-data` ou somente `data`.

Na primeira execução, rode o comando abaixo, em que `~` é o local onde a pasta do MongoDB e a pasta de dados do mesmo se encontram, no caso aqui deixei a pasta `data` dentro da pasta de instalação do MongoDB.

    ~\bin\mongod.exe --dbpath=~\data

O servidor estará iniciado. Não feche ou encerro o processo do terminal a não ser que você não queira mais mexer com o MongoDB.

Para facilitar a sua vida, adicione a pasta `~\bin\` nas variáveis do sistema.

## Porta padrão<span id="mongodb_port"></span>

A porta padrão do MongoDB é 27017

## Start<span id="mongodb_start"></span>

Deixe o terminal ou prompt de comando que você iniciou o servidor intacto. Abra **outro** terminal que será onde você iniciará o shell do MongoDB.

Para dar o start, use o comando abaixo:

    mongo --host <hostname> --port <port>

Ou simplesmente

    mongo

## Comandos básicos<span id="mongodb_basic"></span>

    db.version()

Retorna a versão do MongoDB.

    db

Mostra seu banco de dados atual

    db.dropDatabase()

Deleta o banco de dados selecionado

    db.help

Bom, mostra a ajuda

    show dbs

Exibe todos os bancos de dados

    use <nome_do_banco_de_dados>

Cria um banco de dados

    db.createCollection('<nome_da_coleção>')

Cria uma coleção, que seria o equivalente a uma tabela de um banco de dados relacional

    show collections

Exibe todas as coleções

    db.<nome_da_coleção>.drop()

Deleta a coleção

    db.<nome_da_coleção>.insert({documento})

Insere documento na coleção, que seria o equivalente a inserir uma linha numa tabela de um banco de dados relacional.

    db.<nome_da_coleção>.insertMany([{documento1}, {documento2}, {documento3}, ...],
    {
          writeConcern: <document>,
          ordered: <boolean>
    })

Insere mais de uma coleção. Se você quiser, pode escrever apenas `db.<nome_da_coleção>.insertMany([{documento1}, {documento2}, {documento3}, ...])`, o restante é opcional; `writeConcern` é usado quando não queremos usar o *write concern* padrão, enquanto `ordered` especifica se o MongoDB inserirá os documentos de forma ordenada ou não, por padrão é *true*.

    db.<nome_da_coleção>.update(<critério_de_seleção>, <dados_atualizados>)

Atualiza um documento

    db.<nome_da_coleção>.save({_id:ObjectId(),<novos_dados>})

Salva um documento. A diferença entre `.save` e `.insert` é que `.save` insere ou atualiza um documento enquanto `.insert` faz apenas a ação de inserir.

    db.<nome_da_coleção>.remove(<critério_de_deleção>)

Deleta um documento

    db.<nome_da_coleção>.find()

Mostra os elementos de uma coleção

    db.<nome_da_coleção>.find().pretty()

Mostra os elementos de uma coleção de forma mais bonitinha

    exit

Sai do shell do MongoDB

### Uso na prática<span id="mongodb_basic_test"></span>

    show dbs

Só para vermos o que temos num primeiro momento

    use bancoteste

Criamos – ou mudamos para – o banco de dados chamado `bancoteste`

    db.createCollection("estudante")

Criamos uma coleção chamada `estudante`

A partir de agora inseriremos alguns dados na nossa coleção:

    db.estudante.insert({nome: "João", idade: 14})

<span></span>

    db.estudante.insert({nome: "Maria", idade: 13})

<span></span>

    db.estudante.insertMany([{nome: "Tereza", idade: 15},
    {nome: "Laércio", idade: 14},
    {nome: "Thiago", idade: 14},
    {nome: "Fernanda", idade: 14},
    {nome: "Renata", idade: 13}])

<span></span>

    db.estudante.insertMany([{nome: "Marcela", idade: 13},
    {nome: "Geraldo", idade: 15},
    {nome: "Bianca", idade: 14},
    {nome: "Suzane", idade: 14},
    {nome: "Murilo", idade: 14}],
    {
        ordered: false
    })

Agora podemos visualizar nossos dados:

    db.estudante.find()

Se quisermos ver com um visual mais bonito:

    db.estudante.find().pretty()

Se quisermos ver só quem tem 13 anos:

    db.estudante.find({idade:13})

Se quisermos ver só quem tem idade superior a 13 anos:

    db.estudante.find({idade: {$gt:13}})

## Drivers<span id="mongodb_drivers"></span>

Talvez você precise baixar os drivers manualmente ou seguir algumas instruções, siga até o endereço [https://www.mongodb.com/docs/drivers/](https://www.mongodb.com/docs/drivers/).