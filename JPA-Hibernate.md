**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [JPA e Hibernate](#jpa)

	* [Configurações](#jpa_config)

		* [IDE STS](#jpa_config_ide)

		* [Maven](#jpa_config_maven)

		* [persistence.xml](#jpa_config_persistence)

	* [Mapeamentos](#jpa_mapeamentos)

	* [Adição](#jpa_adicao)

	* [Recuperação de dados](#jpa_recuperacao)

	* [Entidade monitorada](#jpa_monitorada)

# Introdução<span id="intro"></span>

Leia o [README](README.md).

# JPA e Hibernate<span id="jpa"></span>

*Antes de inicar este tutorial, sugiro fortemente que você já tenha familiaridade com o [JDBC](JDBC.md).*

JPA *(Java Persistence API)* é uma especificação Java para ferramentas [ORM](https://pt.wikipedia.org/wiki/Mapeamento_objeto-relacional), usada como link entre o modelo de orientação a objetos e sistemas de banco de dados relacionais. Um framework que implementa o JPA é o [Hibernate](https://pt.wikipedia.org/wiki/Hibernate). O Hibernate, por sua vez, é um framework que atua no modelo ORM que implementa o JPA. O site [toThought](http://tothought.com/post/2) exemplificou isso de forma bem interessante:

Um JPA Provider desenvolvem uma implementação do JPA baseado nas especificações/diretrizes da **J**ava **P**ersistence **A**PI:

    public interface JPA {
        public void insert(Object obj);
        
        public void update(Object obj);
        
        public void delete(Object obj);
        
        public Object select();
    }

No caso, o Hibernate representaria a classe que implementa essa interface:

    public class Hibernate implements JPA {
        public void insert(Object obj) {
           // Código de persistência
        }
    
        public void update(Object obj) {
           // Código de persistência
        }
    
        public void delete(Object obj) {
          // Código de persistência
        }
    
        public Object select() {
            // Código de persistência
        }
        
        public Object superSelect(){
            // Código de persistência
        }
    }

***Tenha em mente que o Hibernate possui métodos que são supérfluos para a interface.***

Poderíamos ter um código assim:

    public class MinhaAplicacao {
        public static JPA jpa = new Hibernate();
        
        public static void main(String[] args) {
            Object obj = new Object();
            jpa.insert(obj);
        }
    }

Se, no futuro, for percebido que há problemas de performance por causa de deficiências do Hibernate, outro provedor pode criar sua própria classe...

    public class HmslimaJPA implements JPA {
        // Implementação
    }

...nós poderemos facilmente mudar para outra implementação:

    public class MinhaAplicacao {
        public static JPA jpa = new HmslimaJPA();
        
        public static void main(String[] args) {
            Object obj = new Object();
            jpa.insert(obj);
        }
    }

Enquanto o JPA é descrito pelo pacote `javax.persistence`, o Hibernate é descrito pelo pacote `org.hibernate`. Geralmente é recomendável que você use `javax.persistence` sempre que possível porque assim você estaria usando as anotações padrão, dessa forma você não fica preso a um provedor em específico e poderá manter a possibilidade de mudar de implementação no futuro se for necessário.

O JPA é a ponte entre os objetos e o banco de dados. Para que ela funcione, é necessário fazer os mapeamentos dos objetos e é precios mexer em alguns arquivos de configuração. 

## Configurações<span id="jpa_config"></span>

### IDE STS<span id="jpa_config_ide"></span>

Para programar, use o [Spring Tool Suite](https://spring.io/tools).

Mude a perspectiva para Java: Window ⇛ Perspective ⇛ Open Perspective ⇛ Java

### Maven<span id="jpa_config_maven"></span>

Crie um projeto Maven: File ⇛ New ⇛ Maven Project

No *Group Id*, costuma ser o nome do pacote da empresa, e no *Artifact Id* cotuma ser o nome do projeto.

Seus códigos serão salvos em ´src/main/java´. Observe que alguns arquivos terão que ser baixado, então pode demorar alguns minutinhos.
Por padrão, o Maven, por padrão, vem com o *compliance* do Java 5, é interessante atualizá-lo. Para atualizar, basta editar o aquivo `pom.xml`. Adicione este trecho:

    <properties>
    		<maven.compiler.source>11</maven.compiler.source>
    		<maven.compiler.target>11</maven.compiler.target>
    </properties>

Clique com o botão direito do mouse sobre o projeto, Maven, Update Project.

Agora você precisa baixar as dependências que você colocará entre...

    <dependencies>
   
    </dependencies>

Para saber o nome das dependências, você precisará pesquisar no seu site de buscas favorito termos como "hibernate maven", você encontrará o site ***mvnrepository***. No nosso caso precisaremos do `hibernate-core`, do `hibernate-entitymanager` e do `mysql-connector-java`. Procure baixa a última versão Final, evite as versões Alpha. No nosso exemplo aqui, usei a versão 5.6.7. É para ficar mais ou menos assim:

    <dependencies>
    
        <!-- https://mvnrepository.com/artifact/org.hibernate/hibernate-core -->
        <dependency>
            <groupId>org.hibernate</groupId>
            <artifactId>hibernate-core</artifactId>
            <version>5.6.7.Final</version>
        </dependency>
    
        <!-- https://mvnrepository.com/artifact/org.hibernate/hibernate-entitymanager -->
        <dependency>
            <groupId>org.hibernate</groupId>
            <artifactId>hibernate-entitymanager</artifactId>
            <version>5.6.7.Final</version>
        </dependency>
    
        <!-- https://mvnrepository.com/artifact/mysql/mysql-connector-java -->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.28</version>
        </dependency>
        
    </dependencies>

No momento que você salvar o arquivo `pom.xml`, a própria IDE farão o download das dependências, você pode vê-las em *Maven Dependencies* naquela janelinha mesmo do *Packager Manager* que fica no lado esquerdo.

### persistence.xml<span id="jpa_config_persistence"></span>

Agora é preciso configurar a JPA no arquivo `persistence.xml`.

Crie a pasta `META-INF` dentro da pasta `src/main/resources`, e dentro desta pasta `META-INF` crie o arquivo `persistence.xml`.

    <?xml version="1.0" encoding="UTF-8"?>
    <persistence version="2.1"
        xmlns="http://xmlns.jcp.org/xml/ns/persistence" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence http://xmlns.jcp.org/xml/ns/persistence/persistence_2_1.xsd">
        <persistence-unit name="jpa-teste" transaction-type="RESOURCE_LOCAL">
            <properties>
                <property name="javax.persistence.jdbc.driver" value="com.mysql.cj.jdbc.Driver" />
                <property name="javax.persistence.jdbc.url" value="jdbc:mysql://localhost:3306/jpa?useSSL=false&&amp;serverTimezone=UTC" />
                <property name="javax.persistence.jdbc.user" value="root" />
                <property name="javax.persistence.jdbc.password" value="root" />

                <property name="hibernate.hbm2ddl.auto" value="update" />
                <property name="hibernate.dialect" value="org.hibernate.dialect.MySQL8Dialect" />
            </properties>
        </persistence-unit>
    </persistence>

*O mais importante: se na hora que você for editar o arquivo `persistence.xml`, não aparecer uma tela editável, mas sim aparecer algo parecido com uma planilha, olhe na aba de baixo que você notará que está em `Design`, selecione a aba `Source`.*

Observe os *values* de cada `<property>`, se você viu meu tutorial de [JDBC](JDBC.md), você notará a familiaridade e saberá como adaptar ao seu caso. Você também poderá editar o apelido de `name` da tag `<persistence-unit>`. Ainda na `<persistence-unit>`, o `transaction-type` pode assumir dois valores:

* `RESOURCE_LOCAL`: indica que a transação será feita via a implementação do provedor do JPA.

* `JTA`: as transações serão manejadas pelo *Application Server*. Essa é a melhor escolha se quisermos que nossas transações tenham outros recursos além do JPA, como EJBs e JMS.

A propriedade `<property name="hibernate.hbm2ddl.auto" value="update"/>` serve para gerar automaticamente o banco de dados. Com o `value` como *update*, isso signifa que o banco de dados será automaticamente atualizado sempre que a aplicação for rodada; mas se eu quiser recriar o banco de dados toda vez que eu rodar a aplicação, é só trocar *update* por *create*.

Você pode ter problemas com a linha `<property name="hibernate.dialect" value="org.hibernate.dialect.MySQL8Dialect" />`. Qualquer coisa, acesse [esta página](https://docs.jboss.org/hibernate/orm/6.0/javadocs/org/hibernate/dialect/package-summary.html) *(ou outra página relativa a uma versão mais nova/velha que esta...)*

## Mapeamentos<span id="jpa_mapeamentos"></span>

**Funcionario.java**

    import javax.persistence.Entity; // Ele automaticamente busca a implementação do Hibernate, a preferência é usar o javax.persistence para que nada a mais seja usado
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    
    @Entity
    public class Funcionario implements Serializable {
        private static final long serialVersionUID = 1L;
        
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        private Integer id;
        private String nome;
        private String email;

        public Funcionario() {
        	}
        
        public Funcionario(Integer id, String nome, String email) {
            this.id = id;
            this.nome = nome;
            this.email = email;
        }
    
        public int getId() {
            return id;
        }
    
        public void setId(int id) {
            this.id = id;
        }
    
        public String getNome() {
            return nome;
        }
    
        public void setNome(String nome) {
            this.nome = nome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        @Override
        public String toString() {
            return "Funcionario [id=" + id + ", nome=" + nome + ", email=" + email + "]";
        }
    }

Um entity é a representação da linha de uma tabela como um objeto. O `@Entity` informa que a classe é uma entidade, assim o JPA estabelecerá uma relação entre esta classe e uma tabela de mesmo nome no banco de dados. O `@Id`, por sua vez, é uma anotação obrigatória que informa qual campo será a chave primária. O `@GeneratedValue` define a estratégia de geração da chave primária, há quatro estratégias disponíveis, `AUTO`, `IDENTITY`, `SEQUENCE` e `TABLE`, no `IDENTITY` os valores a serem atribuídos serão gerados pela coluna de autoincremento, ou seja, um valor do identificador é gerado para cada registro no banco de dados.

Por padrão, o JPA criará uma tabela com o mesmo nome da classe e criará as colunas com os mesmos nomes dos atributos da classe; se você quiser um nome diferente, você insere `@column(name="<a_palavra_que_você_quiser>")`. 

    @column(name="nomecompleto")
    this.nome = nome;

## Adição<span id="jpa_adicao"></span>

**Main.java**

    import javax.persistence.EntityManager;
    import javax.persistence.EntityManagerFactory;
    import javax.persistence.Persistence;
    
    import dominio.Funcionario;
    
    public class Main {
    
        public static void main(String[] args) {
            Funcionario f1 = new Funcionario (null, "Thiago Sampaio", "thiago@gmail.com");
            Funcionario f2 = new Funcionario (null, "Maria Tulipa", "tulipa@gmail.com");
            Funcionario f3 = new Funcionario (null, "Sérgio Mascarenhas", "sergio@gmail.com");
            
            EntityManagerFactory emf = Persistence.createEntityManagerFactory("jpa-teste");
            EntityManager em = emf.createEntityManager();
            
            em.getTransaction().begin(); // Quando o JPA faz uma operação que vai além de uma mera leitura, essa linha é necessária
            
            em.persist(f1);
            em.persist(f2);
            em.persist(f3);
            
            em.getTransaction().commit();

            em.close();
            emf.close();
        }
    }

Quanto a linha `EntityManagerFactory emf = Persistence.createEntityManagerFactory("jpa-teste");`, esse nome `"jpa-teste"` veio do `name` da linha `<persistence-unit name="jpa-teste" transaction-type="RESOURCE_LOCAL">` do arquivo persistence.xml.

*Na execução, você verá um conjunto de linhas de texto na cor vermelha com um conteúdo mais ou menos assim:*

> abr. 11, 2022 8:22:37 PM org.hibernate.jpa.internal.util.LogHelper logPersistenceUnitInformation
> 
> INFO: HHH000204: Processing PersistenceUnitInfo [name: jpa-teste]
> 
> abr. 11, 2022 8:22:37 PM org.hibernate.Version logVersion
> 
> INFO: HHH000412: Hibernate ORM core version 5.6.7.Final
> 
> abr. 11, 2022 8:22:38 PM org.hibernate.annotations.common.reflection.java.JavaReflectionManager <clinit>
> 
> INFO: HCANN000001: Hibernate Commons Annotations {5.1.2.Final}

*Isso é normal, é assim mesmo.*

Se você consultar o banco de dados MySQL, deverá estar mais ou menos assim:

```
+----+------------------+---------------------+
| id | email            | nome                |
+----+------------------+---------------------+
|  1 | thiago@gmail.com | Thiago Sampaio      |
|  2 | tulipa@gmail.com | Maria Tulipa        |
|  3 | sergio@gmail.com | Sérgio Mascarenhas  |
+----+------------------+---------------------+
```


## Recuperação de dados<span id="jpa_recuperacao"></span>

**Main.java**

    import javax.persistence.EntityManager;
    import javax.persistence.EntityManagerFactory;
    import javax.persistence.Persistence;
    
    import dominio.Funcionario;
    
    public class Main {
    
        public static void main(String[] args) {
            
            EntityManagerFactory emf = Persistence.createEntityManagerFactory("jpa-teste");
            EntityManager em = emf.createEntityManager();
            
            Funcionario f = em.find(Funcionario.class, 2); // Procura a pessoa da tabela Funcionario cujo Id é 2
            
            System.out.println(f);
    
            em.close();
            emf.close();
        }
    }

A propósito, espero que você tenha feito um construtor vazio na sua classe. Sem ele, haverá erro, frameworks geralmente exigem a existência de um construtor vazio dentro da classe.

**Funcionario.java**

    [...]
    public Funcionario() {
    }
    [...]

## Entidade monitorada<span id="jpa_monitorada"></span>

Tente rodar o código abaixo cuja função é remover uma entrada da tabela:

    import javax.persistence.EntityManager;
    import javax.persistence.EntityManagerFactory;
    import javax.persistence.Persistence;
    
    import dominio.Funcionario;
    
    public class Main {
    
        public static void main(String[] args) {
            
            EntityManagerFactory emf = Persistence.createEntityManagerFactory("jpa-teste");
            EntityManager em = emf.createEntityManager();
            
            Funcionario f = new Funcionario (2, null, null);
            
            em.remove(f);
    
            em.close();
            emf.close();
        }
    }

Dará o erro:

> Exception in thread "main" java.lang.IllegalArgumentException: Removing a detached instance dominio.Funcionario#2

O problema é que a instância está destacada. O objeto – que no caso é `f` – precisa estar monitorado. Um objeto monitorado ou é um que você acabou de inserir ou um objeto que foi recuperado do banco de dados (`em.find()`) e ainda não fechou o EntityManager (`em.close()`).

    import javax.persistence.EntityManager;
    import javax.persistence.EntityManagerFactory;
    import javax.persistence.Persistence;
    
    import dominio.Funcionario;
    
    public class Main {
    
        public static void main(String[] args) {
            
            EntityManagerFactory emf = Persistence.createEntityManagerFactory("jpa-teste");
            EntityManager em = emf.createEntityManager();
            
            Funcionario f = em.find(Funcionario.class, 2);
            
            em.getTransaction().begin(); // Nunca se esqueça, se não é uma mera operação de leitura, você precisará desse .getTransaction()
            em.remove(f);
            em.getTransaction().commit();
    
            em.close();
            emf.close();
        }
    }