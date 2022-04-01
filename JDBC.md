# Índice

* [Introdução](#intro)

* [JDBC](#jdbc)

	* [Download](#jdbc_download)

	* [Instalação e configuração](#jdbc_inst)

		* [Eclipse](#jdbc_inst_eclipse)
	
	* [Primeiro código JDBC](#jdbc_primeiroCodigo)
</div>

# Introdução<span id="intro"></span>

Leia o [README](README.md).

E saiba que estou usando as tabelas criadas no tutorial de [SQL](SQL.md)

<div class="espacoEntreCapitulos"></div>

# JDBC<span id="jdbc"></span>

JDBC *(Java Database Connectivity)* é uma API que nos permitir conectar a um banco de dados por meio de um driver específico, que serve como tradutor.

## Download<span id="jdbc_download"></span>

Procure baixar o arquivo em formato .jar *(geralmente fica na seção "Platform Independent")*.

### MySQL

O driver para MySQL pode ser baixado [aqui](https://dev.mysql.com/downloads/connector/j/).

Você verá mais a frente, mas o parâmetro para o driver MySQL em `Class.forName()` é ~*"com.mysql.jdbc.Driver"*~ *"com.mysql.cj.jdbc.Driver"*

### MariaDB

O driver para MariaDB pode ser baixado [aqui](https://mariadb.com/kb/en/about-mariadb-connector-j/).

Você verá mais a frente, mas o parâmetro para o driver MariaDB em `Class.forName()` é *"org.mariadb.jdbc.Driver"*

## Instalação e configuração<span id="jdbc_inst"></span>

### Eclipse<span id="jdbc_inst_eclipse"></span>

Coloque o aquivo .jar numa pasta.
 
Vá em **Window** ⇒ **Preferences** ⇒ **Java** ⇒ **Build Path** ⇒ **User Libraries** ⇒ **New** ⇒ **Add external JARs**

Ao criar o novo projeto, lembre-se de adicionar a UserLibrary. Se você se esquecer ou for fazer isso depois do projeto ter sido criado, clique sobre o nome do projeto em **Package Explorer** com o botão direito do mouse ⇒ **Properties** ⇒ **Java Build Path**.


## Primeiro código JDBC<span id="jdbc_primeiroCodigo"></span>

Gostei muito da analogia do site GeeksforGeeks: Há um lugar A *(aplicação Java)* e um lugar B *(banco de dados)* e as pessoas de um lugar não conhecem a linguagem das pessoas do outro. A tradução é feita pelo motorista *(driver)*, a estrada que une os dois lugares é a *conexão* e o veículo é o *statement object*. O *requerimento* é a consulta SQL e o processamento dos dados é feito em *ResultSet*.

O código é bem simplesinho.

<div class="codigo">

    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.ResultSet;
    import java.sql.Statement;
    
    public class Main {
    
        public static void main(String[] args) throws Exception {

            Class.forName("com.mysql.cj.jdbc.Driver"); // Esta linha é opcional
            
            Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/teste", "root", "root"); // Conexão
            
            Statement st = con.createStatement(); // Statement
            
            ResultSet rs = st.executeQuery("SELECT * FROM funcionarios"); // Comando SQL
            
            rs.next(); // Preciso executar isso pelo menos uma vez para pegar o 1º dado
            
            System.out.print(rs.getString("Nome"));
            
            con.close(); // Fechamento da conexão
        }
    }
</div>


Agora vamos ver todos os dados da tabela **funcionarios**:

<div class="codigo">

    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.ResultSet;
    import java.sql.Statement;
    
    public class Main {
    
        public static void main(String[] args) throws Exception {
            
            Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/teste", "root", "root");
            
            Statement st = con.createStatement();
            
            ResultSet rs = st.executeQuery("SELECT * FROM funcionarios");
            
            while (rs.next()) {
                System.out.print(rs.getInt("Id"));
                System.out.print(" | ");
                System.out.print(rs.getString("Nome"));
                System.out.print(" | ");
                System.out.print(rs.getString("Sobrenome"));
                System.out.print(" | ");
                System.out.print(rs.getString("Genero"));
                System.out.print(" | ");
                System.out.print(rs.getString("email"));
                System.out.print(" | ");
                System.out.println(rs.getFloat("Salario"));
            }
            
            System.out.println("----------");
            System.out.println("DE NOVO, MAS DE FORMA DIFERENTE");
            System.out.println("----------");
            
            rs = st.executeQuery("SELECT * FROM funcionarios");
            
            while (rs.next()) {
                System.out.print(rs.getInt(1));
                System.out.print(" | ");
                System.out.print(rs.getString(2));
                System.out.print(" | ");
                System.out.print(rs.getString(3));
                System.out.print(" | ");
                System.out.print(rs.getString(4));
                System.out.print(" | ");
                System.out.print(rs.getString(5));
                System.out.print(" | ");
                System.out.println(rs.getFloat(6));
            }
            
            con.close();
        }
    }
</div>


Vamos fazer um código com `try` `catch`:

<div class="codigo">

    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;
    
    public class Main {
    
        public static void main(String[] args) {
            
            try {
                Class.forName("com.mysql.cj.jdbc.Driver");
            }
            catch(ClassNotFoundException e) {
                System.out.println("Driver não encontrado:" + e.getMessage());
            }
            
            Connection con = null;
            Statement st = null;
            ResultSet rs = null;
            try { // Coloquei tudo no mesmo try, mas talvez fosse bom colocar alguns em trys diferentes porque se houver algum erro, será mais fácil achar onde está o problema
                con = DriverManager.getConnection("jdbc:mysql://localhost:3306/teste", "root", "root");
                st = con.createStatement();
                rs = st.executeQuery("SELECT * FROM funcionarios");
                
                while (rs.next()) {
                    System.out.print(rs.getInt("Id"));
                    System.out.print(" | ");
                    System.out.print(rs.getString("Nome"));
                    System.out.print(" | ");
                    System.out.print(rs.getString("Sobrenome"));
                    System.out.print(" | ");
                    System.out.print(rs.getString("Genero"));
                    System.out.print(" | ");
                    System.out.print(rs.getString("email"));
                    System.out.print(" | ");
                    System.out.println(rs.getFloat("Salario"));
                }
                
                con.close();
            }
            catch(SQLException e) {
                System.out.println(e.getMessage());
            }        
        }
    }
</div>




</div> <!-- Fim do container -->