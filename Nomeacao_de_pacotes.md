**Autor:** Henrique Matheus da Silva Lima

# Nomeação de pacotes

Para evitar conflitos por conta dos nomes ds pacotes, existem algumas convenções para os nomes:

* Todas as letras devem estar em minúscula *(letras ASCII!)* para evitar conflito com nomes de classes ou interfaces

* As palavras são separadas por pontos

* Nomes são definidos com base na organização ou companhia a qual eles pertencem. Por exemplo, o pacote criado por um programador para `empresax.com.br`, do projeto `banco` será `br.com.empresax.banco`; percebe que é invertido?

Como dito em [Caelum](https://www.caelum.com.br/apostila-java-orientacao-objetos/pacotes-organizando-suas-classes-e-bibliotecas), o padrão da Sun é este:

> br.com.nomedaempresa.nomedoprojeto.subpacote
> br.com.nomedaempresa.nomedoprojeto.subpacote2
> br.com.nomedaempresa.nomedoprojeto.subpacote2.subpacote3

Por exemplo, o nome completo da classe `Funcionario` no pacote `br.com.empresax.banco` seria `br.com.empresax.banco.Funcionario`.

Cada pacote e subpacote tem seu diretório, para `br.com.empresax.banco` teríamos a estrutura de diretórios `br/com/empresax/banco` *(ou, usando a linguagem do Windows, a estrutura de pastas `br\com\empresax\banco`)*.

Se, por acaso, o nome do pacote conter uma palavra que contenha um elemento ilegal *(começa com um número, tem um caractere especial, possui hífen)*, adicione um sublinhado (_).

| Nome do domínio    | Nome do prefixo do pacote      |
| ------------------ | -------------------------------|
| ola-mundo.org      | org.ola_mundo                  |
| matematicos.int.br | br.int_.matematicos            |
| 5irmaos.com.br     | br.com._5irmaos                |

## Exemplo

**Funcionario.java**

    package br.com.exemplo.pessoal;
    
    public class Funcionario {
        String nome;
    }

**Execucao.java**

    package br.com.exemplo.pessoal;
    
    public class Execucao {
    
        public static void main(String[] args) {
            Funcionario funcionario = new Funcionario();
        }
    }

Se ambos os arquivos estão dentro do mesmo pacote, posso acessar outras classes livremente.

Entretanto, se a classe `Execucao` estivesse em um pacote diferente, eu teria que referenciar o nome do pacote da classe importada:

**Execucao.java**

    package br.com.exemplo.pessoal.app;
    
    public class Execucao {
    
        public static void main(String[] args) {
            br.com.exemplo.pessoal.Funcionario funcionario = new br.com.exemplo.pessoal.Funcionario();
        }
    }

Mas assim o código fica muito verboso, podemos melhorar isso através do `import`:

**Execucao.java**

    package br.com.exemplo.pessoal.app;
    
    import br.com.exemplo.pessoal.Funcionario;
    
    public class Execucao {
    
        public static void main(String[] args) {
            Funcionario funcionario = new Funcionario();
        }
    }