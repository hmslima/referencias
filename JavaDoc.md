# Índice

* [Introdução](#javadoc_intro)

* [Uso](#javadoc_uso)

* [Geração da documentação](#javadoc_gerar)

# JavaDoc<span id="javadoc"></span>

## Introdução<span id="javadoc_intro"></span>


JavaDoc é uma ferramenta de geração de documentos em HTML para a linguagem Java, ou seja, ele gera uma API documentada por meio de comentários no meio do código.

Primeiros vamos relembrar como adicionamos comentários comuns na linguagem Java:

    // Comentário comum de uma linha
    
    /*
    * Comentário comum de múltiplas linhas
    */

Os comentários do JavaDoc são como os comuns de multilinhas, mas têm um asterisco a mais na primeira linha:

    /**
    * Comentário do JavaDoc
    */

## Uso<span id="javadoc_uso"></span>

Os comentários do JavaDoc são postos acima das classes e métodos que queremos documentar.

**Funcionario.java**

    package teste;
    /** <p>Esta classe lida com o cadastro de funcionários.</p> */
    public class Funcionario {
        /**
         * <p>Este método cria um funcionário</p>
         * @param nome O nome completo do funcionário
         * @param setor O setor onde o respectivo funcionário será alocado
         */
        public void CriarFuncionario (String nome, String setor) {
            // Algum código
        }
    }

Você jé deve ter reparado na `@param`. Há outras, elas ajudam a organizar melhor as informações

| Tag      | Descrição                                                         |
| -------- | ----------------------------------------------------------------- |
| @author  | Nome do autor                                                     |
| @param   | Descrição do parâmetro                                            |
| @see     | Gera um link                                                      |
| @version | Versão da classe, interface ou enumeração                         |
| @since   | Especifica em que versão a classe, campo ou método foi adicionado |
| @return  | Fornece uma descrição do que o método vai ou pode retornar        |
| @throws  | Explica os casos em que pode ocorrer uma exceção                  |
| @deprecated | Explica porque aquele pedaço de código se tornou obsoleto      | 

Mas nem todas as tags podem ser utilizadas em todos os lugares. `@author`, por exemplo, só pode ser utilizado em resumos, módulos, pacotes, classes e interfaces.

## Geração da documentação<span id="javadoc_gerar"></span>

Use o comando `javadoc` mais o nome do arquivo ou nome do pacote. 

    javadoc Funcionario.java

*Quando na mesma pasta que o arquivo.*

ou 

    javadoc simple

*Quando na mesma pasta `src`*