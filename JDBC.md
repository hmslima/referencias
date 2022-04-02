# Índice

* [Introdução](#intro)

* [JDBC](#jdbc)

	* [Download](#jdbc_download)

	* [Instalação e configuração](#jdbc_inst)

		* [Eclipse](#jdbc_inst_eclipse)
	
	* [Primeiro código JDBC](#jdbc_primeiroCodigo)

	* [Código com tratamento de exceções](#jdbc_cdctratamentoexcecoes)

	* [db.properties](#jdbc_dbproperties)

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
            
            Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/teste?useSSL=false&serverTimezone=UTC", "root", "root"); // Conexão, os parâmetros são a url, o usuário e a senha
            
            Statement st = con.createStatement(); // Statement
            
            ResultSet rs = st.executeQuery("SELECT * FROM funcionarios"); // Comando SQL
            
            rs.next(); // Preciso executar isso pelo menos uma vez para pegar o 1º dado
            
            System.out.print(rs.getString("Nome"));
            
            con.close(); // Fechamento da conexão
        }
    }

</div>

Acho que a url `jdbc:mysql://localhost:3306/teste?useSSL=false&serverTimezone=UTC` necessita de um pouco de atenção, vamos dividí-la em partes:

* `jdbc:mysql:`: o protocolo. Por exemplo, se estivéssimos lidando com um banco de dados PostgreSQL, o protocolo seria `jdbc:postgresql:`

* `localhost:3306`: o endereço. Como estou rodando na minha própria máquina, é no localhost

* `teste`: o banco de dados.

* `?useSSL=false&serverTimezone=UTC` as propriedades, no caso temos duas aqui, `useSSL=false` e `serverTimezone=UTC`. No meu caso, eu pude rodar o programa sem usar esses parâmetros, ou seja, meu código rodou bem mesmo assim:

    \[...\]    
    Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/teste", "root", "root");    
    \[...\]

Sobre esse `useSSL=false` em particular: SSL é um protocolo de criptografia que criptografa todos os dados usados na comunicaçã entre o servidor e o driver JDBC. Por padrão, `useSSL` é definidido como `true` em certas versões do MySQL. Estou comentando que possa ser que você receba uma mensagem de erro por causa do SSL e defini-lo como `false` é a solução.


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

## Código com tratamento de exceções<span id="jdbc_cdctratamentoexcecoes"></span>

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

## db.properties<span id="jdbc_dbproperties"></span>

Podemos deixar as informações de nome de usuário, senha e link para o banco de dados em um arquivo externo chamado `db.properties`, ele fica na mesma pasta *(não dentro!)* onde a pasta`src` se encontra.

Aproveitarei e deixarei o código um pouco mais profissional, basicamente seguindo o que Poul Klausen fez no livro dele, *"Java 6: JDBC and database applications"*  misturado ao uso do arquivo db.properties.

Eis o conteúdo do nosso arquivo `db.properties`:

<div class="codigo">

    usuario=root
    senha=root
    dburl=jdbc:mysql://localhost:3306/teste
    useSSL=false

</div>

Nosso arquivo Java será assim:

<div class="codigo">

    import java.io.FileInputStream;
    import java.io.IOException;
    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;
    import java.util.Properties;
    
    public class Main {
    
        public static void main(String[] args) {
            Connection conn = null;
            Statement stmt = null;
            String url = null;
            String usuario = null;
            String senha = null;
    
            try (FileInputStream arquivoDB = new FileInputStream("db.properties")) {
                Properties pros = new Properties();
                pros.load(arquivoDB);
        	
                url = pros.getProperty("dburl");
                usuario = pros.getProperty("usuario");
                senha = pros.getProperty("senha");
            }
            catch(IOException e) {
                System.out.println(e.getMessage());
            }
    
            try {
                conn = DriverManager.getConnection(url, usuario, senha);
                stmt = conn.createStatement();
                ResultSet res = stmt.executeQuery("SELECT * FROM funcionarios");
        	
                res.next();
                System.out.print(res.getString("Nome"));
            }
            catch(SQLException e) {
                System.out.println(e.getMessage());
            }
            catch(Exception e) {
                System.out.println(e.getMessage());
            }
            finally {
                try {
                    if (stmt != null) stmt.close();
                    if (conn != null) conn.close();
                }
        	        catch(SQLException e) {
                    System.out.println(e.getMessage());
                }
            }
        }
    }

</div>

Um último exemplo onde colocamos os detalhes de conexão em um arquivo separado e deixamos o arquivo principal mais enxuto:

Manteremos o arquivo `db.properties`. Logo a seguir temos o arquivo `JDBCUtil.java`:

<div class="codigo">

    import java.io.FileInputStream;
    import java.io.IOException;
    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.SQLException;
    import java.util.Properties;
    
    public class JDBCUtil {
        public static Connection conectar() throws SQLException {
            Connection con = null;
		
            try (FileInputStream arquivoDB = new FileInputStream("db.properties")) {
                Properties pros = new Properties();
                pros.load(arquivoDB);
    	
                String url = pros.getProperty("dburl");
                String usuario = pros.getProperty("usuario");
                String senha = pros.getProperty("senha");
            
                con = DriverManager.getConnection(url, usuario, senha);
            }
            catch(IOException e) {
                System.out.println(e.getMessage());
            }
		
            return con;
        }
    }

</div>

E o arquivo principal `Main.class`:

<div class="codigo">

    import java.sql.Connection;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;

    public class Main {

        public static void main(String[] args) {
        
            try(Connection con = JDBCUtil.conectar()) {
                Statement stmt = con.createStatement();
                ResultSet res = stmt.executeQuery("SELECT * FROM funcionarios");
        
                res.next();
                System.out.print(res.getString("Nome"));
            }
            catch(SQLException e) {
                System.out.println(e.getMessage());
            }
        }
    }

</div>
