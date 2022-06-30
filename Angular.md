**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [Angular](#angular)

	* [Instalação](#angular_install)

	* [O básico](#angular_basic)

	* [Geração de componentes](#angular_componentgeneration)

	* [Geração de classes](#angular_classgeneration)

	* [Integrando o Bootstrap no projeto](#angular_bootstrap)

	* [Condicionais](#angular_conditionals)

	* [Transformaãço de dados com Angular Pipes](#angular_pipe)

# Introdução<span id="intro"></span>

Leia o [README](README.md).

# Angular<span id="angular"></span>

## Instalação<span id="angular_install"></span>

Para instalar, você precisa anter ter o Node.js e NPM instalados em sua máquina, tenha certeza de ter a última versão LTS.

Para instalar o Angular, rode o seguinte comando:

    npm install -g @angular/cli

<span style="color: red;">*Se você usa Linux, não se esqueça de adiconar o `sudo`*</span>

## O básico<span id="angular_basic"></span>

Pronto, para ver a versão instalada, use o comando:

    ng version

Para ver a lista de comandos:

    ng help

Para rodar o Angular, entramos na pasta onde ele se encontra e rodamos o comando...

    ng serve

...que faz:

1. Construção do aplicativo (compilação,/transpilação)

2. Inicia o servidor

3. Olha os arquivos-fonte

4. Reconstrói o aplicativo quando a fonte é atualizada *(hot reload)*

No Windows, tive problemas de permissão para rodar esse comando do `ng serve`, mas a solução é simples, qualquer problema basta usar o comando abaixo:

    npm run ng serve

Por padrão, o servidor roda na porta 4200. Para facilitar, podemos usar o comando `ng serve --open` que abre o navegador pra gente. Para mudar a porta, basta usar o parâmetro `--port`, por exemplo, `ng server --port 5102`

Para criar um novo projeto, usamos o comando

    ng new <nome-do-seu-projeto>

Com o projeto criado, você pode rodar o comando `ng serve` para rodar a aplicação.

Para editar a página inicial, vá em `src/app/app.component.html`. Geralmente as pessoas deletam todo o conteúdo desta pasta. Procure pela linha `<span>{{ title }} app is running!</span>` só para você ter conhecimento dela e compare com o que é mostrado no navegador.

Abra o arquivo `src/index.html` para eu explicar uma coisa:

    <!doctype html>
    <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>Hello</title>
      <base href="/">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <link rel="icon" type="image/x-icon" href="favicon.ico">
    </head>
    <body>
      <app-root></app-root>
    </body>
    </html>

Repare esse `<app-root></app-root>`. Abra agora o arquivo `src/app/app.component.ts`:

    import { Component } from '@angular/core';
    
    @Component({
      selector: 'app-root',
      templateUrl: './app.component.html',
      styleUrls: ['./app.component.css']
    })
    export class AppComponent {
      title = 'hello';
    }

O `<app-root></app-root>` faz referência ao `selector: 'app-root'`. O arquivo `app.component.ts`, inclusive, faz referência ao arquivo `app.component.html` por meio da linha `templateUrl: './app.component.html'`, ele também interage com o template HTML em `export class AppComponent {title = 'hello';}` *(está lembrado de `title`?)*.

OK, edite o arquivo `app.component.html` para que ele fique assim:


    <h1>Lista de estudantes</h1>

	<p>O título desta aplicação é {{title}}.</p>

## Geração de componentes<span id="angular_componentgeneration"></span>

No terminal, criaremos um novo componente chamado `lista`

    ng generate component lista

Abra o arquivo `lista.component.ts`. Copie o valor de `selector` *(no caso aqui, foi `app-lista`)*. Com base nesse selector, você criará uma tag no arquivo `app.component.html`:

      <h1>Lista de estudantes</h1>
    
      <app-lista></app-lista>

## Geração de classes<span id="angular_classgeneration"></span>

No terminal, criaremos uma nova classe chamada `estudante` dentro do componente `lista`

    ng generate class lista/estudante

No arquivo `estudante.js`, tenha o seguinte conteúdo

    export class Estudante {
    
        constructor(public nome: string,
                    public sobrenome: string,
                    public idade: number,
                    public score: number) {
                        
                    }
    }

Vá para o arquivo `lista.component.ts`, dentro de `export class ListaComponent implements OnInit {...}`, logo no início, antes de `constructor() { }`, ponha o seguinte conteúdo:

    listaDeEstudantes: Estudante[] = [
        new Estudante ("Cuca", "Beludo", 15, 6.5),
        new Estudante ("Joana", "Vitória", 14, 8.0),
        new Estudante ("Thiago", "Potter", 15, 7.9),
        new Estudante ("Vinícius", "Olivieira", 15, 9.8),
        new Estudante ("Mara", "Madre", 14, 9.0)
      ];

Se você estiver usando uma boa IDE, talvez ela automaticamente adicione o import da classe Estudante, mas caso não o faça, aqui está o import:

    import { Estudante } from './estudante/estudante';

Abra o arquivo `lista.component.html` e adicione o seguinte conteúdo:

    <table border="1">
        <thead>
            <tr>
                <th>Nome</th>
                <th>Sobrenome</th>
                <th>Idade</th>
                <th>Score</th>
            </tr>
        </thead>
        <tbody>
            <tr *ngFor="let estudanteTemp of listaDeEstudantes">
                <td>{{estudanteTemp.nome}}</td>
                <td>{{estudanteTemp.sobrenome}}</td>
                <td>{{estudanteTemp.idade}}</td>
                <td>{{estudanteTemp.score}}</td>
            </tr>
        </tbody>
    </table>

## Integrando o Bootstrap no projeto<span id="angular_bootstrap"></span>

**index.html**

    <!doctype html>
    <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>Hello</title>
      <base href="/">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-0evHe/X+R7YkIZDRvuzKMRqM+OrBnVFBL6DOitfPri4tjfHxaWutUpFmBp4vmVor" crossorigin="anonymous">
      <link rel="icon" type="image/x-icon" href="favicon.ico">
    </head>
    <body>
      <app-root></app-root>
    </body>
    </html>

**app.component.html**

    <div class="container">
      <h1 class="mt-3 mb-3">Lista de estudantes</h1>
    
      <app-lista></app-lista>
    </div>

**lista.component.html**

    <table class="table table-hover">
        <thead class="table-dark">
            <tr>
                <th>Nome</th>
                <th>Sobrenome</th>
                <th>Idade</th>
                <th>Score</th>
            </tr>
        </thead>
        <tbody>
            <tr *ngFor="let estudanteTemp of listaDeEstudantes">
                <td>{{estudanteTemp.nome}}</td>
                <td>{{estudanteTemp.sobrenome}}</td>
                <td>{{estudanteTemp.idade}}</td>
                <td>{{estudanteTemp.score}}</td>
            </tr>
        </tbody>
    </table>

## Condicionais<span id="angular_conditionals"></span>

    <table class="table table-hover">
        <thead class="table-dark">
            <tr>
                <th>Nome</th>
                <th>Sobrenome</th>
                <th>Idade</th>
                <th>Score</th>
                <th>Destino</th>
            </tr>
        </thead>
        <tbody>
            <tr *ngFor="let estudanteTemp of listaDeEstudantes">
                <td>{{estudanteTemp.nome}}</td>
                <td>{{estudanteTemp.sobrenome}}</td>
                <td>{{estudanteTemp.idade}}</td>
                <td>{{estudanteTemp.score}}</td>
    
                <td>
                    <div *ngIf="estudanteTemp.score >= 8.0 else meuElse">Passou</div>
                    <ng-template #meuElse>Vai pra recuperação</ng-template>
                </td>
            </tr>
        </tbody>
    </table>

## Transformaãço de dados com Angular Pipes<span id="angular_pipe"></span>

Um *[pipe](https://angular.io/guide/pipes)*, em Angular, é um transformador de dados. Como deixar letras maiúsculas em minúsculas e vice e versa, adapta numeração a sistema monetário e coisas do tipo.

No nosso caso aqui, os números fracionários dos *scores* estão formatados com pontos *(convenção de países anglófonos)* em vez de vírgulas *(nossa convenção)*, vamos corrigir isso já que o texto está em português.

**lista.component.html**

    <table class="table table-hover">
        <thead class="table-dark">
            <tr>
                <th>Nome</th>
                <th>Sobrenome</th>
                <th>Idade</th>
                <th>Score</th>
                <th>Destino</th>
            </tr>
        </thead>
        <tbody>
            <tr *ngFor="let estudanteTemp of listaDeEstudantes">
                <td>{{estudanteTemp.nome}}</td>
                <td>{{estudanteTemp.sobrenome}}</td>
                <td>{{estudanteTemp.idade}}</td>
                <td>{{estudanteTemp.score | number:'1.2-2':'pt-BR'}}</td>
    
                <td>
                    <div *ngIf="estudanteTemp.score >= 8.0 else meuElse">Passou</div>
                    <ng-template #meuElse>Vai pra recuperação</ng-template>
                </td>
            </tr>
        </tbody>
    </table>

Para que o *locale* funcione, precisamos adicionar algumas coisas no nosso arquivo `app.module.ts`:

    import { NgModule, LOCALE_ID } from '@angular/core';
    import { BrowserModule } from '@angular/platform-browser';
    
    import { AppComponent } from './app.component';
    import { ListaComponent } from './lista/lista.component';
    import ptBr from '@angular/common/locales/pt';
    import { registerLocaleData } from '@angular/common';
    registerLocaleData(ptBr)
    
    @NgModule({
      declarations: [
        AppComponent,
        ListaComponent
      ],
      imports: [
        BrowserModule
      ],
      providers: [],
      bootstrap: [AppComponent]
    })
    export class AppModule { }

