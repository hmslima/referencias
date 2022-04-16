**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [Spring](#spring)

	* [Criação do projeto](#spring_criacaoprojeto)

	* [Primeiros passos](#spring_criacaoprojeto)

	* [JPA e Banco de dados H2](#spring_JPAH2)

	* [Repositórios](#spring_repository)

	* [Camada de serviço](#spring_servico)


# Introdução<span id="intro"></span>

Leia o [README](README.md).

# Spring<span id="spring"></span>

*Antes de inicar este tutorial, sugiro fortemente que você já tenha familiaridade com o [JDBC](JDBC.md) e com o [JPA](JPA-Hibernate.md).* 

Spring é um framework completo que fornece uma estrutura para criar aplicações Java. Esse framework é constituído de módulos agrupados em *Core Container*, *Data Access/Integration*, *Web*, *AOP (Aspect Oriented Programming)*, *Instrumentation* e *Test*.

Por exemplo, dentro do *Data Access/Integration* (Integração/Acesso aos Dados), temos o JDBC, ORM, OXM, JMS e Transactions. Já esse ORM, provê integração a APIs como JPA, JDO, Hibernate e iBatis.

O nosso projeto terá a seguinte estrutura, a aplicação conversa com o *Resource Layer (rest controllers)*, este por sua vez conversa com *Service Layer* e este último conversa com *Data Access Layer (data repositories)*.

## Criação do projeto<span id="spring_criacaoprojeto"></span>

Tudo será feito no STS *(Spring Tool Suite)*.

File ⇒ New ⇒ Spring Starter Project

No `name` eu coloquei *curso*, mas a escolha é sua.

É esperado que a configuração padrão esteja do jeito que queremos, `Type` como *Maven Project*, `Java Version` como a última versão LTS do Java, `Packaging` como *Jar* e `Language` como *Java*. É lógico que, caso você for fazer algo diferente, como programar wem Kotlin, achar melhor usar o Gradle ou outra coisa, você é livre para modificar.

Em `Group`, você coloca o nome de acordo com o da empresa. No exemplo, colocarei *com.hmslima*. Em `Package` deixei *com.hmslima.curso*.

Clique em Next.

Você estará numa janela com o título "New Spring Starter Project Dependencies". Selecione a opção "Spring Web Starter", se você não encontrar exatamente essa opção, escolha "Spring Web". Clique em `Finish` e espere o STS baixar as dependências.

Para verificar se tudo está OK, abra o arquivo .java dentro de `src/main/java` e execute-o como *Spring Boot App*, assim será iniciado o servidro do [Tomcat](https://pt.wikipedia.org/wiki/Apache_Tomcat). Você poderá ver se tudo está rodando na aba `Console`. Lá também você poderá ver em que porta o servidor está rodando, a não ser que outro servidor esteja rodando na sua máquina, a porta usada será a 8080:

    Tomcat initialized with port(s): 8080 (http)

Assumindo que, no seu computador, a porta escolhida pelo Tomcat foi a 8080, é para que o endereço [http://localhost:8080/](http://localhost:8080/) esteja funcionando. É normal que apareça a mensagem de erro abaixo na página que você for abrir.

> **Whitelabel Error Page**
> 
> This application has no explicit mapping for /error, so you are seeing this as a fallback.
> 
> Tue Apr 12 21:19:07 BRT 2022
> 
> There was an unexpected error (type=Not Found, status=404).

*É lógico que a data que aparecerá no seu computador será diferente...*

Para finalizar este capítulo, repare que dentro da pasta do seu projeto, onde você iniciaria o Git, o próprio Spring Boot criou o arquivo `.gitignore`

## Primeiros passos<span id="spring_criacaoprojeto"></span>

Nossos arquivos serão criados em `src/main/java`.

Crie a classe *User* no pacote *entities*. No meu caso aqui, como defini o prefixo do meu pacote como `com.hmslima.curso`, o nome completo do pacote *entities* será `com.hmslima.curso.entities`.

    package com.hmslima.curso.entities;
    
    import java.io.Serializable;
    
    public class User implements Serializable {
        private static final long serialVersionUID = 1L;
        
        private Long id;
        private String name;
        private String email;
        private String password;
        
        public User() {
            
        }
    
        public User(Long id, String name, String email, String password) {
            this.id = id;
            this.name = name;
            this.email = email;
            this.password = password;
        }
    
        public Long getId() {
            return id;
        }
    
        public void setId(Long id) {
            this.id = id;
        }
    
        public String getName() {
            return name;
        }
    
        public void setName(String name) {
            this.name = name;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        public String getPassword() {
            return password;
        }
    
        public void setPassword(String password) {
            this.password = password;
        }
    
        @Override
        public int hashCode() {
            final int prime = 31;
            int result = 1;
            result = prime * result + ((id == null) ? 0 : id.hashCode());
            return result;
        }
    
        @Override
        public boolean equals(Object obj) {
            if (this == obj)
                return true;
            if (obj == null)
                return false;
            if (getClass() != obj.getClass())
                return false;
            User other = (User) obj;
            if (id == null) {
                if (other.id != null)
                    return false;
            } else if (!id.equals(other.id))
                return false;
            return true;
        }
    }

*Na hora de pôr o STS para gerar o hashCode() e equals(), você pode deixar só a opção de Id selecionada.*

Agora criaremos um recurso *(da camada Resource Layer)* baseado na classe *User* que se chamará *UserResource* no subpacote *resources*. *UserResource* será nosso primeiro controlador REST.

**UserResource.java**

    package com.hmslima.curso.resources;
    
    import org.springframework.http.ResponseEntity;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import com.hmslima.curso.entities.User;
    
    // O @RestController é uma annotation que indica que a classe é um recurso web que é implementado por um controlador REST
    // O @RequestMapping serve para dar um nome ao recurso. O valor de value é o caminho do recurso
    @RestController
    @RequestMapping(value="/users")
    public class UserResource {
    
        //Endpoint para acessar os usuários. Para indicar que o método findAll responde à requisição do tipo GET do HTTP, usaremos o annotation @GetMapping
        @GetMapping
        public ResponseEntity<User> findAll() {
            // Só para teste, vou instanciar um usuário
            User usuario = new User(1L, "João Freitas", "joao@terra.com.br", "12345");
            return ResponseEntity.ok().body(usuario);
        }
    }

Para testar se tudo está OK, rode o arquivo principal como *Spring Boot App* e então acesse o endereço [http://localhost:8080/users](http://localhost:8080/users) pelo seu navegador, é esperado que apareça as informações do usuário que você instanciou em forma de JSON.

## JPA e Banco de dados H2<span id="spring_JPAH2"></span>

O H2 é um sistema de gerenciamento de banco de dados relacional escriot em Java. Ele roda na memória e já vem integrado no Spring.

O JPA você já conhece [do meu outro tutorial](JPA-Hibernate.md). O que faremos não será novidade para você, vamos pôr as dependências no arquivo `pom.xml`. Vá lá no site MvnRepository e baixe as dependências para **Spring Boot Starter Data JPA** e **H2**.

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    
    <dependency>
        <groupId>com.h2database</groupId>
        <artifactId>h2</artifactId>
        <scope>runtime</scope>
    </dependency>

Agora vá na pasta `src/main/resources`, no arquivo `application.properties` *(se ele, por acaso, não existir, crie-o)*. É normal que ele esteja vazio. Adicionaremos as seguintes linhas:

    spring.profiles.active=test
    
    spring.jpa.open-in-view=true

É no arquivo `application.properties` onde ficam as configurações de desenvolvimento, o próprio nome do arquivo e sua extensão mostram a função desde arquivo que é automaticamente detectado pelo Spring.

Em `spring.profiles.active`, definimos o apelido do *profile* que usaremos, isso indica qual *profile* está ativo. Observe que tem que ser um *profile* que exista, por padrão o Spring já monta um perfil chamado *test* para você.

Para entender o `spring.jpa.open-in-view`, precisamos entender o que é *Open Session in View (OSIV)*: Spring abre uma nova *session* do Hibernate no início de cada *request* que não são necessariamente conectadas ao banco de dados, toda vez que uma aplicação necessita de uma *session*, será reutilizada uma já existente e, no final da *request*, o interceptador fecha a *session*. O problema, é que as vezes o OSIV pode causar problemas de performance, então, se for necessário desativar o OSIV, usamos a propriedade de configuração `spring.jpa.open-in-view=false`.

Ainda na pasta `src/main/resources`, crie o arquivo `application-test.properties`. É esse arquivo que conterá as configurações do banco de dados H2.

    spring.datasource.url=jdbc:h2:mem:testdb
    spring.datasource.username=sa
    spring.datasource.password=
    
    spring.h2.console.enabled=true
    spring.h2.console.path=/h2console
    
    spring.jpa.show-sql=true
    spring.jpa.properties.hibernate.format_sql=true

A propriedade `spring.datasource.url` requer uma explicação: o `testdb` é o nome do banco de dados; o `mem` indica que será um banco de dados em memória, ou seja, não haverá nenhum arquivo no disco.

Agora precisamos adicionar algumas *annotations* do JPA na nossa clase *User* para que ele converta os objetos para o modelo relacional.

**User.java**

    package com.hmslima.curso.entities;
    
    import java.io.Serializable;
    
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    
    @Entity
    public class User implements Serializable {
        private static final long serialVersionUID = 1L;
        
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;
        private String name;
        private String email;
        private String password;
        
        public User() {
            
        }
    
        public User(Long id, String name, String email, String password) {
            this.id = id;
            this.name = name;
            this.email = email;
            this.password = password;
        }
    
        public Long getId() {
            return id;
        }
    
        public void setId(Long id) {
            this.id = id;
        }
    
        public String getName() {
            return name;
        }
    
        public void setName(String name) {
            this.name = name;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        public String getPassword() {
            return password;
        }
    
        public void setPassword(String password) {
            this.password = password;
        }
    
        @Override
        public int hashCode() {
            final int prime = 31;
            int result = 1;
            result = prime * result + ((id == null) ? 0 : id.hashCode());
            return result;
        }
    
        @Override
        public boolean equals(Object obj) {
            if (this == obj)
                return true;
            if (obj == null)
                return false;
            if (getClass() != obj.getClass())
                return false;
            User other = (User) obj;
            if (id == null) {
                if (other.id != null)
                    return false;
            } else if (!id.equals(other.id))
                return false;
            return true;
        }
    }

Rode a aplicação como *Spring Boot App*.

Abra o seu navegador e vá até o endereço [http://localhost:8080/h2console](http://localhost:8080/h2console) *(se você não entende este "h2-console", lembre-se que o definimos no arquivo `application-test.properties`)*.

Você preencherá os valores de acordo com o que está no seu arquivo `application-test.properties`.

## Repositórios<span id="spring_repository"></span>

Vamos criar a interface `UserRepository` no subpacote `repositories`. Ele serve para salvar os dados no banco de dados.

**UserRepository.java**

    package com.hmslima.curso.repositories;
    
    import org.springframework.data.jpa.repository.JpaRepository;
    
    import com.hmslima.curso.entities.User;
    
    // O "Long" no generic se refere ao tipo do Id
    public interface UserRepository extends JpaRepository<User, Long> {
        // Só o fato de eu ter usado o JpaRepository, essa interface já terá uma implementação automaticamente, até mesmo a annotation @Repository está implicitamente posta nessa classe
    }

Agora criaremos uma classe de configuração específica para o *profile* `test` no subpacote `config`. Essa classe servirá para popular o banco de dados com objetos.

**TestConfig.java**

    package com.hmslima.curso.config;
    
    import java.util.Arrays;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.boot.CommandLineRunner;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.context.annotation.Profile;
    
    import com.hmslima.curso.entities.User;
    import com.hmslima.curso.repositories.UserRepository;
    
    @Configuration
    @Profile("test")
    public class TestConfig implements CommandLineRunner {
        @Autowired
        private UserRepository userRepository; // Com a annotation @Autowired, o Sprign resolverá as dependências e associará a instância do UserRepository com o TestConfig  
    
        @Override
        public void run(String... args) throws Exception {
            // Tudo que for colocado neste método será rodado quando a aplicação for iniciada
            User u1 = new User(null, "Marcelino Ficha", "marcelino@gmail.com", "12345678");
            User u2 = new User(null, "Tânia Conceicão", "tc@gmail.com", "12345678");
            
            // Salvaremos agora u1 e u2 no banco de dados
            userRepository.saveAll(Arrays.asList(u1, u2));
        }
    }

*Com `@Profile("test")`, o Spring saberá que ele só rodará essa configuração no *profile* de `test`.*

Rode a aplicação como Spring Boot App, acesse o endereço [http://localhost:8080/h2console](http://localhost:8080/h2console) (ou o endereço que você definiu) e veja se os usuários "Marcelino Ficha" e "Tânia Conceicão" foram adicionados à lista.

## Camada de serviço<span id="spring_servico"></span>

O controlador precisa da camada de serviço em vez de acessar diretamente o repositório porque essa é a forma preferencial, porque assim é possível implementar regras de negócio ou qualquer outra manipulação.

Agora criaremos a classe `UserService` no subpacote `services`.

    package com.hmslima.curso.services;
    
    import java.util.List;
    import java.util.Optional;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    
    import com.hmslima.curso.entities.User;
    import com.hmslima.curso.repositories.UserRepository;
    
    // @Component // Além do @Component, o Spring tem outras annotations com uma semântica mais específica, como nossa classe se trata de um service, usamos o @Service aqui
    @Service
    public class UserService {
        @Autowired
        private UserRepository repository;
        
        public List<User> findAll() {
            return repository.findAll();
        }
        
        public User findById(Long Id) {
            Optional<User> obj = repository.findById(Id);
            return obj.get();
        }
    }

E modifique o arquivo `UserResource`:

    package com.hmslima.curso.resources;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.http.ResponseEntity;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import com.hmslima.curso.entities.User;
    import com.hmslima.curso.services.UserService;
    
    @RestController
    @RequestMapping(value="/users")
    public class UserResource {
        
        @Autowired
        private UserService service; // Para o UserService funcionar, ela tem que estar registrada como componente do Spring, por isso que adicionamos a annotation @Component na classe UserService
    
        @GetMapping
        public ResponseEntity<List<User>> findAll() {
            List<User> list = service.findAll(); // Aqui chamo o serviço
            return ResponseEntity.ok().body(list);
        }
        
        @GetMapping(value="/{id}")
        public ResponseEntity<User> findById(@PathVariable Long id) { // O @PathVariable serve para linkar o parâmetro id com o valor definido no @GetMapping
            User obj = service.findById(id);
            return ResponseEntity.ok().body(obj);
        }
    }

Rode o aplicativo como Spring Boot App para ver se está tudo OK e então abra o Postman, se você ainda não o baixou, [este é o site](https://www.postman.com/).

Ao abrir o Postman, vá em `Workspace` ⇒ `New Workspace` ⇒ `+` ⇒ `New Collection` ⇒ `Add a request`

Vá em `Get started with Postman` ⇒ `Start with something new` ⇒ `Create New →` ⇒ `New Collection` ⇒ `Add request`. Em *Enter request URL*, ponha [http://localhost:8080/users](http://localhost:8080/users). Lembre-se, o Tomcat tem que estar funcionando.

Agora teste com o endereço [http://localhost:8080/users/1](http://localhost:8080/users/1)

## Classe de pedido<span id="spring_pedido"></span>




Um pedido (order) tem um cliente e um cliente tem vários pedidos. Na classe User, adicione o atributo Order e seu respectivos getter ~e setters~ *(nada de colocar setter para coleções!)*.

    @OneToMany(mappedBy = "client") // "client" porque na classe Order, User está mapeado pelo atributo client
    private List<Order> orders = new ArrayList<>();

A annotation `@ManyToOne` permite que o JPA faça as chaves estrangeiras entre Order e User.

Crie um service e repository para a classe *Order* da mesma forma que você criou para  aclasse *User*. E não esqueça de atualizar o arquivo `TestConfig.java`

Você reparará que usuário chama pedido, pedido chama usuário e cai num loop infinito. Por isso que o @JsonIgnore é posto em um dos dois lados

    @JsonIgnore
    @OneToMany(mappedBy = "client")
    private List<Order> orders = new ArrayList<>();

Outro conceito importante é o "lazy loading". Quando há uma chamada de um objeto Order, o JPA automaticamente carrega o objeto User associado a ele por padrão, entretanto isso não acontece do lado do "um para muitos", se você carrega um objeto com associação para muitos, o JPA não carregar os objetos do lado do "muitos" por padrão.

Se coloco o `spring.jpa.open-in-view` *(do arquivo `application-test.properties`)* como *false*, desabilito a possibilidade do jackson, lá no fim do ciclo de vida, convocar o JPA para trazer os objetos de Order associados aos objetos de User.

Na classe Order.java, para garantir que o Instant seja mostrado no formato ISO 8601 no JSON, uso o annotation ao lado

    @JsonFormat(shape = JsonFormat.Shape.STRING, pattern = "yyyy-MM-dd'T'HH:mm:ss'Z'", timezone = "GMT")
	private Instant moment;