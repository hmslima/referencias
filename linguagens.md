# índice

* [Comparação entre linguagens de programação](#linguagens)

	* [Hello World](#linguagens_helloworld)

	* [Arrays](#linguagens_arrays)

	* [Funções](#linguagens_functions)

	* [Classes](#linguagens_classes)

# Introdução

***Primeiramente, preciso deixar uma coisa clara:*** *nenhum desses códigos é meu, copiei tudo de todos os cantos da internet. Se você ver o seu código aqui e quiser que eu o retire, avise-me que farei isso sem demora.*

Este documento serve apenas para refrescar a minha memória, quando trabalhamos com muitas linguagens, é comum esquecermos certos detalhes da sintaxe ou usar as regras de uma sintaxe em outra linguagem.

Como é algo feito pra mim, não coloquei aqui todos os aspectos de uma linguagem, apenas do que sinto necessidade. O mesmo se diz das linguagens escolhidas, pus exemplos apenas das linguagens que me interessam.


# Comparação entre linguagens de programação<span id="linguagens"></span>

## Hello World<span id="linguagens_helloworld"></span>

### C

    #include <stdio.h>

    int main() {
        printf("Hello World");
        return 0;
    }

### C++ 

    #include <iostream>

    int main() {
        std::cout << "Hello World!";
        return 0;
    }

.

    #include <iostream>
    using namespace std;
    
    int main() {
        cout << "Hello, World!";
        return 0;
    }

### C#

    namespace HelloWorld
    {
        class Hello {
            static void Main(string[] args)
           {
                System.Console.WriteLine("Hello World");
            }
        }
    }

### Java

    package <nome_do_pacote>;
    
    // Tudo o que você precisar importar. No eclipse basta apertar Ctrl Shift O para importar tudo o que você precisa
    
    class <nome_do_arquivo> {
        public static void main (String[] args) {
           System.out.println("Hello World");
        }
    }

### Kotlin

    fun main(args: Array<String>){
        println("Hello World")
    }

### Dart

    void main() {
        print('Hello, World!');
    }

### JavaScript

    console.log('Hello World');

### PHP

    <!DOCTYPE html>
        <html>
        <body>
    
            <h1>My first PHP page</h1>
    
            <?php
                echo "Hello World!";
            ?>
    
        </body>
    </html> 

## Arranjos<span id="linguagens_arrays"></span>

### C/C++

    int myNumbers[] = {25, 50, 75, 100};

### C#

    string[] cars;

.

    string[] cars = {"Volvo", "BMW", "Ford", "Mazda"};


### Java

    int intArray[];    //declaring array
    intArray = new int[20];  // allocating memory to array

.

    int[] intArray = new int[20];

.

    int arr[] = {3, 1, 2, 5, 4};

.

    int intArray[] = {1,2,3};

.

    int[][] intArray = new int[10][20]; //a 2D array or matrix
    int[][][] intArray = new int[10][20][10]; //a 3D array

### Kotlin

    val num = arrayOf(1, 2, 3, 4)   //implicit type declaration
    val num = arrayOf<Int>(1, 2, 3) //explicit type declaration

.

    val num = intArrayOf(1, 2, 3, 4)

### Dart

    var arr = ['a','b','c','d','e'];

.

    var arr = new List(5);// creates an empty array of length 5

.

    List<String> strArr = ['hello', 'world'];

Arranjos são listas em Dart

### JavaScript

    const cars = ["Saab", "Volvo", "BMW"];

.

    const cars = [
      "Saab",
      "Volvo",
      "BMW"
    ];

### PHP

    $directors = array( "Alfred Hitchcock", "Stanley Kubrick", "Martin Scorsese", "Fritz Lang" );

.

    $movie = array( "title" => "Rear Window",
                    "director" => "Alfred Hitchcock",
                    "year" => 1954 );

.

    $myArray = array();

## Funções<span id="linguagens_functions"></span>

### C/C++

    int max(int num1, int num2) {
        int result;
        if (num1 > num2)
            result = num1;
        else
            result = num2;
    
        return result; 
    }

.

    void printDate(int month, int day, int year)
    {
        cout << "The date is " << month << '-' << day;
        cout << '-' << year << endl;
    }

### C#

*Na verdade são métodos em C#...*

    namespace Declaring_Method
    {
      class Program
       {
         string name, city;
         int age;
     
         // Creating method for accepting details
         public void acceptdetails()
          {
            Console.Write("\nEnter your name:\t");
            name = Console.ReadLine();
     
            Console.Write("\nEnter Your City:\t");
            city = Console.ReadLine();
     
            Console.Write("\nEnter your age:\t\t");
            age = Convert.ToInt32(Console.ReadLine());
          }
     
         // Creating method for printing details
         public void printdetails()
          {
            Console.Write("\n\n===================");
            Console.Write("\nName:\t" + name);
            Console.Write("\nCity:\t" + city);
            Console.Write("\nAge:\t" + age);
            Console.Write("\n===================\n");
          }
     
         static void Main(string[] args)
          {
            Program p = new Program();
            p.acceptdetails();
            p.printdetails();
            Console.ReadLine();
          }
       }
    }

### Java

*Na verdade são métodos em Java...*

    package com.techvidvan.methods;
    public class MethodDemo
    {
        //Program to find cube of a number using a method/function
        //Defining a function
        public static double getCube(double num)
        {
            double result = num * num * num;
            return result;
        }
        public static void main(String args[])
        {
            double number = 7.5, cube =0;
            // creating an instance of MethodDemo class
            MethodDemo demo = new MethodDemo();
            // calling getCube method using instance created in the above step
            cube = demo.getCube(number); //Control gets transferred to function definition
            System.out.println("The cube of " +number + " is: " +cube);
        }
    }

### Kotlin

    fun double(x: Int): Int {
        return 2 * x
    }

.

    fun printHello(name: String?): Unit {
        if (name != null)
            println("Hello $name")
        else
            println("Hi there!")
        // `return Unit` or `return` is optional
    }

### Dart

    void main() { 
        print(factorial(6));
    }  
    factorial(number) { 
        if (number <= 0) {     
            return 1; 
        } else { 
            return (number * factorial(number - 1));
        } 
    }

### JavaScript

    function multiplicar(p1, p2) {
        return p1 * p2;
    }

### PHP

    function writeMsg() {
        echo "Hello world!";
    }

.

    function addNumbers(int $a, int $b) {
        return $a + $b;
    }

## Classes<span id="linguagens_classes"></span>

### C++

    #include <bits/stdc++.h>
    using namespace std;
    class Geeks
    {
        // Access specifier
        public:
     
        // Data Members
        string geekname;
     
        // Member Functions()
        void printname()
        {
           cout << "Geekname is: " << geekname;
        }
    };
     
    int main() {
     
        // Declare an object of class geeks
        Geeks obj1;
     
       // accessing data member
        obj1.geekname = "Abhi";
     
        // accessing member function
        obj1.printname();
        return 0;
    }

.

    #include <iostream>
    using namespace std;
     
    class Point
    {
    private:
        int x, y;
     
    public:
        // Parameterized Constructor
        Point(int x1, int y1)
        {
            x = x1;
            y = y1;
        }
     
        int getX()
        {
            return x;
        }
        int getY()
        {
            return y;
        }
    };
     
    int main()
    {
        // Constructor called
        Point p1(10, 15);
     
        // Access values assigned by constructor
        cout << "p1.x = " << p1.getX() << ", p1.y = " << p1.getY();
     
        return 0;
    }

### Kotlin

    class Account {
        var acc_no: Int = 0
        var name: String =  ""
        var amount: Float = 0.toFloat()
        fun insert(ac: Int,n: String, am: Float ) {
            acc_no=ac
            name=n
            amount=am
            println("Account no: ${acc_no} holder :${name} amount :${amount}")
        }
      
        fun deposit() {
            //deposite code
        }
      
        fun withdraw() {
           // withdraw code
        }
      
        fun checkBalance() {
            //balance check code
         }
      
    }
    fun main(args: Array<String>){  
        Account()  
        var acc= Account()
        acc.insert(832345,"Ankit",1000f) //accessing member function
        println("${acc.name}") //accessing class property
    }

.

    class myClass{  
    
        constructor(name: String, id: Int){
            println("Name = ${name}")
            println("Id = ${id}")
        }
    }
    
    fun main(args: Array<String>){
        val myclass = myClass ("Ashu", 101)
    }

.

    class myClass(name: String, id: Int) {
        val e_name: String
        var e_id: Int
        init{  
            e_name = name.capitalize()
            e_id = id
  
            println("Name = ${e_name}")
            println("Id = ${e_id}")
        }
    }
    
    fun main(args: Array<String>){
        val myclass = myClass ("Ashu", 101)
    }

### Dart

    void main() { 
        Car c= new Car(); 
        c.disp(); 
    }  
    class Car {  
        // field 
        String engine = "E1001";  
        
        // function 
        void disp() { 
            print(engine); 
        } 
    }

.

    void main() { 
        Car c = new Car('E1001'); 
    } 
    class Car { 
        Car(String engine) { 
            print(engine); 
        } 
    }

### JavaScript

    class Car {
        constructor(name, year) {
            this.name = name;
            this.year = year;
        }
        age() {
            let date = new Date();
            return date.getFullYear() - this.year;
        }
    }
    
    let myCar = new Car("Ford", 2014);

### PHP

    <?php
    class Fruit {
        // Properties
        public $name;
        public $color;
    
        // Methods
        function set_name($name) {
            $this->name = $name;
        }
        function get_name() {
            return $this->name;
        }
    }
    
    $apple = new Fruit();
    $banana = new Fruit();
    $apple->set_name('Apple');
    $banana->set_name('Banana');
    
    echo $apple->get_name();
    echo "<br>";
    echo $banana->get_name();
    ?>

.

    <?php
    class Fruit {
        public $name;
        public $color;
    
        function __construct($name) {
            $this->name = $name;
        }
        function get_name() {
            return $this->name;
        }
    }
    
    $apple = new Fruit("Apple");
    echo $apple->get_name();
    ?> 