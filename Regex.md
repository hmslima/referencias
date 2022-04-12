# Índice

* [RegEx](#regex)

# RegEx<span id="regex"></span>

*Regular Expressions* (ou "Expressões Regulares" em português) são uma sequência de caracteres que procuram por padrões. É bastante útil para realizar pesquisas em textos.

Vejamos um exemplo na linguagem Java:

    public class Main {
    
        public static void main(String[] args) {
            String texto = "O rato roeu as roupas do rei de Roma. 350 homens podem construir uma estrada em 2 meses.";
            
            System.out.println(texto.replaceAll("rato", "xxx")); // Qualquer ocorrência de "rato"
            System.out.println(texto.replaceAll(".", "x")); // Qualquer caractere
            System.out.println(texto.replaceAll("as+", "x")); // O caractere que precede o + pode ocorrer uma ou mais vezes ("as" ou "ass")
            System.out.println(texto.replaceAll("as*", "x")); // O caractere que precede o * pode ocorrer nenhuma ou mais vezes ("a", "as" ou "ass")
            System.out.println(texto.replaceAll("as?", "x")); // O caractere que precede o ? pode ocorrer nenhuma ou uma única vez. Esse é mais interessante se usado com agrupamento por parênteses, por exemplo, "roupa(s)?" representaria "roupa" ou "roupas"
            System.out.println(texto.replaceAll("^", "x")); // Qualquer ocorrência de um início de linha
            System.out.println(texto.replaceAll("$", "x")); // Qualquer ocorrência de um fim de linha
            System.out.println(texto.replaceAll("as", "x")); // Qualquer ocorrência de "as"
            System.out.println(texto.replaceAll("a|s", "x")); // Encontra "a" ou "s"
            System.out.println(texto.replaceAll("[as]", "x")); // Qualquer ocorrência de "a" "s"
            System.out.println(texto.replaceAll("[abc]", "x")); // Qualquer ocorrência de "a", "b" ou "c"
            System.out.println(texto.replaceAll("[aei][ns]", "x")); // Qualquer ocorrência de "a", "e" ou "i" seguido por "n" ou "s"
            System.out.println(texto.replaceAll("[^abc]", "x")); // Qualquer ocorrência que NÃO seja "a", "b" e "c"
            System.out.println(texto.replaceAll("[a-z]", "x"));  // Qualquer ocorrência de "a" a "z" (somente letras minúsculas)
            System.out.println(texto.replaceAll("[a-zA-Z]", "x"));  // Qualquer ocorrência de "a" a "z" (letras minúsculas e maiúsculas)
            System.out.println(texto.replaceAll("[0-9]", "x"));  // Qualquer ocorrência de "0" a "9"
            System.out.println(texto.replaceAll("[a-zA-Z]{4}", "x")); // Qualquer sequência de letras cujo tamanho seja 4
        }
    }

Saída:

> O xxx roeu as roupas do rei de Roma. 350 homens podem construir uma estrada em 2 meses.
> 
> xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
> 
> O rato roeu x roupx do rei de Roma. 350 homens podem construir uma estrada em 2 meses.
> 
> O rxto roeu x roupx do rei de Romx. 350 homens podem construir umx estrxdx em 2 meses.
> 
> O rxto roeu x roupx do rei de Romx. 350 homens podem construir umx estrxdx em 2 meses.
> 
> xO rato roeu as roupas do rei de Roma. 350 homens podem construir uma estrada em 2 meses.
> 
> O rato roeu as roupas do rei de Roma. 350 homens podem construir uma estrada em 2 meses.x
> 
> O rato roeu x roupx do rei de Roma. 350 homens podem construir uma estrada em 2 meses.
> 
> O rxto roeu xx roupxx do rei de Romx. 350 homenx podem conxtruir umx extrxdx em 2 mexex.
> 
> O rxto roeu xx roupxx do rei de Romx. 350 homenx podem conxtruir umx extrxdx em 2 mexex.
> 
> O rxto roeu xs roupxs do rei de Romx. 350 homens podem xonstruir umx estrxdx em 2 meses.
> 
> O rato roeu x roupx do rei de Roma. 350 homxs podem construir uma xtrada em 2 mxx.
> 
> xxxaxxxxxxxxaxxxxxxaxxxxxxxxxxxxxxxaxxxxxxxxxxxxxxxxxxxcxxxxxxxxxxxaxxxxxaxaxxxxxxxxxxxx
> 
> O xxxx xxxx xx xxxxxx xx xxx xx Rxxx. 350 xxxxxx xxxxx xxxxxxxxx xxx xxxxxxx xx 2 xxxxx.
> 
> x xxxx xxxx xx xxxxxx xx xxx xx xxxx. 350 xxxxxx xxxxx xxxxxxxxx xxx xxxxxxx xx 2 xxxxx.
> 
> O rato roeu as roupas do rei de Roma. xxx homens podem construir uma estrada em x meses.
> 
> O x x as xas do rei de x. 350 xns xm xxr uma xada em 2 xs.


## Tabelas<span id="regex_tabelas"></span>

| Modificador de repetição | Descrição                                         |
| ------------------------ | ------------------------------------------------- |
| +                        | Corresponde a pelo menos uma vez                  |
| ?                        | Corresponde a no máximo uma vez                   |
| *                        | Corresponde em qualquer vez                       |
| {x}                      | Corresponde a exatamente x vezez                  |
| {x,}                     | Corresponde a pelo menos x vezez                  |
| {x, z}                   | Corresponde a no mínimo x vezes e no máximo z vezes |

O `+` é um *placeholder* que significa um ou qualquer número de caracteres.

O `*` é um *placeholder* que significa nenhum ou qualquer número de caracteres.

O `?` é um *placeholder* que significa nenhum ou um caractere.


## Exemplo: Encontrando CPF

    public class Main {
    
        public static void main(String[] args) {
            String texto = "O CPF de Marcos Antônio ou é 634.086.910-61 ou é 634.086.10-61, tente descobrir qual é.";
            
            System.out.println(texto.replaceAll("[0-9]{3}.?[0-9]{3}.?[0-9]{3}-?[0-9]{2}", "x"));
        }
    }

Saída:

> O CPF de Marcos Antônio ou é x ou é 634.086.10-61, tente descobrir qual é.