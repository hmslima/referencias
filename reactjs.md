**Autor:** Henrique Matheus da Silva Lima

# índice

* [Introdução](#intro)

* [React.js](#reactjs)

# Introdução<span id="intro"></span>

Leia o [README](README.md).

# React.js<span id="reactjs"></span>

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <script src="https://unpkg.com/react@18/umd/react.production.min.js" crossorigin></script>
        <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js" crossorigin></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/6.26.0/babel.min.js" crossorigin></script>
        <title>Frontend em React.js</title>
    </head>
    <body>
        <div id="root"></div>
        <script type="text/babel">
    
            const comidas = [
                "arroz",
                "feijão",
                "carne"
            ]
    
            function Header() {
                return (
                    <header>
                        <h1>Lista de Empregados</h1>
                    </header>
                )
            }
    
            function Main(props) {
                return (
                    <section>
                        <p>Empregado: olá, {props.name}</p>
                        <br />
                        <ul>
                            {comidas.map(comida => (<li>{comida}</li>))}
                        </ul>
                    </section>
                )
            }
    
            function App() {
                return (
                    <React.Fragment>
                        <Header />
                        <Main name="Matheus" />
                    </React.Fragment>
                )
            }
    
            ReactDOM.render(
                <App />,
                document.getElementById("root")
            )
    
        </script>
    </body>
    </html>

Ok, vamos entender as partes menos óbvias do código.

    <script type="text/babel">

É assim em vez de `<script type="text/javascript">` para que o Babel compile nosso conteúdo em JSX.

    <React.Fragment>...</React.Fragment>

Quando retornamos alguma coisa nas funções, tudo tem que estar empacotado num elemento como `<header></header>`, `<section></section>` ou `<div></div>`. O `<React.Fragment></React.Fragment>` simplesmente faz essa função e podemos abreviar para `<></>`

## Create react App

Existe o comando `ngx create-react-app <nome_do_projeto>` que cria 