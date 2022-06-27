**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [Emscripten](#emscripten)

	* [Instalação](#emscripten_install)

		* [Se você usa Linux](#emscripten_install_linuxl)

		* [Se você usa Windows](#emscripten_install_windows)

		* [Pós-instalação](#emscripten_install_pos)

	* [Compilação](#emscripten_compile)

		* [Compilação de múltiplos arquivos](#emscripten_compile_mult)

	* [Como chamar código compilado do C/C++ a partir do JavaScript](#emscripten_jscalls)

# Introdução<span id="intro"></span>

Leia o [README](README.md).

# Emscripten<span id="emscripten"></span>

## Instalação<span id="emscripten_install"></span>

tenha certeza de ter os softwares listados abaixo instalados:

* Git

* Python

	* Se você usa Windows, sugiro que você instale a versão do Python da Windows Store, para fazer isso da forma mais fácil, tente rodar o comando `python` no prompt de comando que o próprio Windows abrirá a Windows Store pra você com a página do Python já aberta. De qualquer forma, o importante é que o comando `python` esteja funcionando no prompt de comando.

* Node.js *(não é obrigatório, mas é bom ter)*

Baixe o Emscripten:

    git clone https://github.com/emscripten-core/emsdk.git
    cd emsdk

### Se você usa Linux<span id="emscripten_install_linux"></span>

    git pull
    ./emsdk install latest
    ./emsdk activate latest
    source ./emsdk_env.sh

### Se você usa Windows<span id="emscripten_install_windows"></span>

    git pull
    emsdk install latest
    emsdk activate latest
    emsdk_env.bat

Adicione as pasta onde você instalou o Emscripten ao PATH do sistema se um dos comandos anteriores não fez este trabalho.

No Windows 10, abra as configurações => Sistema => Sobre => Configurações avançadas do sistema => Variáveis do ambiente = *Selecione `Path`* e aperte no botão `Editar`. Você poderá seguir daqui

Considere `~` como o caminho para a pasta do Emscripten, por exemplo, se instalo Emscripten em `C:\Program Files\emsdk`, aqui o referenciarei por `~\emsdk` para que você possa adequar as informações deste tutoria à sua realidade. Bom, adicione os dois endereços abaixo ao PATH:

* ~\emsdk

* ~\emsdk\upstream\emscripten

* <span style="color: red;">*Você se lembrou de substituir o `~`, né?*</span>

### Pós-instalação<span id="emscripten_install_pos"></span>

Para verificar se tudo deu certo, tente rodar o comando `emcc -v`.

## Compilação<span id="emscripten_compile"></span>

Entre na pasta onde se encontra o arquivo a ser compilado e use ou o comando `emcc` *(para códigos em C)* ou o comando `em++` *(para códigos em C++)*. Vamos dizer que temos o seguinte arquivo:

**main.cpp**

    #include <iostream>
    
    int main () {
        std::cout << "Olá mundo" << std::endl;
    }

Na pasta onde se encontra esse arquivo, rode o comando abaixo:

    em++ main.cpp

No meu caso aqui, o *output* foi nomeado como `a.out.js`. Se foi direrente para você, então adapte o comando seguinte ao seu contexto. A propósito, usamos o comando `em++` porque compilamos um código C++, se fosse um código em C, o comando seria `emcc`

Para rodar o programa, use o Node.js:

    node a.out.js

Agora vamos criar um *output* que inclui um arquivo HTML:

    em++ main.cpp -o index.html --emrun

Muitos navegadores não permitem rodar o wasm se o endereço vem da URL `file://``. Mas não tem problemas, o próprio Emscripten nos fornece um comando para criar um servidor.

    emrun index.html

### Compilação de múltiplos arquivos<span id="emscripten_compile_mult"></span>

*Antes de continuarmos, lembre-se que usarei o comando `em++` porque meus códigos são em C++, se fossem em C o comando seria `emcc`*.

Vamos dizer que temos o seguinte código fonte:

**main.cpp**

    #include <iostream>
    #include "conta.h"
    
    int main () {
        std::cout << soma(5,8) << std::endl;
    }

**conta.cpp**

    #include "conta.h"
   
    int soma(int x, int y) {
    	return x + y;
    }

**conta.h**

    #ifndef CONTA_H
    #define CONTA_H
    
    int soma(int x, int y);
    
    #endif

Da mesma forma que você faria como tradicional compilador `g++`, você compila múltiplos arquivos desta forma:

    em++ main.cpp conta.cpp

Então você poderá testar o resultado com o node.js (ou com seu navegador se você adicionou o output como uma página HTML)

## Como chamar código compilado do C/C++ a partir do JavaScript<span id="emscripten_jscalls"></span>

Eis os nossos arquivos:

**numeracao.cpp**

    #include <emscripten.h>
    
    extern "C" {
    
    	int EMSCRIPTEN_KEEPALIVE numero () {
    		return 2;
    	} 
    
    }

**index.html**

    <DOCTYPE html>
    <html>
    	<head>
    		<title>Teste de Emscripten</title>
    		<script src="numeracao.js"></script>
    	</head>
    	<body>
    		<p>Abra o inspecionador do seu navegador para ver se a mensagem de console.log exibe o resultado esperado</p>
    		<script>
    			Module.onRuntimeInitialized = () => {
    				var resultado = Module.ccall('numero', 'number', null, null);
    				console.log(resultado);
    			}
    		</script>
    	</body>
    </html>

Para compilar o código cpp, use o comando abaixo:

    em++ numeracao.cpp -o numeracao.js -sEXPORTED_RUNTIME_METHODS=ccall

E então rode o comando para criar um servidor para `index.html`

    emrun index.html

Agora vamos tentar entender esse código:

    #include <emscripten.h>

Dispensa explicação, é o include que insere as funções e métodos necessários para a execução do Emscripten.

    extern "C" { ... }

No C++, como os nomes das funções podem ser sobrecarregados, então o compilador modifica os nomes das funções para garantir que eles sejam únicos. Isso é um problema em um contexto que um código externo quer chamar uma função C++ porque o nome da função não existirá mais. `extern "C" { ... }` simplesmente diz para o compilador não modificar os nomes, porque os chamaremos através do código do JavaScript.

Já `EMSCRIPTEN_KEEPALIVE` adiciona a função à lista de funções exportadas. Se não quisermos utilizá-lo no código, teríamos que adicionar o parâmetro `-s EXPORTED_FUNCTIONS=_numero` no comando `em++`.

    var resultado = Module.ccall('numero', 'number', null, null);

Guarda o retorno da função `numero()` na variável JavaScript `resultado`. Veja a estrutura do método `Module.ccall()`.

    Module.ccall(
        '<nome_da_função>',
        '<tipo_da_função>',
        ['<tipo_do_argumento_1>', '<tipo_do_argumento_2>', 'etc'],
        [argumento_1, argumento_2, etc]
    )

Vamos prosseguir.

    Module.onRuntimeInitialized = () => { ... }

Chamar uma função antes da página estar carregada pode resultar em erro do tipo `native function `x` called before runtime initialization`. É preciso fazer a função esperar a inicialização do runtime. O método `Module.onRuntimeInitialized` nos auxilia nisso.

<br>

Vamos brincar um pouco mais:

**palavra.cpp**

    #include <emscripten.h>
    
    double x {0.0};
    
    extern "C" {
    
    	int EMSCRIPTEN_KEEPALIVE numero () {
    		return 2;
    	}
    	
    	char* EMSCRIPTEN_KEEPALIVE texto () {
    		return "Olá mundo";
    	}
    	
    	void EMSCRIPTEN_KEEPALIVE mudaVariavel (double novoNumero) {
    		x = novoNumero;
    	}
    	
    	double EMSCRIPTEN_KEEPALIVE verVariavel() {
    		return x;
    	}
    	
    	int EMSCRIPTEN_KEEPALIVE soma (int a, int b) {
    		return a + b;
    	}
    	
    }

**index.html**

    <!DOCTYPE html>
    <html>
    	<head>
    		<title>Teste de Emscripten</title>
    		<script src="palavra.js"></script>
    	</head>
    	<body>
    		<p>Abra o inspecionador do seu navegador para ver se a mensagem de console.log</p>
    		<script>
    			Module.onRuntimeInitialized = () => {
    				var resultado1 = Module.ccall('numero', 'numer', null, null);
    				var resultado2 = Module.ccall('texto', 'string', null, null);
    				Module.ccall('mudaVariavel', null, 'number', [5.8]);
    				var resultado3 = Module.ccall('verVariavel', 'number', null, null);
    				var resultado4 = Module.ccall('soma', 'number', ['number', 'number'], [9, 2]);
    				console.log(resultado1);
    				console.log(resultado2);
    				console.log(resultado3);
    				console.log(resultado4);
    			}
    		</script>
    	</body>
    </html>

## Inclusão condicional<span id="emscripten_"></span>

As vezes queremos usar nosso código para outros contextos que não a compilação para WebAssembly. Por exemplo, quero reusar meu código para dektop (Linux, Windows, MacOS) ou mobile (Android, iOS). Eu poderia remover as partes referentes ao Emscripen, mas isso seria trabalho, felizmente podemos usar diretivas do C/C++ que tornam nosos código mais portável.

**main.cpp**

    #include <iostream>
    
    #ifdef __EMSCRIPTEN__
    #include <emscripten.h>
    #endif
    
    #ifndef __EMSCRIPTEN__
    int soma (int x, int y);
    
    
    int main () {
    	
    	int numero1 {0}, numero2 {0};
    	
    	std::cout << "Insira o primeiro número da soma: ";
    	std::cin >> numero1;
    	std::cout << "\n";
    	
    	std::cout << "Insira o segundo número da soma: ";
    	std::cin >> numero2;
    	std::cout << "\n";
    	
    	std::cout << "O resultado da soma é " << soma(numero1, numero2) << std::endl;
    	
    }
    #endif
    
    #ifdef __EMSCRIPTEN__
    extern "C" {
    #endif
    
    #ifdef __EMSCRIPTEN__
    EMSCRIPTEN_KEEPALIVE
    #endif
    int soma (int x, int y) {
        return x + y;
    }
    
    #ifdef __EMSCRIPTEN__
    }
    #endif

**index.html**

    <!DOCTYPE html>
    <html>
    	<head>
    		<meta charset="UTF-8">
    		<title>Teste de Emscripten</title>
    		<script src="main.js"></script>
    	</head>
    	<body>
    		<form>
    			<label for="numero1">Insira o primeiro número da soma:</label>
    			<input type="number" id="numero1" name="numero1" placeholder="Insira um número inteiro">
    			
    			<br><br>
    			
    			<label for="numero2">Insira o segundo número da soma:</label>
    			<input type="number" id="numero2" name="numero2" placeholder="Insira um número inteiro">
    			
    			<br><br>
    			
    			<button onclick="somar()" type="button" >Somar</button>
    		</form>
    		
    		<br><br>
    		
    		<span style="font-size: 3rem;"><strong>Resultado: </strong> <span id="resultado"></span></span>
    		
    		<script>
    			
    			function somar() {
    			
    				var numero1 = parseInt(document.getElementById("numero1").value, 10);
    				var numero2 = parseInt(document.getElementById("numero2").value, 10);
    				
    				var resultado = Module.ccall('soma', 'number', ['number', 'number'], [numero1, numero2]);
    				
    				document.getElementById("resultado").innerHTML = resultado;
    			}
    		</script>
    	</body>
    </html>