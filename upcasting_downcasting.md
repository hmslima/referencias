**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [Type casting com classes](#typecasting)

	* [Upcasting](#typecasting_upcasting)

	* [Downcasting](#typecasting_downcasting)

	* [Exemplo](#typecasting_exemplo)

	* [Qual é o propósito do upcasting e downcasting?](#typecasting_proposito)

# Introdução<span id="intro"></span>

*Type casting* é o processo de conversão de um tipo de dado em outro.

O *casting* pode ser feito de forma implícita ou explícita. Na forma implícita, basta fazer uma simples atribuição:

    public class Main {
        public static void main(String[] args) {
            int x = 2;
            double y = x;
            
        
            System.out.println(x); // Saída: 2
            System.out.println(y); // Saída: 2.0
        }
    }

A forma explícita exige o uso de um *casting* no código como `(int)`, `(double)`:

    public class Main {
    
        public static void main(String[] args) {
            double x = 2.5;
            int y = (int) x;
		
            System.out.println(x); // Saída: 2.5
            System.out.println(y); // Saída: 2
        }
    }

O *casting* implícito *(isto é, automático)* ocorre quando convertemos de um tipo menor para um maior.

byte ⇒ short ⇒ char ⇒ int ⇒ long ⇒ float ⇒ double

O *casting* explícito *(isto é, manual)* ocorre quando convertemos de um tipo maior para um menor.

double ⇒ float ⇒ long ⇒ int ⇒ char ⇒ short ⇒ byte


# Type casting com classes<span id="typecasting"></span>

O mesmo processo pode ser feito com classes, é um processo que envole o relacionamento de herança entre as classes envolvidas.

## Upcasting<span id="typecasting_upcasting"></span>

Quando o *casting* é feito de uma classe filha para sua respectiva classe mãe. O *upcasting* pode ser feito de forma implícita.

    class Pai {}
    
    class Filho extends Pai {}
    
    public class Main {
    
        public static void main(String[] args) {
            Pai p = new Filho();
        }
    }

## Downcasting<span id="typecasting_downcasting"></span>

Quando o *casting* é feito de uma classe mãe para uma de suas classes filhas. O *downcasting* só pode ser feito de forma explícita.

    class Pai {}
    
    class Filho extends Pai {}
    
    public class Main {
    
        public static void main(String[] args) {
            Pai p = new Pai();
            Filho f = (Filho) p;
        }
    }

## Exemplo<span id="typecasting_exemplo"></span>


    import java.util.ArrayList;
    import java.util.List;
    
    class Pai {
        public String name;
        public int age;
        
        public void dizer () {
            System.out.println("Eu sou um pai");
        }
    }
    
    class Filho extends Pai {
        public String nomeDoMelhorAmigo = "Bruno";
        
        @Override
        public void dizer () {
            System.out.println("Eu sou um filho");
        }
        
        public void amizade () {
            System.out.println("O nome do melhor amigo é " + this.nomeDoMelhorAmigo);
        }
    }
    
    class Filha extends Pai {
        public String nomeDoMelhorAmigo = "Ana";
        
        @Override
        public void dizer () {
            System.out.println("Eu sou uma filha");
        }
        
        public void amizade () {
            System.out.println("O nome do melhor amigo é " + this.nomeDoMelhorAmigo);
        }
    }
    
    public class Main {
    
        public static void main(String[] args) {
            
            // Instanciação normal
            Filho c = new Filho();
            c.dizer();
            c.amizade();
            
            System.out.println("--------------");
            
            // Upcasting
            Pai p = new Filho();
            p.dizer();
            //p.amizade(); // Não posso executar este método porque Pai não o tem
            
            Pai p2 = new Filha();
            p2.dizer();
            
            System.out.println("--------------");
            
            // Downcasting
            Filho c2 = (Filho) p; // Só é possível através de um casting explícito que pe o (Filho)
            c2.dizer();
            c2.amizade();
            
            System.out.println("--------------");
            System.out.println("--------------");
            System.out.println("--------------");
            
            // Mixing everything
            List<Pai> familia = new ArrayList<Pai>();
            familia.add(c);
            familia.add(p);
            familia.add(p2);
            familia.add(c2);
            
            for (Pai member : familia) {
                member.dizer();
            }
        }
    }

A saída do código logo acima é a seguinte:

> Eu sou um filho
> 
> O nome do melhor amigo é Bruno
> 
> --------------
> 
> Eu sou um filho
> 
> Eu sou uma filha
> 
> --------------
> 
> Eu sou um filho
> 
> O nome do melhor amigo é Bruno
> 
> --------------
> --------------
> --------------
> Eu sou um filho
> 
> Eu sou um filho
> 
> Eu sou uma filha
> 
> Eu sou um filho

Olha só que interessante, ainda que o objeto seja do tipo `Pai`, ele herdou os valores de atributos e instruções de métodos das classes filhas `Filho`/`Filha`.

    // Upcasting
    Pai p = new Filho();
    p.dizer();
    //p.amizade(); // Não posso executar este método porque Pai não o tem

Entretanto, o objeto `p` não pode usar o método `amizade()` porque a classe mãe `Pai` não o possui.

## Qual é o propósito do upcasting e downcasting?<span id="typecasting_proposito"></span>

Uma coisa é saber **o que são** *upcasting* e *downcasting*, outra é entender **para que eles servem** na prática.

No caso do ***upcasting***, um objeto de um tipo mais específico pode ser usado numa situação que exige um tipo mais genérico. Vamos relembrar o nosso exemplo:

    [...]
    List<Pai> familia = new ArrayList<Pai>();
    familia.add(c);
    familia.add(p);
    familia.add(p2);
    familia.add(c2);
        
    for (Pai member : familia) {
        member.dizer();
    }
    [...]

Na lista `familia` pude adicionar objetos `c`, `p`, `p2` e `c2` todos juntos porque todos eles tecnicamente são do tipo `Pai`, ainda que uns deles tragam dentro de si valores e instruções das classes específicas `Filho` e `Filha`.

A propósito, é necessário o *upcasting* da classe `List` porque ela é uma interface, não pode ser instanciada. Você só pode criar uma lista de uma das duas formas abaixo:

    List<Pai> familia = new ArrayList<Pai>();

ou

    ArrayList<Pai> familia = new ArrayList<Pai>();

Nesse caso o *upcasting* por conta da reusabilidade. Por exemplo, se uso algo como...

    public void sort(ArrayList lst);

...,só poderei usar listas `ArrayList` como parâmetro. Entretanto, se eu usar...

    public void sort(List lst);

...terei maior flexibilidade.

A respeito do ***downcasting***, é muito usado em casos onde lhe é retornado um *factory objet* de um supertipo *(o tipo maior, da classe mãe)* e você quer converter esse objeto para um tipo mais específico no qual você tem um código mais customizado em que você poderá trabalhar com aquele objeto de forma mais específica.