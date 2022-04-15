**Autor:** Henrique Matheus da Silva Lima

# índice

* [Node.js](#nodejs)

	* [Hello World](#nodejs_primeiroservidor)

	* [Um "Hello World" mais completo](#nodejs_primeiroservidor_maiscompleto)

	* [Servindo HTML para o cliente](#nodejs_primeiroservidor_html)

	* [Servindo JSON para o cliente](#nodejs_primeiroservidor_json)

* [Nossos próprios módulos](#nodejs_nmodulos)

* [Instalação de módulos com o NPM](#nodejs_npm)

* [Framework Express](#nodejs_express)

# Node.js<span id="nodejs"></span>


eeeeeeeeeeeeeeeeeeeee

Acesse [este site](https://nodejs.org/) para fazer o download do Node.js. PPra quem usa Linux: mesmo que você tenha o Node.js nos repositórios de sua distro, prefira baixar a versão LTS mais recente que está presente no site para evitar conflitos com dependências que venhamos a baixar, é claro que esse conselho é desnecessário para quem usa distros *rolling release*.

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

Nodemon é uma ferramenta interessante. Ela funciona da seguinte forma, toda vez que modificamos o nosso projeto, o servidor é recarregado automaticamente, sem precisarmos ter que ficar desligando e ligando o servidor toda hora pra ver se as atualizações funcionaram.

Instale o Nodemon ou como dependência...

    npm install nodemon --save-dev

...ou globalmente:

    npm install -g nodemon

Para executar seu aplicativo através do Nodemon, é só usar o comando abaixo:

    nodemon <seu_projeto>

No meu caso aqui, usei o comando `nodemon index.js`.

## Framework Express<span id="nodejs_express"></span>

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

A vantagem desse framework é que o routing é muito fácil:

    const express = require('express');
    const app = express();
    
    app.get('/', (req, res) => {
        res.send("Página inicial, clique <a href='contato'>aqui</a> para acessar a página de contatos");
    });
    
    app.get('/contato', (req, res) => {
        res.send("Contato");
    });
    
    app.listen(3000);