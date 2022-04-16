**Autor:** Henrique Matheus da Silva Lima

# índice

* [Introdução](#intro)

* [Node.js](#nodejs)

	* [Hello World](#nodejs_primeiroservidor)

		* [Um "Hello World" mais completo](#nodejs_primeiroservidor_maiscompleto)

		* [Servindo HTML para o cliente](#nodejs_primeiroservidor_html)

		* [Servindo JSON para o cliente](#nodejs_primeiroservidor_json)

	* [Nossos próprios módulos](#nodejs_nmodulos)

	* [Instalação de módulos com o NPM](#nodejs_npm)

	* [Framework Express](#nodejs_express)

		* [View engine](#nodejs_express_viewengine)

		* [app.use e public](#nodejs_express_usepublic)

		* [params](#nodejs_express_params)

	* [CRUD no MySQL](#nodejs_mysql)

		* [Pelo pacote mysql](#nodejs_mysql_mysql)

		* [Pelo pacote Sequelize](#nodejs_mysql_sequelize)

			* [Criação de tabelas](#nodejs_mysql_sequelize_c)

			* [Leitura de tabelas](#nodejs_mysql_sequelize_r)

				* [Leitura de tabelas legadas](#nodejs_mysql_sequelize_r_l)

			* [Atualização de tabelas](#nodejs_mysql_sequelize_u)

			* [Deleção de tabelas](#nodejs_mysql_sequelize_d)

			* [Queries](#nodejs_mysql_sequelize_queries)

# Introdução<span id="intro"></span>

Leia o [README](README.md).

# Node.js<span id="nodejs"></span>

Node.js é um software que permite rodar códigos JavaScript fora do navegador, um dos seus maiores usos é no *back-end* do lado do servidor.

Acesse [este site](https://nodejs.org/) para fazer o download do Node.js. PPra quem usa Linux: mesmo que você tenha o Node.js nos repositórios de sua distro, prefira baixar a versão LTS mais recente que está presente no site para evita_expressr conflitos com dependências que venhamos a baixar, é claro que esse conselho é desnecessário para quem usa distros *rolling release*.

Primeiro precisamos montar nosso arquivo `package.json`, ele é quem gerenciará as dependências do nosso projeto. Para criá-lo automarticamente, use o comando abaixo:

    npm init

Você verá uma série de perguntas, você pode deixar tudo sem responder sem quiser apenas teclando ENTER.

Abra seu arquivo `pacjage.json`, ele estará mais ou menos assim:

    {
      "name": "nodejs",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "",
      "license": "ISC",
      "dependencies": {
        "express": "^4.17.3",
        "http-status-codes": "^2.2.0"
      }
    }

É interessante que seu arquivo .js principal esteja com o nome indicado por `"main":`, que no caso aqui é `index.js`, mas poderia ser `main.js.`

## Hello World<span id="nodejs_primeiroservidor"></span>

Vamos criar o exemplo mais simples possível:

    const http = require('http');
    
    const server = http.createServer((req, res) => {
        res.end("Olá mundo");
    });
    
    server.listen(3000);

*Observe que a mensagem "Olá mundo" não é exibida perfeitamente, o "á" sofre uma "corrupção"*

Para pôr esse código para funcionar, abra o terminal na pasta onde se encontra o arquivo .js e use o comando `node`. Aqui eu colocarei o arquivo `index.js`, que contém o código acima, para rodar:

    node index.js

*Nos nossos códigos, assumirei que você salvou o código no arquivo chamado `index.js`. Não tem problema se você usar outro nome, mas lembre-se de adaptar o nome nos comandos que eu lhe passar.*

Se não apareceu nenhuma mensagem de erro, poderemos acessar nosso primeiro servidor Node.js pelo link [http://localhost:3000/](http://localhost:3000/).

Para finalizar o servidor, tecle Ctrl C no terminal.

OK, agora vamos analisar linha por linha:

    const http = require('http');

 Aqui requeremos o módulo interno do Node.js que nos permite criar um servidor

    const server = http.createServer((req, res) => {

O `http.createServer` é bem explicativo, é ele quem torna seu computador num servidor. O parâmetro `req` e `res` da função anônima respectivamente lidam com as requisições ao servidor e as respostas do mesmo. Normalmente os desenvolvedores nomeiam essas variáveis nessas formas abreviadas, mas podem escrever os nomes completos `http.createServer((request, response)`, isso vai do desenvolvedor.

    res.end("Olá mundo");

O método `.end()` de `res.end("Olá mundo");` assinala que o servidor pode considerar a resposta como completa. Aqui nós podemos, nessa mesma função, colocar a mensagem que queremos passar, mas se quisíssemos, poderíamos ter colocado a menssagem num métodp próprii, que no caso seria `.write()`

    server.listen(3000);

A função `server.listen()` criar um "ouvidor" para uma determinada porta ou caminho, que no caso é na porta 3000, por isso que só podemos acessar a página pelo link [http://localhost:3000/](http://localhost:3000/) e não por outro link como [http://localhost:8080/](http://localhost:8080/) ou [http://localhost:8124/](http://localhost:8124/).

Na verdade, esse método `listen()` aceita até 4 parâmetros:

    server.listen(port, hostname, backlog, callback);

Aqui um exemplo em que defino a porta e o endereço:

    server.listen(8124, "127.0.0.1");

O `backlog` especifica o tamanho máximo da fila de coneções pendendes (o padrão é 511) e `callback` seria uma função a ser executada quando a o *listener* for adicionado.

A propósito, `.listen` poderia estar "colado" no método `.createServer`:

    const http = require('http');
    
    const server = http.createServer((req, res) => {
        res.end("Olás mundo");
    }).listen(3000);

### Um "Hello World" mais completo<span id="nodejs_primeiroservidor_maiscompleto"></span>

    const http = require('http');
    const port = process.env.PORT || 3000;
    const host = '127.0.0.1';
    
    const server = http.createServer((req, res) => {
        res.writeHead(200, {'Content-Type': 'text/plain'});
        res.write("Olá mundo");
        res.end();
    }).listen(port, host, (error) => {
        if (error) {
            return console.log("Erro: ", error);
        }
        console.log(`O servidor foi iniciado no endereço ${host}:${port}`);
    });

O código acima faz a mesmíssima coisa do primeiro código que vimos neste tutorial.

    const port = process.env.PORT || 3000;

O `process.env` é uma variável global injetada pleo Node que representa o estado do ambiente de ssitema da sua aplicação, em outras palavras, `process.env` é uma referência às variáveis de ambiente de sistema. Quando você vê `port = process.env.PORT || 3000;`, você está dizendo: *use a porta 3000 a não ser que exista uma porta pré configurada*

    const host = '127.0.0.1';

Apenas definimos manualmente o host aqui. `127.0.0.1` é o mesmo que `localhost`, ou seja, `127.0.0.1:3000` é sinônimo de `localhost:3000`.

    res.writeHead(200, {'Content-Type': 'text/plain'});

Esse método escreve o cabeçalho da resposta HTTP, ele envia o *[status code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)* para o cliente. O 200 literalmente significa "OK", indicando que a ação requerida pelo cliente foi recebida, entendida e aceita.                                                                                

Aqui a sintaxe do método:

    response.writeHead(statusCode[, statusMessage][, headers]);

* `statusCode`: você já conhece, usamos 200 no caso

* `statusMessage`: qualquer string que mostre a mensagem de status

* `headers`: qualquer array ou string

Se tivéssemos armazenado a mensagem numa variável, poderíamos ter escrito nosso `.writeHead()` desse jeito:

    const http = require('http');
    const port = process.env.PORT || 3000;
    const host = '127.0.0.1';
    
    const server = http.createServer((req, res) => {
        let body = "Olá mundo";
        res.writeHead(200, {
            'Content-Length': Buffer.byteLength(body),
            'Content-Type': 'text/plain'
          })
          .end(body);
    }).listen(port, host, (error) => {
        if (error) {
            return console.log("Erro: ", error);
        }
        console.log(`O servidor foi iniciado no endereço ${host}:${port}`);
    });

Mais um exemplo de `.writeHead()` onde passo um vídeo:

    res.writeHead(200, {'Content-Type': 'video/mp4'});

Nosso próximo método:

    res.write("Olá mundo");

Envia um texto ou *stream* de texto para o cliente.

    .listen(port, host, (error) => {
        if (error) {
            return console.log("Erro: ", error);
        }
        console.log(`O servidor foi iniciado no endereço ${host}:${port}`);

Não tem muito o que explicar, fornecemos a porta pela variável `port`, o endereço pela variável `host` e uma função anônima para verificar a existência de um erro. A linha `console.log(`O servidor foi iniciado no endereço ${host}:${port}`);` nos informa que o servidor foi montado e aproveito para informar o endereço.

Para finalizar, desligue o servidor e rode o comando abaixo:

    PORT=9999 node index.js

Note que o endereço [http://localhost:3000/](http://localhost:3000/) não funciona mais, mas sim o [http://localhost:9999/](http://localhost:9999/).

### Servindo HTML para o cliente<span id="nodejs_primeiroservidor_html"></span>

Crie um arquivo HTML qualquer cmo algum conteúdo. Você pode dar o nome que quiser, no meu caso darei o nome `index.html`, se você escolher um nome diferente, lembre-se de adaptar o código:

    const http = require('http');
    const fs = require('fs');
    
    http.createServer((req, res) => {
        res.writeHead(200, {'Content-Type': 'text/html'});
        fs.readFile('index.html', (err, data) => {
            if (err) 
                throw err;
            res.end(data);
        });
    }).listen(3000);

Outro módulo interno do Node.js que importamos é o `fs`, com ele podemos usar o método `readFile()`, que lê um arquivo do computador. Ele tem a seguinte sintaxe:

    .readFile(arquivo, [codificação], [callback]);

Um exemplo onde peço para ler um arquivo de texto:

    .readFile('texto.txt', 'utf8' , (err, data) => {

A propósito, você viu como o *'Content-Type'* do `writeHead` do nosso código mudou para *'text/html'*?

### Servindo JSON para o cliente<span id="nodejs_primeiroservidor_json"></span>

    const http = require('http');
    const fs = require('fs');
    
    http.createServer((req, res) => {
        res.writeHead(200, {'Content-Type': 'application/json'});
        let mensagem_json = {
            nome: "João",
            salario: 3500,
            dias_que_trabalha: ["segunda", "terça", "quarta", "quinta", "sexta", "sábado"]
        }
        res.end(JSON.stringify(mensagem_json));
    }).listen(3000);

Só direi mais esta vez: fique repadando como a linha `.writeHead(200, {'Content-Type': '...'})` muda para cada tipo de arquivo enviado.

Não sei se você conhece o `JSON.stringify()`, mas essa função serve para converter um objeto numa *string*. Fazemos isso porque quando enviamos dados para os servidor, eles tem que ser em formato de *string*.

Vou parar por aqui porque se você quiser saber como enviar um PDF, áudio ou vídeo, você poderá pesquisar como enviar esses tipos de dados em Node.js puro.

## Nossos próprios módulos <span id="nodejs_nmodulos"></span>

Crie um novo arquivo .js, crierei um chamado `mensagens.js`.

**mensagens.js**

    module.exports.numero = 13;
    
    module.exports.texto = [
        "Olá mundo",
        "Estou bem",
        "E você?"
    ];
    
    module.exports.somar= (x, y) => {
        return x + y;
    }

**index.js**

    const http = require('http');
    const meuModulo = require('./mensagens');
    
    const server = http.createServer((req, res) => {
        console.log(meuModulo.numero);
        console.log(meuModulo.texto);
        console.log(meuModulo.somar(3,5));
        res.end();
    });
    
    server.listen(3000);

Neste caso você não verá o resultado no navegador, mas sim no terminal. Quando você executar o comando `node index.js`, acesse/atualize a página [http://localhost:3000/](http://localhost:3000/) pelo menos uma vez para que as variáveis sejam acessadas e as funções sejam executadas.

Perceba que quando chamamos um módulo nosso, usamos `./` antes do nome do arquivo e também note que não precisamos pôr a extensão do arquivo.

Outra coisa que você precisa saber é que podemos abreviar `module.exports` para simplesmente `exports`:

    exports.numero = 13;
    
    exports.texto = [
        "Olá mundo",
        "Estou bem",
        "E você?"
    ];
    
    exports.somar= (x, y) => {
        return x + y;
    }

Ou até mesmo assim:

    var numero = 13;
    
    var texto = [
        "Olá mundo",
        "Estou bem",
        "E você?"
    ];
    
    function somar(x, y) {
        return x + y;
    }
    
    module.exports.numero = numero;
    module.exports.texto = texto;
    module.exports.somar = somar;

## Instalação de módulos com o NPM<span id="nodejs_npm"></span>

Você já conhece o comando `npm init` que cria o arquivo `package.json`. o que posso adicionar aqui é que se você tivesse usado o comando `npm init --yes`, teria pulado todas aquelas perguntas. Vamos para além disso.

Para instalar um pacote, o comando básico é um dos dois abaixo:

    npm install <módulo>

<span></span>

    npm i <módulo>

Quando instalamos um módulo, é criada a pasta `node_modules` onde são armazenados todos os módulos. Você verá muitos arquivos porque os módulos muitas vezes também possuem suas próprias dependências.

Ainda podemos adiconar alguns parâmetros. O primeiro deles é `--save`:

    npm install <módulo> --save

<span></span>

    npm install --save <módulo>

Assim deixamos explícito que aquele pacote é uma dependência do nosso projeto. Quando você compartilhar seu código, você não precisará enviar os arquivos da pasta `node_modules`, o arquivo `package.json` é o suficiente, com ele em mãos, bastarpa rodar o comando `npm install` para que todas as dependências sejam baixadas automaticamente.

***Na verdade, a flag `--save` não é mais necessária, pois o comando `npm install <módulo>` por si só já informa a dependência ao arquivo `package.json`.***

Também temos a *flag* `--save-dev`, que é similar ao `--save`, mas esta nova informa que o módulo em questão é útil para os desenvolvedores, não para o consumidor final da aplicação.

    npm install <módulo> --save-dev

<span></span>

    npm install --save-dev <módulo>

Outras *flags* são a `--save-optional` e `--no-save`, em que a primeira informa que o pacote é opcional enquanto a segunda informa que o módulo não deve ser salvo no `package.json`.

Por fim, temos a *flag* `--global`, esta em vez de instalar o módulo de forma local, instalará o módulo no sistema, é por isso que, durante a sua instalação, será pedido um usuário privilegiado para instalar o módulo, como se você estivesse instalando um programa comum no seu sistema operacional.

## Nodemon

[Website](https://nodemon.io/)

Nodemon é uma ferramenta interessante. Ela funciona da seguinte forma, toda vez que modificamos o nosso projeto, o servidor é recarregado automaticamente, sem precisarmos ter que ficar desligando e ligando o servidor toda hora pra ver se as atualizações funcionaram.

Instale o Nodemon ou como dependência...

    npm install nodemon --save-dev

...ou globalmente:

    npm install -g nodemon

Para executar seu aplicativo através do Nodemon, é só usar o comando abaixo:

    nodemon <seu_projeto>

No meu caso aqui, usei o comando `nodemon index.js`.

## Framework Express<span id="nodejs_express"></span>

[Website](https://expressjs.com)

O Express é tão utilizado que há muitos desenvolvedores que literalmente não sabem usar o Node.js sem ele.

Esse framework não faz parte do Node.js, portanto precisamos baixá-lo. Na pasta do seu projeto, faça download dele pelo NPM:

    npm i express

Se você olhar o arquivo `packages.json`, você o verá nas dependências:

    {
      "name": "nodejs",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "",
      "license": "ISC",
      "dependencies": {
        "express": "^4.17.3"
      }
    }

O nosso arquivo `index.js` ficará assim:

    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.send("Olá mundo");
    });
    
    app.listen(3000);


*Observe que agora a mensagem "Olá mundo" é exibida perfeitamente*

A vantagem desse framework é que o *routing* é muito fácil:

    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.send("Página inicial, clique <a href='contato'>aqui</a> para acessar a página de contatos");
    });
    
    app.get('/contato', (req, res) => {
        res.send("Contato");
    });
    
    app.listen(3000);

### View engine<span id="nodejs_express_viewengine"></span>

O Express pode renderizar arquivos de modelo. Mas para isso precisamos instalar um *view engine* que faça esse trabalho para nós. A boa *(ou má...)* notícia é que há vários, como EJS, PUG e Handlebars. Terei que escolher um para os nossos exemplos, mas aqui estão os sites de cada um deles:

* [EJS](https://ejs.co/)

* [PUG](https://pugjs.org/)

* [Handlebars](https://handlebarsjs.com/)

Terei escolher um e o felizardo será o EJS. Não tenho motivos técnicos para usar este em vez dos outros, o escolhi porque foi o que aprendi melhor e gostei.

Primeiro, vamos instalar o EJS:

    npm i ejs

Crie a pasta `views`, ela é obrigatória.

Dentro da pasta `views`, crie a pasta `pages` e ponha lá dentro o arquivo `index.ejs` *(isso mesmo, com a extesão ejs)*.

Também dentro da pasta `views`, crie a pasta `partials` e ponha lá dentro os arquivos `head.ejs`, `header.ejs` e `footer.ejs`.

Eis os conteúdos de cada arquivo:

**views/partials/head.ejs**

    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Teste</title>

**views/partials/header.ejs**

    <div class="menu">Início | Projetos | Contatos</div>

**views/partials/footer.ejs**

    © Copyright 2020 HMSLIMA

**views/pages/index.ejs**

    <!DOCTYPE html>
    <html lang="pt-br">
    <head>
        <%- include('../partials/head'); %>
    </head>
    <body>
        <header>
            <%- include('../partials/header'); %>
        </header>
    
        <p>Olá mundo!</p>
    
        <footer>
            <%- include('../partials/footer'); %>
        </footer>
    </body>
    </html>

**index.js**

    const express = require('express');
    const ejs = require('ejs');
    
    const app = express();
    
    app.set('view engine', 'ejs');
    
    app.get('/', (req, res) => {
        res.render("pages/index");
    });
    
    app.listen(3000);

Não tenho o que falar dos arquivos dentro da pasta `views/partials/` uma vez 	que eles contém o HTML básico que você já conhece.

No arquivo `index.ejs`, temos as *tags* `<%- %>` onde colocamos nossos *includes*. Também não tem muito o que explicar, o `<%- include(); %>` insere um pedaço de HTML em outro arquivo HTML.

Quanto ao arquivo `index.js`, a linha `const app = express();` cria uma aplicação Express para você.

`app.set()` atribui um nome de configuração a um valor. No caso mexemos com a propriedade `view engine`, em que atribuimos a ela o valor `ejs`. Se, por exemplo, estivéssemos usando a tecnologia Handlebars, essa linha seria `app.set('view engine', 'hbs');`.

O método `res.render()` renderiza um *view* e manda a *string* de HTML renderizada para o cliente. Esse método tem a senguinte sintaxe:

    res.render(view [, locals] [, callback])

* `locals`: objeto cujas propriedades definem as variáveis locais da view.

* `callback`: função callback, que pode retornar um error ou a *string* renderizada.

Vamos deixar nosso projeto mais interessante.

**index.js**

    const express = require('express');
    const ejs = require('ejs');
    
    const app = express();
    
    app.set('view engine', 'ejs');
    
    app.get('/', (req, res) => {
        res.render("pages/index", {nome: "João"}, (err, html) => {
            res.send(html);
        });
    });
    
    app.listen(3000);

**views/pages/index.ejs**

    <!DOCTYPE html>
    <html lang="pt-br">
    <head>
        <%- include('../partials/head'); %>
    </head>
    <body>
        <header>
            <%- include('../partials/header'); %>
        </header>
    
        <p>Olá <%= nome %>!</p>
    
        <footer>
            <%- include('../partials/footer'); %>
        </footer>
    </body>
    </html>

A mudança no arquivo `index.ejs` é mínima, a mudança foi apenas esta linha `<p>Olá <%= nome %>!</p>` onde adicionei uma variável por meio da *tag* `<%= %>`; preste atenção, a *tag* que insere uma variável é `<%= %>` enquanto a que insere um *include* é `<%- %>`, olhe direitinho que você notará a diferença.

### app.use e public<span id="nodejs_express_usepublic"></span>

Crie a pasta `public` *(na pasta principal do projeto mesmo)* e dentro desta pasta crie as pastas `css` e `js`. Ponha um arquivo css e um arquivo de scripts normal .js em suas respectivas pastas, pode ser qualquer um, mas eu usarei os [arquivos do Bootstrap](https://getbootstrap.com/) no meu exemplo.

Também modifiquei o arquivo `views/partials/head.ejs` para que este ficasse assim:

    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/bootstrap.css">
    <script src="js/bootstrap.js"></script>
    <title>Teste</title>

E nosso arquivo `index.js` ficará assim agora:

    const express = require('express');
    const ejs = require('ejs');
    
    const app = express();
    
    app.set('view engine', 'ejs');
    app.use(express.static('public'));
    
    app.get('/', (req, res) => {
        res.render("pages/index");
    });
    
    app.listen(3000);

Se você atualizar a pasta, só em olhar a fonte você reparará que o Bootstrap está em ação. Agora vamos tentar entender o que aconteceu:

     app.use(express.static('public'));

Temos duas coisas aqui, o `app.use()` e o `express.static()`. O `app.use()` monta uma função *[middleware](https://pt.wikipedia.org/wiki/Middleware)* específica. O `express.static()`, por sua vez, é uma função *middleware* do Express que serve arquivos estáticos, o parâmetro dessa função é a pasta onde estão os arquivos estáticos.

Repare que, no monento quando colocamos os endereços dos arquivos .css e .js, eles foram...

    <link rel="stylesheet" href="css/bootstrap.css">
    <script src="js/bootstrap.js"></script>

...em vez de:

    <link rel="stylesheet" href="public/css/bootstrap.css">
    <script src="public/js/bootstrap.js"></script>

### params<span id="nodejs_express_params"></span>

Crie um novo arquivo na pasta `views/pages`, vamos chamá-lo de `usuario.ejs`.

**index.js**

    const express = require('express');
    const ejs = require('ejs');
    
    const app = express();
    
    app.set('view engine', 'ejs');
    
    app.get('/', (req, res) => {
        res.render("pages/index");
    });
    
    app.get('/usuario/:nome_id', (req, res) => {
        let nome_id = req.params.nome_id;
        res.render('pages/usuario', {nome_id: nome_id});
    });
    
    app.listen(3000);

*Aproveita e retira aquela tag `<%= nome %>` do arquivo `views/pages/index.ejs` para ele não causar mensagens de erro inesperadas para nós depois...*

**views/pages/usuario.ejs**

    <!DOCTYPE html>
    <html lang="pt-br">
    <head>
        <%- include('../partials/head'); %>
    </head>
    <body>
        <header>
            <%- include('../partials/header'); %>
        </header>
    
        <p>Olá <%= nome_id %>!</p>
    
        <footer>
            <%- include('../partials/footer'); %>
        </footer>
    </body>
    </html>

Agora acesse os endereços abaixo:

[http://localhost:3000/usuario/Thiago](http://localhost:3000/usuario/Thiago)

[http://localhost:3000/usuario/Júlia](http://localhost:3000/usuario/Júlia)

Acho que o código é bem explicativo.

    app.get('/usuario/:nome_id', (req, res) => {

Através dos dois pontos (`:`), definimos a palavra `nome_id` como parâmetro e "capturei" esse parâmetro por meio do método `req.params`.

## CRUD no MySQL<span id="nodejs_mysql"></span>

Para não perdermos tempo, usaremos a tabela `funcionarios` criada [neste tutorial de SQL](SQL.md).

<hr>

    CREATE DATABASE teste;

<span></span>

    USE teste;

<span></span>
    
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

<span></span>

    INSERT INTO funcionarios VALUES(Null, "Mariana", "Cardoso", "F", "mariana@terra.com.br", 4000.00, "Financeiro");
    INSERT INTO funcionarios VALUES(Null, "Thiago", "Silva", "M", "thiago@terra.com.br", 1500.00, "TI");
    INSERT INTO funcionarios VALUES(Null, "Tião", "Trovão", "M", "danadinha@gmail.com.br", 2000.00, "TI");
    INSERT INTO funcionarios VALUES(Null, "Iara", "Schmidt", "F", "schmidt@gmail.com.br", 4500.00, "Financeiro");
    INSERT INTO funcionarios VALUES(Null, "Patrícia", "Oliveira", "F", "patioliveira@gmail.com.br", 8000.00, "Financeiro");
    INSERT INTO funcionarios VALUES(Null, "Railton", "Carneiro", "M", "rai@hotmail.com.br", 3000.00, "TI");
    INSERT INTO funcionarios VALUES(Null, "Pedro", "dos Santos", "M", "pedrao@hotmail.com.br", 12000.00, "TI");

<hr>

### Pelo pacote mysql<span id="nodejs_mysql_mysql"></span>

[Website](https://www.npmjs.com/package/mysql)

Instale o pacote `mysql`:

    npm install mysql


Como ficará nosso arquivo `index.js`:

    const mysql = require('mysql');
    
    const conn = mysql.createConnection({
        host: "127.0.0.1",
        user: "root",
        password: "root"
    });
    
    conn.connect((err) => {
        if (err) throw err;
    
        console.log("Conexão feita com sucesso!");
    });

    conn.end();

*Não sei porque, mas quando eu definia `localhost` para `host`, dava errado pra mim. Estou falando isso porque muitos tutoriais usam a intrução `host: 'localhost'`...*

No meu caso aqui, tanto o nome de usuário quanto a senha são "root", mas pode ser diferente para você, então veja como é para você.

Todo método que você invoca, é enfileirado e executado em sequência. Você fecha a conexão por meio do método `end()`

    const mysql = require('mysql');
    
    const conn = mysql.createConnection({
        host: "127.0.0.1",
        user: "root",
        password: "root",
        database: "teste"
    });
    
    conn.connect();
    
    let comando_mysql = "SELECT * FROM funcionarios;";
    
    conn.query(comando_mysql, (erro, resultados) => {
        if (erro) throw erro;
        for (resultado of resultados) {
            console.log(resultado);
        }
    })
    
    conn.end();

Dentro do método `createConnection`, temos uma novidade, que é a seleção do banco de dados `teste` em `database: "teste"`.

Por meio do método `.query`, podemos utilizar um comando MySQL.

    const mysql = require('mysql');
    
    const conn = mysql.createConnection({
        host: "127.0.0.1",
        user: "root",
        password: "root",
        database: "teste"
    });
    
    conn.connect();
    
    let comando_mysql = "SELECT * FROM funcionarios;";
    
    conn.query(comando_mysql, (erro, resultados) => {
        if (erro) throw erro;
        for (resultado of resultados) {
            console.log(resultado);
        }
    })
    
    conn.end();

Naturalmente que podemos usar mais de um comando:

    const mysql = require('mysql');
    
    const conn = mysql.createConnection({
        host: "127.0.0.1",
        user: "root",
        password: "root",
        database: "teste"
    });
    
    conn.connect();
    
    let comando_mysql = "SELECT * FROM funcionarios;";
    let comando_mysql2 = "SELECT * FROM funcionarios WHERE Genero=\"F\";";
    
    conn.query(comando_mysql, (erro, resultados) => {
        if (erro) throw erro;
        for (resultado of resultados) {
            console.log(resultado);
        }
        console.log("----------") // Só para separar os diferentes queries
    })
    
    conn.query(comando_mysql2, (erro, resultados) => {
        if (erro) throw erro;
        for (resultado of resultados) {
            console.log(resultado);
        }
    })
    
    conn.end();

O trecho abaixo que é do código acima...

    for (resultado of resultados) {
        console.log(resultado);
    }

...está ali só para vermos os resultados, que é bom conveniente para um comando SQL do tipo `SELECT *`, mas com esse código aí você pode fazer qualquer coisa com seu banco de dados SQL como criação, leitura, atualização e deleção de dados.

### Pelo pacote Sequelize<span id="nodejs_mysql_sequelize"></span>

[Website](https://sequelize.org/)

Instale o pacote `sequelize`:

    npm i sequelize

O Squelize também exigirá a instalação manual do módulo referente ao banco de dados que você for usar: 

* PostgreSQL: `pg` `pg-hstore`

* MySQL: `mysql2`

* MariaDB: `mariadb`

* SQLite: `sqlite3`

* Microsoft SQL Server: `tedious`

Eis o nosso código:

    const { Sequelize } = require('sequelize');
    
    const conn = new Sequelize('teste', 'root', 'root', {
        host: '127.0.0.1',
        dialect: 'mysql'
    });
    
    (async function(){
        try {
            await conn.authenticate();
            console.log('A conexão foi estabelecida com sucesso.');
            conn.close();
        } catch (error) {
            console.error('Não foi possível estabelecer uma conexão com o banco de dados:', error);
        }
    }())

Os parâmetros de `Sequelize()` são:

    Sequelize('<banco_de_dados>', '<usuário>', '<senha>', {
        host: '<>',
        dialect: '<>'
    });

O `dialect` pode ser *'mysql'*, *'mariadb'*, *'postgres'* ou *'mssql'*.

Na hora de autenticar a conexão *(`.authenticate()`)*, precisamos usar a palavra chave `await` porque a conexão pode ser fechada *(`.close()`)* antes mesmo de ser autenticada, o que causará erros.

#### Criação de tabelas<span id="nodejs_mysql_sequelize_c"></span>

    const { Sequelize, DataTypes } = require('sequelize');
    
    const sequelize = new Sequelize('teste', 'root', 'root', {
        host: '127.0.0.1',
        dialect: 'mysql'
    });
    
    const Usuario = sequelize.define("Usuario", {
        Nome: {
            type: DataTypes.STRING,
            allowNull: false
        },
        email: {
            type: DataTypes.STRING,
            allowNull: false
        },
        Salario: {
            type: DataTypes.DOUBLE,
            allowNull: false
        }
    });
    
    (async () => {
        await Usuario.sync();
    })();

* `sequelize.define()`: define um novo modelo, que representa uma tabela no banco de dados.

* `sync()`: cria uma tabela se ela não existir e faz nada se ele já existir. A seguir vamos ver outras variações desse método:

	* `.sync({ force: true })`: cria uma nova tabela, deletando a anterior com mesmo nome se esta existir

	* `.sync({ alter: true })`: checa a tabela atual *(quais colunas existem, os tipos de dados...)* e realiza as mudanças necessárias na tabela para que esta se adeque ao novo modelo.

* Eu creio que o resto seja bem auto-informativo. Se você, por exemplo, quiser saber quais são os tipos de dados possíveis neste ou naquele sistema de banco de dados, sugiro que você consulte a documentação presente no site.

O código acima faz o mesmo que o comando MySQL abaixo:

    CREATE TABLE IF NOT EXISTS `Usuarios` (`id` INTEGER NOT NULL auto_increment , `Nome` VARCHAR(255) NOT NULL, `email` VARCHAR(255) NOT NULL, `Salario` DOUBLE PRECISION NOT NULL, `createdAt` DATETIME NOT NULL, `updatedAt` DATETIME NOT NULL, PRIMARY KEY (`id`)) ENGINE=InnoDB;

Repare que ele também criou a coluna `id` automaticamente pra nós, vejamos os detalhes dessa tabela:

    +-----------+--------------+------+-----+---------+----------------+
    | Field     | Type         | Null | Key | Default | Extra          |
    +-----------+--------------+------+-----+---------+----------------+
    | id        | int(11)      | NO   | PRI | NULL    | auto_increment |
    | Nome      | varchar(255) | NO   |     | NULL    |                |
    | email     | varchar(255) | NO   |     | NULL    |                |
    | Salario   | double       | NO   |     | NULL    |                |
    | createdAt | datetime     | NO   |     | NULL    |                |
    | updatedAt | datetime     | NO   |     | NULL    |                |
    +-----------+--------------+------+-----+---------+----------------+

Há outra maneira de criar uma tabela que é por meio da extenção da classe `Model` do Sequelize.

    const { Sequelize, DataTypes, Model } = require('sequelize');
    
    const sequelize = new Sequelize('teste', 'root', 'root', {
        host: '127.0.0.1',
        dialect: 'mysql'
    });
    
    class Usuario extends Model {}
    
    Usuario.init({
        Nome: {
            type: DataTypes.STRING,
            allowNull: false
        },
        email: {
            type: DataTypes.STRING,
            allowNull: false
        },
        Salario: {
            type: DataTypes.DOUBLE,
            allowNull: false
        }
    }, {
        sequelize,
        modelName: 'Usuario'
    });
    
    (async () => {
        await Usuario.sync();
    })();

Observe que no momento que importo o módulo `sequelize`, também peço pela classe `Model`:

    const { Sequelize, DataTypes, Model } = require('sequelize');

Saiba que, internamente, `sequelize.define` chama `odel.init`, portanto ambos são equivalente.

    sequelize,
    modelName: 'Usuario'

Essa linha `sequelize,` logo acima passa a instância da conexão enquanto `modelName:` escolhe o nome do modelo.

#### Leitura de tabelas<span id="nodejs_mysql_sequelize_r"></span>

Não tem muito o que falar aqui, o código seria basicamente o mesmo da criação de uma tabela; se você manter o `.sync()` que impede a deleção/modificação da tabela já existente, você não terá problemas.

##### Leitura de tabelas legadas<span id="nodejs_mysql_sequelize_r_l"></span>

E se estivermos lidando com uma tabela antiga? Primeiro definimos essa tabela como se você estivesse criando uma nova. Vejamos a tabela `funcionarios` que já temos em mãos:

    +--------------+--------------+------+-----+---------+----------------+
    | Field        | Type         | Null | Key | Default | Extra          |
    +--------------+--------------+------+-----+---------+----------------+
    | Id           | int(11)      | NO   | PRI | NULL    | auto_increment |
    | Nome         | varchar(255) | NO   |     | NULL    |                |
    | Sobrenome    | varchar(255) | NO   |     | NULL    |                |
    | Genero       | char(1)      | NO   |     | NULL    |                |
    | email        | varchar(255) | NO   |     | NULL    |                |
    | Salario      | float(7,2)   | NO   |     | NULL    |                |
    | Departamento | varchar(255) | NO   |     | NULL    |                |
    +--------------+--------------+------+-----+---------+----------------+

Depois você precisa ter em mente que o próprio Sequelize, por padrão, cria tabelas como a *primary key* `id` e as variáveis "*timestamp*" `createdAt` e `updatedAt`.

    const { Sequelize, DataTypes } = require('sequelize');
    
    const sequelize = new Sequelize('teste', 'root', 'root', {
        host: '127.0.0.1',
        dialect: 'mysql'
    });
    
    const Funcionarios = sequelize.define("funcionarios", {
        Nome: {
            type: DataTypes.STRING,
            allowNull: false
        },
        Sobrenome: {
            type: DataTypes.STRING,
            allowNull: false
        },
        Genero: {
            type: DataTypes.CHAR(1),
            allowNull: false
        },
        email: {
            type: DataTypes.STRING,
            allowNull: false
        },
        Salario: {
            type: DataTypes.FLOAT(7, 2),
            allowNull: false
        },
        Departamento: {
            type: DataTypes.STRING,
            allowNull: false
        },
    }, {
        timestamps: false
    });
    
    (async () => {
        await Funcionarios.sync();
    })();
    
    // Vamos usar uns queries pra testar se tudo deu realmente certo
    // Você não precisa entender o trecho de código abaixo agora
    (async () => {
        const funcionarios = await Funcionarios.findAll();
        console.log("Todos os funcionarios:", JSON.stringify(funcionarios, null, 2));
    })();

Primeiro repare que não precisei definir o `id` porque o próprio Sequelize faz isso. O mais interessante é esse código aqui:

    {
        timestamps: false
    });

Se não adicione esse trecho de código, o Sequelize vai procurar pela colunas `createdAt` e `updatedAt` e não as encontrará, o que resultará em erro. A linha `timestamps: false` avisa para não adicionar as colunas `createdAt` e `updatedAt`. Veja com mais detalhes:

* `timestamps: false`: não adicione os atributos "*timestamp*", que são `createdAt` e `updatedAt`

* `createdAt: false`: não adicione o atributo `createdAt`

* `updatedAt: false`: não adicione o atributo `updatedAt`

#### Atualização de tabelas<span id="nodejs_mysql_sequelize_u"></span>

É só usar `.sync({ alter: true })`.

Vejamos um exemplo em que deleto a coluna `email` da tabela `Usuarios` e ainda mudo o tipo de `Salario` de *double* para inteiro:

    const { Sequelize, DataTypes } = require('sequelize');
    
    const sequelize = new Sequelize('teste', 'root', 'root', {
        host: '127.0.0.1',
        dialect: 'mysql'
    });
    
    const Usuario = sequelize.define("Usuario", {
        Nome: {
            type: DataTypes.STRING,
            allowNull: false
        },
        Salario: {
            type: DataTypes.INTEGER,
            allowNull: false
        }
    });
    
    (async () => {
        await Usuario.sync({ alter: true });
    })();

#### Deleção de tabelas<span id="nodejs_mysql_sequelize_d"></span>

Trocamos a linha...

    Usuario.sync();

...pela linha: 

    Usuario.drop();

<span></span>

    const { Sequelize, DataTypes } = require('sequelize');
    
    const sequelize = new Sequelize('teste', 'root', 'root', {
        host: '127.0.0.1',
        dialect: 'mysql'
    });
    
    const Usuario = sequelize.define("Usuario");
    
    (async () => {
        await Usuario.drop();
    })();

#### Queries<span id="nodejs_mysql_sequelize_queries"></span>
