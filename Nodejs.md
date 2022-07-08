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

	* [Manipulação de JSON](#nodejs_json)

	* [Nodemon](#nodejs_nodemon)

	* [Framework Express](#nodejs_express)

		* [Roteamento](#nodejs_express_roteamento)

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

				* [Insert](#nodejs_mysql_sequelize_queries_insert)

				* [Select](#nodejs_mysql_sequelize_queries_select)

				* [Where](#nodejs_mysql_sequelize_queries_where)

				* [Update](#nodejs_mysql_sequelize_queries_update)

				* [Delete](#nodejs_mysql_sequelize_queries_delete)

				* [Ordenamento](#nodejs_mysql_sequelize_queries_ordenamento)

	* [CRUD no MongoDB](#nodejs_mongodb)

		* [INSERT](#nodejs_mongodb_insert)

		* [FIND](#nodejs_mongodb_find)

		* [O resto](#nodejs_mongodb_resto)

		* [REST APIs](#nodejs_mongodb_rest)

	* [Projeto: Lista de Tarefas](#nodejs_projetotarefas)

	* [Projeto: REST API com Express.js e PostgreSQL](#nodejs_projetoapi)

	* [Conclusão](#nodejs_conclusao)

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
      "name": "nome_do_projeto",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "",
      "license": "ISC"
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
        res.end("Olá mundo");
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

## CommonJS vs módulos EMCAScript<span id="nodejs_commonjsvsesmodules"></span>

No ecossistema do navegador, são usadas as palavras chaves `import` e `export` para importar e exporat módulos. Já o Node.js usa o CommonJS para carregar os módulos, como você viu com `require()` e `module.exports`.

Vejamos um exemplo usando o CommonJS que você já conhece:

**utilidades.js**

    const {somar} = require('./utilidades')
    
    console.log(somar(2,3))

**index.js**

    const {somar} = require('./utilidades')
    
    console.log(somar(2,3))

Agora vamos usar o modo do EMCAScript. Há duas maneiras: ou mudamos a extensão dos arquivos de `.js` mapa `.mjs`, ou mantemos as extensões `.js`, mas adicionamos `{"type": "module"}` no arquivo `package.json`, o exemplo a seguir segue essa segunda maneira.

**package.json**

    {
      "name": "delete",
      "version": "1.0.0",
      "type": "module",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "keywords": [],
      "author": "",
      "license": "ISC"
    }

*Repare no `"type": "module"` que adicionei manualmente*

**utilidades.js**

    export function somar(a, b) {
        return a + b;
    }

**index.js**

    import {somar} from './utilidades.js'
    
    console.log(somar(2,3))

*De novo, se usássemos as extensões `.mjs` no lugar de `.js`, não precisaríamos configurar o arquivo `package.json`*

## Manipulação de JSON<span id="nodejs_json"></span>

    const fs = require('fs');
    
    // Objeto JavaScript
    const livro = {
        titulo: "O Senhor dos Anés",
        autor: "Tolkien"
    }
    
    // JSON.stringify converte objeto para string, quando enviamos dados para o servidor, esse dado precisa ser uma string
    const livroJSON = JSON.stringify(livro);
    
    console.log("O objeto");
    console.log(livro);
    
    console.log(); // Só pr apular uma linha
    
    console.log("A string");
    console.log(livroJSON);
    
    console.log();
    
    // Salva um arquivo JSON no seu computador
    fs.writeFileSync('livro.json', livroJSON);
    
    // Lê um arquivo chamado "livro.json"
    const dataBuffer = fs.readFileSync('livro.json');
    
    console.log("O arquivo JSON como binário");
    console.log(dataBuffer);
    
    console.log();
    
    console.log("O arquivo JSON como string");
    console.log(dataBuffer.toString());

## Nodemon<span id="nodejs_nodemon"></span>

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

### Roteamento<span id="nodejs_express_roteamento"></span>

Vamos aprender sobre `.get()` e `.post()`.

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

Quanto ao arquivo `index.js`, a linha `const app = express();` cria uma aplicação Express para você, ou seja, `const app = express();` retorna um objeto de aplicativo.

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

Primeiro vamos entender o que é um *middleware*: *middleware* é um método, função ou operação chamada entre o processamento do *request* e o envio da *response* no método da sua aplicação.

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

##### LEITURA DE TABELAS LEGADAS<span id="nodejs_mysql_sequelize_r_l"></span>

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

##### INSERT<span id="nodejs_mysql_sequelize_queries_insert"></span>

Vamos inserir 4 usuários:

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
        await Usuario.sync().then(() => {
            (async () => {
                const usuario = await Usuario.create({ Nome: "Marcelo Ferreira", email: "marcelo@terra.com.br", Salario: 3000.00 });
            })();
    
            (async () => {
                const usuario = await Usuario.create({ Nome: "Tatiana Castro", email: "tati@bol.com.br", Salario: 2200.00 });
            })();
    
            (async () => {
                const usuario = await Usuario.create({ Nome: "Eliza Camos", email: "elcampos@gmail.com.br", Salario: 4000.00 });
            })();
    
            (async () => {
                const usuario = await Usuario.create({ Nome: "Thiago Vasconcelos", email: "vasconcelos@gmail.com.br", Salario: 1500.00 });
            })();
        });
    })();

##### SELECT<span id="nodejs_mysql_sequelize_queries_select"></span>

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
        await Usuario.sync().then(() => {
            (async () => {
                const usuarios = await Usuario.findAll();
                console.log("Todos os usuários:", JSON.stringify(usuarios, null, 2));
            })();
        });
    })();

<hr>

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
        await Usuario.sync().then(() => {
            (async () => {
                const usuarios = await Usuario.findAll({attributes: ['Nome', 'email']}); // Seleciona apenas os atributos "Nome" e "email"
                console.log("Todos os usuários:", JSON.stringify(usuarios, null, 2));
            })();
        });
    })();

##### WHERE<span id="nodejs_mysql_sequelize_queries_where"></span>

Exibe os usuários com salário superior a 2500.

    const { Sequelize, DataTypes, Op } = require('sequelize');
    
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
        await Usuario.sync().then(() => {
            (async () => {
                const usuarios = await Usuario.findAll({
                    where: {
                        Salario: {
                            [Op.gte]: 2500.00
                        }
                    }
                });
                console.log(JSON.stringify(usuarios, null, 2));
            })();
        });
    })();

Observe que na importação, também peguei o `Op`. Há várias operações que você pode fazer com o `Op`, por exemplo:

* `[Op.eq]: 12`: = 12

* `[Op.gt]: 10`: > 10

* `[Op.lte]: 8`: < 8

* *Veja o resto no site*

##### UPDATE<span id="nodejs_mysql_sequelize_queries_update"></span>

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
        await Usuario.sync().then(() => {
            (async () => {
                const usuario = await Usuario.update({ Nome: "Sérgio Smith"}, {
                    where: {
                        id: 1
                    }
                });
            })();
        });
    })();

##### DELETE<span id="nodejs_mysql_sequelize_queries_delete"></span>

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
        await Usuario.sync().then(() => {
            (async () => {
                const usuario = await Usuario.destroy({
                    where: {
                        id: 1
                    }
                });
            })();
        });
    })();

##### ORDENAMENTO<span id="nodejs_mysql_sequelize_queries_ordenamento"></span>

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
        await Usuario.sync().then(() => {
            (async () => {
                const usuarios = await Usuario.findAll({
                    order: [
                        ['Nome', 'DESC'] // DESC é decrescente, pra crescente (que é o padrão) seria ASC
                    ]
                }).then((usuarios) => {
                    console.log(JSON.stringify(usuarios, null, 2));
                })
            })();
        });
    })();

## CRUD no MongoDB<span id="nodejs_mongodb"></span>

Sugiro que você veja meu tutorial de [MongoDB](mongodb.md).

Inicie o servidor, abra o shell do MongoDB.

E baixe o MongoDB para Node.js

    npm i mongodb

### INSERT<span id="nodejs_mongodb_insert"></span>

    const mongodb = require('mongodb')
    const MongoClient = mongodb.MongoClient
    
    const connectionURL = 'mongodb://127.0.0.1:27017'
    const databaseName = 'teste'
    
    MongoClient.connect(connectionURL, {useNewUrlParser: true}, (error, client) => {
        if (error) {
            return console.log("Não foi possível se conectar com o banco de dados. Motivo:" + error);
        }
        
        const db = client.db(databaseName) // Cria um banco de dados com esse nome se o mesmo não existir
    
        db.collection('Usuarios').insertOne({
            nome: 'João',
            idade: 15
        })
    
        db.collection('Usuarios').insertOne({
            nome: 'Thiago',
            idade: 28
        }, (error, result) => {
            if (error) {
                return console.log("Não foi possível inserir o usuário:" + error)
            }
        })
    
        db.collection('Usuarios').insertMany([
            {
                nome: 'Marcelino',
                idade: 30
            },
            {
                nome: 'Milena',
                idade: 8
            },
            {
                nome: 'Tatiano',
                idade: 16
            }
        ], (error, result) => {
            if (error) {
                return console.log("Não foi possível inserir o usuário:" + error)
            }
        })
    })

Para inserir com os IDs definidos por nós:

    const {MongoClient, ObjectId} = require('mongodb')
    
    const id = new ObjectId()
    
    console.log(id) // Compare com o que você ver no servidor
    console.log(id.getTimestamp())
    console.log(id.id)
    console.log(id.id.length)
    
    const connectionURL = 'mongodb://127.0.0.1:27017'
    const databaseName = 'teste'
    
    MongoClient.connect(connectionURL, {useNewUrlParser: true}, (error, client) => {
        if (error) {
            return console.log("Não foi possível se conectar com o banco de dados. Motivo:" + error);
        }
        
        const db = client.db(databaseName) // Cria um banco de dados com esse nome se o mesmo não existir
    
        db.collection('Usuarios').insertOne({
            _id: id,
            nome: 'Enzo',
            idade: 18
        }, (error, result) => {
            if (error) {
                return console.log("Não foi possível inserir o usuário:" + error)
            }
        })
    })

### FIND<span id="nodejs_mongodb_find"></span>

    const {MongoClient, ObjectId} = require('mongodb')
    
    const connectionURL = 'mongodb://127.0.0.1:27017'
    const databaseName = 'teste'
    
    MongoClient.connect(connectionURL, {useNewUrlParser: true}, (error, client) => {
        if (error) {
            return console.log("Não foi possível se conectar com o banco de dados. Motivo:" + error);
        }
        
        const db = client.db(databaseName) // Cria um banco de dados com esse nome se o mesmo não existir
    
        db.collection('Usuarios').findOne({nome: 'Milena'}, (error, usuario) => {
            if (error) {
                return console.log("Não foi possível recuperar o usuário:" + error)
            }
            console.log(usuario)
            console.log("-----------------------")
        })
    
        db.collection('Usuarios').find({idade: {$gte: 20}}).toArray((error, usuario) => {
            if (error) {
                return console.log("Não foi possível recuperar o usuário:" + error)
            }
            console.log(usuario)
        })
    })

### O resto<span id="nodejs_mongodb_resto"></span>

O resto você pode consultar na [documentação](https://mongodb.github.io/node-mongodb-native/)...

### REST APIs<span id="nodejs_mongodb_rest"></span>

Conheça o projeto [Mongoose](https://mongoosejs.com/).

    npm i mongoose

Vamos nos conectar ao banco de dados e criar um documento:

    const mongoose = require('mongoose')
    
    mongoose.connect('mongodb://127.0.0.1:27017/teste', {
                    useNewUrlParser: true
    })
    
    const Usuario = mongoose.model('Usuario', { // Mongoose automaticamente criará a coleção usuarios (sim, já com o -s no final)
        nome: {
            type: String
        },
        idade: {
            type: Number
        }
    })
    
    const juliana = new Usuario({
        nome: 'Juliana',
        idade: 30
    })
    
    juliana.save().then(() => {
        console.log(juliana)
    }).catch((error)=> {
        console.log(error)
    })

Vou parar por aqui porque o maior foco será nos bancos de dados relacionais. Se você quiser mais informações, pesquise por si só.

## Projeto: Lista de Tarefas<span id="nodejs_projetotarefas"></span>

Esse é um projetinho bem simples que consiste em criar uma lista de tarefas. Através deles aprenderemos mais alguns coisas básicas:

**views/partials/head.ejs**

    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/bootstrap.css">
    <title>Lista de Tarefas</title>

**views/partials/header.ejs**

    <h1>Lista de Tarefas</h1>

**views/partials/footer.ejs**

    © Copyright 2020

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
    
        <p><a class="btn btn-primary" href="tarefa">Clique aqui para adicionar uma nova tarefa</a></p>.
    
        <hr>
    
        <% tarefas.forEach(tarefa => { %>
            <br>
            <div class="card">
                <div class="card-header">
                    <h3><%= tarefa.Titulo %></h3>
                </div>
                <div class="card-body">
                    <table class="table">
                        <tr>
                            <td>
                                <%= tarefa.Descricao %>
                            </td>
                            <td style="width: 5rem;">
                                <%= tarefa.Data %>
                            </td>
                            <td style="width: 4rem;">
                                <form method="POST" action="/deletartarefa" style="display: inline;" onsubmit="confirmarDelecao(event, this)">
                                    <input type="hidden" name="id" value="<%= tarefa.id %>">
                                    <button class="btn btn-danger">Deletar</button>
                                </form>
                            </td>
                        </tr>
                    </table>
                </div>
            </div>
        <% }); %>
    
        
    
        <footer>
            <%- include('../partials/footer'); %>
        </footer>
    
        <script>
            function confirmarDelecao(event, form) {
                event.preventDefault();
                let decision = confirm("Você realmente quer deletar esta tarefa?");
                if (decision) {
                    form.submit();
                }
            }
        </script>
    </body>
    </html>

**views/pages/tarefa.ejs**

    <!DOCTYPE html>
    <html lang="pt-br">
    <head>
        <%- include('../partials/head'); %>
    </head>
    <body>
        <header>
            <%- include('../partials/header'); %>
        </header>
    
        <div class="card">
            <div class="card-hearder">
                Criar Tarefa
            </div>
            <div class="card-body">
                <form method="POST" action="/salvartarefa">
                    <label>Título</label>
                    <input type="text" placeholder="Título" class="form-control" name="titulo">
                    <label>Descrição</label>
                    <textarea placeholder="Descreva sua tarefa aqui" class="form-control" name="descricao"></textarea>
                    <label>Data</label>
                    <input type="date" class="form-control" name="data">
                    <br>
                    <button class="btn btn-success">Enviar tarefa</button>
                </form>
            </div>
        </div>
    
        <footer>
            <%- include('../partials/footer'); %>
        </footer>
    </body>
    </html>

**database/database.js**

    const { Sequelize, DataTypes } = require('sequelize');
    
    const connection = new Sequelize('teste', 'root', 'root', {
        host: '127.0.0.1',
        dialect: 'mysql'
    });
    
    module.exports = connection;

**public/css/bootstrap.css**

Baixe o arquivo .css do Bootstrap [no site do projeto](https://getbootstrap.com/).

**tarefas/Tarefa.js**

    const { Sequelize, DataTypes } = require('sequelize');
    const connection = require('../database/database');
    
    const Tarefa = connection.define("Tarefa", {
        Titulo: {
            type: DataTypes.STRING,
            allowNull: false
        },
        Descricao: {
            type: DataTypes.STRING,
            allowNull: false
        },
        Data: {
            type: DataTypes.DATEONLY,
            allowNull: false
        }
    });
    
    Tarefa.sync().then(() => {});
    
    module.exports = Tarefa;

**tarefas/TarefaController.js**

    const express = require('express');
    const Tarefa = require ('./Tarefa');
    
    const router = express.Router();
    
    router.get('/tarefa', (req, res) => {
        res.render('pages/tarefa');
    });
    
    router.post('/salvartarefa', (req, res) => {
        let titulo = req.body.titulo;
        let descricao = req.body.descricao;
        let data = req.body.data;
    
        Tarefa.create({
            Titulo: titulo,
            Descricao: descricao,
            Data: data
        }).then(() => {
            res.redirect('/');
        });
    });
    
    router.post('/deletartarefa', (req, res) => {
        let id = req.body.id;
    
        if (id != undefined) {
            if (!isNaN(id)) {
                Tarefa.destroy({
                    where: {id: id}
                })
                .then(() => {
                    res.redirect('/');
                });
            }
            else {
                res.redirect('/');
            }
        }
        else {
            res.redirect('/');
        }
    });
    
    module.exports = router;

**index.js**

    const express = require('express');
    const ejs = require('ejs');
    
    const connection = require ('./database/database');
    
    const tarefaController = require ('./tarefas/TarefaController');
    
    const Tarefa = require ('./tarefas/Tarefa');
    
    const app = express();
    
    connection.authenticate()
        .then(() => {
            console.log('Conexão realizada com sucesso');
        })
        .catch((mensagemDeErro) => {
            console.log(mensagemDeErro);
        });
    
    app.set('view engine', 'ejs');
    app.use(express.static('public'));
    app.use(expresapp.use(express.urlencoded({extended: true}));
    app.use(express.json());s.urlencoded());
    
    app.use('/', tarefaController); // Tem que ficar após a declaração do urlencoded()
    
    app.get('/', (req, res) => {
        Tarefa.findAll({
            order: [
                ['id', 'DESC']
            ]
        }).then(tarefas => {
            res.render('pages/index', {
                tarefas: tarefas
            });
        });
    });
    
    app.listen(3000, () =>{
        console.log('Server iniciado na porta 3000');
    });

Agora vamos analisar as novidades:

    app.use(express.urlencoded({extended: true}));
    app.use(express.json());

`express.json()` and `express.urlencoded()` são para *requests* POST e PUT porque você está enviando dados que estão incluidos no *body* (como você viu no `req.body`), não para *requests* GET e DELETE. O `express.json()` é um método que reconhece *Request Objects* do tipo JSON enquanto o `express.urlencoded()` é um método que reconhece *Request Objects* do tipo *string* or *array*.

O `extended` informa ao framework Express qual biblioteca utilizar para fazer o *parsing* do conteúdo, se for *true* usará a biblioteca [qs](https://www.npmjs.com/package/qs), se for *false* usará [query-string](https://www.npmjs.com/package/query-string). A diferença é que o `qs` permite o qs permite o aninhamento de objetos da mesma forma feita pelo JSON.

    app.use('/', tarefaController);

Este aqui é para tratar dos caminhos. O `'/'` aqui serve como prefixo, se fosse "/x", para acessar /tarefa eu teria que digitar "*nomedosite.com/x/tarefa*"

    const router = express.Router();

O `express.Router` permite criar manipuladores de rotas. É como o `const app = express();`, o `const router = express.Router();` retorna um miniaplicativo, a ideia é que cada miniaplicativo desses possa se tornar mais complexo e você poderá mover todo esse código para um arquivo separado. Por exemplo, posso pôr rotas em um arquivo `gatos.js` e exportá-los (`module.exports = router;`) para o arquivo principal que os chamaria (`const gatos = require('/routes/gatos'); app.use('/gatos', gatos)`)

    router.post('/salvartarefa', (req, res) => {

O `router.post` *(bem como o `app.post` no caso de que se tudo estivesse dentro de `index.js`)* serve para ações POST do HTML.

    let titulo = req.body.titulo;
    let descricao = req.body.descricao;
    let data = req.body.data;

Os valores (`name`) de umformulário serão "capturados" por `req.body`.

    res.redirect('/');

Bem óbvio, né? Redireciona para a rota estabelecida no parâmetro desse método.

## Projeto: REST API com Express.js e PostgreSQL<span id="nodejs_projetoapi"></span>

Tenha certeza que o servidor PostgreSQL está ativo e devidamente configurado.

Crie uma pasta onde você criará seu projeto e faça as configurações iniciais com o NPM

    npm init -y
    npm i express pg dotenv

**bd.sql**

    \c teste;
    
    CREATE TABLE users (
        user_id SERIAL PRIMARY KEY,
        user_name VARCHAR(255) UNIQUE NOT NULL
    );
    
    CREATE TABLE todos (
        todo_id SERIAL PRIMARY KEY,
        todo_description TEXT NOT NULL,
        todo_done BOOLEAN NOT NULL,
        user_id INT NOT NULL,
        FOREIGN KEY (user_id) REFERENCES users (user_id)
    );
    
    INSERT INTO users (user_name) VALUES ('Marcelino');
    INSERT INTO users (user_name) VALUES ('Cláudia');
    INSERT INTO users (user_name) VALUES ('João'); 

**.env**

    POSTGRES_URL = postgres://meunome:12345@localhost:5432/teste

**src/index.js**

    const express = require('express')
    const { Pool } = require('pg')
    require('dotenv').config()
    
    const app = express()
    
    const PORT = 3333
    
    const pool = new Pool({
        connectionString: process.env.POSTGRES_URL
    })
    
    app.use(express.json())
    
    app.get('/', function (req, res) {
        res.send("Página inicial")
    })
    
    app.get('/users', async (req, res) => {
        try {
            const { rows } = await pool.query('SELECT * FROM users')
            return res.status(200).send(rows)
        }
        catch (err) {
            return res.status(400).send(err)
        }
    })
    
    app.post('/session', async (req, res) => {
        const { username } = req.body
    
        let user = ''
    
        try {
            user = await pool.query('SELECT * FROM users WHERE user_name = ($1)', [username])
            if (!user.rows[0]) {
                // Esse RETURNING * é só para que quando usarmos o Postman ou programa parecido, volte pra gente o que inserimos
                const user = await pool.query('INSERT INTO users (user_name) VALUES ($1) RETURNING *', [username])
            }
            return res.status(200).send(user.rows)
        }
        catch (err) {
            return res.status(400).send(err)
        }
    
    })
    
    app.get('/todo/:user_id', async (req, res) => {
        const { user_id } = req.params
        try {
            const allTodos = await pool.query('SELECT * FROM todos WHERE user_id = ($1)', [user_id])
            return res.status(200).send(allTodos.rows)
        }
        catch (err) {
            return res.status(400).send(err)
        }
    })
    
    app.post('/todo/:user_id', async (req, res) => {
        const { description, done } = req.body
        const { user_id } = req.params
        try {
            const newTodo = await pool.query('INSERT INTO todos (todo_description, todo_done, user_id) VALUES ($1, $2, $3) RETURNING *', [description, done, user_id])
            return res.status(200).send(newTodo.rows)
        }
        catch (err) {
            return res.status(400).send(err)
        }
    })
    
    app.patch('/todo/:user_id/:todo_id', async (req, res) => {
        const { todo_id, user_id } = req.params
        const data = req.body
        try {
            const belongsTo = await pool.query('SELECT * FROM todos WHERE user_id = ($1) AND todo_id = ($2)', [user_id, todo_id])
            if (!belongsTo.rows[0]) {
                return res.status(400).send("Operação não permitida")
            }
            const updatedTodo = await pool.query('UPDATE todos SET todo_description = ($1), todo_done = ($2) WHERE todo_id = ($3) RETURNING *', [data.description, data.done, todo_id])
            return res.status(200).send(updatedTodo.rows)
        }
        catch (err) {
            return res.status(400).send(err)
        }
    })
    
    app.delete('/todo/:user_id/:todo_id', async (req, res) => {
        const { todo_id, user_id } = req.params
        try {
            const belongsTo = await pool.query('SELECT * FROM todos WHERE user_id = ($1) AND todo_id = ($2)', [user_id, todo_id])
            if (!belongsTo.rows[0]) {
                return res.status(400).send("Operação não permitida")
            }
            const deletedTodo = await pool.query('DELETE FROM todos WHERE todo_id = ($1) RETURNING *', [ todo_id])
            return res.status(200).send({
                message: "TODO deletado com sucesso",
                deletedTodo: deletedTodo.rows
            })
        }
        catch (err) {
            return res.status(400).send(err)
        }
    })
    
    app.listen(PORT, () => console.log(`Server running on the port ${PORT}`))

## Conclusão<span id="nodejs_conclusao"></span>

Acho que você já tem uma boa base, a partir daqui sugiro o seguinte curso gratuito:

* [30 days of Node](https://www.nodejsera.com/30-days-of-node.html)