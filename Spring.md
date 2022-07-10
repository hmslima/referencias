**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [Spring Framework](#spring)

	* [Configuração](#spring_config)

	* [Primeiro projeto](#spring_primeiropro)

		* [Com configuração XML](#spring_primeiropro_xml)

			* [Projeto com dependências](#spring_primeiropro_xml_dependencias)

			* [Lidando com setters](#spring_primeiropro_xml_setters)

			* [Injeção de valores literais](#spring_primeiropro_xml_literalvalues)

			* [Injeção de valores de um arquivo](#spring_primeiropro_xml_properties)

		* [Inversão de controle e Injeção de Dependência](#spring_primeiropro_iocinj)

		* [Com Java Annotations](#spring_primeiropro_javaannotations)

			* [@Qualifier](#spring_primeiropro_javaannotations_qualifier)

		* [Sem configuração XML](#spring_primeiropro_semxml)

			* [@Bean](#spring_primeiropro_semxml_bean)

			* [Injeção de valores de um arquivo](#spring_primeiropro_semxml_properties)

	* [@Bean vs @Component](#spring_beanxcomponent)

* [Spring MVC](#springmvc)

	* [Controllers](#springmvc_controllers)

	* [Formulários](#springmvc_forms)

	* [Usando Models](#springmvc_models)

	* [Recursos estáticos](#springmvc_staticresources)

	* [@RequestParam](#springmvc_requestparam)

	* [Tags Form](#springmvc_tagsform)

		* [Só mais um exemplo de tag](#springmvc_tagsform_maisumexemplor)

	* [Validação](#springmvc_validation)

* [Hibernate](#hibernate)

	* [Configuração](#hibernate_config)

	* [Testando a conexão JDBC](#hibernate_jdbc)

	* [Arquivo de configuração do Hibernate](#hibernate_configfile)

	* [Anotações do Hibernate](#hibernate_annotations)

	* [CRUD](#hibernate_crud)

		* [Criação](#hibernate_crud_c)

		* [Leitura](#hibernate_crud_r)

		* [Atualização](#hibernate_crud_u)

		* [Deleção](#hibernate_crud_u)

	* [Querying](#hibernate_querying)

	* [Trabalhando com datas](#hibernate_datas)

	* [Mappings avançados](#hibernate_mappings)

		* [@OneToOne unidirecional](#hibernate_mappings_onetooneuni)

		* [@OneToOne bidirecional](#hibernate_mappings_onetoonebi)

		* [@OneToMany bidirecional](#hibernate_mappings_onetomanybi)

		* [Eager Loading x Lazy Loading](#hibernate_mappings_fetching)

		* [@ManyToMany](#hibernate_mappings_manytomany)

* [Como usar Spring MVC e Hibernate juntos](#springmvchibernate)

	* [Mais configurações](#springmvchibernate_config)

	* [Teste com um Controller](#springmvchibernate_testecontroller)

	* [Início do projeto](#springmvchibernate_inicio)

	* [Floreio: CSS e Página de Boas-Vindas](#springmvchibernate_floreio)

	* [Mapping](#springmvchibernate_mapping)

	* [Salvar cliente](#springmvchibernate_add)

	* [Atualizar cliente](#springmvchibernate_update)

	* [Deletar cliente](#springmvchibernate_delete)

	* [Sistema de busca](#springmvchibernate_search)

	* [Ordenação](#springmvchibernate_order)

	* [BÔNUS: O projeto completo](#springmvchibernate_full)

* [Programação orientada a aspecto](#aop)

	* [Expressões Pointcut](#aop_pointcutexpressions)

	* [Declarações Pointcut](#aop_pointcutdeclarations)

	* [Aspects de ordenação](#aop_orderingaspects)

	* [JoinPoints](#aop_joinpoints)

	* [@AfterReturning](#aop_afterreturning)

	* [@AfterThrowing](#aop_afterthrowing)

	* [@After](#aop_after)

	* [@Around](#aop_around)

	* [AOP no Spring MVC](#aop_springmvc)

		* [Arquivo XML](#aop_springmvc_configxml)

		* [Aspect](#aop_springmvc_aspect)

 * [Spring Security](#springsecurit)

	* [Instalação e configuração do Spring Framework](#springsecurit_installconfigspringframework)

	* [Instalação do Spring Security](#springsecurit_installspringsecurity)

	* [Configuração do Spring Security](#springsecurit_config)

	* [Tela de login customizada](#springsecurit_login)

	* [Logout](#springsecurit_logout)

	* *[Cross Site Request Forgery](#springsecurit_csrf)*

	* [Id de usuário e *role*](#springsecurit_userroles)

	* [Restrição de acesso baseado em *roles*](#springsecurit_restrictaccessrole)

		* [Página customizada de acesso negado](#springsecurit_restrictaccessrole_accessdenied)

		* [Exibição de conteúdo baseado nos *roles*](#springsecurit_restrictaccessrole_contentroles)

	* [Autenticação de banco de dados JDBC](#springsecurit_jdbc)

		* [Encriptação de senha](#springsecurit_jdbc_crypt)

	* [BÔNUS: O projeto final](#springsecurit_final)

* [Spring REST](#springrest)

	* [JSON Data Binding](#springrest_jsondatabinding)

	* [Conceitos básicos](#springrest_basicconcepts)

	* [REST Controller](#springrest_restcontroller)

	* [Coletar POJO como JSON](#springrest_pojojson)

	* [@PathVariable](#springrest_pathvariable)

	* [Exception Handling](#springrest_exceptionhandling)

	* [CRUD](#springrest_crud)

		* [Leitura de um único cliente](#springrest_crud_r1)

		* [Exception Handling](#springrest_crud_exceptionhandling)

		* [Adição de um cliente](#springrest_crud_c)

		* [Atualização de um cliente](#springrest_crud_u)

		* [Deleção de um cliente](#springrest_crud_d)

	* [BÔNUS: O projeto final](#springrest_final)

* [Spring Boot](#springboot)

	* [Spring Boot Initializr](#springboot_initializr)

	* [Uma página inicial bem simples](#springboot_simplehome)

	* [Spring Boot Dev Tools](#springboot_devtools)

	* [Spring Boot Actuator](#springboot_actuator)

	* [Segurança](#springboot_security)

	* [Como rodar aplicativos do Spring Boot via linha de comando](#springboot_commandline)

	* [Application Properties](#springboot_applicationproperties)

	* [REST API com Hibernate](#springboot_resthibernate)

	* [REST API com JPA](#springboot_restjpa)

	* [Spring Data](#springboot_data)

		* [Spring Data JPA](#springboot_data_jpa)

		* [Spring Data REST](#springboot_data_rest)

		* [BÔNUS: O projeto final](#springboot_data_final)

* [Thymeleaf](#thymeleaf)

	* [Tabelas](#thymeleaf_tables)

	* [Projeto completo CRUD: Thymeleaf + Spring Boot](#thymeleaf_crudfinal)

* [BÔNUS: Calculadora](#calculator)

* [BÔNUS: RPC API](#rpc)

# Introdução<span id="intro"></span>

Leia o [README](README.md).

# Spring Framework<span id="spring"></span>

Spring é um framework completo que fornece uma estrutura para criar aplicações Java. Esse framework é constituído de módulos agrupados em *Core Container*, *Data Access/Integration*, *Web*, *AOP (Aspect Oriented Programming)*, *Instrumentation* e *Test*.

Por exemplo, dentro do *Data Access/Integration* (Integração/Acesso aos Dados), temos o JDBC, ORM, OXM, JMS e Transactions. Já esse ORM, provê integração a APIs como JPA, JDO, Hibernate e iBatis.

## Configuração<span id="spring_config"></span>

Usaremos o Eclipse EE. É bem simples, crie um novo `Java Project`, mas **não** crie um `module-info.java` pra ele!

Baixe o [Tomcat](https://tomcat.apache.org/). Se você for usar o Spring 5.x, fique sabendo que essa versão só é compatível com a versão 9 do Tomcat. Mude para o modo de perspectiva do Java EE, na parte de baixo clique na aba `Servers` e clique no link para criar um novo servidor. Depois de configurar você pode voltar para a perspectiva normal do Java.<br>
Precisamos escolher uma versão mais antiga porque o Jakarta EE *(uma versão comunitária do Java EE, mas que não substitui o Java EE,)* renomeou os nomes dos pacotes, ou seja, de `javax.*` foi para `jakarta.*`, o que gera uma série de incompatibilidades. Por exemplo, o que antes era `javax.servlet.http.HttpServlet` é agora `jakarta.servlet.http.HttpServlet`. Spring 5 ainda é baseado em Java EE (`javax.*`).

Acesse o site do [JFrog](https://repo.spring.io/ui/) e siga este caminho: `Artifactory` => `Artifacts` => `libs-release` => `org` => `springframework` => `spring` => Escolha a versão mais recente => `spring-x.x.x-dist.zip` *(sendo `x.x.x` a versão)*. Baixe e descompacte o arquivo .zip, crie uma pasta `lib` no seu projeto, cole os arquivos jar lá e adicione-os ao seu projeto: clique com o botão direito do mouse sobre o nome do projeto => `Build Path` => `Configure Build Path` => Vá na aba `Libraries` => Selecione `Class Path` => `Add JARs...` => Procure os arquivos JARs na pasta `lib` do seu projeto => Aplique as mudanças

## Primeiro projeto<span id="spring_primeiropro"></span>

Há 3 formas de configurar um projeto:

* Com arquivo XML

* Com *Annotations*

* Sem arquivo XML

Atualmente se usa mais esses dois últimos. Vamos ver cada um deles.

### Com configuração XML<span id="spring_primeiropro_xml"></span>

Dentro da pasta `src`, crie o arquivo `applicationContext.xml`, este será o conteúdo dele:

**applicationContext.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">
    
        
        <!-- Defina seus beans aqui -->
        
        <bean id="meuTecnico" class="dominio.spring1.TecnicoDeFutebol">             
        </bean>
    
    </beans>

Crie um pacote chamado `dominio.spring1`. Dentro dele crie os seguintes arquivos:

**Tecnico.java**

    package dominio.spring1;
    
    public interface Tecnico {
        public String getTarefa();
    }

**TecnicoDeFutebol.java**

    package dominio.spring1;
    
    public class TecnicoDeFutebol implements Tecnico {
    
        @Override
        public String getTarefa() {
            
            return "Correr 5km";
        }
    
    }

**App.java**

    package dominio.spring1;
    
    import org.springframework.context.support.ClassPathXmlApplicationContext;
    
    public class App {
    
        public static void main(String[] args) {
            
            ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
            
            Tecnico oTecnico = context.getBean("meuTecnico", Tecnico.class);
            
            System.out.println(oTecnico.getTarefa());
            
            context.close();
    
        }
    
    }


Vamos entender esse código: A ideia é simples, tem uma interface `Tecnico` que é usada na classe `TecnicoDeFutebol` e esta classe tem um método que exibirá uma certa mensagem. Basicamente toda classe que nos gerará um objeto.

No arquivo .xml temos a linha abaixo:

    <bean id="meuTecnico" class="dominio.spring1.TecnicoDeFutebol"></bean>

Definimos um *bean* para a classe TecnicoDeFutebol cujo id será "meuTecnico" *(eu poderia escolher qualquer palavra)*. Em `class` colocamos o caminho para a classe.

No arquivo `App.java`, temos a linha a seguir:

    ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");

Ele serve para apontar o arquivo .xml de configuração, eu poderia ter escolhido qualquer nome para o arquivo .xml.

    Tecnico oTecnico = context.getBean("meuTecnico", Tecnico.class);

É assim que criamos uma bean.

Depois você precisará fechar o bean.

    context.close();

Por padrão, as beans tem escopo *singleton*, de forma que se eu fizer isso:

    Tecnico oTecnico = context.getBean("meuTecnico", Tecnico.class);
    Tecnico oOutroTecnico = context.getBean("meuTecnico", Tecnico.class);

Continuaremos com o mesmo objeto, pois `oTecnico` e `oOutroTecnico` apontarão para o mesmo espaço de memória. Posso provar isso, modifique o arquivo `App.java` pra isso e veja por si só:

    package dominio.spring1;
    
    import org.springframework.context.support.ClassPathXmlApplicationContext;
    
    public class App {
    
        public static void main(String[] args) {
            
            ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
            
            Tecnico oTecnico = context.getBean("meuTecnico", Tecnico.class);
            Tecnico oOutroTecnico = context.getBean("meuTecnico", Tecnico.class);
            
            System.out.println(oTecnico == oOutroTecnico);
            
            context.close();
    
        }
    
    }


Para criar *beans* individualizados, precisamos definir o escopo como propotype. É simples, vá em `applicationContext.xml` e adicione o atributo `scope="prototype"`:

    <bean id="meuTecnico" class="dominio.spring1.TecnicoDeFutebol" scope="prototype"></bean>

Agora veja se `System.out.println(oTecnico == oOutroTecnico)` continuará retornando *true*.

#### Projeto com dependências<span id="spring_primeiropro_xml_dependencias"></span>

**applicationContext.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">
    
        <!-- Defina suas dependências aqui -->  
        <bean id="minhaDica" class="dominio.spring1.DicaDoTecnico">
        </bean>
        
        <!-- Defina seus beans aqui -->    
        <bean id="meuTecnico" class="dominio.spring1.TecnicoDeFutebol">
        	<!-- define a injeção de construtor -->
        	<constructor-arg ref="minhaDica" />
        </bean>
    
    </beans>

**Dica.java**

    package dominio.spring1;
    
    public interface Dica {
        public String getDica();
    }

**DicaDoTecnico.java**

    package dominio.spring1;
    
    public class DicaDoTecnico implements Dica {
    
        @Override
        public String getDica() {
            return "Todo dia, pela manhã, beba suco de limão com ovo";
        }
    
    }

**Tecnico.java**

    package dominio.spring1;
    
    public interface Tecnico {
        public String getTarefa();
        public String getDica();
    }

**TecnicoDeFutebol.java**

    package dominio.spring1;
    
    public class TecnicoDeFutebol implements Tecnico {
        
        private Dica dica;
    
        public TecnicoDeFutebol(Dica dica) {
            this.dica = dica;
        }
    
        @Override
        public String getTarefa() {
            
            return "Correr 5km";
        }
    
        @Override
        public String getDica() {
            return dica.getDica();
        }
    
    }

**App.java**

    package dominio.spring1;
    
    import org.springframework.context.support.ClassPathXmlApplicationContext;
    
    public class App {
    
        public static void main(String[] args) {
            
            ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
            
            Tecnico oTecnico = context.getBean("meuTecnico", Tecnico.class);
            
            System.out.println(oTecnico.getTarefa());
            System.out.println(oTecnico.getDica());
            
            context.close();
    
        }
    
    }

Vejamos as novidades.

Em `applicationContext.xml` criamos a bean para a classe `DicaDoTecnico`

    <bean id="minhaDica" class="dominio.spring1.DicaDoTecnico"></bean>

E referenciamos essa nova *bean* dentro da bean da classe `TecnicoDeFutebol`:

    <bean id="meuTecnico" class="dominio.spring1.TecnicoDeFutebol">
        <constructor-arg ref="minhaDica" />
    </bean>

Repare que o atributo `ref` contém o `id` da *bean* a qual ela referencia. Compare o trecho acima com o trecho debaixo, que se refere ao construtor da classe `TecnicoDeFutebol`:

    public TecnicoDeFutebol(Dica dica) {
        this.dica = dica;
    }

#### Lidando com setters<span id="spring_primeiropro_xml_setters"></span>

**applicationContext.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">
    
        <!-- Defina suas dependências aqui -->  
        <bean id="minhaDica" class="dominio.spring1.DicaDoTecnico">
        </bean>
        
        <!-- Defina seus beans aqui -->    
        <bean id="meuTecnico" class="dominio.spring1.TecnicoDeFutebol">
            <!-- define a injeção do setter -->
            <property name="dica" ref="minhaDica" />
        </bean>
    
    </beans>

**TecnicoDeFutebol.java**

    package dominio.spring1;
    
    public class TecnicoDeFutebol implements Tecnico {
        
        private Dica dica;
    
        public TecnicoDeFutebol() {
            
        }
    
        public void setDica(Dica dica) {
            this.dica = dica;
        }
    
        @Override
        public String getTarefa() {
            
            return "Correr 5km";
        }
    
        @Override
        public String getDica() {
            return dica.getDica();
        }
    
    }

**App.java**

    package dominio.spring1;
    
    import org.springframework.context.support.ClassPathXmlApplicationContext;
    
    public class App {
    
        public static void main(String[] args) {
            
            ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
            
            Tecnico oTecnico = context.getBean("meuTecnico", Tecnico.class);
            
            System.out.println(oTecnico.getTarefa());
            System.out.println(oTecnico.getDica());
            
            context.close();
    
        }
    
    }

Os dois atributos da *tag* `<property name="dica" ref="minhaDica" />` merecem nossa atenção. O Spring transformará o valor atribuído em `name` em *set + Valor*, que no caso transformará *"dica"* em *"<b>setD</b>ica"*; um exemplo pra fixar, se o valor de `name` fosse *"storageService"*, Spring criaria *"<b>setS</b>torageService"*; tenha certeza que o nome a ser criado pelo Spring é o mesmo nome do método da classe referenciada. Já o valor de `ref` deve ser o `id` da *bean* que será injetada.

#### Injeção de valores literais<span id="spring_primeiropro_xml_literalvalues"></span>

**applicationContext.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">
    
        <!-- Defina suas dependências aqui -->  
        <bean id="minhaDica" class="dominio.spring1.DicaDoTecnico">
        </bean>
        
        <!-- Defina seus beans aqui -->    
        <bean id="meuTecnico" class="dominio.spring1.TecnicoDeFutebol">
            <!-- define a injeção do setter -->
            <property name="dica" ref="minhaDica" />
            
            <!-- injeta literal values -->
            <property name="email" value="nome@email.com" />
            <property name="cidade" value="Rio de Janeiro" />
        </bean>
    
    </beans>

**TecnicoDeFutebol.java**

    package dominio.spring1;
    
    public class TecnicoDeFutebol implements Tecnico {
        
        private Dica dica;
        
        private String email;
        private String cidade;
    
        public TecnicoDeFutebol() {
            
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        public String getCidade() {
            return cidade;
        }
    
        public void setCidade(String cidade) {
            this.cidade = cidade;
        }
    
        public void setDica(Dica dica) {
            this.dica = dica;
        }
    
        @Override
        public String getTarefa() {
            
            return "Correr 5km";
        }
    
        @Override
        public String getDica() {
            return dica.getDica();
        }
    
    }

**App.java**

    package dominio.spring1;
    
    import org.springframework.context.support.ClassPathXmlApplicationContext;
    
    public class App {
    
        public static void main(String[] args) {
            
            ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
            
            TecnicoDeFutebol oTecnico = context.getBean("meuTecnico", TecnicoDeFutebol.class);
            
            System.out.println(oTecnico.getTarefa());
            System.out.println(oTecnico.getDica());
            
            System.out.println(oTecnico.getEmail());
            System.out.println(oTecnico.getCidade());
            
            context.close();
    
        }
    
    }

Creio que você consiga interpretar o que está acontecendo no arquivo .xml, repare que defino os valores lá mesmo no arquivo .xml. Na classe `TecnicoDeFutebol` adicionei as duas variáveis `email` e `cidade`.

Caso você estranhe porque mudei de...

     Tecnico oTecnico = context.getBean("meuTecnico", Tecnico.class);

...para

    TecnicoDeFutebol oTecnico = context.getBean("meuTecnico", TecnicoDeFutebol.class);

, é porque a interface `Tecnico` não tem os métodos `getEmail()`/`setEmail()` e `getCidade()`/`setCidade()` que se encontra somente na classe `TecnicoDeFutebol`. Isso é conhecimento de Java, não de Spring, não se permita ter tais dúvidas.

#### Injeção de valores de um arquivo<span id="spring_primeiropro_xml_properties"></span>

Inserir valores diretamente no arquivo .xml pode não ser a melhor abordagem, portanto pode ser mais interessante utilizar um arquivo de propriedades.

Na pasta `src`, crie o arquivo chamado `dados.properties`.

**dados.properties**

    foo.email=nome@email.com
    foo.cidade=Rio de Janeiro

**applicationContext.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">
    
        <!-- Carrega o arquivo .properties -->
        <context:property-placeholder location="classpath:dados.properties" />
    
        <!-- Defina suas dependências aqui -->  
        <bean id="minhaDica" class="dominio.spring1.DicaDoTecnico">
        </bean>
        
        <!-- Defina seus beans aqui -->    
        <bean id="meuTecnico" class="dominio.spring1.TecnicoDeFutebol">
        	<!-- define a injeção do setter -->
        	<property name="dica" ref="minhaDica" />
        	
        	<!-- injeta literal values -->
        	<property name="email" value="${foo.email}" />
        	<property name="cidade" value="${foo.cidade}" />
        </bean>
    
    </beans>

Além do arquivo .properties, as novidades no arquivo `applicationContext.xml` são:

    <context:property-placeholder location="classpath:dados.properties" />

Que carrega o arquivo com os valores.

    	<property name="email" value="${foo.email}" />
    <property name="cidade" value="${foo.cidade}" />

A substituição dos valores que estavam *hardcoded* dentro do arquivo .xml por variáveis *(`${foo.email}` e `${foo.cidade}`)*. Não é obrigado que você use esse `foo.` e nem mesmo que o arquivo tenha a extensão .properties, se eu quisesse eu poderia escrever assim:

**dados**

    email=nome@email.com
    qualquercoisa.cidade=Rio de Janeiro

**applicationContext.xml**

    [...]
    <context:property-placeholder location="classpath:dados" />
    [...]
    <property name="email" value="${email}" />
    	<property name="cidade" value="${qualquercoisa.cidade}" />
    [...]

### Inversão de controle e Injeção de Dependência<span id="spring_primeiropro_iocinj"></span>

Na minha opinião, fica mais fácil explicar esses conceitos após você ter sido exposto(a) ao Spring. Vamos ver como seria nosso projeto se ele fosse escrito em Java puro:

**Dica.java**

    package dominio;
    
    public interface Dica {
        public String getDica();
    }

**DicaDoTecnico.java**

    package dominio;
    
    public class DicaDoTecnico implements Dica {
    
        @Override
        public String getDica() {
            return "Todo dia, pela manhã, beba suco de limão com ovo";
        }
    
    }

**Tecnico.java**

    package dominio;
    
    public interface Tecnico {
        public String getTarefa();
        public String getDica();
    }

**TecnicoDeFutebol.java**

    package dominio;
    
    public class TecnicoDeFutebol implements Tecnico {
        
        private Dica dica;
        public TecnicoDeFutebol(Dica dica) {
            this.dica = dica;
        }
    
        @Override
        public String getTarefa() {
            
            return "Correr 5km";
        }
    
        @Override
        public String getDica() {
            return dica.getDica();
        }
    
    }


**App.java**

    package dominio;
    
    
    public class App {
    
        public static void main(String[] args) {
            
            DicaDoTecnico dica = new DicaDoTecnico(); 
            
            Tecnico oTecnico = new TecnicoDeFutebol(dica);
            
            System.out.println(oTecnico.getTarefa());
            System.out.println(oTecnico.getDica());
    
        }
    
    }

Num programa Java comum, nós mesmos instanciamos um objeto:

    Tecnico oTecnico = new TecnicoDeFutebol(...);

Na **Inversão de Controle**, a instanciação é feita externamente e não dentro da classe em questão

    Tecnico oTecnico = context.getBean(...);

A **Injeção de Dependência** é similar, injeta a dependência de uma classe para outra classe.

### Com Java Annotations<span id="spring_primeiropro_javaannotations"></span>

Recriaremos o projeto anterior com menor uso do arquivo .xml. Mostrarei aqui apenas os arquivos que precisaremos editar, o resto continuará como no exemplo anterior:

**applicationContext.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">
    
        <!-- Habilita o escaneamento de componentes -->  
        <context:component-scan base-package="dominio.spring1" />
    
    </beans>

**DicaDoTecnico.java**

    package dominio.spring1;
    
    import org.springframework.stereotype.Component;
    
    @Component
    public class DicaDoTecnico implements Dica {
    
        @Override
        public String getDica() {
            return "Todo dia, pela manhã, beba suco de limão com ovo";
        }
    
    }

**TecnicoDeFutebol.java**

    package dominio.spring1;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Component;
    
    @Component
    public class TecnicoDeFutebol implements Tecnico {
        
        private Dica dica;
    
        @Autowired
        public TecnicoDeFutebol(Dica dica) {
            this.dica = dica;
        }
    
        @Override
        public String getTarefa() {
            
            return "Correr 5km";
        }
    
        @Override
        public String getDica() {
            return dica.getDica();
        }
    
    }

**App.java**

    package dominio.spring1;
    
    import org.springframework.context.support.ClassPathXmlApplicationContext;
    
    public class App {
    
        public static void main(String[] args) {
            
            ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
            
            Tecnico oTecnico = context.getBean("tecnicoDeFutebol", Tecnico.class);
            
            System.out.println(oTecnico.getTarefa());
            System.out.println(oTecnico.getDica());
            
            context.close();
    
        }
    
    }

É só colocar `@Component` sobre as classes que virarão *beans*. O `@Autowired` serve para injetar *beans* dependentes em outros *beans*.

Se você prestar atenção, se perguntará porque na linha...

    Tecnico oTecnico = context.getBean("tecnicoDeFutebol", Tecnico.class);

...do arquivo `App.java`, pudemos definir o nome `"tecnicoDeFutebol"` sem precisar ter estabelecido um `id` pra ele. É que o próprio Spring gera esse nome pra nós, ele pega o nome da classe e deixa minúscula a primeira letra, ou seja, o próprio Spring pegou o nome da classe `TecnicoDeFutebol` e criou a id `TecnicoDeFutebol`. Entretanto, se a primeira e segunda letra forem maiúsculas, como por exemplo em `RESTFutebol`,o nome continuará o mesmo. Mas podemos definir um nome qui quisermos na anotação:

**TecnicoDeFutebol.java**

    package dominio.spring1;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Component;
    
    @Component("meuTecnico")
    public class TecnicoDeFutebol implements Tecnico {
        
        private Dica dica;
    
        @Autowired
        public TecnicoDeFutebol(Dica dica) {
            this.dica = dica;
        }
    
        @Override
        public String getTarefa() {
            
            return "Correr 5km";
        }
    
        @Override
        public String getDica() {
            return dica.getDica();
        }
    
    }

**App.java**

    package dominio.spring1;
    
    import org.springframework.context.support.ClassPathXmlApplicationContext;
    
    public class App {
    
        public static void main(String[] args) {
            
            ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
            
            Tecnico oTecnico = context.getBean("meuTecnico", Tecnico.class);
            
            System.out.println(oTecnico.getTarefa());
            System.out.println(oTecnico.getDica());
            
            context.close();
    
        }
    
    }

Você pode pôr a anotação xxxxx em outros locais relacionados:

**TecnicoDeFutebol.java**

    package dominio.spring1;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Component;
    
    @Component
    public class TecnicoDeFutebol implements Tecnico {
        
        @Autowired
        private Dica dica;
    
        public TecnicoDeFutebol(Dica dica) {
            this.dica = dica;
        }
    
        @Override
        public String getTarefa() {
            
            return "Correr 5km";
        }
    
        @Override
        public String getDica() {
            return dica.getDica();
        }
    
    }

#### @Qualifier<span id="spring_primeiropro_javaannotations_qualifier"></span>

O que acontece se eu criar uma nova dica? Repare que não tem nada definindo a *Dica* `dicaDoTecnico`. Crie uma nova classe que estende `Dica`.

**DicaDoProfessor**

    package dominio.spring1;
    
    import org.springframework.stereotype.Component;
    
    @Component
    public class DicaDoProfessor implements Dica {
    
        @Override
        public String getDica() {
            return "Leia livros todos os dias";
        }
    
    }

Tente rodar o programa. Você verá o seguinte erro:

> Error creating bean with name 'tecnicoDeFutebol' defined in file [~/eclipse-workspace/spring1/bin/dominio/spring1/TecnicoDeFutebol.class]: Unsatisfied dependency expressed through constructor parameter 0; nested exception is org.springframework.beans.factory.NoUniqueBeanDefinitionException: No qualifying bean of type 'dominio.spring1.Dica' available: expected single matching bean but found 2: dicaDoProfessor,dicaDoTecnico

Especialmente esta parte: `but found 2: dicaDoProfessor,dicaDoTecnico`. *A propósito, repare que o próprio Spring deixou a primeira letra em minúsculo*.

Podemos usar a anotação `@Qualifier` para definir qual *bean* usar.

    package dominio.spring1;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.beans.factory.annotation.Qualifier;
    import org.springframework.stereotype.Component;
    
    @Component
    public class TecnicoDeFutebol implements Tecnico {
        
        @Autowired
        @Qualifier("dicaDoProfessor")
        private Dica dica;
    
        public TecnicoDeFutebol() {
        
        }
    
        @Override
        public String getTarefa() {
            
            return "Correr 5km";
        }
    
        @Override
        public String getDica() {
            return dica.getDica();
        }
    
    }

Se você quiser, você nem precisa pôr a dependência no construtor da *bean*.

    package dominio.spring1;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Component;
    
    @Component
    public class TecnicoDeFutebol implements Tecnico {
        
        @Autowired
        private Dica dica;
    
        public TecnicoDeFutebol() {
            
        }
    
        @Override
        public String getTarefa() {
            
            return "Correr 5km";
        }
    
        @Override
        public String getDica() {
            return dica.getDica();
        }
    
    }

### Sem configuração XML<span id="spring_primeiropro_semxml"></span>

Finalmente poderemos nos livrar do arquivo .xml. Delete o arquivo `applicationContext.xml` se você quiser.

Crie o arquivo `ArquivoDeConfiguracao.java` dentro do pacote. Assim como o arquivo .xml, você pode usar o nome que quiser.

**ArquivoDeConfiguracao.java**

    package dominio.spring1;
    
    import org.springframework.context.annotation.ComponentScan;
    import org.springframework.context.annotation.Configuration;
    
    @Configuration
    @ComponentScan("dominio.spring1")
    public class ArquivoDeConfiguracao {
    
    }

E edite o arquivo `App.java`:

**App.java**

    package dominio.spring1;
    
    import org.springframework.context.annotation.AnnotationConfigApplicationContext;
    
    public class App {
    
        public static void main(String[] args) {
            
            AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(ArquivoDeConfiguracao.class);
            
            Tecnico oTecnico = context.getBean("tecnicoDeFutebol", Tecnico.class);
            
            System.out.println(oTecnico.getTarefa());
            System.out.println(oTecnico.getDica());
            
            context.close();
    
        }
        
    }

Em `ArquivoDeConfiguracao.java`, a linha `@ComponentScan("dominio.spring1")` faz o papel de `<context:component-scan base-package="dominio.spring1" />`. O resto deve ser óbvio para você.

Em `App.java`, simplesmente substitui...

    ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");

... por:

    AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(ArquivoDeConfiguracao.class);

#### @Bean<span id="spring_primeiropro_semxml_bean"></span>

Em vez de usar `@Component`, podemos usar a anotação `@Bean`. Mas essas anotações colocamos no arquivo que contém a anotação `@Configuration`.

Para que você não se perca, re-exibirei todos os arquivos do projeto:

**Dica.java**

    package dominio.spring1;
    
    public interface Dica {
        public String getDica();
    }

**DicaDoTecnico.java**

    package dominio.spring1;
    
    public class DicaDoTecnico implements Dica {
    
        @Override
        public String getDica() {
            return "Todo dia, pela manhã, beba suco de limão com ovo";
        }
    
    }

**Tecnico.java**

    package dominio.spring1;
    
    public interface Tecnico {
        public String getTarefa();
        public String getDica();
    }

**TecnicoDeFutebol.java**

    package dominio.spring1;
    
    public class TecnicoDeFutebol implements Tecnico {
        
        private Dica dica;
    
        public TecnicoDeFutebol(Dica dica) {
            this.dica = dica;
        }
    
        @Override
        public String getTarefa() {
            
            return "Correr 5km";
        }
    
        @Override
        public String getDica() {
            return dica.getDica();
        }
    
    }

**ArquivoDeConfiguracao.java**

    package dominio.spring1;
    
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.Configuration;
    
    @Configuration
    public class ArquivoDeConfiguracao {
        
        @Bean
        Dica dicaDoTecnico () {
            return new DicaDoTecnico();
        }
        
        @Bean
        Tecnico tecnicoDeFutebol () {
            return new TecnicoDeFutebol(dicaDoTecnico());
        }
    
    }

**App.java**

    package dominio.spring1;
    
    import org.springframework.context.annotation.AnnotationConfigApplicationContext;
    
    public class App {
    
        public static void main(String[] args) {
            
            AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(ArquivoDeConfiguracao.class);
            
            Tecnico oTecnico = context.getBean("tecnicoDeFutebol", Tecnico.class);
            
            System.out.println(oTecnico.getTarefa());
            System.out.println(oTecnico.getDica());
            
            context.close();
    
        }
        
    }

#### Injeção de valores de um arquivo<span id="spring_primeiropro_semxml_properties"></span>

**dados.properties**

    foo.email=nome@email.com
    foo.cidade=Rio de Janeiro

**ArquivoDeConfiguracao.java**

    package dominio.spring1;
    
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.context.annotation.PropertySource;
    
    @Configuration
    @PropertySource("classpath:dados.properties")
    public class ArquivoDeConfiguracao {
        
        @Bean
        Dica dicaDoTecnico () {
            return new DicaDoTecnico();
        }
        
        @Bean
        Tecnico tecnicoDeFutebol () {
            return new TecnicoDeFutebol(dicaDoTecnico());
        }
    
    }

**TecnicoDeFutebol.java**

    package dominio.spring1;
    
    import org.springframework.beans.factory.annotation.Value;
    
    public class TecnicoDeFutebol implements Tecnico {
        
        private Dica dica;
        
        @Value("${foo.email}")
        private String email;
        
        @Value("${foo.cidade}")
        private String cidade;
    
        public TecnicoDeFutebol(Dica dica) {
            this.dica = dica;
        }
        
        public String getEmail() {
            return email;
        }
    
        public String getCidade() {
            return cidade;
        }
    
        @Override
        public String getTarefa() {
            return "Correr 5km";
        }
    
        @Override
        public String getDica() {
            return dica.getDica();
        }
    
    }

**App.java**

    package dominio.spring1;
    
    import org.springframework.context.annotation.AnnotationConfigApplicationContext;
    
    public class App {
    
        public static void main(String[] args) {
            
            AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(ArquivoDeConfiguracao.class);
            
            TecnicoDeFutebol oTecnico = context.getBean("tecnicoDeFutebol", TecnicoDeFutebol.class);
            
            System.out.println(oTecnico.getTarefa());
            System.out.println(oTecnico.getDica());
            
            System.out.println(oTecnico.getEmail());
            System.out.println(oTecnico.getCidade());
            
            context.close();
    
        }
        
    }

## @Bean vs @Component<span id="spring_beanxcomponent"></span>

Talvez você tenha dúvidas de quando usar um ou outro. Vejamos esta tabela que fiz com base na resposta [neste link](https://stackoverflow.com/questions/10604298/spring-component-versus-bean).

| @Component | @Bean      |
| :--------: | :--------: |
| Auto detecta e configura a *bean* | Explicitamente declara uma única *bean* |
| Não desassocia a declaração da *bean* da definição da classe | Desassocia   |
| Anotação de nível de classe/tipo | Anotação de nível de método |
| Não deve ser usado com a anotação `@Configuration` | Deve ser usado com `@Configuration` |
| Não se pode criar uma *bean* através de `@Component` se a classe em questão estiver fora do *container* do Spring | Com @Bean podemos, uma boa aplicação é poder utilizar componentes de bibliotecas de terceiros |
| Tem diferentes especializações como `@Controller`, `@Repository` e `@Service` | Não tem nada disso |


# Spring MVC<span id="springmvc"></span>

**Dica de ouro:** Antes de continuar, procure estudar o conteito de MVC antes de progredir. Não precisa ir muito a fundo, parar para escrever código e coisas do tipo, só preciso que você entenda bem o padrão de projeto *Model–view–controller*.

Mude a perspectiva do Eclipse para Java EE.

`File` => `New` => `Dynamic Web Project`

Observe a versão do Tomcat que você utilizará

Copie e cole os JARs que você já baixou dentro da pasta `WEB-INF/lib` *(pode ser que o caminho completo da pasta seja `src/main/java/webapp/WEB-INF/lib`)*. Não precisa ir em `Build Path` porque, neste caso, no momento em que você coloca os arquivos JAR nessa pasta `lib`, eles são automaticamente reconhecidos

Além desses arquivos, você precisará de mais 2:

* [javax.servlet.jsp.jstl](https://mvnrepository.com/artifact/org.glassfish.web/javax.servlet.jsp.jstl)

* [javax.servlet.jsp.jstl-api](https://mvnrepository.com/artifact/javax.servlet.jsp.jstl/javax.servlet.jsp.jstl-api)

Dentro da pasta `WEB-INF`, adicionamos os dois arquivos abaixo:

**web.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd" id="WebApp_ID" version="4.0">
      <display-name>spring-mvc</display-name>
     
        <absolute-ordering />
     
        <!-- Passo 1: Configura Spring MVC Dispatcher Servlet -->
        <servlet>
            <servlet-name>dispatcher</servlet-name>
            <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
            <init-param>
                <param-name>contextConfigLocation</param-name>
                <param-value>/WEB-INF/spring-mvc.xml</param-value>
            </init-param>
            <load-on-startup>1</load-on-startup>
        </servlet>
     
        <!-- Step 2: Prepara o URL mapping para o Spring MVC Dispatcher Servlet -->
        <servlet-mapping>
            <servlet-name>dispatcher</servlet-name>
            <url-pattern>/</url-pattern>
        </servlet-mapping>
    </web-app>

**spring-mvc.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xmlns:mvc="http://www.springframework.org/schema/mvc"
        xsi:schemaLocation="
            http://www.springframework.org/schema/beans
            http://www.springframework.org/schema/beans/spring-beans.xsd
            http://www.springframework.org/schema/context
            http://www.springframework.org/schema/context/spring-context.xsd
            http://www.springframework.org/schema/mvc
            http://www.springframework.org/schema/mvc/spring-mvc.xsd">
    
        <!-- Passo 3: Adiciona suporte para component scanning -->
        <context:component-scan base-package="dominio.spring" />
    
        <!-- Passo 4: Adiciona suporte para conversão, formatação e suporte a validação -->
        <mvc:annotation-driven/>
    
        <!-- Passo 5: Define Spring MVC view resolver -->
        <bean
            class="org.springframework.web.servlet.view.InternalResourceViewResolver">
            <property name="prefix" value="/WEB-INF/view/" />
            <property name="suffix" value=".jsp" />
        </bean>
    
    </beans>

Na pasta `WEB-INF`, criamos a pasta `view`

## Controllers<span id="springmvc_controllers"></span>

Crie o pacote dentro de `src/main/java` *(ou `src` se você estiver usando uma versão antiga do Eclipse)*. Chamarei meu pacote de `dominio.spring.mvc`

Dentro desse pacote, crie o seguinte arquivo:

**HomeController.java**

    package dominio.spring.mvc;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.RequestMapping;
    
    @Controller
    public class HomeController {
    
        @RequestMapping("/")
        public String exibirPagina() {
            return "home"; // No arquivo spring-mvc.xml, temos propriedades com os valores prefix e suffix, eles próprios complementam esse nome, de forma que ele é, na verdade, /WEB-INF/view/home.jsp. Essa é a mágica do Spring 
        }
    }

`@Controller` extende `@Component`

Em `WEB-INF/view`, crie o arquivo abaixo:

**home.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring MVC</title>
    </head>
    <body>
        <p>Olá Mundo!</p>
    </body>
    </html>

Agora você pode clicar com o botão direito do mouse sobre o nome do projeto, `Run As` => `Run on server`

Sobre a linha `<context:component-scan base-package="dominio.spring" />`, coloquei o nome do pacote como `dominio.spring` em vez de `dominio.spring.mvc` por nenhuma razão especial, ambos serviriam, até mesmo somente `dominio` serviria.

Quando eu estava testando esse código, eu tive um erro 404 no Spring em que a página me deu a seguinte mensagem de erro:

> **Description** The origin server did not find a current representation for the target resource or is not willing to disclose that one exists.

E no log tinha:

    [...]
    mai. 08, 2022 9:00:54 PM org.springframework.web.servlet.DispatcherServlet noHandlerFound
    ADVERTÊNCIA: No mapping for GET /spring-mvc-demo/

Se você se deparar com este erro e tiver certeza que seu código está correto, tente criar um novo Workspace no Eclipse.

Outra solução mais elegante é:

1. Remover o projeto do Eclipse

2. Abrir a pasta *(com seu gerenciador de arquivos mesmo)* e remover todos os arquivos e pastas com exceção de `src`

3. Abrir o projeto no Eclipse

4. Clicar com o botão direito do mouse sobre o projeto e ir em `Properties`.

5. Verificar se o `Java Build Path`, `Java Compiler`, `Project Facets` estão usando a mesma versão do Java

6. Removee o servidor da tab `Servers` e adicioná-lo novamente.

7. Reconstruir o projeto

8. `Run on Server`.

## Formulários<span id="springmvc_forms"></span>

Modifique o arquivo `home.jsp`:

**home.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring MVC</title>
    </head>
    <body>
        <p>Olá Mundo!</p>
        
        <p>Clique <a href="mostrarForm">aqui</a> para acessar a página do formulário</p>
    </body>
    </html>

E crie o arquivo `FormController.java` dentro do pacote.

**FormController.java**

    package dominio.spring.mvc;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.RequestMapping;
    
    @Controller
    public class FormController {
        
        @RequestMapping("/mostrarForm")
        public String exibirForm() {
            return "form";
        }
        
        @RequestMapping("/processarForm")
        public String processarForm() {
            return "resultado";
        }
    }

Dentro da pasta `WEB-INF/view`, crie os dois arquivos abaixo:

**form.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring MVC</title>
    </head>
    <body>
        <form action="processarForm" method="GET">
            <input type="text" name="nomeDoFuncionario" placeholder="Por favor, insira o nome" />
            <input type="submit" />
        </form>
    </body>
    </html>

**resultado.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring MVC</title>
    </head>
    <body>
        <p>O nome do funcionário ou funcionária é: ${param.nomeDoFuncionario}</p>
    </body>
    </html>

## Usando Models<span id="springmvc_models"></span>

Faça as seguintes modificações:

**form.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring MVC</title>
    </head>
    <body>
        <h1>Página de formulários</h1>
        
        <hr>
        
        <br>
        
        <hr>
        
        <h2>Formulário 1</h2>
        <form action="processarForm" method="GET">
            <input type="text" name="nomeDoFuncionario" placeholder="Por favor, insira o nome" />
            <input type="submit" />
        </form>
        
        <hr>
        
        <h2>Formulário 2</h2>
        <form action="processarForm2" method="GET">
            <input type="text" name="texto" placeholder="Escreva qualquer coisa aqui" />
            <input type="submit" />
        </form>
    </body>
    </html>

**FormController.java**

    package dominio.spring.mvc;
    
    import javax.servlet.http.HttpServletRequest;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.RequestMapping;
    
    @Controller
    public class FormController {
        
        @RequestMapping("/mostrarForm")
        public String exibirForm() {
            return "form";
        }
        
        @RequestMapping("/processarForm")
        public String processarForm() {
            return "resultado";
        }
        
        @RequestMapping("/processarForm2")
        public String processarForm2(HttpServletRequest request, Model model) {
            
            String texto = request.getParameter("texto");
            
            texto = texto.toUpperCase();
                    
            model.addAttribute("valorDoModel", texto);
            
            return "resultado2";
        }
    }

Em `WEB-INF/view`, crie o arquivo abaixo:

**resultado2.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring MVC</title>
    </head>
    <body>
        <p>O texto original era ${param.texto}, o modificado é ${valorDoModel}</p>
    </body>
    </html>

## Recursos estáticos<span id="springmvc_staticresources"></span>

Para usar recursos como CSS, JavaScript, imagens, etc, você deve processá-los como um URL Mapping.

Colocarei tudo numa pasta chamada `assets` – que será criada dentro da pasta `webapp` –, mas você pode pôr o nome que quiser. Também criarei uma pasta `layout` dentro da pasta `view` para guardar arquivos .jsp que basicamente são pedaços de HTML que reaproveitarei em outras páginas do projeto.

**WEB-INF/view/layout/head.jsp**

    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" type="text/css" href="${pageContext.request.contextPath}/assets/css/estilo.css">
        <title>Spring MVC</title>
    </head>

**webapp/assets/css/estilo.css**

    body {
        background-color: #FEF5E7;
    }

**webapp/assets/images/x.jpg**

*Ponha uma imagem qualquer aqui. Para que você não se perca, sugiro que você use uma imagem renomeada para `x` cuja extensão seja .jpg.*

E atualize o conteúdo dos seguintes arquivos:

**/WEB-INF/spring-mvc.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xmlns:mvc="http://www.springframework.org/schema/mvc"
        xsi:schemaLocation="
            http://www.springframework.org/schema/beans
            http://www.springframework.org/schema/beans/spring-beans.xsd
            http://www.springframework.org/schema/context
            http://www.springframework.org/schema/context/spring-context.xsd
            http://www.springframework.org/schema/mvc
            http://www.springframework.org/schema/mvc/spring-mvc.xsd">
    
        <context:component-scan base-package="dominio.spring" />
    
        <mvc:annotation-driven/>
        
        <mvc:resources mapping="/assets/**" location="/assets/"></mvc:resources>
    
        <bean
            class="org.springframework.web.servlet.view.InternalResourceViewResolver">
            <property name="prefix" value="/WEB-INF/view/" />
            <property name="suffix" value=".jsp" />
        </bean>
    
    </beans>

**WEB-INF/view/home.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <jsp:include page="layout/head.jsp" />
    <body>
       <p>Olá Mundo!</p>
       
       <p>Clique <a href="mostrarForm">aqui</a> para acessar a página do formulário</p>
       
       <br>
       
       <img src="${pageContext.request.contextPath}/assets/images/x.jpg" width="200px">
    </body>
    </html>

**WEB-INF/view/form.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <jsp:include page="layout/head.jsp" />
    <body>
        <h1>Página de formulários</h1>
        
        <hr>
        
        <br>
        
        <hr>
        
        <h2>Formulário 1</h2>
        <form action="processarForm" method="GET">
            <input type="text" name="nomeDoFuncionario" placeholder="Por favor, insira o nome" />
            <input type="submit" />
        </form>
        
        <hr>
        
        <h2>Formulário 2</h2>
        <form action="processarForm2" method="GET">
            <input type="text" name="texto" placeholder="Escreva qualquer coisa aqui" />
            <input type="submit" />
        </form>
    </body>
    </html>

**WEB-INF/view/resultado2.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <jsp:include page="layout/head.jsp" />
    <body>
        <p>O texto original era ${param.texto}, o modificado é ${valorDoModel}</p>
    </body>
    </html>

## @RequestParam<span id="springmvc_requestparam"></span>

Podemos usar uma anotação para captar os parâmetros de um formulário:

**FormController.java**

    package dominio.spring.mvc;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RequestParam;
    
    @Controller
    public class FormController {
        
        @RequestMapping("/mostrarForm")
        public String exibirForm() {
            return "form";
        }
        
        @RequestMapping("/processarForm")
        public String processarForm() {
            return "resultado";
        }
        
        @RequestMapping("/processarForm2")
        public String processarForm2(@RequestParam("texto") String texto, Model model) {
            
            texto = texto.toUpperCase();
                    
            model.addAttribute("valorDoModel", texto);
            
            return "resultado2";
        }
    }

## Tags Form<span id="springmvc_tagsform"></span>

Crie os seguintes arquivos:

**src/main/java/Funcionario.java**

    package dominio.spring.mvc;
    
    public class Funcionario {
        
        private String nome;
        
        private String sobreNome;
        
        public Funcionario () {
            
        }
    
        public String getNome() {
            return nome;
        }
    
        public void setNome(String nome) {
            this.nome = nome;
        }
    
        public String getSobreNome() {
            return sobreNome;
        }
    
        public void setSobreNome(String sobreNome) {
            this.sobreNome = sobreNome;
        }
    }

**src/main/java/FuncionarioController.java**

    package dominio.spring.mvc;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.ModelAttribute;
    import org.springframework.web.bind.annotation.RequestMapping;
    
    @Controller
    @RequestMapping("funcionario")
    public class FuncionarioController {
        
        @RequestMapping("/mostrarForm")
        public String mostrarFormulario (Model modelo) {
            
            Funcionario oFuncionario = new Funcionario();
            
            modelo.addAttribute("funcionario", oFuncionario);
            
            return "funcionario-form";
        }
        
        @RequestMapping("/processarForm")
        public String processarForm (@ModelAttribute("funcionario") Funcionario funcionario) { // Lembra onde tem um ModelAttribute="funcionario"?
            
            return "confirmacao-funcionario";
        }
    }

**WEB-INF/view/funcionario-form.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
        
    <!DOCTYPE html>
    <html>
    <jsp:include page="layout/head.jsp" />
    <body>
    
    <h1>Formulário funcionário</h1>
    
    <hr>
    
    <!-- Lembra onde mais tem um ModelAttribute="funcionario"? -->
    <form:form action="processarForm" modelAttribute="funcionario">
    
        <!-- Quando o form for carregado, Spring chamará funcionario.getNome() -->
        Nome: <form:input path="nome" />
        
        <br><br>
        
        <!-- Quando o form for carregado, Spring chamará funcionario.getSobreNome() -->
        Sobrenome: <form:input path="sobreNome" />
        
        <br><br>
        
        <!-- Quando o form for enviado, Spring chamará funcionario.setNome() e funcionario.setSobreNome() -->
        <input type="submit" />
    
    </form:form>
    
    </body>
    </html>

**WEB-INF/view/confirmacao-funcionario.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <jsp:include page="layout/head.jsp" />
    <body>
        <p>O funcionário foi confirmado: ${funcionario.nome} ${funcionario.sobreNome}</p>
    </body>
    </html>

E atualize o arquivo `home.jsp*`, só para facilitar nossa vida.

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <jsp:include page="layout/head.jsp" />
    <body>
        <p>Olá Mundo!</p>
        
        <p>Clique <a href="mostrarForm">aqui</a> para acessar a página do formulário antigo</p>
        
        <p>Clique <a href="funcionario/mostrarForm">aqui</a> para acessar a página do formulário do funcionário</p>
        
        <br>
        
        <img src="${pageContext.request.contextPath}/assets/images/x.jpg" width="200px">
    </body>
    </html>

Vamos lá. Repare que a classe `FuncionarioController` tem dois níveis de `@RequestMapping`, por isso que o endereço de `mostrarForm` dessa classe é `funcionario/mostrarForm`.

A linha `<%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>` habilita o suporte às *tags* `form`, que vêm da biblioteca `spring-webmvc.jar`.

### Só mais um exemplo de tag<span id="springmvc_tagsform_maisumexemplor"></span>

**Funcionario.java**

    package dominio.spring.mvc;
    
    public class Funcionario {
        
        private String nome;
        
        private String sobreNome;
        
        private String pais;
        
        public Funcionario () {
            
        }
    
        public String getNome() {
            return nome;
        }
    
        public void setNome(String nome) {
            this.nome = nome;
        }
    
        public String getSobreNome() {
            return sobreNome;
        }
    
        public void setSobreNome(String sobreNome) {
            this.sobreNome = sobreNome;
        }
    
        public String getPais() {
            return pais;
        }
    
        public void setPais(String pais) {
            this.pais = pais;
        }
        
    }

**funcionario-form.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
        
    <!DOCTYPE html>
    <html>
    <jsp:include page="layout/head.jsp" />
    <body>
    
    <h1>Formulário funcionário</h1>
    
    <hr>
    
    <!-- Lembra onde mais tem um ModelAttribute="funcionario"? -->
    <form:form action="processarForm" modelAttribute="funcionario">
    
        <!-- Quando o form for carregado, Spring chamará funcionario.getNome() -->
        Nome: <form:input path="nome" />
        
        <br><br>
        
        <!-- Quando o form for carregado, Spring chamará funcionario.getSobreNome() -->
        Sobrenome: <form:input path="sobreNome" />
        
        <br><br>
        
        <!-- Quando o form for carregado, Spring chamará funcionario.getPais() -->
        País:
        
        <form:select path="pais">
            <form:option value="Brasil" label="Brasil" />
            <form:option value="Estados Unidos" label="Estados Unidos" />
            <form:option value="&Iacute;ndia" label="Índia" />
            <form:option value="Fran&ccedil;a" label="França" />
        </form:select>
        
        <br><br>
        
        <!-- Quando o form for enviado, Spring chamará funcionario.setNome(), funcionario.setSobreNome() e funcionario.setPais() -->
        <input type="submit" />
    
    </form:form>
    
    </body>
    </html>

**confirmacao-funcionario.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <jsp:include page="layout/head.jsp" />
    <body>
        <p>O funcionário foi confirmado: ${funcionario.nome} ${funcionario.sobreNome}</p>
        
        <p>Ele mora em ${funcionario.pais}</p>
    </body>
    </html>

## Validação<span id="springmvc_validation"></span>

Comecemos com a tabela:

| Annotation      | Descrição                                          |
| --------------- | -------------------------------------------------- |
| @NotNull        | Checa se o valor anotado não é nulo                |
| @Min            | Deve ser maior ou igual a certo valor              |
| @Max            | Deve ser menor ou igual a certo valor              |
| @Size           | Tamanho deve corresponder a certo tamanho          |
| @Pattern        | Deve corresponder a um Regex                       |
| @Future / @Past | Dava deve estar no futuro ou passado de certa data |

O *Java's Standard Bean Validation API* é uma especificação, é necessário uma implementação. Usaremos a implementação do Hibernate. Você pode fazer o download [aqui](https://hibernate.org/validator/).

**Mas atenção**, Hibernate Validator 7 é baseado no Jakarta EE 9. É, tá lembrado do que falamos lá no [capitulo de configuração](#spring_config)? Portanto, Spring 5 não é compatível com Hibernate Validator 7, mas [Hibernate Validator 6.2](https://hibernate.org/validator/releases/6.2/) é compatível com Spring 5. *Fica tranquilo que as versões 6.2 e 7 têm as mesmas capacidades*.

Baixe o arquivo .zip e copie os 3 arquivos .jar dentro da pasta `hibernate-validator-6.2.x.Final/dist/` e os 4 arquivos .jar da pasta `hibernate-validator-6.2.x.Final/dist/lib/required/`.

A seguir veremos os arquivos que atualizaremos:

**Funcionario.java**

    package dominio.spring.mvc;
    
    import javax.validation.constraints.NotNull;
    import javax.validation.constraints.Size;
    
    public class Funcionario {
        
        @NotNull
        @Size(min=1, message="É necessário")
        private String nome;
        
        private String sobreNome;
        
        private String pais;
        
        public Funcionario () {
            
        }
    
        public String getNome() {
            return nome;
        }
    
        public void setNome(String nome) {
            this.nome = nome;
        }
    
        public String getSobreNome() {
            return sobreNome;
        }
    
        public void setSobreNome(String sobreNome) {
            this.sobreNome = sobreNome;
        }
    
        public String getPais() {
            return pais;
        }
    
        public void setPais(String pais) {
            this.pais = pais;
        }
        
    }

**FuncionarioController.java**

    package dominio.spring.mvc;
    
    import javax.validation.Valid;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.validation.BindingResult;
    import org.springframework.web.bind.annotation.ModelAttribute;
    import org.springframework.web.bind.annotation.RequestMapping;
    
    @Controller
    @RequestMapping("funcionario")
    public class FuncionarioController {
        
        @RequestMapping("/mostrarForm")
        public String mostrarFormulario (Model modelo) {
            
            Funcionario oFuncionario = new Funcionario();
            
            modelo.addAttribute("funcionario", oFuncionario);
            
            return "funcionario-form";
        }
        
        @RequestMapping("/processarForm")
        public String processarForm (@Valid @ModelAttribute("funcionario") Funcionario funcionario, BindingResult bindingResult) { // O objeto de BindingResult armazena o resultado da validação
            
            if (bindingResult.hasErrors()) { // Sehá erros, eu quero que o usuário volte à página de formulário
                return "funcionario-form";
            }
            return "confirmacao-funcionario";
        }
    }

**webapp/assets/css/estilo.css**

    body {
        background-color: #FEF5E7;
    }
    
    .error {
        color: red;
    }

**WEB-INF/view/funcionario-form.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
        
    <!DOCTYPE html>
    <html>
    <jsp:include page="layout/head.jsp" />
    <body>
    
    <h1>Formulário funcionário</h1>
    
    <hr>
    
    <!-- Lembra onde mais tem um ModelAttribute="funcionario"? -->
    <form:form action="processarForm" modelAttribute="funcionario">
    
        <!-- Quando o form for carregado, Spring chamará funcionario.getNome() -->
        Nome: <form:input path="nome" />
        <form:errors path="nome" cssClass="error" />
        <!-- O cssClass="error" se refere ao .error do arquivo CSS -->
        
        <br><br>
        
        <!-- Quando o form for carregado, Spring chamará funcionario.getSobreNome() -->
        Sobrenome: <form:input path="sobreNome" />
        
        <br><br>
        
        <!-- Quando o form for carregado, Spring chamará funcionario.getPais() -->
        País:
        
        <form:select path="pais">
            <form:option value="Brasil" label="Brasil" />
            <form:option value="Estados Unidos" label="Estados Unidos" />
            <form:option value="&Iacute;ndia" label="Índia" />
            <form:option value="Fran&ccedil;a" label="França" />
        </form:select>
        
        <br><br>
        
        <!-- Quando o form for enviado, Spring chamará funcionario.setNome(), funcionario.setSobreNome() e funcionario.setPais() -->
        <input type="submit" />
    
    </form:form>
    
    </body>
    </html>


O parâmetro `BindingResult` deve aparecer logo após o atributo do modelo.

Apliquei a verificação apenas no campo nome, mas podemos burlar essa verificação digitando apenas espaços em branco. Como resolver essa falha?

    package dominio.spring.mvc;
    
    import javax.validation.Valid;
    
    import org.springframework.beans.propertyeditors.StringTrimmerEditor;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.validation.BindingResult;
    import org.springframework.web.bind.WebDataBinder;
    import org.springframework.web.bind.annotation.InitBinder;
    import org.springframework.web.bind.annotation.ModelAttribute;
    import org.springframework.web.bind.annotation.RequestMapping;
    
    @Controller
    @RequestMapping("funcionario")
    public class FuncionarioController {
        
        @InitBinder
        public void initBinder (WebDataBinder databinder) {
            
            StringTrimmerEditor stringTrimmerEditor = new StringTrimmerEditor (true);
            
            databinder.registerCustomEditor(String.class, stringTrimmerEditor);
            
        }
        
        @RequestMapping("/mostrarForm")
        public String mostrarFormulario (Model modelo) {
            
            Funcionario oFuncionario = new Funcionario();
            
            modelo.addAttribute("funcionario", oFuncionario);
            
            return "funcionario-form";
        }
        
        @RequestMapping("/processarForm")
        public String processarForm (@Valid @ModelAttribute("funcionario") Funcionario funcionario, BindingResult bindingResult) { // O objeto de BindingResult armazena o resultado da validação
            
            if (bindingResult.hasErrors()) { // Sehá erros, eu quero que o usuário volte à página de formulário
                return "funcionario-form";
            }
            return "confirmacao-funcionario";
        }
    }

`@InitBinder` pré-processa todas as requisições web que vão ao *Controller*. O `StringTrimmerEditor` é definido pela Spring API e remove os espaços em branco.

# Hibernate<span id="hibernate"></span>

*Eu já fiz um tutorial sobre [JPA/Hibernate](JPA-Hibernate.md), mas escrevo este novo em um capítulo para usar a abordagem de outra fonte de estudo. Mas leia antes esse material que fiz para o JPA/Hibernate para que eu não repita informações aqui.*

*Também seria interessante saber [SQL](SQL.md)*

## Configuração<span id="hibernate_config"></span>

Assumirei que você já tem o MySQL instalado. Use os seguintes comandos:

***Cria o usuário estudante***

    CREATE USER 'estudante'@'localhost' IDENTIFIED BY 'estudante';
    GRANT ALL PRIVILEGES ON * .* TO 'estudante'@'localhost';

Entre de novo no MySQL com a conta `estudante` e use o conjunto de códigos abaixo:

    CREATE DATABASE IF NOT EXISTS `estudantebd`;
    USE `estudantebd`;
    DROP TABLE IF EXISTS `estudante`;
    CREATE TABLE `estudante` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;

No Eclipse, você pode estar na perspectiva normal do Java se você quiser.

`File` => `New` => `Java Project`

Dê o nome que você quiser, simplesmente chamarei o meu de `hibernate`. Depois, clique com o botão direito do mouse sobre o nome do projeto e peça para criar uma nova pasta, chame-a de `lib`.

Vá até o site do [Hibernate/ORM](https://hibernate.org/orm/) para baixar os JARs do Hibernate. Se você não achar onde baixar o arquivo .zip contendo os JARs, vá na [página Source Forge do Hibernate](https://sourceforge.net/projects/hibernate/files/), em "_hibernate-orm_". Extraimos os arquivos do arquivo .zip, vou na pasta `lib` do arquivo baixado, depois em `required`, copie todos os arquivos JAR de lá e ponha-os dentro da pasta `lib` do **seu** projeto.

Agora precisamos baixar o *driver* do JDBC *(a página de download [é esta](https://dev.mysql.com/downloads/connector/j/))*, escolha a opção `Platform independent`. Ponha o arquivo JAR dentro da pasta `lib` do seu projeto.

Você já sabe como adicionar os arquivos JAR no ClassPath.

## Testando a conexão JDBC<span id="hibernate_jdbc"></span>

Vamos ver se tudo está funcionando. Crei um pacote chamado `dominio.jdbc`. Dentro desse pacote crie uma classe chamada `TestarJdbc` com o método main.

    package dominio.jdbc;
    
    import java.sql.Connection;
    import java.sql.DriverManager;
    
    public class TestarJdbc {
    
        public static void main(String[] args) {
            
            String urlJDBC = "jdbc:mysql://localhost:3306/estudantebd?useSSL=false&serverTimezone=UTC";
            String usuario = "estudante";
            String senha = "estudante";
            
            try {
                
                Connection conn = DriverManager.getConnection(urlJDBC, usuario, senha);
                
                System.out.println("Conexão realizada com sucesso");
                
            } catch (Exception e) {
                e.printStackTrace();
            }
    
        }
    
    }

Se você viu a mensagem _"Conexão realizada com sucesso"_ no console, isso significa que tudo está funcionando bem até aqui.

## Arquivo de configuração do Hibernate<span id="hibernate_configfile"></span>

Crie o arquivo `hibernate.cfg.xml` na pasta `src`.

    <!DOCTYPE hibernate-configuration PUBLIC
            "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
            "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
    
    <hibernate-configuration>
    
        <session-factory>
    
            <!-- Configurações de conexão do JDBC Database -->
            <property name="connection.driver_class">com.mysql.jdbc.Driver</property>
            <property name="connection.url">jdbc:mysql://localhost:3306/estudantebd?useSSL=false</property>
            <property name="connection.username">estudante</property>
            <property name="connection.password">estudante</property>
    
            <!-- Configurações do JDBC connection pool ... usando test pool integrado -->
            <property name="connection.pool_size">1</property>
    
            <!-- Seleciona o dialeto de SQL -->
            <property name="dialect">org.hibernate.dialect.MySQLDialect</property>
    
            <!-- Ecoa o SQL para stdout -->
            <property name="show_sql">true</property>
    
            <!-- Define o atual contexto de sessão -->
            <property name="current_session_context_class">thread</property>
     
        </session-factory>
    
    </hibernate-configuration>

## Anotações do Hibernate<span id="hibernate_annotations"></span>

Crie o pacote `dominio.hibernate.entity`. Dentro dele crie a classe `Estudante`.

    package dominio.hibernate.entity;
    
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="estudante")
    public class Estudante {
            
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="nome")
        private String nome;
        
        @Column(name="sobrenome")
        private String sobrenome;
        
        @Column(name="email")
        private String email;
        
        public Estudante () {
            
        }
    
        public Estudante(String nome, String sobrenome, String email) {
            this.nome = nome;
            this.sobrenome = sobrenome;
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        // Apenas pra debug...
        @Override
        public String toString() {
            return "Estudante [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email + "]";
        }
        
    }

O Eclipse perguntará qual pacote importar, sempre escolha `javax.persistence`, porque JPA é a especificação padrão enquanto Hibrnate é a implementação, até mesmo o time do Hibernate sugere o uso das anotações do JPA como boa prática.

`@Entity` marca uma classe Java para ser mapeada numa tabela de banco de dados.

## CRUD<span id="hibernate_crud"></span>

### Criação<span id="hibernate_crud_c"></span>

Clique com o botão direito em `src` e crie a classe `CriarEstudante` no pacote `dominio.hibernate` *(preste atenção no nome do pacote)*.

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Estudante;
    
    public class CriarEstudante {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Estudante.class)
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {
                
                Estudante estudanteTemp = new Estudante("Tião", "Trovão", "danadinha@gmail.com.br");
                
                session.beginTransaction();
                
                session.save(estudanteTemp);
                
                session.getTransaction().commit();
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

* **SessionFactory:** lê o arquivo de configuração, se conecta com o banco de dados, cria objetos de sessão e é um objeto pesado que é criado uma única vez no projeto.

* **Session:** é um envoltório de uma conexão JDBC, é um objeto principal usado para salvar ou recuperar outros objetos e tem vida curta.

A propósito, você não precisaria definir o arquivo XML na definição do objeto de SessionFactory, poderia ser assim:

    SessionFactory factory = new Configuration()
                             .configure()
                             .addAnnotatedClass(Estudante.class)
                             .buildSessionFactory();

Quando não definimos o arquivo XML, o próprio Hibernate automaticamente procura pelo arquivo `hibernate.cfg.xml`.

### Leitura<span id="hibernate_crud_r"></span>

Adicione mais alguns dados, só para nos ajudar em nossos testes. Se você quiser já uns dados prontos para agilizar, já preparei alguns pra você.

    INSERT INTO estudante VALUES(null, "Marcela", "Cardoso", "ma@bol.com.br");
    INSERT INTO estudante VALUES(null, "Gerônimo", "de Jesus", "geronimo@terra.com.br");
    INSERT INTO estudante VALUES(null, "Tália", "Amorim", "tamorim@hotmal.com");
    INSERT INTO estudante VALUES(null, "Gizele", "Lima", "gil@hotmail.com");
    INSERT INTO estudante VALUES(null, "Mateus", "Amorim", "mat@hotmail.com");

Crie a classe `LerEstudante` no pacote `dominio.hibernate`.

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Estudante;
    
    public class LerEstudante {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Estudante.class)
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {
                
                session.beginTransaction();
                
                Estudante estudanteTemp = session.find(Estudante.class, 2); // Procura a pessoa da tabela Funcionario cujo Id é 2
                
                System.out.println(estudanteTemp);
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

### Atualização<span id="hibernate_crud_u"></span>

Crie a classe `AtualizarEstudante` no pacote `dominio.hibernate`.

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Estudante;
    
    public class AtualizarEstudante {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Estudante.class)
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {
                
                session.beginTransaction();
                
                Estudante estudanteTemp = session.find(Estudante.class, 2); // Procura a pessoa da tabela Funcionario cujo Id é 2
                
                estudanteTemp.setNome("Pedro");
                
                session.getTransaction().commit(); // Se não coloco esta linha, você até vê a atualização no console, mas a atualização não é feita no banco de dados
                
                System.out.println(estudanteTemp);
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

### Deleção<span id="hibernate_crud_d"></span>

Crie a classe `DeletarEstudante` no pacote `dominio.hibernate`.

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Estudante;
    
    public class DeletarEstudante {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Estudante.class)
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {
                
                session.beginTransaction();
                
                Estudante estudanteTemp = session.find(Estudante.class, 2); // Procura a pessoa da tabela Funcionario cujo Id é 2
                
                session.delete(estudanteTemp);
                
                session.getTransaction().commit(); // Se não coloco esta linha, a deleção não terá efeito
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

## Querying<span id="hibernate_querying"></span>

Vamos dizer quero encontrar todos os estudantes que têm os sobrenome "Amorim" e "de Jesus". Espero que você tenha adicionado os dados que sugeri.

Crie a classe `QueryEstudante` no pacote `dominio.hibernate` *(preste atenção no nome do pacote)*.

    package dominio.hibernate;
    
    import java.util.List;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Estudante;
    
    public class QueryEstudante {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Estudante.class)
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {
                
                session.beginTransaction();
                
                // Mostra todos os estudantes
                List<Estudante> estudantes = session.createQuery("from Estudante").getResultList();
                for (Estudante estudanteTemp : estudantes) {
                    System.out.println(estudanteTemp);
                }
                
                System.out.println("-------------------"); // Só um separador
                
                // Mostra todos os estudantes cujos sobrenomes sejam "Amorim" ou "de Jesus"
                estudantes = session.createQuery("from Estudante est where"
                                + " est.sobrenome='Amorim' OR est.sobrenome='de Jesus'").getResultList();
                for (Estudante estudanteTemp : estudantes) {
                    System.out.println(estudanteTemp);
                }
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

Sugiro que você leia sobre ***Hibernate Query Language***.

E é claro que podemos fazer outras operações de CRUD com query. Vejamos um exemplo em que deleto um estudante cujo `id` seja 3.

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Estudante;
    
    public class DeletarEstudante {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Estudante.class)
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {
                
                session.beginTransaction();
                
                session.createQuery("delete from Estudante where id=3").executeUpdate();
                
                session.getTransaction().commit();
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

## Trabalhando com datas<span id="hibernate_datas"></span>

Vamos deletar a tabela antiga e criar uma nova:

    DROP TABLE IF EXISTS `estudante`;
    CREATE TABLE `estudante` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      `nascimento` DATETIME DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;

Também vamos adicionar novos valores:

    INSERT INTO estudante VALUES(null, "Marcela", "Cardoso", "ma@bol.com.br", "2008-05-21");
    INSERT INTO estudante VALUES(null, "Gerônimo", "de Jesus", "geronimo@terra.com.br", "2008-04-11");
    INSERT INTO estudante VALUES(null, "Tália", "Amorim", "tamorim@hotmal.com", "2007-08-01");
    INSERT INTO estudante VALUES(null, "Gizele", "Lima", "gil@hotmail.com", "2008-10-06");
    INSERT INTO estudante VALUES(null, "Mateus", "Amorim", "mat@hotmail.com", "2009-01-10");
    INSERT INTO estudante VALUES(null, "Rogério", "Vasconcelos", "mat@hotmail.com", "2008-04-15");

Vamos atualizar a classe `CriarEstudante`:

    package dominio.hibernate;
    
    import java.text.SimpleDateFormat;
    import java.util.Date;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Estudante;
    
    public class CriarEstudante {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Estudante.class)
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            // Criamos a data aqui
            Date dataDeNascimento = new Date();
            SimpleDateFormat formatador = new SimpleDateFormat("dd/MM/yyyy");
            try {
                dataDeNascimento = formatador.parse("20/08/2008");
            }
            catch (Exception e) {
                e.printStackTrace();
            }
            
            
            // Agora criamos o estudante em si
            try {
                
                Estudante estudanteTemp = new Estudante("Maria", "Conceição", "macao@uol.com.br", dataDeNascimento);
                
                session.beginTransaction();
                
                session.save(estudanteTemp);
                
                session.getTransaction().commit();
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

## Mappings avançados<span id="hibernate_mappings"></span>

Reutilizaremos o projeto criado no capítulo anterior, portanto você pode copiá-lo ou atualizá-lo, fica a seu critério.

### @OneToOne unidirecional<span id="hibernate_mappings_onetooneuni"></span>

Faça esta operação SQL:

    DROP SCHEMA IF EXISTS `hb-one-to-one-uni`;
    
    CREATE SCHEMA `hb-one-to-one-uni`;
    
    USE `hb-one-to-one-uni`;
    
    SET FOREIGN_KEY_CHECKS = 0;
    
    DROP TABLE IF EXISTS `chefe_detalhe`;
    
    CREATE TABLE `chefe_detalhe` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `cargo` varchar(128) DEFAULT NULL,
      `departamento` varchar(128) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;
    
    
    DROP TABLE IF EXISTS `chefe`;
    
    CREATE TABLE `chefe` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      `chefe_detalhe_id` int(11) DEFAULT NULL,
      PRIMARY KEY (`id`),
      KEY `FK_DETALHE_idx` (`chefe_detalhe_id`),
      CONSTRAINT `FK_DETALHE` FOREIGN KEY (`chefe_detalhe_id`) REFERENCES `chefe_detalhe` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;
    
    SET FOREIGN_KEY_CHECKS = 1;

Teste pra ver se o *schema* está funcionando OK.

    package dominio.jdbc;
    
    import java.sql.Connection;
    import java.sql.DriverManager;
    
    public class TestarJdbc {
    
        public static void main(String[] args) {
            
            String urlJDBC = "jdbc:mysql://localhost:3306/hb-one-to-one-uni?useSSL=false&serverTimezone=UTC";
            String usuario = "estudante";
            String senha = "estudante";
            
            try {
                
                Connection conn = DriverManager.getConnection(urlJDBC, usuario, senha);
                
                System.out.println("Conexão realizada com sucesso");
                
            } catch (Exception e) {
                e.printStackTrace();
            }
    
        }
    
    }

Atualize o arquivo `hibernate.cfg.xml`:

    <!DOCTYPE hibernate-configuration PUBLIC
            "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
            "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
    
    <hibernate-configuration>
    
        <session-factory>
    
            <!-- Configurações de conexão do JDBC Database -->
            <property name="connection.driver_class">com.mysql.jdbc.Driver</property>
            <property name="connection.url">jdbc:mysql://localhost:3306/hb-one-to-one-uni?useSSL=false</property>
            <property name="connection.username">estudante</property>
            <property name="connection.password">estudante</property>
    
            <!-- Configurações do JDBC connection pool ... usando test pool integrado -->
            <property name="connection.pool_size">1</property>
    
            <!-- Seleciona o dialeto de SQL -->
            <property name="dialect">org.hibernate.dialect.MySQLDialect</property>
    
            <!-- Ecoa o SQL para stdout -->
            <property name="show_sql">true</property>
    
            <!-- Define o atual contexto de sessão -->
            <property name="current_session_context_class">thread</property>
     
        </session-factory>
    
    </hibernate-configuration>

Dentro do pacote `dominio.hibernate.entity`, crie os arquivos:

**ChefeDetalhe.java**

    package dominio.hibernate.entity;
    
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="chefe_detalhe")
    public class ChefeDetalhe {
            
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="cargo")
        private String cargo;
        
        @Column(name="departamento")
        private String departamento;
        
        public ChefeDetalhe () {
            
        }
    
        public ChefeDetalhe(String cargo, String departamento) {
            this.cargo = cargo;
            this.departamento = departamento;
        }
    
        public int getId() {
            return id;
        }
    
        public void setId(int id) {
            this.id = id;
        }
    
        public String getCargo() {
            return cargo;
        }
    
        public void setCargo(String cargo) {
            this.cargo = cargo;
        }
    
        public String getDepartamento() {
            return departamento;
        }
    
        public void setDepartamento(String departamento) {
            this.departamento = departamento;
        }
        
    }

**Chefe.java**

    package dominio.hibernate.entity;
    
    import javax.persistence.CascadeType;
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.JoinColumn;
    import javax.persistence.OneToOne;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="chefe")
    public class Chefe {
            
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="nome")
        private String nome;
        
        @Column(name="sobrenome")
        private String sobrenome;
        
        @Column(name="email")
        private String email;
        
        @OneToOne(cascade=CascadeType.ALL)
        @JoinColumn(name="chefe_detalhe_id")
        private ChefeDetalhe chefeDetalhe;
        
        public Chefe () {
            
        }
    
        public Chefe(String nome, String sobrenome, String email) {
            this.nome = nome;
            this.sobrenome = sobrenome;
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        public ChefeDetalhe getChefeDetalhe() {
            return chefeDetalhe;
        }
    
        public void setChefeDetalhe(ChefeDetalhe chefeDetalhe) {
            this.chefeDetalhe = chefeDetalhe;
        }

        @Override
        public String toString() {
            return "Chefe [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email
                    + ", chefeDetalhe=" + chefeDetalhe + "]";
        }
        
    }

*Por padrão, nenhuma operação é encadeada (cascaded).*

Dentro do pacote `dominio.hibernate`, crie os arquivos:

**CriarChefe.java**

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Chefe;
    import dominio.hibernate.entity.ChefeDetalhe;
    
    public class CriarChefe {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Chefe.class)
                                     .addAnnotatedClass(ChefeDetalhe.class) // Repare nesta novidade
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {
                
                Chefe chefTemp = new Chefe("Marcelo", "Guimarães", "marcelo@gmail.com.br");
                
                ChefeDetalhe chefDetalheTemp = new ChefeDetalhe("Diretor comercial", "Vendas");
                
                chefTemp.setChefeDetalhe(chefDetalheTemp);
                
                session.beginTransaction();
                
                // Automaticamente salvará chefDetalheTemp por causa de CascadeType.ALL
                session.save(chefTemp);
                
                session.getTransaction().commit();
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

**DeletarChefe.java**

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Chefe;
    import dominio.hibernate.entity.ChefeDetalhe;
    
    public class DeletarChefe {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Chefe.class)
                                     .addAnnotatedClass(ChefeDetalhe.class) // Repare nesta novidade também
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {            
                session.beginTransaction();
                
                Chefe chefTemp = session.find(Chefe.class, 1);
                
                if (chefTemp != null) {
                    // Automaticamente deletará chefDetalheTemp por causa de CascadeType.ALL
                    session.delete(chefTemp);
                }
                
                session.getTransaction().commit();
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

Pronto, agora rode a classe `CriarChefe`, veja o resultado no banco de dados, depois rode a classe `DeletarChefe` e veja o resultado.

### @OneToOne bidirecional<span id="hibernate_mappings_onetoonebi"></span>

Pra criar um relacionamento bidirecional, atualize o arquivo `ChefeDetalhe.java`:

    package dominio.hibernate.entity;
    
    import javax.persistence.CascadeType;
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.OneToOne;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="chefe_detalhe")
    public class ChefeDetalhe {
            
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="cargo")
        private String cargo;
        
        @Column(name="departamento")
        private String departamento;
        
        @OneToOne(mappedBy="chefeDetalhe", cascade=CascadeType.ALL) // Esse objeto chamado chefeDetalhe tem que estar na classe Chefe
        private Chefe chefe;
        
        public ChefeDetalhe () {
            
        }
    
        public ChefeDetalhe(String cargo, String departamento) {
            this.cargo = cargo;
            this.departamento = departamento;
        }
    
        public int getId() {
            return id;
        }
    
        public void setId(int id) {
            this.id = id;
        }
    
        public String getCargo() {
            return cargo;
        }
    
        public void setCargo(String cargo) {
            this.cargo = cargo;
        }
    
        public String getDepartamento() {
            return departamento;
        }
    
        public void setDepartamento(String departamento) {
            this.departamento = departamento;
        }
    
        public Chefe getChefe() {
            return chefe;
        }
    
        public void setChefe(Chefe chefe) {
            this.chefe = chefe;
        }
    
        @Override
        public String toString() {
            return "ChefeDetalhe [id=" + id + ", cargo=" + cargo + ", departamento=" + departamento + "]";
        }
        
    }

E crie a classe `VerChefeDetalhe`:

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Chefe;
    import dominio.hibernate.entity.ChefeDetalhe;
    
    public class VerChefeDetalhe {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Chefe.class)
                                     .addAnnotatedClass(ChefeDetalhe.class)
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {            
                session.beginTransaction();
                
                ChefeDetalhe chefDetalheTemp = session.find(ChefeDetalhe.class, 2);
                
                System.out.println(chefDetalheTemp);
                System.out.println(chefDetalheTemp.getChefe());
                
                session.getTransaction().commit();
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

Eu ia colocar o código aqui para deletar o objeto de `ChefeDetalhe` junto do objeto de `Chefe` *(lembre-se, estão todos encadeados)*, mas você já sabe como fazer esse código. Vamos seguir em frente e ver como deletar apenas o objeto de `ChefeDetalhe` e manter o objeto de `Chefe`. É simples, vá até o arquivo `ChefeDetalhe.java` e mudar a linha...

    @OneToOne(mappedBy="chefeDetalhe", cascade=CascadeType.ALL)

...para:

	@OneToOne(mappedBy="chefeDetalhe", cascade={CascadeType.DETACH, CascadeType.MERGE, CascadeType.PERSIST,
				CascadeType.REFRESH})

Ou seja, acontecerá tudo com os dois ao mesmo tempo, exceto deleção *(que seria gerida pelo código `CascadeType.REMOVE` que não está ali)*.

E na classe que você usará para executar o código de deleção, você fará assim:

    [...]
    session.beginTransaction();
    
    ChefeDetalhe chefeDetalheTemp = session.find(ChefeDetalhe.class, 2);
    
    // Quebra a ligação
    chefeDetalheTemp.getChefe().setChefeDetalhe(null);
    
    // Agora podemos remover apenas o objeto de ChefeDetalhe com segurança
    session.remove(chefeDetalheTemp);
    
    session.getTransaction().commit();
    [..]

### @OneToMany bidirecional<span id="hibernate_mappings_onetomanybi"></span>

Primeiro vamos mexer no banco de dados.

    DROP SCHEMA IF EXISTS `hb-one-to-many`;
    
    CREATE SCHEMA `hb-one-to-many`;
    
    USE `hb-one-to-many`;
    
    SET FOREIGN_KEY_CHECKS = 0;
    
    DROP TABLE IF EXISTS `chefe_detalhe`;
    
    CREATE TABLE `chefe_detalhe` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `cargo` varchar(128) DEFAULT NULL,
      `departamento` varchar(128) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;
    
    
    DROP TABLE IF EXISTS `chefe`;
    
    CREATE TABLE `chefe` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      `chefe_detalhe_id` int(11) DEFAULT NULL,
      PRIMARY KEY (`id`),
      KEY `FK_DETALHE_idx` (`chefe_detalhe_id`),
      CONSTRAINT `FK_DETALHE` FOREIGN KEY (`chefe_detalhe_id`)
      REFERENCES `chefe_detalhe` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;
    
    SET FOREIGN_KEY_CHECKS = 1;
    
    CREATE TABLE `empregado` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(128) DEFAULT NULL,
      `chefe_id` int(11) DEFAULT NULL,
      
      PRIMARY KEY (`id`),
      
      UNIQUE KEY `TITLE_UNIQUE` (`nome`),
      
      KEY `FK_CHEFE_idx` (`chefe_id`),
      
      CONSTRAINT `FK_CHEFE` 
      FOREIGN KEY (`chefe_id`) 
      REFERENCES `chefe` (`id`) 
      
      ON DELETE NO ACTION ON UPDATE NO ACTION
    ) ENGINE=InnoDB AUTO_INCREMENT=10 DEFAULT CHARSET=latin1;
    
    
    SET FOREIGN_KEY_CHECKS = 1;

Vamos criar o nosso novo chefe:

Atualize:

**hibernate.cfg.xml**

    <!DOCTYPE hibernate-configuration PUBLIC
            "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
            "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
    
    <hibernate-configuration>
    
        <session-factory>
    
            <!-- Configurações de conexão do JDBC Database -->
            <property name="connection.driver_class">com.mysql.jdbc.Driver</property>
            <property name="connection.url">jdbc:mysql://localhost:3306/hb-one-to-many?useSSL=false</property>
            <property name="connection.username">estudante</property>
            <property name="connection.password">estudante</property>
    
            <!-- Configurações do JDBC connection pool ... usando test pool integrado -->
            <property name="connection.pool_size">1</property>
    
            <!-- Seleciona o dialeto de SQL -->
            <property name="dialect">org.hibernate.dialect.MySQLDialect</property>
    
            <!-- Ecoa o SQL para stdout -->
            <property name="show_sql">true</property>
    
            <!-- Define o atual contexto de sessão -->
            <property name="current_session_context_class">thread</property>
     
        </session-factory>
    
    </hibernate-configuration>

Em `dominio.hibernate.entity`, crie:

**Empregado.class**

    package dominio.hibernate.entity;
    
    import javax.persistence.CascadeType;
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.JoinColumn;
    import javax.persistence.ManyToOne;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="empregado")
    public class Empregado {
        
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="nome")
        private String nome;
        
        @ManyToOne(cascade= {CascadeType.PERSIST, CascadeType.MERGE,
                 CascadeType.DETACH, CascadeType.REFRESH})
        @JoinColumn(name="chefe_id")
        private Chefe chefe;
        
        public Empregado () {
            
        }
    
        public Empregado(String nome) {
            this.nome = nome;
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
    
        public Chefe getChefe() {
            return chefe;
        }
    
        public void setChefe(Chefe chefe) {
            this.chefe = chefe;
        }
    
        @Override
        public String toString() {
            return "Empregado [id=" + id + ", nome=" + nome + "]";
        }
    
    }

E atualize:

**Chefe.java**

    package dominio.hibernate.entity;
    
    import java.util.ArrayList;
    import java.util.List;
    
    import javax.persistence.CascadeType;
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.JoinColumn;
    import javax.persistence.OneToMany;
    import javax.persistence.OneToOne;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="chefe")
    public class Chefe {
            
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="nome")
        private String nome;
        
        @Column(name="sobrenome")
        private String sobrenome;
        
        @Column(name="email")
        private String email;
        
        @OneToOne(cascade=CascadeType.ALL)
        @JoinColumn(name="chefe_detalhe_id")
        private ChefeDetalhe chefeDetalhe;
        
        @OneToMany(mappedBy="chefe", // Se refere ao objeto chamado chefe criado na classe Empregado
                cascade= {CascadeType.PERSIST, CascadeType.MERGE,
                         CascadeType.DETACH, CascadeType.REFRESH}) // Observe que não tem CascadeType.REMOVE
        private List<Empregado> empregados;
        
        public Chefe () {
            
        }
    
        public Chefe(String nome, String sobrenome, String email) {
            this.nome = nome;
            this.sobrenome = sobrenome;
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        public ChefeDetalhe getChefeDetalhe() {
            return chefeDetalhe;
        }
    
        public void setChefeDetalhe(ChefeDetalhe chefeDetalhe) {
            this.chefeDetalhe = chefeDetalhe;
        }
    
        public List<Empregado> getEmpregados() {
            return empregados;
        }
    
        public void setEmpregados(List<Empregado> empregados) {
            this.empregados = empregados;
        }
        
        public void contratar(Empregado empregadoTemp) {
            if (empregados == null) {
                empregados = new ArrayList<>();
            }
            
            empregados.add(empregadoTemp);
            
            empregadoTemp.setChefe(this);
        }
    
        @Override
        public String toString() {
            return "Chefe [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email
                    + ", chefeDetalhe=" + chefeDetalhe + "]";
        }
        
    }

Em `dominio.hibernate`, atualize:

**CriarChefe.java**

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Chefe;
    import dominio.hibernate.entity.ChefeDetalhe;
    import dominio.hibernate.entity.Empregado;
    
    public class CriarChefe {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure()
                                     .addAnnotatedClass(Chefe.class)
                                     .addAnnotatedClass(ChefeDetalhe.class)
                                     .addAnnotatedClass(Empregado.class) // Olha esta novidade aqui
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {
                
                Chefe chefTemp = new Chefe("Honório", "Smith", "honorio@gmail.com.br");
                
                ChefeDetalhe chefDetalheTemp = new ChefeDetalhe("Presidente", "Geral");
                
                chefTemp.setChefeDetalhe(chefDetalheTemp);
                
                session.beginTransaction();
                
                session.save(chefTemp);
                
                session.getTransaction().commit();
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

Agora vamos criar um empregado. Crie e execute o seguinte arquivo no pacote `dominio.hibernate`:

**CriarEmpregados.java**

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Chefe;
    import dominio.hibernate.entity.ChefeDetalhe;
    import dominio.hibernate.entity.Empregado;
    
    public class CriarEmpregados {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure()
                                     .addAnnotatedClass(Chefe.class)
                                     .addAnnotatedClass(ChefeDetalhe.class)
                                     .addAnnotatedClass(Empregado.class) // Olha esta novidade aqui
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {
                
                session.beginTransaction();
                
                Chefe chefeTemp = session.get(Chefe.class, 1);
                
                Empregado empregadoTemp1 = new Empregado("Iara Brandão");
                Empregado empregadoTemp2 = new Empregado("Cuca Beludo");
                
                chefeTemp.contratar(empregadoTemp1);
                chefeTemp.contratar(empregadoTemp2);
                
                session.save(empregadoTemp1);
                session.save(empregadoTemp2);
                
                session.getTransaction().commit();
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
            	session.close();
                factory.close();
            }
    
        }
    
    }

Para visualizar, vamos criar a classe `VerEmpregados` no pacote `dominio.hibernate`:

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Chefe;
    import dominio.hibernate.entity.ChefeDetalhe;
    import dominio.hibernate.entity.Empregado;
    
    public class VerEmpregados {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Chefe.class)
                                     .addAnnotatedClass(ChefeDetalhe.class)
                                     .addAnnotatedClass(Empregado.class)
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {            
                session.beginTransaction();
                
                Chefe chefeTemp = session.find(Chefe.class, 1);
                
                // System.out.println(chefeTemp.getEmpregados()); // Esse também serviria, mas um for loop dá uma informação mais limpa
                
                for (Empregado empregado : chefeTemp.getEmpregados()) {
                	System.out.println(empregado);
                }
                
                session.getTransaction().commit();
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

### Eager Loading x Lazy Loading<span id="hibernate_mappings_fetching"></span>

* **Eager Loading:** acessa todos os dados, vai carregar todas as *entities* de uma só vez. Pode dá problemas de performance.

* **Lazy Loading:** acessa dados por demanda. Sempre prefira este modo

Um exemplo de uso:

    @OneToOne(fetch=FetchType.LAZY)

Vejamos os valores padrão:

| Mapping     | Tipo de Fetching |
| ----------- | ---------------- |
| @OneToOne   | FetchType.EAGER  |
| @OneToMany  | FetchType.LAZY   |
| @ManyToOne  | FetchType.EAGER  |
| @ManyToMany | FetchType.LAZY   |

Modifique a classe `Chefe`:

    package dominio.hibernate.entity;
    
    import java.util.ArrayList;
    import java.util.List;
    
    import javax.persistence.CascadeType;
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.FetchType;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.JoinColumn;
    import javax.persistence.OneToMany;
    import javax.persistence.OneToOne;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="chefe")
    public class Chefe {
            
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="nome")
        private String nome;
        
        @Column(name="sobrenome")
        private String sobrenome;
        
        @Column(name="email")
        private String email;
        
        @OneToOne(cascade=CascadeType.ALL)
        @JoinColumn(name="chefe_detalhe_id")
        private ChefeDetalhe chefeDetalhe;
        
        @OneToMany(fetch=FetchType.EAGER,
                mappedBy="chefe", // Se refere ao objeto chamado chefe criado na classe Empregado
                cascade= {CascadeType.PERSIST, CascadeType.MERGE,
                         CascadeType.DETACH, CascadeType.REFRESH}) // Observe que não tem CascadeType.REMOVE
        private List<Empregado> empregados;
        
        public Chefe () {
            
        }
    
        public Chefe(String nome, String sobrenome, String email) {
            this.nome = nome;
            this.sobrenome = sobrenome;
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        public ChefeDetalhe getChefeDetalhe() {
            return chefeDetalhe;
        }
    
        public void setChefeDetalhe(ChefeDetalhe chefeDetalhe) {
            this.chefeDetalhe = chefeDetalhe;
        }
    
        public List<Empregado> getEmpregados() {
            return empregados;
        }
    
        public void setEmpregados(List<Empregado> empregados) {
            this.empregados = empregados;
        }
        
        public void contratar(Empregado empregadoTemp) {
            if (empregados == null) {
                empregados = new ArrayList<>();
            }
            
            empregados.add(empregadoTemp);
            
            empregadoTemp.setChefe(this);
        }
    
        @Override
        public String toString() {
            return "Chefe [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email
                    + ", chefeDetalhe=" + chefeDetalhe + "]";
        }
        
    }

E modifique também `VerEmpregados`:

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Chefe;
    import dominio.hibernate.entity.ChefeDetalhe;
    import dominio.hibernate.entity.Empregado;
    
    public class VerEmpregados {
    
        public static void main(String[] args) {
            
            SessionFactory factory = new Configuration()
                                     .configure("hibernate.cfg.xml")
                                     .addAnnotatedClass(Chefe.class)
                                     .addAnnotatedClass(ChefeDetalhe.class)
                                     .addAnnotatedClass(Empregado.class)
                                     .buildSessionFactory();
            
            Session session = factory.getCurrentSession();
            
            try {            
                session.beginTransaction();
                
                Chefe chefeTemp = session.find(Chefe.class, 1);
                
                System.out.println("Nosso código (chefeTemp): " + chefeTemp); // Adicionei essas linhas "Nosso código" só para ajudar na visualização
                
                System.out.println("---------------");
                
                System.out.println("Nosso código (chefeTemp.getEmpregados()): " + chefeTemp.getEmpregados());
                
                session.getTransaction().commit();
                
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
            	session.close();
                factory.close();
            }
    
        }
    
    }

Para que você entenda como funciona, sugiro que você ponha um *breakpoint* na linha `System.out.println(chefeTemp);` e mude para o mode de *debug*. Repare que, na linha `System.out.println(chefeTemp);`, tudo é carregado de uma vez. *Naturalmente que essa não é a melhor prática, mas foi pra demonstrar pra você*.

Agora volte para a classe `Chefe` e mude a linha...

    @OneToMany(fetch=FetchType.EAGER,

para:

    @OneToMany(fetch=FetchType.LAZY,

Agora volte a rodar o código em modo *debug*.

### @ManyToMany<span id="hibernate_mappings_manytomany"></span>

Nesse tipo de relação, usamos uma *Join Table*, uma tabela especial que mantém uma relação especial entre as tabelas envolvidas. Uma *Join Table* provê *mappings* entre as duas tabelas e tem *foreign keys* de cada tabela.

Primeiro vamos mexer no banco de dados:

    DROP SCHEMA IF EXISTS `hb-many-to-many`;
    
    CREATE SCHEMA `hb-many-to-many`;
    
    USE `hb-many-to-many`;
    
    SET FOREIGN_KEY_CHECKS = 0;
    
    DROP TABLE IF EXISTS `professor_detalhe`;
    
    CREATE TABLE `professor_detalhe` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `disciplina` varchar(128) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;
    
    
    DROP TABLE IF EXISTS `professor`;
    
    CREATE TABLE `professor` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      `professor_detalhe_id` int(11) DEFAULT NULL,
      PRIMARY KEY (`id`),
      KEY `FK_DETALHE_idx` (`instructor_detail_id`),
      CONSTRAINT `FK_DETALHE` FOREIGN KEY (`professor_detalhe_id`) 
      REFERENCES `professor_detalhe` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;
    
    DROP TABLE IF EXISTS `curso`;
    
    CREATE TABLE `curso` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(128) DEFAULT NULL,
      `professor_id` int(11) DEFAULT NULL,
      
      PRIMARY KEY (`id`),
      
      UNIQUE KEY `NOME_UNICO` (`nome`),
      
      KEY `FK_PROFESSOR_idx` (`professor_id`),
      
      CONSTRAINT `FK_PROFESSOR` 
      FOREIGN KEY (`professor_id`) 
      REFERENCES `professor` (`id`) 
      
      ON DELETE NO ACTION ON UPDATE NO ACTION
    ) ENGINE=InnoDB AUTO_INCREMENT=10 DEFAULT CHARSET=latin1;
    
    
    DROP TABLE IF EXISTS `avaliacao`;
    
    CREATE TABLE `avaliacao` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `comentario` varchar(256) DEFAULT NULL,
      `curso_id` int(11) DEFAULT NULL,
    
      PRIMARY KEY (`id`),
    
      KEY `FK_CURSO_ID_idx` (`curso_id`),
    
      CONSTRAINT `FK_CURSO` 
      FOREIGN KEY (`curso_id`) 
      REFERENCES `curso` (`id`) 
    
      ON DELETE NO ACTION ON UPDATE NO ACTION
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;
    
    DROP TABLE IF EXISTS `estudante`;
    
    CREATE TABLE `estudante` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;
    
    DROP TABLE IF EXISTS `curso_estudante`;
    
    CREATE TABLE `curso_estudante` (
      `curso_id` int(11) NOT NULL,
      `estudante_id` int(11) NOT NULL,
      
      PRIMARY KEY (`curso_id`,`estudante_id`),
      
      KEY `FK_ESTUDANTE_idx` (`curso_id`),
      
      CONSTRAINT `FK_CURSO_05` FOREIGN KEY (`curso_id`) 
      REFERENCES `curso` (`id`) 
      ON DELETE NO ACTION ON UPDATE NO ACTION,
      
      CONSTRAINT `FK_ESTUDANTE` FOREIGN KEY (`estudante_id`) 
      REFERENCES `estudante` (`id`) 
      ON DELETE NO ACTION ON UPDATE NO ACTION
    ) ENGINE=InnoDB DEFAULT CHARSET=latin1;
    
    SET FOREIGN_KEY_CHECKS = 1;

Pra este caso, vamos criar um novo projeto *(chame-o com quiser)*, só por quesãto de organização.

Copie a pasta `lib` do projeto anterior para o novo projeto e instale os arquivos JAR no *ClassPath* do projeto.

OK, vamos criar os arquivos agora:

Em `src`:

**hibernate.cfg.xml**

    <!DOCTYPE hibernate-configuration PUBLIC
            "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
            "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
    
    <hibernate-configuration>
    
        <session-factory>
    
            <property name="connection.driver_class">com.mysql.jdbc.Driver</property>
            <property name="connection.url">jdbc:mysql://localhost:3306/hb-many-to-many?useSSL=false</property>
            <property name="connection.username">estudante</property>
            <property name="connection.password">estudante</property>
    
            <property name="connection.pool_size">1</property>
    
            <property name="dialect">org.hibernate.dialect.MySQLDialect</property>
    
            <property name="show_sql">true</property>
    
            <property name="current_session_context_class">thread</property>
     
        </session-factory>
    
    </hibernate-configuration>

No pacote `dominio.hibernate.entity`:

**Avaliacao.java**

    package dominio.hibernate.entity;
    
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="avaliacao")
    public class Avaliacao {
            
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="comentario")
        private String comentario;
        
        public Avaliacao () {
            
        }
    
        public Avaliacao(String comentario) {
            this.comentario = comentario;
        }
    
        public int getId() {
            return id;
        }
    
        public void setId(int id) {
            this.id = id;
        }
    
        public String getComentario() {
            return comentario;
        }
    
        public void setComentario(String comentario) {
            this.comentario = comentario;
        }
    
        @Override
        public String toString() {
            return "Avaliacao [id=" + id + ", comentario=" + comentario + "]";
        }
        
    }

**Curso.java**

    package dominio.hibernate.entity;
    
    import java.util.ArrayList;
    import java.util.List;
    
    import javax.persistence.CascadeType;
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.FetchType;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.JoinColumn;
    import javax.persistence.JoinTable;
    import javax.persistence.ManyToMany;
    import javax.persistence.ManyToOne;
    import javax.persistence.OneToMany;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="curso")
    public class Curso {
            
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="nome")
        private String nome;
        
        @ManyToOne(cascade= {CascadeType.PERSIST, CascadeType.MERGE,
                 CascadeType.DETACH, CascadeType.REFRESH})
        @JoinColumn(name="professor_id")
        private Professor professor;
        
        @OneToMany(fetch=FetchType.LAZY, cascade=CascadeType.ALL)
        @JoinColumn(name="curso_id")
        private List<Avaliacao> avaliacoes;
        
        @ManyToMany(fetch=FetchType.LAZY,
                cascade= {CascadeType.PERSIST, CascadeType.MERGE,
                 CascadeType.DETACH, CascadeType.REFRESH})
        @JoinTable(
                name="curso_estudante",
                joinColumns=@JoinColumn(name="curso_id"),
                inverseJoinColumns=@JoinColumn(name="estudante_id")
                )    
        private List<Estudante> estudantes;
        
        public Curso () {
            
        }
    
        public Curso(String nome) {
            super();
            this.nome = nome;
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
    
        public Professor getProfessor() {
            return professor;
        }
    
        public void setProfessor(Professor professor) {
            this.professor = professor;
        }
    
        public List<Avaliacao> getAvaliacoes() {
            return avaliacoes;
        }
    
        public void setAvaliacoes(List<Avaliacao> avaliacoes) {
            this.avaliacoes = avaliacoes;
        }
    
        public List<Estudante> getEstudantes() {
            return estudantes;
        }
    
        public void setEstudantes(List<Estudante> estudantes) {
            this.estudantes = estudantes;
        }
    
        public void adicionarAvaliacao(Avaliacao aAvaliacao) {
            if (avaliacoes == null) {
                avaliacoes = new ArrayList<>();
            }
            
            avaliacoes.add(aAvaliacao);
        }
        
        public void adicionarEstudante(Estudante oEstudante) {
            if (estudantes == null) {
                estudantes = new ArrayList<>();
            }
            
            estudantes.add(oEstudante);
        }
    
        @Override
        public String toString() {
            return "Curso [id=" + id + ", nome=" + nome + "]";
        }
        
    }

**Estudante.java**

package dominio.hibernate.entity;
    
    import java.util.List;
    
    import javax.persistence.CascadeType;
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.FetchType;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.JoinColumn;
    import javax.persistence.JoinTable;
    import javax.persistence.ManyToMany;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="estudante")
    public class Estudante {
            
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="nome")
        private String nome;
        
        @Column(name="sobrenome")
        private String sobrenome;
        
        @Column(name="email")
        private String email;
        
        @ManyToMany(fetch=FetchType.LAZY,
                cascade= {CascadeType.PERSIST, CascadeType.MERGE,
                 CascadeType.DETACH, CascadeType.REFRESH})
        @JoinTable(
                name="curso_estudante",
                joinColumns=@JoinColumn(name="estudante_id"),
                inverseJoinColumns=@JoinColumn(name="curso_id")
                )
        private List<Curso> cursos;
        
        public Estudante () {
            
        }
    
        public Estudante(String nome, String sobrenome, String email) {
            this.nome = nome;
            this.sobrenome = sobrenome;
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        public List<Curso> getCursos() {
            return cursos;
        }
    
        public void setCursos(List<Curso> cursos) {
            this.cursos = cursos;
        }
    
        @Override
        public String toString() {
            return "Estudante [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email + "]";
        }
        
    }

**ProfessorDetalhe.java**

    package dominio.hibernate.entity;
    
    import javax.persistence.CascadeType;
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.OneToOne;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="professor_detalhe")
    public class ProfessorDetalhe {
            
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="cargo")
        private String cargo;
        
        @Column(name="departamento")
        private String departamento;
        
        @OneToOne(mappedBy="professorDetalhe", cascade={CascadeType.DETACH, CascadeType.MERGE, CascadeType.PERSIST,
                    CascadeType.REFRESH})
        private Professor professor;
        
        public ProfessorDetalhe () {
            
        }
    
        public ProfessorDetalhe(String cargo, String departamento) {
            this.cargo = cargo;
            this.departamento = departamento;
        }
    
        public int getId() {
            return id;
        }
    
        public void setId(int id) {
            this.id = id;
        }
    
        public String getCargo() {
            return cargo;
        }
    
        public void setCargo(String cargo) {
            this.cargo = cargo;
        }
    
        public String getDepartamento() {
            return departamento;
        }
    
        public void setDepartamento(String departamento) {
            this.departamento = departamento;
        }
    
        public Professor getProfessor() {
            return professor;
        }
    
        public void setProfessor(Professor professor) {
            this.professor = professor;
        }
    
        @Override
        public String toString() {
            return "ProfessorDetalhe [id=" + id + ", cargo=" + cargo + ", departamento=" + departamento + "]";
        }
        
    }

**Professor.java**

    package dominio.hibernate.entity;
    
    import java.util.ArrayList;
    import java.util.List;
    
    import javax.persistence.CascadeType;
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.FetchType;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.JoinColumn;
    import javax.persistence.OneToMany;
    import javax.persistence.OneToOne;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="professor")
    public class Professor {
            
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="nome")
        private String nome;
        
        @Column(name="sobrenome")
        private String sobrenome;
        
        @Column(name="email")
        private String email;
        
        @OneToOne(cascade=CascadeType.ALL)
        @JoinColumn(name="professor_detalhe_id")
        private ProfessorDetalhe professorDetalhe;
        
        @OneToMany(fetch=FetchType.LAZY,
                mappedBy="professor",
                cascade= {CascadeType.PERSIST, CascadeType.MERGE,
                         CascadeType.DETACH, CascadeType.REFRESH})
        private List<Curso> cursos;
        
        public Professor () {
            
        }
    
        public Professor(String nome, String sobrenome, String email) {
            super();
            this.nome = nome;
            this.sobrenome = sobrenome;
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        public ProfessorDetalhe getProfessorDetalhe() {
            return professorDetalhe;
        }
    
        public void setProfessorDetalhe(ProfessorDetalhe professorDetalhe) {
            this.professorDetalhe = professorDetalhe;
        }
    
        public List<Curso> getCursos() {
            return cursos;
        }
    
        public void setCursos(List<Curso> cursos) {
            this.cursos = cursos;
        }
    
        @Override
        public String toString() {
            return "Professor [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email
                    + ", professorDetalhe=" + professorDetalhe + "]";
        }
        
        // Este método ajuda na relação bidirecional
        public void adicionarCurso(Curso cursoTemp) {
            
            if (cursos == null) {
                cursos = new ArrayList<>();
            }
            
            cursos.add(cursoTemp);
            
            cursoTemp.setProfessor(this);
        }
        
    }

No pacote `dominio.hibernate`, crie e rode cada uma dessas classes:

**CriarCursoEAvaliacao.java**

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Avaliacao;
    import dominio.hibernate.entity.Curso;
    import dominio.hibernate.entity.Estudante;
    import dominio.hibernate.entity.Professor;
    import dominio.hibernate.entity.ProfessorDetalhe;
    
    public class CriarCursoEAvaliacao {
    
        public static void main(String[] args) {
            SessionFactory factory = new Configuration()
                    .configure("hibernate.cfg.xml")
                    .addAnnotatedClass(Professor.class)
                    .addAnnotatedClass(ProfessorDetalhe.class)
                    .addAnnotatedClass(Curso.class)
                    .addAnnotatedClass(Avaliacao.class)
                    .addAnnotatedClass(Estudante.class)
                    .buildSessionFactory();
    
            Session session = factory.getCurrentSession();
            
            try {            
            
                session.beginTransaction();
                        
                Curso cursoTemp = new Curso("Irrigação - Normas");
                
                cursoTemp.adicionarAvaliacao(new Avaliacao("Amei o curso, a professora explica muito bem"));
                cursoTemp.adicionarAvaliacao(new Avaliacao("Legal!"));
                cursoTemp.adicionarAvaliacao(new Avaliacao("Aprendi muito, parabéns!"));
                        
                session.save(cursoTemp);
        
                session.getTransaction().commit();
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

**CriarCursoEEstudantes.java**

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Avaliacao;
    import dominio.hibernate.entity.Curso;
    import dominio.hibernate.entity.Estudante;
    import dominio.hibernate.entity.Professor;
    import dominio.hibernate.entity.ProfessorDetalhe;
    
    public class CriarCursoEEstudantes {
    
        public static void main(String[] args) {
            SessionFactory factory = new Configuration()
                    .configure("hibernate.cfg.xml")
                    .addAnnotatedClass(Professor.class)
                    .addAnnotatedClass(ProfessorDetalhe.class)
                    .addAnnotatedClass(Curso.class)
                    .addAnnotatedClass(Avaliacao.class)
                    .addAnnotatedClass(Estudante.class)
                    .buildSessionFactory();
    
            Session session = factory.getCurrentSession();
            
            try {
            
                session.beginTransaction();
                        
                Curso cursoTemp = new Curso("Agricultura Orgânica - Como adubar o solo");
                        
                session.save(cursoTemp);
                
                Estudante estudanteTemp1 = new Estudante("Paula", "Rodrigues", "paula@gmail.com");
                Estudante estudanteTemp2 = new Estudante("Cuca", "Beludo", "culudo@gmail.com");
                        
                cursoTemp.adicionarEstudante(estudanteTemp1);
                cursoTemp.adicionarEstudante(estudanteTemp2);
                
                session.save(estudanteTemp1);
                session.save(estudanteTemp2);
        
                session.getTransaction().commit();
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

Veja o resultado no banco de dados:

    SELECT * FROM estudante;
    SELECT * FROM curso;
    SELECT * FROM curso_estudante;
    SELECT * FROM avaliacao;

Agora vamos adicionar mais cursos para um estudante:

    package dominio.hibernate;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.cfg.Configuration;
    
    import dominio.hibernate.entity.Avaliacao;
    import dominio.hibernate.entity.Curso;
    import dominio.hibernate.entity.Estudante;
    import dominio.hibernate.entity.Professor;
    import dominio.hibernate.entity.ProfessorDetalhe;
    
    public class AdicionarCursoParaEstudante {
    
        public static void main(String[] args) {
            SessionFactory factory = new Configuration()
                    .configure("hibernate.cfg.xml")
                    .addAnnotatedClass(Professor.class)
                    .addAnnotatedClass(ProfessorDetalhe.class)
                    .addAnnotatedClass(Curso.class)
                    .addAnnotatedClass(Avaliacao.class)
                    .addAnnotatedClass(Estudante.class)
                    .buildSessionFactory();
    
            Session session = factory.getCurrentSession();
            
            try {            
            
                session.beginTransaction();
                        
                Estudante tempStudent = session.get(Estudante.class, 2);
                        
                Curso cursoTemp1 = new Curso("Ciências do solo");
                Curso cursoTemp2 = new Curso("Climatologia");
                
                cursoTemp1.adicionarEstudante(tempStudent);
                cursoTemp2.adicionarEstudante(tempStudent);
                
                session.save(cursoTemp1);
                session.save(cursoTemp2);
        
                session.getTransaction().commit();
            }
            catch (Exception e) {
                e.getStackTrace();
            }
            finally {
                session.close();
                factory.close();
            }
    
        }
    
    }

Você pode verificar os resultados:

    SELECT * FROM curso;
    SELECT * FROM estudante;
    SELECT * FROM curso_estudante;

# Como usar Spring MVC e Hibernate juntos<span id="springmvchibernate"></span>

Vamos ajeitar nosso banco de dados, use a conta `estudante` mesmo:

    CREATE DATABASE IF NOT EXISTS `cliente_web`;
    USE `cliente_web`;
    
    DROP TABLE IF EXISTS `cliente`;
    CREATE TABLE `cliente` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=latin1;
    
    LOCK TABLES `cliente` WRITE;
    
    INSERT INTO `cliente` VALUES 
    	(1,'Marcelino','Travolta','marcelino@gmail.com'),
    	(2,'Cuca','Beludo','culudo@gmail.com'),
    	(3,'Paula','Barbosa','paulinha@gmail.com'),
    	(4,'Oscar','Alho','alho@gmail.com'),
    	(5,'Maria','Freitas','maria@gmail.com');
    
    UNLOCK TABLES;

Agora, no Eclipse, vá em `File` => `New` => `Dynamic Web Project`: chamarei meu projeto de `cliente-web`, sugiro que você faça o mesmo para que fiquemos na mesma página.

Baixe o [Java Connector pra MySQL](https://dev.mysql.com/downloads/connector/j/) e ponha o arquivo JAR na pasta `src/main/java/webapp/WEB-INF/lib`.

Na pasta `src/main/java`, crie o pacote `dominio.jdbc`.

Agora criaremos um *servlet* neste pacote básico para testar a conexão. Clique no pacote, `New` => `Servlet`, chamarei o arquivo de `ServletDbTeste`, dê `Next` até você chegar numa janela onde você tem algumas opções para deixar marcadas, deixe apenas marcados `Inherited abstract methods` e `doGet`.

    package dominio.jdbc;
    
    import java.io.IOException;
    import java.io.PrintWriter;
    import java.sql.Connection;
    import java.sql.DriverManager;
    
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    
    /**
     * Servlet implementation class ServletDbTeste
     */
    @WebServlet("/ServletDbTeste")
    public class ServletDbTeste extends HttpServlet {
        private static final long serialVersionUID = 1L;
    
        /**
         * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
         */
        protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            String usuario = "estudante";
            String senha = "estudante";
            String UrlJdbc = "jdbc:mysql://localhost:3306/cliente_web?useSSL=false&serverTimezone=UTC";
            String driver = "com.mysql.cj.jdbc.Driver";
            
            try {
                PrintWriter out = response.getWriter();
                Class.forName(driver);
                out.println("Conectando ao banco de dados: " + UrlJdbc);
                Connection conn = DriverManager.getConnection(UrlJdbc, usuario, senha);
                out.println("Conexão realizada com sucesso!");
                conn.close();
            }
            catch (Exception e) {
                e.printStackTrace();
                throw new ServletException(e);
            }
        }
    
    }
    
`Run as Server`

Espero que tudo tenha ido OK pra você

## Mais configurações<span id="springmvchibernate_config"></span>

Crie os seguintes arquivos na pasta `src/main/java/webapp/WEB-INF/`:

**web.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd" id="WebApp_ID" version="4.0">
      <display-name>spring-mvc</display-name>
     
      <absolute-ordering />
    
      <welcome-file-list>
        <welcome-file>index.jsp</welcome-file>
        <welcome-file>index.html</welcome-file>
      </welcome-file-list>
    
      <servlet>
        <servlet-name>dispatcher</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
          <param-name>contextConfigLocation</param-name>
          <param-value>/WEB-INF/spring-mvc.xml</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
      </servlet>
      
      <servlet-mapping>
        <servlet-name>dispatcher</servlet-name>
        <url-pattern>/</url-pattern>
      </servlet-mapping>
    </web-app>

**spring-mvc.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xmlns:tx="http://www.springframework.org/schema/tx"
        xmlns:mvc="http://www.springframework.org/schema/mvc"
        xsi:schemaLocation="
            http://www.springframework.org/schema/beans
            http://www.springframework.org/schema/beans/spring-beans.xsd
            http://www.springframework.org/schema/context
            http://www.springframework.org/schema/context/spring-context.xsd
            http://www.springframework.org/schema/mvc
            http://www.springframework.org/schema/mvc/spring-mvc.xsd
            http://www.springframework.org/schema/tx 
            http://www.springframework.org/schema/tx/spring-tx.xsd">
    
        <!-- Add support for component scanning -->
        <context:component-scan base-package="dominio.springmvchb" />
    
        <!-- Add support for conversion, formatting and validation support -->
        <mvc:annotation-driven/>
    
        <!-- Define Spring MVC view resolver -->
        <bean
            class="org.springframework.web.servlet.view.InternalResourceViewResolver">
            <property name="prefix" value="/WEB-INF/view/" />
            <property name="suffix" value=".jsp" />
        </bean>
    
        <!-- Step 1: Define Database DataSource / connection pool -->
        <bean id="myDataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource"
              destroy-method="close">
            <property name="driverClass" value="com.mysql.cj.jdbc.Driver" />
            <property name="jdbcUrl" value="jdbc:mysql://localhost:3306/cliente_web?useSSL=false" />
            <property name="user" value="estudante" />
            <property name="password" value="estudante" /> 
    
            <!-- these are connection pool properties for C3P0 -->
            <property name="minPoolSize" value="5" />
            <property name="maxPoolSize" value="20" />
            <property name="maxIdleTime" value="30000" />
        </bean>  
        
        <!-- Step 2: Setup Hibernate session factory -->
        <bean id="sessionFactory"
            class="org.springframework.orm.hibernate5.LocalSessionFactoryBean">
            <property name="dataSource" ref="myDataSource" />
            <property name="packagesToScan" value="dominio.springmvchb.entity" />
            <property name="hibernateProperties">
               <props>
                  <prop key="hibernate.dialect">org.hibernate.dialect.MySQLDialect</prop>
                  <prop key="hibernate.show_sql">true</prop>
               </props>
            </property>
       </bean>      
    
        <!-- Step 3: Setup Hibernate transaction manager -->
        <bean id="myTransactionManager"
                class="org.springframework.orm.hibernate5.HibernateTransactionManager">
            <property name="sessionFactory" ref="sessionFactory"/>
        </bean>
        
        <!-- Step 4: Enable configuration of transactional behavior based on annotations -->
        <tx:annotation-driven transaction-manager="myTransactionManager" />
    
    </beans>

Agora adicione esses 2 arquivos à pasta `WEB-INF/lib`:

* [javax.servlet.jsp.jstl](https://mvnrepository.com/artifact/org.glassfish.web/javax.servlet.jsp.jstl)

* [javax.servlet.jsp.jstl-api](https://mvnrepository.com/artifact/javax.servlet.jsp.jstl/javax.servlet.jsp.jstl-api)

Adicione a última versão dos arquivos JAR do Spring, você sabe [onde](https://repo.spring.io/ui/) baixar.

E por fim, baixe os JARs do [Hibernate/ORM](https://hibernate.org/orm/). Pegue todos os arquivos JAR das pastas `required` e `optional/c3p0`

***OBS.:*** *Para quem usa as versões 9+ do Java, os 4 arquivos JAR abaixo serão necessários também.*

* [javax.activation](https://repo1.maven.org/maven2/com/sun/activation/javax.activation/)

* [jaxb-api](https://repo1.maven.org/maven2/javax/xml/bind/jaxb-api/) *(procure ter este e os dois seguintes na mesma versão. Na época que escrevi isto, usei a versão 2.3.0)*

* [jaxb-core](https://repo1.maven.org/maven2/com/sun/xml/bind/jaxb-core/)

* [jaxb-impl](https://repo1.maven.org/maven2/com/sun/xml/bind/jaxb-impl/)

## Teste com um Controller<span id="springmvchibernate_testecontroller"></span>

Crie o pacote `dominio.springmvchb.controller`, dentro dele crie o arquivo:

**ClienteController.java**

    package dominio.springmvchb.controller;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.RequestMapping;
    
    @Controller
    @RequestMapping("/cliente")
    public class ClienteController {
    
        @RequestMapping("/lista")
        public String listaDeClientes(Model modelo) {
            return "lista";
        }
    }

Crie a pasta `view` dentro da pasta `WEB-INF` e dentro de `WEB-INF/view` crie o seguinte arquivo .jsp:

**lista.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring MVC + Hibernate</title>
    </head>
    <body>
    
        <p>Está tudo funcionando!</p>
    
    </body>
    </html>

Clique com o botão direito do mouse sobre o nome do projeto, `Run As` => `Run on Server`.

Sim, você verá um erro 404, mas é porque ainda não definimos uma rota para `/`, mas sim para `/cliente/lista/`. Portanto, tente acessar o endereço [http://localhost:8080/cliente-web/cliente/lista/](http://localhost:8080/cliente-web/cliente/lista/) *(assumo aqui que você usou os mesmíssimos nomes que eu, caso contrário adapte o endereço para o seu caso)*.

## Início do projeto<span id="springmvchibernate_inicio"></span>

**Dica de ouro:** Sei que eu já tinha te pedido para estudar sobre MVC, mas como não sei que materiais você achou, peço que você estude sobre DAO *(Data Access Object)* agora e como ele se relaciona com MVC. Aproveite e pesquise também como essa combinação MVC-DAO faz uso de *services*.

Já testamos tudo, podemos realmente iniciar o projeto. Mas reaproveitaremos os arquivos criados nos dois subcapítulos anteriores.

Crie o pacote `dominio.springmvchb.entity`, dentro dele crie a classe:

**Cliente.java**

    package dominio.springmvchb.entity;
    
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="cliente")
    public class Cliente {
        
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        public int id;
        
        @Column(name="nome")
        public String nome;
        
        @Column(name="sobrenome")
        public String sobrenome;
        
        @Column(name="email")
        public String email;
        
        public Cliente () {
            
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        @Override
        public String toString() {
            return "Cliente [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email + "]";
        }
    
    }

Crie o pacote `dominio.springmvchb.dao`, dentro dele crie a interface:

**ClienteDAO.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteDAO {
    
        public List<Cliente> getClientes();
    
    }

E, no mesmo pacote, a classe:

**ClienteDAOImpl.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import javax.transaction.Transactional;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.query.Query;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.springmvchb.entity.Cliente;
    
    @Repository
    public class ClienteDAOImpl implements ClienteDAO {
        
        @Autowired
        private SessionFactory sessionFactory;
    
        @Override
        @Transactional
        public List<Cliente> getClientes() {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query<Cliente> aQuery = sessionAtual.createQuery("from Cliente", Cliente.class); // Neste caso, importaremos de org.hibernate.query.Query (PRESTA ATENÇÃO NO NOME!) em vez de javax.persistence porque como estamos usando uma versão do Hibernate mais nova que a 5.2 e métodos em outros pacotes se tornaram obsoletos
            
            List<Cliente> clientes = aQuery.getResultList();
            
            return clientes;
        }
    
    }

A *annotation* `@Transactional` automaticamente inicia e termina uma transação no código Hibernate, de forma que você não precisará mais usar `session.beginTransaction()` ou `session.getTransaction().commit()`.

E agora vamos atualizar o Controller:

    package dominio.springmvchb.controller;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.RequestMapping;
    
    import dominio.springmvchb.dao.ClienteDAO;
    import dominio.springmvchb.entity.Cliente;
    
    @Controller
    @RequestMapping("/cliente")
    public class ClienteController {
    
        @Autowired // Spring escaneará por um componente que implementa a interface ClienteDAO
        private ClienteDAO clienteDAO;
        
        @RequestMapping("/lista")
        public String listaDeClientes(Model modelo) {
            
            List<Cliente> osClientes = clienteDAO.getClientes();
            
            modelo.addAttribute("clientes", osClientes);
            
            return "lista";
        }
    }

E também atualizaremos o arquivo JSP:

**lista.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
    <%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring MVC + Hibernate</title>
    </head>
    <body>
    
        <div id="wrapper">
            <div id="header">
                <h1>CRM</h1>
            </div>
        </div>
        
        <div id="container">
            <div id="content">
                
                <table>
                    <tr>
                        <th>Nome</th>
                        <th>Sobrenome</th>
                        <th>Email</th>
                        
                        <c:forEach var="tempCliente" items="${clientes}"> <!-- clientes é o atributo do model... -->
                            <tr>
                                <td>${tempCliente.nome}</td> <!-- Por exemplo, aqui ele chama tempCliente.getNome() -->
                                <td>${tempCliente.sobrenome}</td>
                                <td>${tempCliente.email}</td>
                            </tr>
                        </c:forEach>
                        
                    </tr>
                </table>
                
            </div>
        </div>
    
    </body>
    </html>

A linha `<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>` adiciona suporte a *tags* JSTL Core.

## Floreio: CSS e Página de Boas-Vindas<span id="springmvchibernate_floreio"></span>

Crie a pasta `resources` dentro da pasta `webapp`. Dentro de `resources`, crie  apasta `css` e dentro desta os dois arquivos abaixo:

**estilo.css**

    html, body{
        margin-left:15px; margin-right:15px; 
        padding:0px; 
        font-family:Verdana, Arial, Helvetica, sans-serif;
    }
    
    table {   
        border-collapse:collapse;
        border-bottom:1px solid gray;
        font-family: Tahoma,Verdana,Segoe,sans-serif;
        width:72%;
    }
     
    th {
        border-bottom:1px solid gray;
        background:none repeat scroll 0 0 #09c332;
        padding:10px;
        color: #FFFFFF;
    }
    
    tr {
        border-top:1px solid gray;
        text-align:center;    
    }
     
    tr:nth-child(even) {background: #FFFFFF}
    tr:nth-child(odd) {background: #BBBBBB}    
     
    #wrapper {width: 100%; margin-top: 0px; }
    #header {width: 70%; background: #09c332; margin-top: 0px; padding:15px 0px 15px 15px;}
    #header h2 {width: 100%; margin:auto; color: #FFFFFF;}
    #container {width: 100%; margin:auto}
    #container h3 {color: #000;}
    #container #content {margin-top: 20px;}
    
    .add-button {
        border: 1px solid #666; 
        border-radius: 5px; 
        padding: 4px; 
        font-size: 12px;
        font-weight: bold;
        width: 120px; 
        padding: 5px 10px; 
        
        margin-bottom: 15px;
        background: #cccccc;
    }

**adicionar-cliente.css**

    form {
        margin-top: 10px;
    }
    
    label {
        font-size: 16px; 
        width: 100px; 
        display: block; 
        text-align: right;
        margin-right: 10px;
        margin-top: 8px;
        margin-bottom: 8px;
    }
    
    input {
        width: 250px;
        border: 1px solid #666; 
        border-radius: 5px; 
        padding: 4px; 
        font-size: 16px;
    }
    
    .save {
        font-weight: bold;
        width: 130px; 
        padding: 5px 10px; 
        margin-top: 30px;
        background: #cccccc;
    }
    
    table {   
        border-style:none;
        width:50%;
    }
    
    tr:nth-child(even) {background: #FFFFFF}
    tr:nth-child(odd) {background: #FFFFFF}
    
    tr {
        border-style:none;
        text-align:left;    
    }

Edite o arquivo `spring-mvc.xml`:

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xmlns:tx="http://www.springframework.org/schema/tx"
        xmlns:mvc="http://www.springframework.org/schema/mvc"
        xsi:schemaLocation="
            http://www.springframework.org/schema/beans
            http://www.springframework.org/schema/beans/spring-beans.xsd
            http://www.springframework.org/schema/context
            http://www.springframework.org/schema/context/spring-context.xsd
            http://www.springframework.org/schema/mvc
            http://www.springframework.org/schema/mvc/spring-mvc.xsd
            http://www.springframework.org/schema/tx 
            http://www.springframework.org/schema/tx/spring-tx.xsd">
    
        <!-- Add support for component scanning -->
        <context:component-scan base-package="dominio.springmvchb" />
    
        <!-- Add support for conversion, formatting and validation support -->
        <mvc:annotation-driven/>
    
        <!-- Define Spring MVC view resolver -->
        <bean
            class="org.springframework.web.servlet.view.InternalResourceViewResolver">
            <property name="prefix" value="/WEB-INF/view/" />
            <property name="suffix" value=".jsp" />
        </bean>
    
        <!-- Step 1: Define Database DataSource / connection pool -->
        <bean id="myDataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource"
              destroy-method="close">
            <property name="driverClass" value="com.mysql.cj.jdbc.Driver" />
            <property name="jdbcUrl" value="jdbc:mysql://localhost:3306/cliente_web?useSSL=false" />
            <property name="user" value="estudante" />
            <property name="password" value="estudante" /> 
    
            <!-- these are connection pool properties for C3P0 -->
            <property name="minPoolSize" value="5" />
            <property name="maxPoolSize" value="20" />
            <property name="maxIdleTime" value="30000" />
        </bean>  
        
        <!-- Step 2: Setup Hibernate session factory -->
        <bean id="sessionFactory"
            class="org.springframework.orm.hibernate5.LocalSessionFactoryBean">
            <property name="dataSource" ref="myDataSource" />
            <property name="packagesToScan" value="dominio.springmvchb.entity" />
            <property name="hibernateProperties">
               <props>
                  <prop key="hibernate.dialect">org.hibernate.dialect.MySQLDialect</prop>
                  <prop key="hibernate.show_sql">true</prop>
               </props>
            </property>
       </bean>      
    
        <!-- Step 3: Setup Hibernate transaction manager -->
        <bean id="myTransactionManager"
                class="org.springframework.orm.hibernate5.HibernateTransactionManager">
            <property name="sessionFactory" ref="sessionFactory"/>
        </bean>
        
        <!-- Step 4: Enable configuration of transactional behavior based on annotations -->
        <tx:annotation-driven transaction-manager="myTransactionManager" />
        
        <!-- Add support for web resources -->
        <mvc:resources location="/resources/" mapping="/resources/**"></mvc:resources> <!-- O ** diz que é pra incluir os sub-diretórios -->
    
    </beans>

Crie o arquivo abaixo na pasta `webapp` *(isso, em `webapp`, não em `WEB-INF/view`, porque já tem uma configuração prévia em `web.xml`)*.

**index.jsp**

    <% response.sendRedirect("cliente/lista"); %>

## Mapping<span id="springmvchibernate_mapping"></span>

Crie o pacote `dominio.springmvchb.service`, e dentro dele crie a interface `ClienteService` e a classe `ClienteServiceImpl`.

**ClienteService.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteService {
    
        public List<Cliente> getClientes();
    
    }

**ClienteServiceImpl.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    import org.springframework.transaction.annotation.Transactional;
    
    import dominio.springmvchb.dao.ClienteDAO;
    import dominio.springmvchb.entity.Cliente;
    
    @Service
    public class ClienteServiceImpl implements ClienteService {
        
        @Autowired
        private ClienteDAO clienteDAO;
    
        @Override
        @Transactional
        public List<Cliente> getClientes() {
            return clienteDAO.getClientes();
        }
    
    }

Atualize o arquivo `ClienteDAOImpl`:

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.query.Query;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.springmvchb.entity.Cliente;
    
    @Repository
    public class ClienteDAOImpl implements ClienteDAO {
        
        @Autowired
        private SessionFactory sessionFactory;
    
        @Override
        public List<Cliente> getClientes() {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query<Cliente> aQuery = sessionAtual.createQuery("from Cliente", Cliente.class); // Neste caso, importaremos de org.hibernate.query.Query (PRESTA ATENÇÃO NO NOME!) em vez de javax.persistence porque como estamos usando uma versão do Hibernate mais nova que a 5.2 e métodos em outros pacotes se tornaram obsoletos
            
            List<Cliente> clientes = aQuery.getResultList();
            
            return clientes;
        }
    
    }

`@Transactional` é definido na camada der serviço.

E agora atualize o arquivo `ClienteController`:

    package dominio.springmvchb.controller;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @Controller
    @RequestMapping("/cliente")
    public class ClienteController {
    
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/lista")
        public String listaDeClientes(Model modelo) {
            
            List<Cliente> osClientes = clienteService.getClientes();
            
            modelo.addAttribute("clientes", osClientes);
            
            return "lista";
        }
    }

## Salvar cliente<span id="springmvchibernate_add"></span>

Na pasta `view`, atualize o arquivo `lista.jsp`:

    <%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
    <%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/estilo.css">
        <title>Spring MVC + Hibernate</title>
    </head>
    <body>
    
        <div id="wrapper">
            <div id="header">
                <h1>CRM</h1>
            </div>
        </div>
        
        <div id="container">
            <div id="content">
            
                <input type="button" value="Adicionar cliente" 
                       onclick="window.location.href='mostrarFormParaAdicionar'; return false;"
                       class="add-button"
                />
                <!-- 
                Se eu quisesse, eu poderia escrever esse botão assim
                
                    <form action="mostrarFormParaAdicionar">
    
                    <input type="submit" value="Adicionar cliente" class="add-button/>
    
                    </form>
                
                 -->
                
                <table>
                    <tr>
                        <th>Nome</th>
                        <th>Sobrenome</th>
                        <th>Email</th>
                        
                        <c:forEach var="tempCliente" items="${clientes}"> <!-- clientes é o atributo do model... -->
                            <tr>
                                <td>${tempCliente.nome}</td> <!-- Por exemplo, aqui ele chama tempCliente.getNome() -->
                                <td>${tempCliente.sobrenome}</td>
                                <td>${tempCliente.email}</td>
                            </tr>
                        </c:forEach>
                        
                    </tr>
                </table>
                
            </div>
        </div>
    
    </body>
    </html>

E crie o arquivo `cliente-form.jsp`:

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="UTF-8">
            <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/estilo.css">
            <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/adicionar-cliente.css">
            <title>Adicionar Cliente</title>
        </head>
        <body>
        
            <div id="wrapper">
                <div id="header">
                    <h1>CRM</h1>
                </div>
            </div>
            
            <div id="container">
                <h3>Adicionar Cliente</h3>
                
                <form:form action="salvarCliente" modelAttribute="cliente" method="POST">
                
                    <table>
                        <tbody>
                            <tr>
                                <td><label>Nome: </label></td>
                                <td><form:input path="nome" /></td>
                            </tr>
                            <tr>
                                <td><label>Sobrenome: </label></td>
                                <td><form:input path="sobrenome" /></td>
                            </tr>
                            <tr>
                                <td><label>E-mail: </label></td>
                                <td><form:input path="email" /></td>
                            </tr>
                            <tr>
                                <td><label></label></td>
                                <td><input type="submit" value="Salvar" class="save" /></td>
                            </tr>
                        </tbody>
                    </table>
                
                </form:form>
                
                <div style="clear; both;">
                
                    <p>
                        <a href="${pageContext.request.contextPath}">Voltar pra lista</a>
                    </p>
                
                </div>
                
            </div>
        
        </body>
    </html>

Atualize os seguintes arquivos:

**ClienteDAO.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteDAO {
        
        public List<Cliente> getClientes();
        
        public void salvarCliente(Cliente oCliente);
    
    }

**ClienteDAOImpl.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.query.Query;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.springmvchb.entity.Cliente;
    
    @Repository
    public class ClienteDAOImpl implements ClienteDAO {
        
        @Autowired
        private SessionFactory sessionFactory;
    
        @Override
        public List<Cliente> getClientes() {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query<Cliente> aQuery = sessionAtual.createQuery("from Cliente", Cliente.class); // Neste caso, importaremos de org.hibernate.query.Query (PRESTA ATENÇÃO NO NOME!) em vez de javax.persistence porque como estamos usando uma versão do Hibernate mais nova que a 5.2 e métodos em outros pacotes se tornaram obsoletos
            
            List<Cliente> clientes = aQuery.getResultList();
            
            return clientes;
        }
    
        @Override
        public void salvarCliente(Cliente oCliente) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            sessionAtual.save(oCliente);
            
        }
    
    }

**ClienteService.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteService {
        
        public List<Cliente> getClientes();
        
        public void salvarCliente(Cliente oCliente);
    
    }

**ClienteServiceImpl.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    import org.springframework.transaction.annotation.Transactional;
    
    import dominio.springmvchb.dao.ClienteDAO;
    import dominio.springmvchb.entity.Cliente;
    
    @Service
    public class ClienteServiceImpl implements ClienteService {
        
        @Autowired
        private ClienteDAO clienteDAO;
    
        @Override
        @Transactional
        public List<Cliente> getClientes() {
            return clienteDAO.getClientes();
        }
    
        @Override
        @Transactional
        public void salvarCliente(Cliente oCliente) {
            clienteDAO.salvarCliente(oCliente);        
        }
    
    }

**ClienteController.java**

    package dominio.springmvchb.controller;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.ModelAttribute;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @Controller
    @RequestMapping("/cliente")
    public class ClienteController {
    
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/lista")
        public String listaDeClientes(Model modelo) {
            
            List<Cliente> osClientes = clienteService.getClientes();
            
            modelo.addAttribute("clientes", osClientes);
            
            return "lista";
        }
        
        @GetMapping("/mostrarFormParaAdicionar")
        public String mostrarFormParaAdicionar(Model modelo) {
            
            Cliente oCliente = new Cliente();
            
            modelo.addAttribute("cliente", oCliente);
            
            return "cliente-form";
        }
        
        @PostMapping("/salvarCliente")
        public String salvarCliente(@ModelAttribute("cliente") Cliente oCliente) {
        //<form:form action="salvarCliente" modelAttribute="cliente" method="POST">
            
            clienteService.salvarCliente(oCliente);
            
            return "redirect:/cliente/lista";
            
        }
        
    }

Se você quiser que os resultados na página `cliente/lista` sejam ordenados em ordem alfabética, você pode ir no arquivo `ClienteDAOImpl` e mudar a linha...

    Query<Cliente> aQuery = sessionAtual.createQuery("from Cliente", Cliente.class);

...para:

    Query<Cliente> aQuery = sessionAtual.createQuery("from Cliente order by nome", Cliente.class);

Opa, peraí, estamos tendo problemas com inserção de caracteres acentuados no nosso banco de dados. Por exemplo, se insiro "á", esse caractere é guardado como "Ã¡".

Felizmente a solução é bastante simples, no arquivo `cliente-form.jsp` *(onde faremos a inserção dos dados)*, substitua...

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>

por:

    <%@ page language="java" contentType="text/html; charset=ISO-8859-1"
        pageEncoding="UTF-8"%>

## Atualizar cliente<span id="springmvchibernate_update"></span>

Atualize *(no pun intended)* os arquivos abaixo:

**ClienteDAO.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteDAO {
        
        public List<Cliente> getClientes();
        
        public void salvarCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
    }

**ClienteDAOImpl.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.query.Query;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.springmvchb.entity.Cliente;
    
    @Repository
    public class ClienteDAOImpl implements ClienteDAO {
        
        @Autowired
        private SessionFactory sessionFactory;
    
        @Override
        public List<Cliente> getClientes() {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query<Cliente> aQuery = sessionAtual.createQuery("from Cliente", Cliente.class);
            
            List<Cliente> clientes = aQuery.getResultList();
            
            return clientes;
        }
    
        @Override
        public void salvarCliente(Cliente oCliente) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            sessionAtual.saveOrUpdate(oCliente); // Olha essa atualização especial que fizemos aqui
            
        }
    
        @Override
        public Cliente getCliente(int oId) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Cliente oCliente = sessionAtual.get(Cliente.class, oId);
            
            return oCliente;
        }
    
    }

**ClienteService.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteService {
        
        public List<Cliente> getClientes();
        
        public void salvarCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
    }

**ClienteServiceImpl.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    import org.springframework.transaction.annotation.Transactional;
    
    import dominio.springmvchb.dao.ClienteDAO;
    import dominio.springmvchb.entity.Cliente;
    
    @Service
    public class ClienteServiceImpl implements ClienteService {
        
        @Autowired
        private ClienteDAO clienteDAO;
    
        @Override
        @Transactional
        public List<Cliente> getClientes() {
            return clienteDAO.getClientes();
        }
    
        @Override
        @Transactional
        public void salvarCliente(Cliente oCliente) {
            clienteDAO.salvarCliente(oCliente);        
        }
    
        @Override
        @Transactional
        public Cliente getCliente(int oId) {
            return clienteDAO.getCliente(oId);
        }
    
    }

**ClienteController.java**

    package dominio.springmvchb.controller;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.ModelAttribute;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RequestParam;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @Controller
    @RequestMapping("/cliente")
    public class ClienteController {
    
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/lista")
        public String listaDeClientes(Model modelo) {
            
            List<Cliente> osClientes = clienteService.getClientes();
            
            modelo.addAttribute("clientes", osClientes);
            
            return "lista";
        }
        
        @GetMapping("/mostrarFormParaAdicionar")
        public String mostrarFormParaAdicionar(Model modelo) {
            
            Cliente oCliente = new Cliente();
            
            modelo.addAttribute("cliente", oCliente);
            
            return "cliente-form";
        }
        
        @PostMapping("/salvarCliente")
        public String salvarCliente(@ModelAttribute("cliente") Cliente oCliente) {
            
            clienteService.salvarCliente(oCliente);
            
            return "redirect:/cliente/lista";
            
        }
        
        @GetMapping("/mostrarFormParaAtualizar")
        public String mostrarFormParaAtualizar(@RequestParam("clienteId") int oId, Model modelo) {
            
            Cliente oCliente = clienteService.getCliente(oId);
            
            modelo.addAttribute("cliente", oCliente);
            //<form:form action="salvarCliente" modelAttribute="cliente" method="POST">
            
            return "cliente-form";
            
        }
        
    }

**lista.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
    <%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/estilo.css">
        <title>Spring MVC + Hibernate</title>
    </head>
    <body>
    
        <div id="wrapper">
            <div id="header">
                <h1>CRM</h1>
            </div>
        </div>
        
        <div id="container">
            <div id="content">
            
                <input type="button" value="Adicionar cliente" 
                       onclick="window.location.href='mostrarFormParaAdicionar'; return false;"
                       class="add-button"
                />
                <!-- 
                Se eu quisesse, eu poderia escrever esse botão assim
                
                    <form action="mostrarFormParaAdicionar">
    
                    <input type="submit" value="Adicionar cliente" class="add-button/>
    
                    </form>
                
                 -->
                
                <table>
                    <tr>
                        <th>Nome</th>
                        <th>Sobrenome</th>
                        <th>Email</th>
                        <th>Ação</th>
                        
                        <c:forEach var="tempCliente" items="${clientes}"> <!-- clientes é o atributo do model... -->
                        
                            <c:url var="atualizarLink" value="/cliente/mostrarFormParaAtualizar">
                                <c:param name="clienteId" value="${tempCliente.id}" /> <!-- Repare que o tempCliente aqui se refere à variável do c:forEach -->
                            </c:url>
                            
                            <tr>
                                <td>${tempCliente.nome}</td> <!-- Por exemplo, aqui ele chama tempCliente.getNome() -->
                                <td>${tempCliente.sobrenome}</td>
                                <td>${tempCliente.email}</td>
                                <td><a href="${atualizarLink}">Atualizar</a></td> <!-- Repare que o tempCliente aqui se refere à variável do c:url -->
                            </tr>
                        </c:forEach>
                        
                    </tr>
                </table>
                
            </div>
        </div>
    
    </body>
    </html>

**cliente-form.jsp**

    <%@ page language="java" contentType="text/html; charset=ISO-8859-1"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="UTF-8">
            <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/estilo.css">
            <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/adicionar-cliente.css">
            <title>Adicionar Cliente</title>
        </head>
        <body>
        
            <div id="wrapper">
                <div id="header">
                    <h1>CRM</h1>
                </div>
            </div>
            
            <div id="container">
                <h3>Adicionar Cliente</h3>
                
                <form:form action="salvarCliente" modelAttribute="cliente" method="POST">
                
                        <form:hidden path="id" /> <!-- Sem esta linha, você perde o id do cliente -->
                
                    <table>
                        <tbody>
                            <tr>
                                <td><label>Nome: </label></td>
                                <td><form:input path="nome" /></td>
                            </tr>
                            <tr>
                                <td><label>Sobrenome: </label></td>
                                <td><form:input path="sobrenome" /></td>
                            </tr>
                            <tr>
                                <td><label>E-mail: </label></td>
                                <td><form:input path="email" /></td>
                            </tr>
                            <tr>
                                <td><label></label></td>
                                <td><input type="submit" value="Salvar" class="save" /></td>
                            </tr>
                        </tbody>
                    </table>
                
                </form:form>
                
                <div style="clear; both;">
                
                    <p>
                        <a href="${pageContext.request.contextPath}">Voltar pra lista</a>
                    </p>
                
                </div>
                
            </div>
        
        </body>
    </html>

## Deletar cliente<span id="springmvchibernate_delete"></span>

Atualize os arquivos abaixo:

**ClienteDAO.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteDAO {
        
        public List<Cliente> getClientes();
        
        public void salvarCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
        public void deletarCliente(int oId);
    
    }

**ClienteDAOImpl.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.query.Query;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.springmvchb.entity.Cliente;
    
    @Repository
    public class ClienteDAOImpl implements ClienteDAO {
        
        @Autowired
        private SessionFactory sessionFactory;
    
        @Override
        public List<Cliente> getClientes() {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query<Cliente> aQuery = sessionAtual.createQuery("from Cliente", Cliente.class);
            
            List<Cliente> clientes = aQuery.getResultList();
            
            return clientes;
        }
    
        @Override
        public void salvarCliente(Cliente oCliente) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            sessionAtual.saveOrUpdate(oCliente); // Olha essa atualização especial que fizemos aqui
            
        }
    
        @Override
        public Cliente getCliente(int oId) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Cliente oCliente = sessionAtual.get(Cliente.class, oId);
            
            return oCliente;
        }
    
        @Override
        public void deletarCliente(int oId) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query oQuery = sessionAtual.createQuery("delete from Cliente where id=:clienteId");
            
            oQuery.setParameter("clienteId", oId);
            
            oQuery.executeUpdate();
            
        }
    
    }

*Esse `=:` ajuda a prevenir ataques de injeção de SQL, esses dois pontos são uma "bind variable" que permitem que uma única instrução SQL seja reusada muitas vezes, o que ajuda na segurança (desautorizando ataques de injeção de SQL) e performance (reduz a quantidade de parsing exigida)*

*Ah, e você provavelmente está recebendo um aviso ("Query is a raw type. References to generic type Query<R> should be parameterized") nessa mesma linha `Query oQuery = sessionAtual.createQuery("delete from Cliente where id=:clienteId");` porque um generic é recomendado para o caso de recebermos mais que 1 objeto. De qualquer forma, você não precisa se preocupar porque quando deletamos um dado, não precisamos saber o tipo de dado, simplesmente deletamos o dado através do ID.*

**ClienteService.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteService {
        
        public List<Cliente> getClientes();
        
        public void salvarCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
        public void deletarCliente(int oId);
    
    }

**ClienteServiceImpl.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    import org.springframework.transaction.annotation.Transactional;
    
    import dominio.springmvchb.dao.ClienteDAO;
    import dominio.springmvchb.entity.Cliente;
    
    @Service
    public class ClienteServiceImpl implements ClienteService {
        
        @Autowired
        private ClienteDAO clienteDAO;
    
        @Override
        @Transactional
        public List<Cliente> getClientes() {
            return clienteDAO.getClientes();
        }
    
        @Override
        @Transactional
        public void salvarCliente(Cliente oCliente) {
            clienteDAO.salvarCliente(oCliente);        
        }
    
        @Override
        @Transactional
        public Cliente getCliente(int oId) {
            return clienteDAO.getCliente(oId);
        }
    
        @Override
        @Transactional
        public void deletarCliente(int oId) {
            clienteDAO.deletarCliente(oId);  
            
        }
    
    }

**ClienteController.java**

    package dominio.springmvchb.controller;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.ModelAttribute;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RequestParam;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @Controller
    @RequestMapping("/cliente")
    public class ClienteController {
    
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/lista")
        public String listaDeClientes(Model modelo) {
            
            List<Cliente> osClientes = clienteService.getClientes();
            
            modelo.addAttribute("clientes", osClientes);
            
            return "lista";
        }
        
        @GetMapping("/mostrarFormParaAdicionar")
        public String mostrarFormParaAdicionar(Model modelo) {
            
            Cliente oCliente = new Cliente();
            
            modelo.addAttribute("cliente", oCliente);
            
            return "cliente-form";
        }
        
        @PostMapping("/salvarCliente")
        public String salvarCliente(@ModelAttribute("cliente") Cliente oCliente) {
            
            clienteService.salvarCliente(oCliente);
            
            return "redirect:/cliente/lista";
            
        }
        
        @GetMapping("/mostrarFormParaAtualizar")
        public String mostrarFormParaAtualizar(@RequestParam("clienteId") int oId, Model modelo) {
            
            Cliente oCliente = clienteService.getCliente(oId);
            
            modelo.addAttribute("cliente", oCliente);
            
            return "cliente-form";
            
        }
        
        @GetMapping("/deletar")
        public String deletarCliente(@RequestParam("clienteId") int oId) {
        //<c:url var="deletarLink" value="/cliente/deletar">
            
            clienteService.deletarCliente(oId);
            
            return "redirect:/cliente/lista";
            
        }
        
    }

**lista.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
    <%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/estilo.css">
        <title>Spring MVC + Hibernate</title>
    </head>
    <body>
    
        <div id="wrapper">
            <div id="header">
                <h1>CRM</h1>
            </div>
        </div>
        
        <div id="container">
            <div id="content">
            
                <input type="button" value="Adicionar cliente" 
                       onclick="window.location.href='mostrarFormParaAdicionar'; return false;"
                       class="add-button"
                />
                
                <table>
                    <tr>
                        <th>Nome</th>
                        <th>Sobrenome</th>
                        <th>Email</th>
                        <th>Ação</th>
                        
                        <c:forEach var="tempCliente" items="${clientes}">
                        
                            <c:url var="atualizarLink" value="/cliente/mostrarFormParaAtualizar">
                                <c:param name="clienteId" value="${tempCliente.id}" />
                            </c:url>
                            
                            <c:url var="deletarLink" value="/cliente/deletar">
                                <c:param name="clienteId" value="${tempCliente.id}" />
                            </c:url>
                            
                            <tr>
                                <td>${tempCliente.nome}</td>
                                <td>${tempCliente.sobrenome}</td>
                                <td>${tempCliente.email}</td>
                                <td><a href="${atualizarLink}">Atualizar</a>
                                |
                                <a href="${deletarLink}" onclick="if (!(confirm('Você tem certeza?'))) return false;">Deletar</a></td>
                            </tr>
                        </c:forEach>
                        
                    </tr>
                </table>
                
            </div>
        </div>
    
    </body>
    </html>

## Sistema de busca<span id="springmvchibernate_search"></span>

Atualize os arquivos abaixo:

**ClienteDAO.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteDAO {
        
        public List<Cliente> getClientes();
        
        public void salvarCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
        public void deletarCliente(int oId);
    
        public List<Cliente> buscarClientes(String oNomeProcurado);
    
    }

**ClienteDAOImpl.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.query.Query;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.springmvchb.entity.Cliente;
    
    @Repository
    public class ClienteDAOImpl implements ClienteDAO {
        
        @Autowired
        private SessionFactory sessionFactory;
    
        @Override
        public List<Cliente> getClientes() {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query<Cliente> aQuery = sessionAtual.createQuery("from Cliente", Cliente.class);
            
            List<Cliente> clientes = aQuery.getResultList();
            
            return clientes;
        }
    
        @Override
        public void salvarCliente(Cliente oCliente) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            sessionAtual.saveOrUpdate(oCliente); // Olha essa atualização especial que fizemos aqui
            
        }
    
        @Override
        public Cliente getCliente(int oId) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Cliente oCliente = sessionAtual.get(Cliente.class, oId);
            
            return oCliente;
        }
    
        @Override
        public void deletarCliente(int oId) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query oQuery = sessionAtual.createQuery("delete from Cliente where id=:clienteId");
            
            oQuery.setParameter("clienteId", oId);
            
            oQuery.executeUpdate();
            
        }
    
        @Override
        public List<Cliente> buscarClientes(String oNomeProcurado) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query oQuery = null;
            
            if (oNomeProcurado != null && oNomeProcurado.trim().length() > 0) {
                oQuery = sessionAtual.createQuery("from Cliente where lower(nome) like :oNome or lower(sobrenome) like :oNome", Cliente.class);
                oQuery.setParameter("oNome", "%" + oNomeProcurado.toLowerCase() + "%"); // % são "wildcard characters"
            }
            else {
                // O query está vazio, portanto pegue todos os clientes
                oQuery = sessionAtual.createQuery("from Cliente", Cliente.class);
            }
            
            List<Cliente> clientes = oQuery.getResultList();
            
            return clientes;
        }
    
    }

**ClienteService.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteService {
        
        public List<Cliente> getClientes();
        
        public void salvarCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
        public void deletarCliente(int oId);
    
        public List<Cliente> buscarClientes(String oNomeProcurado);
    
    }

**ClienteServiceImpl.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    import org.springframework.transaction.annotation.Transactional;
    
    import dominio.springmvchb.dao.ClienteDAO;
    import dominio.springmvchb.entity.Cliente;
    
    @Service
    public class ClienteServiceImpl implements ClienteService {
        
        @Autowired
        private ClienteDAO clienteDAO;
    
        @Override
        @Transactional
        public List<Cliente> getClientes() {
            return clienteDAO.getClientes();
        }
    
        @Override
        @Transactional
        public void salvarCliente(Cliente oCliente) {
            clienteDAO.salvarCliente(oCliente);        
        }
    
        @Override
        @Transactional
        public Cliente getCliente(int oId) {
            return clienteDAO.getCliente(oId);
        }
    
        @Override
        @Transactional
        public void deletarCliente(int oId) {
            clienteDAO.deletarCliente(oId);  
            
        }
    
        @Override
        @Transactional
        public List<Cliente> buscarClientes(String oNomeProcurado) {
            // TODO Auto-generated method stub
            return clienteDAO.buscarClientes(oNomeProcurado);
        }
    
    }

**ClienteController.java**

    package dominio.springmvchb.controller;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.ModelAttribute;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RequestParam;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @Controller
    @RequestMapping("/cliente")
    public class ClienteController {
    
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/lista")
        public String listaDeClientes(Model modelo) {
            
            List<Cliente> osClientes = clienteService.getClientes();
            
            modelo.addAttribute("clientes", osClientes);
            
            return "lista";
        }
        
        @GetMapping("/mostrarFormParaAdicionar")
        public String mostrarFormParaAdicionar(Model modelo) {
            
            Cliente oCliente = new Cliente();
            
            modelo.addAttribute("cliente", oCliente);
            
            return "cliente-form";
        }
        
        @PostMapping("/salvarCliente")
        public String salvarCliente(@ModelAttribute("cliente") Cliente oCliente) {
            
            clienteService.salvarCliente(oCliente);
            
            return "redirect:/cliente/lista";
            
        }
        
        @GetMapping("/mostrarFormParaAtualizar")
        public String mostrarFormParaAtualizar(@RequestParam("clienteId") int oId, Model modelo) {
            
            Cliente oCliente = clienteService.getCliente(oId);
            
            modelo.addAttribute("cliente", oCliente);
            
            return "cliente-form";
            
        }
        
        @GetMapping("/deletar")
        public String deletarCliente(@RequestParam("clienteId") int oId) {
            
            clienteService.deletarCliente(oId);
            
            return "redirect:/cliente/lista";
            
        }
        
        @GetMapping("/buscar")
        public String buscarClientes(@RequestParam("oNomeProcurado") String oNomeProcurado, Model modelo) {
            
            List<Cliente> osClientes = clienteService.buscarClientes(oNomeProcurado);
            
            modelo.addAttribute("clientes", osClientes);
            
            return "lista";
            
        }
        
    }

**lista.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
    <%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/estilo.css">
        <title>Spring MVC + Hibernate</title>
    </head>
    <body>
    
        <div id="wrapper">
            <div id="header">
                <h1>CRM</h1>
            </div>
        </div>
        
        <div id="container">
            <div id="content">
            
                <input type="button" value="Adicionar cliente" 
                       onclick="window.location.href='mostrarFormParaAdicionar'; return false;"
                       class="add-button"
                />
                
                <form:form action="buscar" method="GET">
                    Procurar cliente: <input type="text" name="oNomeProcurado" />
                    
                    <input type="submit" value="Pesquisar" class="add-button" />
                </form:form>
                
                <table>
                    <tr>
                        <th>Nome</th>
                        <th>Sobrenome</th>
                        <th>Email</th>
                        <th>Ação</th>
                        
                        <c:forEach var="tempCliente" items="${clientes}">
                        
                            <c:url var="atualizarLink" value="/cliente/mostrarFormParaAtualizar">
                                <c:param name="clienteId" value="${tempCliente.id}" />
                            </c:url>
                            
                            <c:url var="deletarLink" value="/cliente/deletar">
                                <c:param name="clienteId" value="${tempCliente.id}" />
                            </c:url>
                            
                            <tr>
                                <td>${tempCliente.nome}</td>
                                <td>${tempCliente.sobrenome}</td>
                                <td>${tempCliente.email}</td>
                                <td><a href="${atualizarLink}">Atualizar</a>
                                |
                                <a href="${deletarLink}" onclick="if (!(confirm('Você tem certeza?'))) return false;">Deletar</a></td>
                            </tr>
                        </c:forEach>
                        
                    </tr>
                </table>
                
            </div>
        </div>
    
    </body>
    </html>

## Ordenação<span id="springmvchibernate_order"></span>

Esse é o último, prometo. Sei que você já está cansado(a)...

Crie o pacote `dominio.springmvchb.util` e dentro dele crie a interface `OrdenarUtil`.

    package dominio.springmvchb.util;
    
    public interface OrdenarUtil {
    
        public static final int NOME = 1;
        public static final int SOBRENOME = 2;
        public static final int EMAIL = 3;
    
    }

Atualize o arquivo `lista.js`:

    <%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
    <%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <%@ page import="dominio.springmvchb.util.OrdenarUtil" %>
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/estilo.css">
        <title>Spring MVC + Hibernate</title>
    </head>
    <body>
    
        <div id="wrapper">
            <div id="header">
                <h1>CRM</h1>
            </div>
        </div>
        
        <div id="container">
            <div id="content">
            
                <input type="button" value="Adicionar cliente" 
                       onclick="window.location.href='mostrarFormParaAdicionar'; return false;"
                       class="add-button"
                />
                
                <form:form action="buscar" method="GET">
                    Procurar cliente: <input type="text" name="oNomeProcurado" />
                    
                    <input type="submit" value="Pesquisar" class="add-button" />
                </form:form>
                
                <table>
                
                    <c:url var="ordenarNome" value="/cliente/lista">
                        <c:param name="ordem" value="<%= Integer.toString(OrdenarUtil.NOME) %>" />
                    </c:url>                    
    
                    <c:url var="ordenarSobreNome" value="/cliente/lista">
                        <c:param name="ordem" value="<%= Integer.toString(OrdenarUtil.SOBRENOME) %>" />
                    </c:url>                    
    
                    <c:url var="ordenarEmail" value="/cliente/lista">
                        <c:param name="ordem" value="<%= Integer.toString(OrdenarUtil.EMAIL) %>" />
                    </c:url>
                    
                    <tr>
                        <th><a href="${ordenarNome}">Nome</a></th>
                        <th><a href="${ordenarSobreNome}">Sobrenome</a></th>
                        <th><a href="${ordenarEmail}">Email</a></th>
                        <th>Ação</th>
                        
                        <c:forEach var="tempCliente" items="${clientes}">
                        
                            <c:url var="atualizarLink" value="/cliente/mostrarFormParaAtualizar">
                                <c:param name="clienteId" value="${tempCliente.id}" />
                            </c:url>
                            
                            <c:url var="deletarLink" value="/cliente/deletar">
                                <c:param name="clienteId" value="${tempCliente.id}" />
                            </c:url>
                            
                            <tr>
                                <td>${tempCliente.nome}</td>
                                <td>${tempCliente.sobrenome}</td>
                                <td>${tempCliente.email}</td>
                                <td><a href="${atualizarLink}">Atualizar</a>
                                |
                                <a href="${deletarLink}" onclick="if (!(confirm('Você tem certeza?'))) return false;">Deletar</a></td>
                            </tr>
                        </c:forEach>
                        
                    </tr>
                </table>
                
            </div>
        </div>
    
    </body>
    </html>

No arquivo `ClienteController`, atualizaremos o método `listaDeClientes()`:

    package dominio.springmvchb.controller;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.ModelAttribute;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RequestParam;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    import dominio.springmvchb.util.OrdenarUtil;
    
    @Controller
    @RequestMapping("/cliente")
    public class ClienteController {
    
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/lista")
        public String listaDeClientes(Model modelo, @RequestParam(required=false) String ordem) {
            
            List<Cliente> osClientes = null;
            
            if (ordem != null) {
                int ordemDoCampo = Integer.parseInt(ordem);
                osClientes = clienteService.getClientes(ordemDoCampo);
            }
            else {
                osClientes = clienteService.getClientes(OrdenarUtil.NOME);
            }
            
            modelo.addAttribute("clientes", osClientes);
            
            return "lista";
        }
        
        @GetMapping("/mostrarFormParaAdicionar")
        public String mostrarFormParaAdicionar(Model modelo) {
            
            Cliente oCliente = new Cliente();
            
            modelo.addAttribute("cliente", oCliente);
            
            return "cliente-form";
        }
        
        @PostMapping("/salvarCliente")
        public String salvarCliente(@ModelAttribute("cliente") Cliente oCliente) {
            
            clienteService.salvarCliente(oCliente);
            
            return "redirect:/cliente/lista";
            
        }
        
        @GetMapping("/mostrarFormParaAtualizar")
        public String mostrarFormParaAtualizar(@RequestParam("clienteId") int oId, Model modelo) {
            
            Cliente oCliente = clienteService.getCliente(oId);
            
            modelo.addAttribute("cliente", oCliente);
            
            return "cliente-form";
            
        }
        
        @GetMapping("/deletar")
        public String deletarCliente(@RequestParam("clienteId") int oId) {
            
            clienteService.deletarCliente(oId);
            
            return "redirect:/cliente/lista";
            
        }
        
        @GetMapping("/buscar")
        public String buscarClientes(@RequestParam("oNomeProcurado") String oNomeProcurado, Model modelo) {
            
            List<Cliente> osClientes = clienteService.buscarClientes(oNomeProcurado);
            
            modelo.addAttribute("clientes", osClientes);
            
            return "lista";
            
        }
        
    }

Agora atualize os serviços:

**ClienteService.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteService {
        
        public List<Cliente> getClientes(int ordemDoCampo);
        
        public void salvarCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
        public void deletarCliente(int oId);
    
        public List<Cliente> buscarClientes(String oNomeProcurado);
    
    }

**ClienteServiceImpl.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    import org.springframework.transaction.annotation.Transactional;
    
    import dominio.springmvchb.dao.ClienteDAO;
    import dominio.springmvchb.entity.Cliente;
    
    @Service
    public class ClienteServiceImpl implements ClienteService {
        
        @Autowired
        private ClienteDAO clienteDAO;
    
        @Override
        @Transactional
        public List<Cliente> getClientes(int ordemDoCampo) {
            return clienteDAO.getClientes(ordemDoCampo);
        }
    
        @Override
        @Transactional
        public void salvarCliente(Cliente oCliente) {
            clienteDAO.salvarCliente(oCliente);        
        }
    
        @Override
        @Transactional
        public Cliente getCliente(int oId) {
            return clienteDAO.getCliente(oId);
        }
    
        @Override
        @Transactional
        public void deletarCliente(int oId) {
            clienteDAO.deletarCliente(oId);  
            
        }
    
        @Override
        @Transactional
        public List<Cliente> buscarClientes(String oNomeProcurado) {
            // TODO Auto-generated method stub
            return clienteDAO.buscarClientes(oNomeProcurado);
        }
    
    }

E por fim, atualize o DAO:

**ClienteDAO.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteDAO {
        
        public List<Cliente> getClientes(int ordemDoCampo);
        
        public void salvarCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
        public void deletarCliente(int oId);
    
        public List<Cliente> buscarClientes(String oNomeProcurado);
    
    }

**ClienteDAOImpl.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.query.Query;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.util.OrdenarUtil;
    
    @Repository
    public class ClienteDAOImpl implements ClienteDAO {
        
        @Autowired
        private SessionFactory sessionFactory;
    
        @Override
        public List<Cliente> getClientes(int ordemDoCampo) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            String oNomeDoCampo = null;
            
            switch(ordemDoCampo) {
                case OrdenarUtil.NOME:
                    oNomeDoCampo = "nome";
                    break;
                case OrdenarUtil.SOBRENOME:
                    oNomeDoCampo = "sobrenome";
                    break;
                case OrdenarUtil.EMAIL:
                    oNomeDoCampo = "email";
                    break;
                default:
                    oNomeDoCampo = "nome";
            }
            
            String customQuery = "from Cliente order by " + oNomeDoCampo;
            
            Query<Cliente> aQuery = sessionAtual.createQuery(customQuery, Cliente.class);
            
            List<Cliente> clientes = aQuery.getResultList();
            
            return clientes;
        }
    
        @Override
        public void salvarCliente(Cliente oCliente) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            sessionAtual.saveOrUpdate(oCliente); // Olha essa atualização especial que fizemos aqui
            
        }
    
        @Override
        public Cliente getCliente(int oId) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Cliente oCliente = sessionAtual.get(Cliente.class, oId);
            
            return oCliente;
        }
    
        @Override
        public void deletarCliente(int oId) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query oQuery = sessionAtual.createQuery("delete from Cliente where id=:clienteId");
            
            oQuery.setParameter("clienteId", oId);
            
            oQuery.executeUpdate();
            
        }
    
        @Override
        public List<Cliente> buscarClientes(String oNomeProcurado) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query oQuery = null;
            
            if (oNomeProcurado != null && oNomeProcurado.trim().length() > 0) {
                oQuery = sessionAtual.createQuery("from Cliente where lower(nome) like :oNome or lower(sobrenome) like :oNome", Cliente.class);
                oQuery.setParameter("oNome", "%" + oNomeProcurado.toLowerCase() + "%"); // % são "wildcard characters"
            }
            else {
                // O query está vazio, portanto pegue todos os clientes
                oQuery = sessionAtual.createQuery("from Cliente", Cliente.class);
            }
            
            List<Cliente> clientes = oQuery.getResultList();
            
            return clientes;
        }
    
    }

## BÔNUS: O projeto completo<span id="springmvchibernate_full"></span>

Como não quero me repetir: se você ainda não tem os arquivos JAR e o banco de dados configurados, vá até o início deste capítulo e depois volte aqui.

**/cliente-web/src/main/webapp/index.jsp**

    <% response.sendRedirect("cliente/lista"); %>

**/cliente-web/src/main/webapp/WEB-INF/web.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd" id="WebApp_ID" version="4.0">
      <display-name>spring-mvc</display-name>
     
      <absolute-ordering />
    
      <welcome-file-list>
        <welcome-file>index.jsp</welcome-file>
        <welcome-file>index.html</welcome-file>
      </welcome-file-list>
    
      <servlet>
        <servlet-name>dispatcher</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
          <param-name>contextConfigLocation</param-name>
          <param-value>/WEB-INF/spring-mvc.xml</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
      </servlet>
      
      <servlet-mapping>
        <servlet-name>dispatcher</servlet-name>
        <url-pattern>/</url-pattern>
      </servlet-mapping>
    </web-app>

**/cliente-web/src/main/webapp/WEB-INF/spring-mvc.xml**

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xmlns:tx="http://www.springframework.org/schema/tx"
        xmlns:mvc="http://www.springframework.org/schema/mvc"
        xsi:schemaLocation="
            http://www.springframework.org/schema/beans
            http://www.springframework.org/schema/beans/spring-beans.xsd
            http://www.springframework.org/schema/context
            http://www.springframework.org/schema/context/spring-context.xsd
            http://www.springframework.org/schema/mvc
            http://www.springframework.org/schema/mvc/spring-mvc.xsd
            http://www.springframework.org/schema/tx 
            http://www.springframework.org/schema/tx/spring-tx.xsd">
    
        <!-- Add support for component scanning -->
        <context:component-scan base-package="dominio.springmvchb" />
    
        <!-- Add support for conversion, formatting and validation support -->
        <mvc:annotation-driven/>
    
        <!-- Define Spring MVC view resolver -->
        <bean
            class="org.springframework.web.servlet.view.InternalResourceViewResolver">
            <property name="prefix" value="/WEB-INF/view/" />
            <property name="suffix" value=".jsp" />
        </bean>
    
        <!-- Step 1: Define Database DataSource / connection pool -->
        <bean id="myDataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource"
              destroy-method="close">
            <property name="driverClass" value="com.mysql.cj.jdbc.Driver" />
            <property name="jdbcUrl" value="jdbc:mysql://localhost:3306/cliente_web?useSSL=false" />
            <property name="user" value="estudante" />
            <property name="password" value="estudante" /> 
    
            <!-- these are connection pool properties for C3P0 -->
            <property name="minPoolSize" value="5" />
            <property name="maxPoolSize" value="20" />
            <property name="maxIdleTime" value="30000" />
        </bean>  
        
        <!-- Step 2: Setup Hibernate session factory -->
        <bean id="sessionFactory"
            class="org.springframework.orm.hibernate5.LocalSessionFactoryBean">
            <property name="dataSource" ref="myDataSource" />
            <property name="packagesToScan" value="dominio.springmvchb.entity" />
            <property name="hibernateProperties">
               <props>
                  <prop key="hibernate.dialect">org.hibernate.dialect.MySQLDialect</prop>
                  <prop key="hibernate.show_sql">true</prop>
               </props>
            </property>
       </bean>      
    
        <!-- Step 3: Setup Hibernate transaction manager -->
        <bean id="myTransactionManager"
                class="org.springframework.orm.hibernate5.HibernateTransactionManager">
            <property name="sessionFactory" ref="sessionFactory"/>
        </bean>
        
        <!-- Step 4: Enable configuration of transactional behavior based on annotations -->
        <tx:annotation-driven transaction-manager="myTransactionManager" />
        
        <!-- Add support for web resources -->
        <mvc:resources location="/resources/" mapping="/resources/**"></mvc:resources> <!-- O ** diz que é pra incluir os sub-diretórios -->
    
    </beans>

Na pasta `/cliente-web/src/main/webapp/WEB-INF/`, crie a pasta `view`.

**/cliente-web/src/main/webapp/WEB-INF/view/lista.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
    <%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <%@ page import="dominio.springmvchb.util.OrdenarUtil" %>
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/estilo.css">
        <title>Spring MVC + Hibernate</title>
    </head>
    <body>
    
        <div id="wrapper">
            <div id="header">
                <h1>CRM</h1>
            </div>
        </div>
        
        <div id="container">
            <div id="content">
            
                <input type="button" value="Adicionar cliente" 
                       onclick="window.location.href='mostrarFormParaAdicionar'; return false;"
                       class="add-button"
                />
                
                <form:form action="buscar" method="GET">
                    Procurar cliente: <input type="text" name="oNomeProcurado" />
                    
                    <input type="submit" value="Pesquisar" class="add-button" />
                </form:form>
                
                <table>
                
                    <c:url var="ordenarNome" value="/cliente/lista">
                        <c:param name="ordem" value="<%= Integer.toString(OrdenarUtil.NOME) %>" />
                    </c:url>                    
    
                    <c:url var="ordenarSobreNome" value="/cliente/lista">
                        <c:param name="ordem" value="<%= Integer.toString(OrdenarUtil.SOBRENOME) %>" />
                    </c:url>                    
    
                    <c:url var="ordenarEmail" value="/cliente/lista">
                        <c:param name="ordem" value="<%= Integer.toString(OrdenarUtil.EMAIL) %>" />
                    </c:url>
                    
                    <tr>
                        <th><a href="${ordenarNome}">Nome</a></th>
                        <th><a href="${ordenarSobreNome}">Sobrenome</a></th>
                        <th><a href="${ordenarEmail}">Email</a></th>
                        <th>Ação</th>
                        
                        <c:forEach var="tempCliente" items="${clientes}">
                        
                            <c:url var="atualizarLink" value="/cliente/mostrarFormParaAtualizar">
                                <c:param name="clienteId" value="${tempCliente.id}" />
                            </c:url>
                            
                            <c:url var="deletarLink" value="/cliente/deletar">
                                <c:param name="clienteId" value="${tempCliente.id}" />
                            </c:url>
                            
                            <tr>
                                <td>${tempCliente.nome}</td>
                                <td>${tempCliente.sobrenome}</td>
                                <td>${tempCliente.email}</td>
                                <td><a href="${atualizarLink}">Atualizar</a>
                                |
                                <a href="${deletarLink}" onclick="if (!(confirm('Você tem certeza?'))) return false;">Deletar</a></td>
                            </tr>
                        </c:forEach>
                        
                    </tr>
                </table>
                
            </div>
        </div>
    
    </body>
    </html>

**/cliente-web/src/main/webapp/WEB-INF/view/cliente-form.jsp**

    <%@ page language="java" contentType="text/html; charset=ISO-8859-1"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="UTF-8">
            <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/estilo.css">
            <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/adicionar-cliente.css">
            <title>Adicionar Cliente</title>
        </head>
        <body>
        
            <div id="wrapper">
                <div id="header">
                    <h1>CRM</h1>
                </div>
            </div>
            
            <div id="container">
                <h3>Adicionar Cliente</h3>
                
                <form:form action="salvarCliente" modelAttribute="cliente" method="POST">
                
                        <form:hidden path="id" /> <!-- Sem esta linha, você perde o id do cliente -->
                
                    <table>
                        <tbody>
                            <tr>
                                <td><label>Nome: </label></td>
                                <td><form:input path="nome" /></td>
                            </tr>
                            <tr>
                                <td><label>Sobrenome: </label></td>
                                <td><form:input path="sobrenome" /></td>
                            </tr>
                            <tr>
                                <td><label>E-mail: </label></td>
                                <td><form:input path="email" /></td>
                            </tr>
                            <tr>
                                <td><label></label></td>
                                <td><input type="submit" value="Salvar" class="save" /></td>
                            </tr>
                        </tbody>
                    </table>
                
                </form:form>
                
                <div style="clear; both;">
                
                    <p>
                        <a href="${pageContext.request.contextPath}">Voltar pra lista</a>
                    </p>
                
                </div>
                
            </div>
        
        </body>
    </html>

Na pasta `/cliente-web/src/main/webapp/`, crie a pasta `resources`, e dentro desta a pasta `css`.

**/cliente-web/src/main/webapp/resources/css/estilo.css**

    html, body{
        margin-left:15px; margin-right:15px; 
        padding:0px; 
        font-family:Verdana, Arial, Helvetica, sans-serif;
    }
    
    table {   
        border-collapse:collapse;
        border-bottom:1px solid gray;
        font-family: Tahoma,Verdana,Segoe,sans-serif;
        width:72%;
    }
     
    th {
        border-bottom:1px solid gray;
        background:none repeat scroll 0 0 #09c332;
        padding:10px;
        color: #FFFFFF;
    }
    
    tr {
        border-top:1px solid gray;
        text-align:center;    
    }
     
    tr:nth-child(even) {background: #FFFFFF}
    tr:nth-child(odd) {background: #BBBBBB}    
     
    #wrapper {width: 100%; margin-top: 0px; }
    #header {width: 70%; background: #09c332; margin-top: 0px; padding:15px 0px 15px 15px;}
    #header h2 {width: 100%; margin:auto; color: #FFFFFF;}
    #container {width: 100%; margin:auto}
    #container h3 {color: #000;}
    #container #content {margin-top: 20px;}
    
    .add-button {
        border: 1px solid #666; 
        border-radius: 5px; 
        padding: 4px; 
        font-size: 12px;
        font-weight: bold;
        width: 120px; 
        padding: 5px 10px; 
        
        margin-bottom: 15px;
        background: #cccccc;
    }

**/cliente-web/src/main/webapp/resources/css/adicionar-cliente.css**

    form {
        margin-top: 10px;
    }
    
    label {
        font-size: 16px; 
        width: 100px; 
        display: block; 
        text-align: right;
        margin-right: 10px;
        margin-top: 8px;
        margin-bottom: 8px;
    }
    
    input {
        width: 250px;
        border: 1px solid #666; 
        border-radius: 5px; 
        padding: 4px; 
        font-size: 16px;
    }
    
    .save {
        font-weight: bold;
        width: 130px; 
        padding: 5px 10px; 
        margin-top: 30px;
        background: #cccccc;
    }
    
    table {   
        border-style:none;
        width:50%;
    }
    
    tr:nth-child(even) {background: #FFFFFF}
    tr:nth-child(odd) {background: #FFFFFF}
    
    tr {
        border-style:none;
        text-align:left;    
    }

Agora crie os seguintes pacotes:

* `dominio.springmvchb.controller`

* `dominio.springmvchb.dao`

* `dominio.springmvchb.entity`

* `dominio.springmvchb.service`

* `dominio.springmvchb.util`

Já podemos criar as seguintes interfaces e classes:

**Cliente.java**

    package dominio.springmvchb.entity;
    
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="cliente")
    public class Cliente {
        
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        public int id;
        
        @Column(name="nome")
        public String nome;
        
        @Column(name="sobrenome")
        public String sobrenome;
        
        @Column(name="email")
        public String email;
        
        public Cliente () {
            
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        @Override
        public String toString() {
            return "Cliente [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email + "]";
        }
    
    }

**ClienteController.java**

    package dominio.springmvchb.controller;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.ModelAttribute;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RequestParam;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    import dominio.springmvchb.util.OrdenarUtil;
    
    @Controller
    @RequestMapping("/cliente")
    public class ClienteController {
    
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/lista")
        public String listaDeClientes(Model modelo, @RequestParam(required=false) String ordem) {
            
            List<Cliente> osClientes = null;
            
            if (ordem != null) {
                int ordemDoCampo = Integer.parseInt(ordem);
                osClientes = clienteService.getClientes(ordemDoCampo);
            }
            else {
                osClientes = clienteService.getClientes(OrdenarUtil.NOME);
            }
            
            modelo.addAttribute("clientes", osClientes);
            
            return "lista";
        }
        
        @GetMapping("/mostrarFormParaAdicionar")
        public String mostrarFormParaAdicionar(Model modelo) {
            
            Cliente oCliente = new Cliente();
            
            modelo.addAttribute("cliente", oCliente);
            
            return "cliente-form";
        }
        
        @PostMapping("/salvarCliente")
        public String salvarCliente(@ModelAttribute("cliente") Cliente oCliente) {
            
            clienteService.salvarCliente(oCliente);
            
            return "redirect:/cliente/lista";
            
        }
        
        @GetMapping("/mostrarFormParaAtualizar")
        public String mostrarFormParaAtualizar(@RequestParam("clienteId") int oId, Model modelo) {
            
            Cliente oCliente = clienteService.getCliente(oId);
            
            modelo.addAttribute("cliente", oCliente);
            
            return "cliente-form";
            
        }
        
        @GetMapping("/deletar")
        public String deletarCliente(@RequestParam("clienteId") int oId) {
            
            clienteService.deletarCliente(oId);
            
            return "redirect:/cliente/lista";
            
        }
        
        @GetMapping("/buscar")
        public String buscarClientes(@RequestParam("oNomeProcurado") String oNomeProcurado, Model modelo) {
            
            List<Cliente> osClientes = clienteService.buscarClientes(oNomeProcurado);
            
            modelo.addAttribute("clientes", osClientes);
            
            return "lista";
            
        }
        
    }

**ClienteDAO.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteDAO {
        
        public List<Cliente> getClientes(int ordemDoCampo);
        
        public void salvarCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
        public void deletarCliente(int oId);
    
        public List<Cliente> buscarClientes(String oNomeProcurado);
    
    }

**ClienteDAOImpl.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.query.Query;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.util.OrdenarUtil;
    
    @Repository
    public class ClienteDAOImpl implements ClienteDAO {
        
        @Autowired
        private SessionFactory sessionFactory;
    
        @Override
        public List<Cliente> getClientes(int ordemDoCampo) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            String oNomeDoCampo = null;
            
            switch(ordemDoCampo) {
                case OrdenarUtil.NOME:
                    oNomeDoCampo = "nome";
                    break;
                case OrdenarUtil.SOBRENOME:
                    oNomeDoCampo = "sobrenome";
                    break;
                case OrdenarUtil.EMAIL:
                    oNomeDoCampo = "email";
                    break;
                default:
                    oNomeDoCampo = "nome";
            }
            
            String customQuery = "from Cliente order by " + oNomeDoCampo;
            
            System.out.println(customQuery); // DELETEEEEEEEEE
            
            Query<Cliente> aQuery = sessionAtual.createQuery(customQuery, Cliente.class);
            
            List<Cliente> clientes = aQuery.getResultList();
            
            return clientes;
        }
    
        @Override
        public void salvarCliente(Cliente oCliente) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            sessionAtual.saveOrUpdate(oCliente); // Olha essa atualização especial que fizemos aqui
            
        }
    
        @Override
        public Cliente getCliente(int oId) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Cliente oCliente = sessionAtual.get(Cliente.class, oId);
            
            return oCliente;
        }
    
        @Override
        public void deletarCliente(int oId) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query oQuery = sessionAtual.createQuery("delete from Cliente where id=:clienteId");
            
            oQuery.setParameter("clienteId", oId);
            
            oQuery.executeUpdate();
            
        }
    
        @Override
        public List<Cliente> buscarClientes(String oNomeProcurado) {
            
            Session sessionAtual = sessionFactory.getCurrentSession();
            
            Query oQuery = null;
            
            if (oNomeProcurado != null && oNomeProcurado.trim().length() > 0) {
                oQuery = sessionAtual.createQuery("from Cliente where lower(nome) like :oNome or lower(sobrenome) like :oNome", Cliente.class);
                oQuery.setParameter("oNome", "%" + oNomeProcurado.toLowerCase() + "%"); // % são "wildcard characters"
            }
            else {
                // O query está vazio, portanto pegue todos os clientes
                oQuery = sessionAtual.createQuery("from Cliente", Cliente.class);
            }
            
            List<Cliente> clientes = oQuery.getResultList();
            
            return clientes;
        }
    
    }

**ClienteService.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteService {
        
        public List<Cliente> getClientes(int ordemDoCampo);
        
        public void salvarCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
        public void deletarCliente(int oId);
    
        public List<Cliente> buscarClientes(String oNomeProcurado);
    
    }

**ClienteServiceImpl.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    import org.springframework.transaction.annotation.Transactional;
    
    import dominio.springmvchb.dao.ClienteDAO;
    import dominio.springmvchb.entity.Cliente;
    
    @Service
    public class ClienteServiceImpl implements ClienteService {
        
        @Autowired
        private ClienteDAO clienteDAO;
    
        @Override
        @Transactional
        public List<Cliente> getClientes(int ordemDoCampo) {
            return clienteDAO.getClientes(ordemDoCampo);
        }
    
        @Override
        @Transactional
        public void salvarCliente(Cliente oCliente) {
            clienteDAO.salvarCliente(oCliente);        
        }
    
        @Override
        @Transactional
        public Cliente getCliente(int oId) {
            return clienteDAO.getCliente(oId);
        }
    
        @Override
        @Transactional
        public void deletarCliente(int oId) {
            clienteDAO.deletarCliente(oId);  
            
        }
    
        @Override
        @Transactional
        public List<Cliente> buscarClientes(String oNomeProcurado) {
            // TODO Auto-generated method stub
            return clienteDAO.buscarClientes(oNomeProcurado);
        }
    
    }

**OrdenarUtil.java**

    package dominio.springmvchb.util;
    
    public interface OrdenarUtil {
    
        public static final int NOME = 1;
        public static final int SOBRENOME = 2;
        public static final int EMAIL = 3;
    
    }

Se você quiser saber como adicionar suporte a "Programação orientada a aspecto" (AOP) neste projeto, vá para [este subcapítulo](#aop_springmvc).

# Programação orientada a aspecto<span id="aop"></span>

Programação orientada a aspecto *(ou “Aspect-oriented programming” (AOP), em inglês)*

Para aplicar o AOP, você pode usar o Spring AOP ou o AspectJ, cada um tem suas vantagens e desvantagens, só que mesmo que você use o Spring AOP, você ainda precisará baixar os arquivos JAR do AspectJ porque o Spring AOP usa algumas *annotations* e classes do AspectJ.

Ah, a propósito, desta vez configuraremos nosso projeto usando apenas código Java, nada de XML. 🙂

Baixe os JARs do Spring que você já sabe onde achar.
 
Baixe os JARs do AspectJ, aqui o [link](https://mvnrepository.com/artifact/org.aspectj/aspectjweaver).

Dê o nome que você quiser ao projeto (*Java Project* normal mesmo), chamarei o meu de `spring-aop`. Na pasta `src`, crie os pacotes `dominio.aop` e `dominio.aop.dao`. Em `dominio.aop.dao`, crie a classe `ContaDAO`:

    package dominio.aop.dao;
    
    import org.springframework.stereotype.Component;
    
    @Component // Eu poderia ter colocado @Repository aqui, mas como não mexeremos com nenhum banco de dados, @Component é o suficiente
    public class ContaDAO {
    
        public void adicionarConta() {
            System.out.println(getClass() + "realizando o trabalho de Banco de Dados. Adicionando conta");
        }
    
    }

 Em `dominio.aop`, crie:

**MeuProjetoConfig.java**

    package dominio.aop;
    
    import org.springframework.context.annotation.ComponentScan;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.context.annotation.EnableAspectJAutoProxy;
    
    @Configuration
    @EnableAspectJAutoProxy // Assim Spring AOP pode usar Proxy Support
    @ComponentScan("dominio.aop")
    public class MeuProjetoConfig {
    
    }

**App.java**

    package dominio.aop;
    
    import org.springframework.context.annotation.AnnotationConfigApplicationContext;
    
    import dominio.aop.dao.ContaDAO;
    
    public class App {
    
        public static void main(String[] args) {
            
            AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(MeuProjetoConfig.class);
            
            ContaDAO aContaDAO = context.getBean("contaDAO", ContaDAO.class);
            
            aContaDAO.adicionarConta();
            
            context.close();
    
        }
    
    }

Crie o pacote `dominio.aop.aspect` e dentro dele crie:

**MeuLoggingAspect.java**

    package dominio.aop.aspect;
    
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.springframework.stereotype.Component;
    
    @Aspect
    @Component // Pra ser descoberto pelo @ComponentScan
    public class MeuLoggingAspect {
        
        @Before("execution(public void adicionarConta())") // Rode este código ANTES da execução do método adicionarConta(), esta é uma Pointcut expression
        public void beforeAdicionarConta() { // Este método poderia ter qualquer nome
            
            System.out.println("\n>> Executando método @Before adicionarConta()");
        }
    
    }

Vamos conhecer logo de antemão cada uma das *annotations*:

| Annotation      | Descrição                                                 |
| --------------- | --------------------------------------------------------- |
| @Before         | Roda antes do método                                      |
| @After *(finally)* | Roda depois do método, indendentemente de sucesso ou erro |
| @AfterReturning | Roda depois do método retornar um resultado *(ou seja, uma execução feita com sucesso)*, que é interceptado |
| @AfterThrowing  | Roda depois do método se uma exceção for lançada, ou seja, somente se houver um erro |
| @Around         | Roda em volta da execução do método, ou seja, roda antes e depois do método, é praticamente uma combinação de `@Before` e `@After` |

## Expressões Pointcut<span id="aop_pointcutexpressions"></span>

Em `@Before("execution(public void adicionarConta())")`, aponto para o método `adicionarConta()` de **qualquer** classe, se eu quisesse ser mais específico essa linha seria `@Before("execution(public void dominio.aop.dao.ContaDAO.adicionarConta())")`.

Também posso usar "coringas", por exemplo, `@Before("execution(public void adicionar*())")` será usado para qualquer método que comece com `public void adicionar`. Se eu quiser pra qualquer tipo, eu poderia colocar `@Before("execution(public * adicionar*())")`, até mesmo o modificador poder ser qualquer um por meio de `@Before("execution(* adicionar*())")`.

O mesmo é aplicado a argumentos:

* `()`: Corresponde a métodos com nenhum argumento, foi o que estávamos usando

* `(*)`: Corresponde a métodos com um argumento de qualquer tipo

* `(..)`: Corresponde a métodos com 0 ou mais argumentos de qualquer tipo

## Declarações Pointcut<span id="aop_pointcutdeclarations"></span>

E se quisermos reutilizar uma expressão pointcut para aplicar a múltiplos *advices*?

Eu poderia copiar e colar:

    [...]
    
    @Before("execution(* dominio.aop.dao.*.*(..))")
    public void beforeAdicionarConta() {
        [...]
    }
    
    @Before("execution(* dominio.aop.dao.*.*(..))")
    public void fazerAnalise() {
        [...]
    }
    
    [...]

Não é a forma ideal, o certo é criar uma única expressão pointcut e utilizá-la pra diferentes *advices*.

    [...]
    
    @Pointcut("execution(* dominio.aop.dao.*.*(..))")
    private void paraOPacoteDao() {}
    
    @Before("paraOPacoteDao()")
    public void beforeAdicionarConta() {
        [...]
    }
    
    @Before("paraOPacoteDao()")
    public void fazerAnalise() {
        [...]
    }
    
    [...]

OK, no pacote `dominio.aop.dao`, crie o arquivo `FiliacaoDAO.java`:

    package dominio.aop.dao;
    
    import org.springframework.stereotype.Component;
    
    @Component
    public class FiliacaoDAO {
        
        public void adicionarMembro() {
            System.out.println(getClass() + "adicionarMembro()");
        }
        
        public void listarMembros() {
            System.out.println(getClass() + "listarMembros()");
        }
    
    }

E atualize os seguintes arquivos:

**ContaDAO.java**

    package dominio.aop.dao;
    
    import org.springframework.stereotype.Component;
    
    @Component
    public class ContaDAO {
    
        public void adicionarConta() {
            System.out.println(getClass() + "realizando o trabalho de Banco de Dados. Adicionando conta");
        }
        
        public void facaUmTrabalho() {
            System.out.println(getClass() + "facaUmTrabalho()");
        }
    
    }

**MeuLoggingAspect.java**

    package dominio.aop.aspect;
    
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.aspectj.lang.annotation.Pointcut;
    import org.springframework.stereotype.Component;
    
    @Aspect
    @Component
    public class MeuLoggingAspect {
        
        @Pointcut("execution(* dominio.aop.dao.*.*(..))")
        private void paraOPacoteDao() {} // Sim, a sintaxe é essa mesmo
        
        @Before("paraOPacoteDao()")
        public void beforeAdicionarConta() {
            
            System.out.println("\n>> Executando advice @Before no método");
        }
        
        @Before("paraOPacoteDao()")
        public void fazerAnalise() {
            
            System.out.println("\n>> Realizando análise");
        }
    
    }

**App.java**

    package dominio.aop;
    
    import org.springframework.context.annotation.AnnotationConfigApplicationContext;
    
    import dominio.aop.dao.ContaDAO;
    import dominio.aop.dao.FiliacaoDAO;
    
    public class App {
    
        public static void main(String[] args) {
            
            AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(MeuProjetoConfig.class);
            
            ContaDAO aContaDAO = context.getBean("contaDAO", ContaDAO.class);
            FiliacaoDAO aFiliacaoDAO = context.getBean("filiacaoDAO", FiliacaoDAO.class);
            
            aContaDAO.adicionarConta();
            aContaDAO.facaUmTrabalho();
            
            aFiliacaoDAO.adicionarMembro();
            aFiliacaoDAO.listarMembros();
            
            context.close();
    
        }
    
    }

Agora aprenderemos como aplicar múltiplas expressões *poincut* para um único *advice*. No nosso exemplos, aplicaremos os advices em tudo, exceto nos *getters* e *setters*. Atualize os arquivos abaixo:

**ContaDAO.java**

    package dominio.aop.dao;
    
    import org.springframework.stereotype.Component;
    
    @Component
    public class ContaDAO {
        
        private String nome;
        private String codigo;
    
        public void adicionarConta() {
            System.out.println(getClass() + " em adicionarConta()");
        }
        
        public void facaUmTrabalho() {
            System.out.println(getClass() + " em facaUmTrabalho()");
        }
    
        public String getNome() {
            System.out.println(getClass() + " em getNome()");
            return nome;
        }
    
        public void setNome(String nome) {
            System.out.println(getClass() + " em setNome()");
            this.nome = nome;
        }
    
        public String getCodigo() {
            System.out.println(getClass() + " em getCodigo()");
            return codigo;
        }
    
        public void setCodigo(String codigo) {
            System.out.println(getClass() + " em setCodigo()");
            this.codigo = codigo;
        }
        
    }

**MeuLoggingAspect.java**

    package dominio.aop.aspect;
    
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.aspectj.lang.annotation.Pointcut;
    import org.springframework.stereotype.Component;
    
    @Aspect
    @Component
    public class MeuLoggingAspect {
        
        @Pointcut("execution(* dominio.aop.dao.*.*(..))")
        private void paraOPacoteDao() {}
        
        // Cria pointcut para métodos get
        @Pointcut("execution(* dominio.aop.dao.*.get*(..))")
        private void getter() {} // De novo, você pode usar o nome que quiser
        
        // Cria pointcut para métodos set
        @Pointcut("execution(* dominio.aop.dao.*.set*(..))")
        private void setter() {} // De novo, você pode usar o nome que quiser
        
        // Inclui paraOPacoteDao() mas esclui os getters e setters
        @Pointcut("paraOPacoteDao() && !(getter() || setter())")
        private void paraOPacoteDaoSemGettersESettes() {}
        
        @Before("paraOPacoteDaoSemGettersESettes()")
        public void beforeAdicionarConta() {
            
            System.out.println("\n>> Executando advice @Before no método");
        }
        
        @Before("paraOPacoteDaoSemGettersESettes()")
        public void fazerAnalise() {
            
            System.out.println(">> Realizando análise");
        }
    
    }

**App.java**

    package dominio.aop;
    
    import org.springframework.context.annotation.AnnotationConfigApplicationContext;
    
    import dominio.aop.dao.ContaDAO;
    import dominio.aop.dao.FiliacaoDAO;
    
    public class App {
    
        public static void main(String[] args) {
            
            AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(MeuProjetoConfig.class);
            
            ContaDAO aContaDAO = context.getBean("contaDAO", ContaDAO.class);
            FiliacaoDAO aFiliacaoDAO = context.getBean("filiacaoDAO", FiliacaoDAO.class);
            
            aContaDAO.adicionarConta();
            aContaDAO.facaUmTrabalho();
            
            System.out.println("-----------");
            
            aContaDAO.setNome("Conta Corrente");
            aContaDAO.setCodigo("88888");
            
            System.out.println("-----------");
            
            
            System.out.println(aContaDAO.getNome());
            System.out.println(aContaDAO.getCodigo());
            
            System.out.println("-----------");
            
            aFiliacaoDAO.adicionarMembro();
            aFiliacaoDAO.listarMembros();
            
            context.close();
    
        }
    
    }

## Aspects de ordenação<span id="aop_orderingaspects"></span>

Como controlar a ordem nas quais os *advices* são aplicados. Para fazer isso, teremos que pôr os *advices* em diferentes *aspects*, ou seja, teremos que refatorar nosso código.

Mexeremos apenas nos arquivos do pacote `dominio.aop.aspect`, editaremos qu que existe e criaremos outros novos:

**MeuLoggingAspect.java**

    package dominio.aop.aspect;
    
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.springframework.core.annotation.Order;
    import org.springframework.stereotype.Component;
    
    @Aspect
    @Component
    @Order(1)
    public class MeuLoggingAspect {
        
        @Before("dominio.aop.aspect.ExpressoesAop.paraOPacoteDaoSemGettersESetters()") // Como estão em arquivos separados, preciso fornecer o "fully qualified name"
        public void beforeAdicionarConta() {
            
            System.out.println("\n>> Executando advice @Before no método");
        }
    
    }

**MinhaAnaliseDeApiAspect.java**

    package dominio.aop.aspect;
    
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.springframework.core.annotation.Order;
    import org.springframework.stereotype.Component;
    
    @Aspect
    @Component
    @Order(2)
    public class MinhaAnaliseDeApiAspect {
    
        @Before("dominio.aop.aspect.ExpressoesAop.paraOPacoteDaoSemGettersESetters()")
        public void fazerAnalise() {
            
            System.out.println(">> Realizando análise");
        }
        
    }

**MinhaLogNuvemAspect.java**

    package dominio.aop.aspect;
    
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.springframework.core.annotation.Order;
    import org.springframework.stereotype.Component;
    
    @Aspect
    @Component
    @Order(3)
    public class MinhaLogNuvemAspect {
        
        @Before("dominio.aop.aspect.ExpressoesAop.paraOPacoteDaoSemGettersESetters()")
        public void logarNaNuvem() {
            
            System.out.println(">> logando na núvem");
        }
    
    }

**ExpressoesAop.java**

    package dominio.aop.aspect;
    
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Pointcut;
    
    @Aspect
    public class ExpressoesAop {
    
        @Pointcut("execution(* dominio.aop.dao.*.*(..))")
        public void paraOPacoteDao() {}
        
        @Pointcut("execution(* dominio.aop.dao.*.get*(..))")
        public void getter() {}
        
        @Pointcut("execution(* dominio.aop.dao.*.set*(..))")
        public void setter() {}
        
        @Pointcut("paraOPacoteDao() && !(getter() || setter())")
        public void paraOPacoteDaoSemGettersESetters() {}
        
    }

Sobre as *annotations* `@Order()`, você pode colocar quaisquer números, não precisa ser uma sequência certinha e os números podem ser negativos, eu poderia ter assim: `@Order(-237)`, `@Order(0)` e `@Order(8)`.

## JoinPoints<span id="aop_joinpoints"></span>

Quando estamos em um *aspect*, como podemos acessar os parâmetros dos métodos. Pra isso usamos o `JoinPoint` que contém os metadados sobre a chamada do método.

No pacote `dominio.aop`, crie o arquivo `Conta.java`:

    package dominio.aop;
    
    public class Conta {
    
        private String nome;
        private String nivel;
        
        public String getNome() {
            return nome;
        }
        public void setNome(String nome) {
            this.nome = nome;
        }
        public String getNivel() {
            return nivel;
        }
        public void setNivel(String nivel) {
            this.nivel = nivel;
        }
    }

Atualize os arquivos abaixo:

**ContaDAO.java**

    package dominio.aop.dao;
    
    import org.springframework.stereotype.Component;
    
    import dominio.aop.Conta;
    
    @Component
    public class ContaDAO {
        
        private String nome;
        private String codigo;
    
        public void adicionarConta(Conta aConta, boolean vip) {
            System.out.println(getClass() + " em adicionarConta()");
        }
        
        public void facaUmTrabalho() {
            System.out.println(getClass() + " em facaUmTrabalho()");
        }
    
        public String getNome() {
            System.out.println(getClass() + " em getNome()");
            return nome;
        }
    
        public void setNome(String nome) {
            System.out.println(getClass() + " em setNome()");
            this.nome = nome;
        }
    
        public String getCodigo() {
            System.out.println(getClass() + " em getCodigo()");
            return codigo;
        }
    
        public void setCodigo(String codigo) {
            System.out.println(getClass() + " em setCodigo()");
            this.codigo = codigo;
        }
        
    }

**MeuLoggingAspect.java**

    package dominio.aop.aspect;
    
    import org.aspectj.lang.JoinPoint;
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.aspectj.lang.reflect.MethodSignature;
    import org.springframework.core.annotation.Order;
    import org.springframework.stereotype.Component;
    
    import dominio.aop.Conta;
    
    @Aspect
    @Component
    @Order(1)
    public class MeuLoggingAspect {
        
        @Before("dominio.aop.aspect.ExpressoesAop.paraOPacoteDaoSemGettersESetters()")
        public void beforeAdicionarConta(JoinPoint oJoinPoint) {
            
            System.out.println("\n>> Executando advice @Before no método");
            
            // Mostra o método de assinatura
            MethodSignature methodSig = (MethodSignature) oJoinPoint.getSignature();
            System.out.println("Método: " + methodSig);
            
            // Mostra os argumentos do método
            Object[] args = oJoinPoint.getArgs();
            
            for (Object argTemp : args) {
                
                System.out.println("Argumento: " + argTemp);
                
                if (argTemp instanceof Conta) {
                    // Faz downcast e printa apenas coisas da casse Conta
                    Conta aConta = (Conta) argTemp;
                    
                    System.out.println("Nome da conta: " + aConta.getNome());
                    System.out.println("Nível da conta: " + aConta.getNivel());                
                }            
            }
        }
    }

**App.java**

    package dominio.aop;
    
    import org.springframework.context.annotation.AnnotationConfigApplicationContext;
    
    import dominio.aop.dao.ContaDAO;
    import dominio.aop.dao.FiliacaoDAO;
    
    public class App {
    
        public static void main(String[] args) {
            
            AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(MeuProjetoConfig.class);
            
            ContaDAO aContaDAO = context.getBean("contaDAO", ContaDAO.class);
            FiliacaoDAO aFiliacaoDAO = context.getBean("filiacaoDAO", FiliacaoDAO.class);
            
            System.out.println("-----------");
            
            Conta minhaConta = new Conta();
            minhaConta.setNome("Luiza");
            minhaConta.setNivel("Bronze");
            
            System.out.println("-----------");
            
            aContaDAO.adicionarConta(minhaConta, true);
            aContaDAO.facaUmTrabalho();
            
            System.out.println("-----------");
            
            aContaDAO.setNome("foobar");
            aContaDAO.setCodigo("888888");
            
            System.out.println("-----------");
            
            aFiliacaoDAO.adicionarMembro();
            aFiliacaoDAO.listarMembros();
            
            context.close();
    
        }
    
    }

## @AfterReturning<span id="aop_afterreturning"></span>

Não explicarei sobre esse porque você já sabe o seu conceito, então vamos ver quais arquivos atualizar:

**Conta.java**

    package dominio.aop;
    
    public class Conta {
    
        private String nome;
        private String nivel;
        
        public Conta() {
            
        }
        
        public Conta(String nome, String nivel) {
            this.nome = nome;
            this.nivel = nivel;
        }
    
        public String getNome() {
            return nome;
        }
        public void setNome(String nome) {
            this.nome = nome;
        }
        public String getNivel() {
            return nivel;
        }
        public void setNivel(String nivel) {
            this.nivel = nivel;
        }
    
        @Override
        public String toString() {
            return "Conta [nome=" + nome + ", nivel=" + nivel + "]";
        }
    }

**ContaDAO.java**

    package dominio.aop.dao;
    
    import java.util.ArrayList;
    import java.util.List;
    
    import org.springframework.stereotype.Component;
    
    import dominio.aop.Conta;
    
    @Component
    public class ContaDAO {
        
        private String nome;
        private String codigo;
        
        public List<Conta> encontrarContas() {
            List<Conta> minhasContas = new ArrayList<>();
            
            Conta contaTemp1 = new Conta("Thiago", "Prata");
            Conta contaTemp2 = new Conta("Carla", "Ouro");
            Conta contaTemp3 = new Conta("Maria", "Bronze");
            
            minhasContas.add(contaTemp1);
            minhasContas.add(contaTemp2);
            minhasContas.add(contaTemp3);
            
            return minhasContas;
        }
    
        public void adicionarConta(Conta aConta, boolean vip) {
            System.out.println(getClass() + " em adicionarConta()");
        }
        
        public void facaUmTrabalho() {
            System.out.println(getClass() + " em facaUmTrabalho()");
        }
    
        public String getNome() {
            System.out.println(getClass() + " em getNome()");
            return nome;
        }
    
        public void setNome(String nome) {
            System.out.println(getClass() + " em setNome()");
            this.nome = nome;
        }
    
        public String getCodigo() {
            System.out.println(getClass() + " em getCodigo()");
            return codigo;
        }
    
        public void setCodigo(String codigo) {
            System.out.println(getClass() + " em setCodigo()");
            this.codigo = codigo;
        }
        
    }

**MeuLoggingAspect.java**

    package dominio.aop.aspect;
    
    import java.util.List;
    
    import org.aspectj.lang.JoinPoint;
    import org.aspectj.lang.annotation.AfterReturning;
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.aspectj.lang.reflect.MethodSignature;
    import org.springframework.core.annotation.Order;
    import org.springframework.stereotype.Component;
    
    import dominio.aop.Conta;
    
    @Aspect
    @Component
    @Order(1)
    public class MeuLoggingAspect {
        
        @AfterReturning(
                pointcut="execution(* dominio.aop.dao.ContaDAO.encontrarContas(..))",
                returning="resultado")
        public void afterReturningEncontrarContasAdvice (JoinPoint oJoinPoint, List<Conta> resultado) { // esse resultado se relaciona com o returning="resultado" de @AfterReturning 
            
            String metodo = oJoinPoint.getSignature().toShortString();
            
            System.out.println(">> Executando @AfterReturning no método: " + metodo);
            System.out.println(">> O resultado é: " + resultado);
            
            // Vamos fazer um pós-processamento do dado
            converterNomesDasContasParaMaiusculas(resultado);
            
            System.out.println("------- Após modificação -------");
            
            System.out.println(">> O resultado é: " + resultado);
        }
        
        private void converterNomesDasContasParaMaiusculas(List<Conta> resultado) {
            
            for (Conta contaTemp : resultado) {
                String maiuscula = contaTemp.getNome().toUpperCase();
                contaTemp.setNome(maiuscula);
            }
        }
    
        @Before("dominio.aop.aspect.ExpressoesAop.paraOPacoteDaoSemGettersESetters()")
        public void beforeAdicionarConta(JoinPoint oJoinPoint) {
            
            System.out.println("\n>> Executando advice @Before no método");
            
            // Mostra o método de assinatura
            MethodSignature methodSig = (MethodSignature) oJoinPoint.getSignature();
            System.out.println("Método: " + methodSig);
            
            // Mostra os argumentos do método
            Object[] args = oJoinPoint.getArgs();
            
            for (Object argTemp : args) {
                
                System.out.println("Argumento: " + argTemp);
                
                if (argTemp instanceof Conta) {
                    // Faz downcast e printa apenas coisas da casse Conta
                    Conta aConta = (Conta) argTemp;
                    
                    System.out.println("Nome da conta: " + aConta.getNome());
                    System.out.println("Nível da conta: " + aConta.getNivel());                
                }            
            }
        }
    
    }

**App.java**

    package dominio.aop;
    
    import java.util.List;
    
    import org.springframework.context.annotation.AnnotationConfigApplicationContext;
    
    import dominio.aop.dao.ContaDAO;
    
    public class App {
    
        public static void main(String[] args) {
            
            AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(MeuProjetoConfig.class);
            
            ContaDAO aContaDAO = context.getBean("contaDAO", ContaDAO.class);
            
            List<Conta> asContas = aContaDAO.encontrarContas(); // Esta linha corresponderá ao advice do @AfterReturning, o @AfterReturning intercepta o resultado de encontrarContas() e, se programado assim, modifica o resultado antes deste chegar em asContas
            
            System.out.println("=====================");
            
            System.out.println(asContas);
            
            System.out.println("\n");
            
            context.close();
    
        }
    
    }

## @AfterThrowing<span id="aop_afterthrowing"></span>

Eis os arquivos que você precisa atualizar:

**ContaDAO.java**

    package dominio.aop.dao;
    
    import java.util.ArrayList;
    import java.util.List;
    
    import org.springframework.stereotype.Component;
    
    import dominio.aop.Conta;
    
    @Component
    public class ContaDAO {
        
        private String nome;
        private String codigo;
        
        public List<Conta> encontrarContas(boolean tripWire) {
            // For academic purposes, vamos simular uma exceção aqui
            if (tripWire == true) {
                throw new RuntimeException("Seu programa vai dar erro. Há! Há! Há!");
            }
            
            List<Conta> minhasContas = new ArrayList<>();
            
            Conta contaTemp1 = new Conta("Thiago", "Prata");
            Conta contaTemp2 = new Conta("Carla", "Ouro");
            Conta contaTemp3 = new Conta("Maria", "Bronze");
            
            minhasContas.add(contaTemp1);
            minhasContas.add(contaTemp2);
            minhasContas.add(contaTemp3);
            
            return minhasContas;
        }
    
        public void adicionarConta(Conta aConta, boolean vip) {
            System.out.println(getClass() + " em adicionarConta()");
        }
        
        public void facaUmTrabalho() {
            System.out.println(getClass() + " em facaUmTrabalho()");
        }
    
        public String getNome() {
            System.out.println(getClass() + " em getNome()");
            return nome;
        }
    
        public void setNome(String nome) {
            System.out.println(getClass() + " em setNome()");
            this.nome = nome;
        }
    
        public String getCodigo() {
            System.out.println(getClass() + " em getCodigo()");
            return codigo;
        }
    
        public void setCodigo(String codigo) {
            System.out.println(getClass() + " em setCodigo()");
            this.codigo = codigo;
        }
        
    }

**MeuLoggingAspect.java**

    package dominio.aop.aspect;
    
    import java.util.List;
    
    import org.aspectj.lang.JoinPoint;
    import org.aspectj.lang.annotation.AfterReturning;
    import org.aspectj.lang.annotation.AfterThrowing;
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.aspectj.lang.reflect.MethodSignature;
    import org.springframework.core.annotation.Order;
    import org.springframework.stereotype.Component;
    
    import dominio.aop.Conta;
    
    @Aspect
    @Component
    @Order(1)
    public class MeuLoggingAspect {
        
        @AfterThrowing(
                pointcut="execution(* dominio.aop.dao.ContaDAO.encontrarContas(..))",
                throwing="aExcecao")
        public void afterThrowingEncontrarContasAdvice (JoinPoint oJoinPoint, Throwable aExcecao) {
            
            String metodo = oJoinPoint.getSignature().toShortString();
            
            System.out.println(">> Executando @AfterThrowing no método: " + metodo);
            System.out.println(">> A exceção é: " + aExcecao);
        }
        
        @AfterReturning(
                pointcut="execution(* dominio.aop.dao.ContaDAO.encontrarContas(..))",
                returning="resultado")
        public void afterReturningEncontrarContasAdvice (JoinPoint oJoinPoint, List<Conta> resultado) { 
            
            String metodo = oJoinPoint.getSignature().toShortString();
            
            System.out.println(">> Executando @AfterReturning no método: " + metodo);
            System.out.println(">> O resultado é: " + resultado);
            
            // Vamos fazer um pós-processamento do dado
            converterNomesDasContasParaMaiusculas(resultado);
            
            System.out.println("------- Após modificação -------");
            
            System.out.println(">> O resultado é: " + resultado);
        }
        
        private void converterNomesDasContasParaMaiusculas(List<Conta> resultado) {
            
            for (Conta contaTemp : resultado) {
                String maiuscula = contaTemp.getNome().toUpperCase();
                contaTemp.setNome(maiuscula);
            }
        }
    
        @Before("dominio.aop.aspect.ExpressoesAop.paraOPacoteDaoSemGettersESetters()")
        public void beforeAdicionarConta(JoinPoint oJoinPoint) {
            
            System.out.println("\n>> Executando advice @Before no método");
            
            // Mostra o método de assinatura
            MethodSignature methodSig = (MethodSignature) oJoinPoint.getSignature();
            System.out.println("Método: " + methodSig);
            
            // Mostra os argumentos do método
            Object[] args = oJoinPoint.getArgs();
            
            for (Object argTemp : args) {
                
                System.out.println("Argumento: " + argTemp);
                
                if (argTemp instanceof Conta) {
                    // Faz downcast e printa apenas coisas da casse Conta
                    Conta aConta = (Conta) argTemp;
                    
                    System.out.println("Nome da conta: " + aConta.getNome());
                    System.out.println("Nível da conta: " + aConta.getNivel());                
                }            
            }
        }
    
    }

**App.java**

    package dominio.aop;
    
    import java.util.List;
    
    import org.springframework.context.annotation.AnnotationConfigApplicationContext;
    
    import dominio.aop.dao.ContaDAO;
    
    public class App {
    
        public static void main(String[] args) {
            
            AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(MeuProjetoConfig.class);
            
            ContaDAO aContaDAO = context.getBean("contaDAO", ContaDAO.class);
            
            List<Conta> asContas = null;
    
            try {
                // Será adicionada uma flag booleana para simular uma exceção
                boolean tripWire = true;
                
                asContas = aContaDAO.encontrarContas(tripWire);
            }
            catch (Exception exc) {
                System.out.println("Exceção pega: " + exc);
            }
            
            System.out.println("=====================");
            
            System.out.println(asContas);
            
            System.out.println("\n");
            
            context.close();
    
        }
    
    }

A propósito, `List<Conta>` é *null* por causa da exceção.

## @After<span id="aop_after"></span>

O `@After` roda independente do método ter tido sucesso ou erro. É como se numa relação `try-catch`, o `@After` fosse o `finally`.

~Entretanto, o `@After` roda antes do `@AfterThrowing`.~ Isso não é mais verdade após a atualização do Spring 5.2.7 *(lançado em 9 de junho de 2020)*, é o contrário agora, o *advice* `@After` é invocado após qualquer *advice* `@AfterReturning` ou `@AfterThrowing` da mesma classe *aspect*.

OK, vejamos os arquivos que precisamos editar:

**MeuLoggingAspect.java**

    package dominio.aop.aspect;
    
    import java.util.List;
    
    import org.aspectj.lang.JoinPoint;
    import org.aspectj.lang.annotation.After;
    import org.aspectj.lang.annotation.AfterReturning;
    import org.aspectj.lang.annotation.AfterThrowing;
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.aspectj.lang.reflect.MethodSignature;
    import org.springframework.core.annotation.Order;
    import org.springframework.stereotype.Component;
    
    import dominio.aop.Conta;
    
    @Aspect
    @Component
    @Order(1)
    public class MeuLoggingAspect {
        
        @After("execution(* dominio.aop.dao.ContaDAO.encontrarContas(..))")
        public void afterFinallyEncontrarContasAdvice (JoinPoint oJoinPoint) {
            
            String metodo = oJoinPoint.getSignature().toShortString();
            
            System.out.println(">> Executando @After( Finally) no método: " + metodo);
            
        }
        
        @AfterThrowing(
                pointcut="execution(* dominio.aop.dao.ContaDAO.encontrarContas(..))",
                throwing="aExcecao")
        public void afterThrowingEncontrarContasAdvice (JoinPoint oJoinPoint, Throwable aExcecao) {
            
            String metodo = oJoinPoint.getSignature().toShortString();
            
            System.out.println(">> Executando @AfterThrowing no método: " + metodo);
            System.out.println(">> A exceção é: " + aExcecao);
        }
        
        @AfterReturning(
                pointcut="execution(* dominio.aop.dao.ContaDAO.encontrarContas(..))",
                returning="resultado")
        public void afterReturningEncontrarContasAdvice (JoinPoint oJoinPoint, List<Conta> resultado) { 
            
            String metodo = oJoinPoint.getSignature().toShortString();
            
            System.out.println(">> Executando @AfterReturning no método: " + metodo);
            System.out.println(">> O resultado é: " + resultado);
            
            // Vamos fazer um pós-processamento do dado
            converterNomesDasContasParaMaiusculas(resultado);
            
            System.out.println("------- Após modificação -------");
            
            System.out.println(">> O resultado é: " + resultado);
        }
        
        private void converterNomesDasContasParaMaiusculas(List<Conta> resultado) {
            
            for (Conta contaTemp : resultado) {
                String maiuscula = contaTemp.getNome().toUpperCase();
                contaTemp.setNome(maiuscula);
            }
        }
    
        @Before("dominio.aop.aspect.ExpressoesAop.paraOPacoteDaoSemGettersESetters()")
        public void beforeAdicionarConta(JoinPoint oJoinPoint) {
            
            System.out.println("\n>> Executando advice @Before no método");
            
            // Mostra o método de assinatura
            MethodSignature methodSig = (MethodSignature) oJoinPoint.getSignature();
            System.out.println("Método: " + methodSig);
            
            // Mostra os argumentos do método
            Object[] args = oJoinPoint.getArgs();
            
            for (Object argTemp : args) {
                
                System.out.println("Argumento: " + argTemp);
                
                if (argTemp instanceof Conta) {
                    // Faz downcast e printa apenas coisas da casse Conta
                    Conta aConta = (Conta) argTemp;
                    
                    System.out.println("Nome da conta: " + aConta.getNome());
                    System.out.println("Nível da conta: " + aConta.getNivel());                
                }            
            }
        }
    }

**App.java**

    package dominio.aop;
    
    import java.util.List;
    
    import org.springframework.context.annotation.AnnotationConfigApplicationContext;
    
    import dominio.aop.dao.ContaDAO;
    
    public class App {
    
        public static void main(String[] args) {
            
            AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(MeuProjetoConfig.class);
            
            ContaDAO aContaDAO = context.getBean("contaDAO", ContaDAO.class);
            
            List<Conta> asContas = null;
    
            try {
                // Será adicionada uma flag booleana para simular uma exceção
                boolean tripWire = true;
                
                asContas = aContaDAO.encontrarContas(tripWire);
            }
            catch (Exception exc) {
                System.out.println("Exceção pega: " + exc);
            }
            
            System.out.println("=====================");
            
            System.out.println(asContas);
            
            System.out.println("\n");
            
            context.close();
    
        }
    
    }

## @Around<span id="aop_around"></span>

Crie o pacote `dominio.aop.service` e dentro dele crie o arquivo `TrafegoFortunaService.java`:

    package dominio.aop.service;
    
    import java.util.concurrent.TimeUnit;
    
    import org.springframework.stereotype.Component;
    
    @Component // Eu poderia ter usado @Service aqui, mas como @Service é subclasse de @Component, não tem problema
    public class TrafegoFortunaService {
        
        public String getFortuna() {
            
            // Simula um delay
            try {
                TimeUnit.SECONDS.sleep(5);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            
            // Retorna a fortuna
            return "O trânsito estará bom quando você voltar pra casa";
        }
    
    }

E atualize os seguintes arquivos:

**MeuLoggingAspect.java**

    package dominio.aop.aspect;
    
    import java.util.List;
    
    import org.aspectj.lang.JoinPoint;
    import org.aspectj.lang.ProceedingJoinPoint;
    import org.aspectj.lang.annotation.After;
    import org.aspectj.lang.annotation.AfterReturning;
    import org.aspectj.lang.annotation.AfterThrowing;
    import org.aspectj.lang.annotation.Around;
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.aspectj.lang.reflect.MethodSignature;
    import org.springframework.core.annotation.Order;
    import org.springframework.stereotype.Component;
    
    import dominio.aop.Conta;
    
    @Aspect
    @Component
    @Order(1)
    public class MeuLoggingAspect {
        
        @Around("execution(* dominio.aop.service.*.getFortuna(..))")
        public Object aroundGetFortuna(ProceedingJoinPoint oProceedingJoinPoint) throws Throwable {
            
            String metodo = oProceedingJoinPoint.getSignature().toShortString();
            
            System.out.println(">> Executando @Around no método: " + metodo);
            
            long inicio = System.currentTimeMillis();
            
            Object resultado = oProceedingJoinPoint.proceed(); // proceed() executa o método alvo
            
            long fim = System.currentTimeMillis();
            
            long duracao = fim - inicio;
            System.out.println("\nO método levou " + duracao / 1000 + " segundos para ser executado");
            
            return resultado;
        }
        
        @After("execution(* dominio.aop.dao.ContaDAO.encontrarContas(..))")
        public void afterFinallyEncontrarContasAdvice (JoinPoint oJoinPoint) {
            
            String metodo = oJoinPoint.getSignature().toShortString();
            
            System.out.println(">> Executando @After( Finally) no método: " + metodo);
            
        }
        
        @AfterThrowing(
                pointcut="execution(* dominio.aop.dao.ContaDAO.encontrarContas(..))",
                throwing="aExcecao")
        public void afterThrowingEncontrarContasAdvice (JoinPoint oJoinPoint, Throwable aExcecao) {
            
            String metodo = oJoinPoint.getSignature().toShortString();
            
            System.out.println(">> Executando @AfterThrowing no método: " + metodo);
            System.out.println(">> A exceção é: " + aExcecao);
        }
        
        @AfterReturning(
                pointcut="execution(* dominio.aop.dao.ContaDAO.encontrarContas(..))",
                returning="resultado")
        public void afterReturningEncontrarContasAdvice (JoinPoint oJoinPoint, List<Conta> resultado) { 
            
            String metodo = oJoinPoint.getSignature().toShortString();
            
            System.out.println(">> Executando @AfterReturning no método: " + metodo);
            System.out.println(">> O resultado é: " + resultado);
            
            // Vamos fazer um pós-processamento do dado
            converterNomesDasContasParaMaiusculas(resultado);
            
            System.out.println("------- Após modificação -------");
            
            System.out.println(">> O resultado é: " + resultado);
        }
        
        private void converterNomesDasContasParaMaiusculas(List<Conta> resultado) {
            
            for (Conta contaTemp : resultado) {
                String maiuscula = contaTemp.getNome().toUpperCase();
                contaTemp.setNome(maiuscula);
            }
        }
    
        @Before("dominio.aop.aspect.ExpressoesAop.paraOPacoteDaoSemGettersESetters()")
        public void beforeAdicionarConta(JoinPoint oJoinPoint) {
            
            System.out.println("\n>> Executando advice @Before no método");
            
            // Mostra o método de assinatura
            MethodSignature methodSig = (MethodSignature) oJoinPoint.getSignature();
            System.out.println("Método: " + methodSig);
            
            // Mostra os argumentos do método
            Object[] args = oJoinPoint.getArgs();
            
            for (Object argTemp : args) {
                
                System.out.println("Argumento: " + argTemp);
                
                if (argTemp instanceof Conta) {
                    // Faz downcast e printa apenas coisas da casse Conta
                    Conta aConta = (Conta) argTemp;
                    
                    System.out.println("Nome da conta: " + aConta.getNome());
                    System.out.println("Nível da conta: " + aConta.getNivel());                
                }            
            }
        }
    }

**App.java**

    package dominio.aop;
    
    import org.springframework.context.annotation.AnnotationConfigApplicationContext;
    
    import dominio.aop.service.TrafegoFortunaService;
    
    public class App {
    
        public static void main(String[] args) {
            
            AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(MeuProjetoConfig.class);
            
            TrafegoFortunaService oTrafegoFortunaService = context.getBean("trafegoFortunaService", TrafegoFortunaService.class);
            
            String dados = oTrafegoFortunaService.getFortuna();
            
            System.out.println("\nMinha fortuna é: " + dados);
            
            System.out.println("FIM");
            
            context.close();
    
        }
    
    }

## AOP no Spring MVC<span id="aop_springmvc"></span>

Mude Eclipse para a perspectiva do Java EE. Agora abra aquele projeto que fizemos no capítulo do Spring MVC e Hibernate; se você não tiver mais os arquivos, você pode ver o código-font completo [aqui](#springmvchibernate_full).

Adicione o arquivo JAR do AspectJ neste projeto.

E rode o projeto pra ver se está tudo funcionando OK. *Não se esqueça de iniciar o MySQL...*

### Arquivo XML<span id="aop_springmvc_configxml"></span>

Abra o arquivo `webapp/WEB-INF/spring-mvc.xml` e adicione as linhas referentesao AOP. Ficará assim:

    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:context="http://www.springframework.org/schema/context"
        xmlns:tx="http://www.springframework.org/schema/tx"
        xmlns:mvc="http://www.springframework.org/schema/mvc"
        xmlns:aop="http://www.springframework.org/schema/aop"
        xsi:schemaLocation="
            http://www.springframework.org/schema/beans
            http://www.springframework.org/schema/beans/spring-beans.xsd
            http://www.springframework.org/schema/context
            http://www.springframework.org/schema/context/spring-context.xsd
            http://www.springframework.org/schema/mvc
            http://www.springframework.org/schema/mvc/spring-mvc.xsd
            http://www.springframework.org/schema/tx 
            http://www.springframework.org/schema/tx/spring-tx.xsd
            http://www.springframework.org/schema/aop
            http://www.springframework.org/schema/aop/spring-aop.xsd">
    
        <!-- Add AspectJ autoproxy support for AOP -->
        <aop:aspectj-autoproxy />
        
        <!-- Add support for component scanning -->
        <context:component-scan base-package="dominio.springmvchb" />
    
        <!-- Add support for conversion, formatting and validation support -->
        <mvc:annotation-driven/>
    
        <!-- Define Spring MVC view resolver -->
        <bean
            class="org.springframework.web.servlet.view.InternalResourceViewResolver">
            <property name="prefix" value="/WEB-INF/view/" />
            <property name="suffix" value=".jsp" />
        </bean>
    
        <!-- Step 1: Define Database DataSource / connection pool -->
        <bean id="myDataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource"
              destroy-method="close">
            <property name="driverClass" value="com.mysql.cj.jdbc.Driver" />
            <property name="jdbcUrl" value="jdbc:mysql://localhost:3306/cliente_web?useSSL=false" />
            <property name="user" value="estudante" />
            <property name="password" value="estudante" /> 
    
            <!-- these are connection pool properties for C3P0 -->
            <property name="minPoolSize" value="5" />
            <property name="maxPoolSize" value="20" />
            <property name="maxIdleTime" value="30000" />
        </bean>  
        
        <!-- Step 2: Setup Hibernate session factory -->
        <bean id="sessionFactory"
            class="org.springframework.orm.hibernate5.LocalSessionFactoryBean">
            <property name="dataSource" ref="myDataSource" />
            <property name="packagesToScan" value="dominio.springmvchb.entity" />
            <property name="hibernateProperties">
               <props>
                  <prop key="hibernate.dialect">org.hibernate.dialect.MySQLDialect</prop>
                  <prop key="hibernate.show_sql">true</prop>
               </props>
            </property>
       </bean>      
    
        <!-- Step 3: Setup Hibernate transaction manager -->
        <bean id="myTransactionManager"
                class="org.springframework.orm.hibernate5.HibernateTransactionManager">
            <property name="sessionFactory" ref="sessionFactory"/>
        </bean>
        
        <!-- Step 4: Enable configuration of transactional behavior based on annotations -->
        <tx:annotation-driven transaction-manager="myTransactionManager" />
        
        <!-- Add support for web resources -->
        <mvc:resources location="/resources/" mapping="/resources/**"></mvc:resources> <!-- O ** diz que é pra incluir os sub-diretórios -->
    
    </beans>

A propósito, se você fizesse a configuração via arquivos Java, sem XML, você usaria `@EnableAspectJAutoProxy`.

### Aspect<span id="aop_springmvc_aspect"></span>

Crie o pacote `dominio.springmvchb.aspect` e dentro dele crie a classe `CRMLoggingAspect`

    package dominio.springmvchb.aspect;
    
    import java.util.logging.Logger;
    
    import org.aspectj.lang.JoinPoint;
    import org.aspectj.lang.annotation.AfterReturning;
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    import org.aspectj.lang.annotation.Pointcut;
    import org.springframework.stereotype.Component;
    
    @Aspect
    @Component
    public class CRMLoggingAspect {
        
        // Configurar logger
        private Logger logger = Logger.getLogger(getClass().getName()); // Logging é uma API que permite aos usuários rastrear o erro gerado a partir de classes específicas. O getLogger é um método estático presente na classe Logger que cria um logger se não estiver presente no sistema com o nome fornecido
        
        // Configurar declarações pointcut para Controller
        @Pointcut("execution(* dominio.springmvchb.controller.*.*(..))")
        private void paraPacoteDeController() {}
        
        // Configurar declarações pointcut para Service
        @Pointcut("execution(* dominio.springmvchb.service.*.*(..))")
        private void paraPacoteDeService() {}
        
        // Configurar declarações pointcut para DAO
        @Pointcut("execution(* dominio.springmvchb.dao.*.*(..))")
        private void paraPacoteDeDao() {}
        
        // Combino os pointcuts aqui
        @Pointcut("paraPacoteDeController() || paraPacoteDeService() || paraPacoteDeDao()")
        private void paraFluxoDoApp() {}
        
        // Adicionar advice @Before
        @Before("paraFluxoDoApp()")
        public void before(JoinPoint joinPoint) {
            
            // Exibe o método que estamos chamando
            String method = joinPoint.getSignature().toShortString();
            
            // Exibe os argumentos do método
            logger.info("=======>> em @Before, é chamado o método: " + method);
            
            // Pega os aergumentos
            Object[] args = joinPoint.getArgs();
            
            // Faz um loop e exibe os argumentos
            for (Object argTemp : args) {
                logger.info(">>>>>>>>> em @Before, é usado o argumento: " + argTemp);
            }
        }
        
        // Adicionar advice @AfterReturning
        @AfterReturning(
                pointcut="paraFluxoDoApp()",
                returning="resultado")
        public void afterReturning(JoinPoint joinPoint, Object resultado) {
            
            // Exibe o método do qual estamos retornando
            String method = joinPoint.getSignature().toShortString();
            
            // Exibe os argumentos do método
            logger.info("=======>> em @AfterReturning, é retornado o método: " + method);
            
            // Exibe o resultado
            logger.info("=======>> Resultado: " + resultado);
            
        }
    
    }

# Spring Security<span id="springsecurit"></span>

A partir de agora usaremos o Maven, que baixa as dependências pra você e as coloca na pasta `m2`, esta pasta fica:

* No Windows: `C:\Users\<seu_nome_de_usuário>\.m2` ou `C:\Documents and Settings\<seu_nome_de_usuário>\.m2`

	* É claro que você terá que trocar o `<seu_nome_de_usuário>` pelo seu nome de usuário, né? Estou mostrando isso, porque se você tiver qualquer problema, você saberá onde a pasta `m2` está localizada

* No Linux ou MacOS: `~/.m2`

No Eclipse, mude para a perspectiva do Java EE.

`File` => `New` => `Maven Project`

Marque a opção para criar um projeto simples. Clique em `Next`

Em *Group Id* ponha `dominio`

Em *Artifact Id* ponha `springsecurity`

## Instalação e configuração do Spring Framework<span id="springsecurit_installconfigspringframework"></span>

Edite o arquivo `pom.xml` para que ele fique assim:

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
      <modelVersion>4.0.0</modelVersion>
      <groupId>dominio</groupId>
      <artifactId>springsecurity</artifactId>
      <version>0.0.1-SNAPSHOT</version>
      <packaging>war</packaging>
      
      <name>springsecurity</name>
      
      <properties>
            <springframework.version>5.3.20</springframework.version>
    
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
      </properties>
      
      <dependencies>
    
            <!-- Spring MVC support -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-webmvc</artifactId>
                <version>${springframework.version}</version>
            </dependency>
    
            <!-- Servlet, JSP and JSTL support -->
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>javax.servlet-api</artifactId>
                <version>3.1.0</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet.jsp</groupId>
                <artifactId>javax.servlet.jsp-api</artifactId>
                <version>2.3.1</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>jstl</artifactId>
                <version>1.2</version>
            </dependency>
    
            <!-- to compensate for java 9+ not including jaxb -->
            <dependency>
                <groupId>javax.xml.bind</groupId>
                <artifactId>jaxb-api</artifactId>
                <version>2.3.0</version>
            </dependency>
    
            <dependency>
                <groupId>junit</groupId>
                <artifactId>junit</artifactId>
                <version>3.8.1</version>
                <scope>test</scope>
            </dependency>
    
        </dependencies>
        
        <!-- Add support for Maven WAR Plugin -->
        
        <build>
            <finalName>springsecurity</finalName>
            <pluginManagement>
                <plugins>
                    <!-- Add Maven coordinates for> maven-war-plugin -->
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-war-plugin</artifactId>
                        <version>3.3.2</version>
                    </plugin>
                </plugins>
            </pluginManagement>
        </build>
      
    </project>

Você pode mudar a versão do Java e do [Spring](https://search.maven.org/search?q=g%3Aorg.springframework) se você quiser.

O arquivo `pom.xml` foi testado, se você encontrar qualquer problema, alguma mensagem de erro ou algo do tipo, tente deletar a pasta `m2`.

Na pasta `src/main/java`, crie o pacote `dominio.springsecurity.config` e dentro dele crie a classe `MinhaAppConfig.java`:

    package dominio.springsecurity.config;
    
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.ComponentScan;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.web.servlet.ViewResolver;
    import org.springframework.web.servlet.config.annotation.EnableWebMvc;
    import org.springframework.web.servlet.view.InternalResourceViewResolver;
    
    @Configuration
    @EnableWebMvc // Fornece suporte similar de <mvc:annotation-driven>
    @ComponentScan(basePackages="dominio.springsecurity")
    public class MinhaAppConfig {
        
        @Bean
        public ViewResolver viewResolver () {
            
            InternalResourceViewResolver viewResolver = new InternalResourceViewResolver();
            
            viewResolver.setPrefix("/WEB-INF/view/");
            viewResolver.setSuffix(".jsp");
            
            return viewResolver;
        }
    
    }

Criaremos outra classe neste pacote, mas este exige uma atenção especial no momento da sua criação. Comece a criar uma classe nesse pacote (o nome será `MeuSpringMvcDispatcherServletInitializer`), mas mude o conteúdo de *Superclass:*, clique em `Browser` e pesquise por `AbstractAnnotationConfigDispatcherServletInitializer`.

    package dominio.springsecurity.config;
    
    import org.springframework.web.servlet.support.AbstractAnnotationConfigDispatcherServletInitializer;
    
    public class MeuSpringMvcDispatcherServletInitializer extends AbstractAnnotationConfigDispatcherServletInitializer {
    
        @Override
        protected Class<?>[] getRootConfigClasses() { // Não teremos arquivos de configuração root no nosso projeto
            // TODO Auto-generated method stub
            return null;
        }
    
        @Override
        protected Class<?>[] getServletConfigClasses() {
    
            return new Class[] {MinhaAppConfig.class};
        }
    
        @Override
        protected String[] getServletMappings() {
    
            return new String[] { "/" };
        }
    
    }

Agora crie o pacote `dominio.springsecurity.controller` e dentro dele crie a classe `Controller`:

    package dominio.springsecurity.controller;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.GetMapping;
    
    @Controller
    public class MeuController {
        
        @GetMapping("/")
        public String mostrarHome() {        
            return "home";        
        }
    
    }

Finalmente podemos criar nosso arquivo JSP, crie o arquivo `home.jsp` dentro da pasta `/springsecurity/src/main/webapp/WEB-INF/view` *(talvez o Maven só tenha criado até a pasta `/springsecurity/src/main/webapp/`, então crie o que estiver faltando...)*:

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring Security</title>
    </head>
    <body>
    
        <p>Olá mundo</p>
    
    </body>
    </html>

Ponha o projeto pra "Run on server" pra ver se está tudo rodando direito.

## Instalação do Spring Security<span id="springsecurit_installspringsecurity"></span>

Vendo que está tudo OK, vamos instalar as dependências do Spring Security.

* [spring-security-web](https://mvnrepository.com/artifact/org.springframework.security/spring-security-web)

Para evitar problemas de incompatibilidade *(nem sempre as versões estão sintonizadas...)*, olhe para o arquivo `pom.xml` do projeto `spring-security-web`. No meu exemplo, eu estava usando a versão 5.3.20 do Spring Framework, mas a última versão do Spring Security *(a 5.6.3 na época que escrevi este tutorial)* suportava a 5.3.19. Pode ser que o Spring Security 5.6.3 seja compatível com o Spring Framework 5.3.20. Vamos atualizar nosso arquivo `pom.xml`

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>dominio</groupId>
        <artifactId>springsecurity</artifactId>
        <version>0.0.1-SNAPSHOT</version>
        <packaging>war</packaging>
    
        <name>springsecurity</name>
    
        <properties>
            <springframework.version>5.3.19</springframework.version>
            <springsecurity.version>5.6.3</springsecurity.version>
    
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
        </properties>
    
        <dependencies>
    
            <!-- Spring Framework -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-webmvc</artifactId>
                <version>${springframework.version}</version>
            </dependency>
    
            <!-- Spring Security -->
            <dependency>
                <groupId>org.springframework.security</groupId>
                <artifactId>spring-security-web</artifactId>
                <version>${springsecurity.version}</version>
            </dependency>
    
            <dependency>
                <groupId>org.springframework.security</groupId>
                <artifactId>spring-security-config</artifactId>
                <version>${springsecurity.version}</version>
            </dependency>
    
            <!-- Servlet, JSP and JSTL support -->
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>javax.servlet-api</artifactId>
                <version>3.1.0</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet.jsp</groupId>
                <artifactId>javax.servlet.jsp-api</artifactId>
                <version>2.3.1</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>jstl</artifactId>
                <version>1.2</version>
            </dependency>
    
            <!-- to compensate for java 9+ not including jaxb -->
            <dependency>
                <groupId>javax.xml.bind</groupId>
                <artifactId>jaxb-api</artifactId>
                <version>2.3.0</version>
            </dependency>
    
            <dependency>
                <groupId>junit</groupId>
                <artifactId>junit</artifactId>
                <version>3.8.1</version>
                <scope>test</scope>
            </dependency>
    
        </dependencies>
    
        <!-- Add support for Maven WAR Plugin -->
    
        <build>
            <finalName>springsecurity</finalName>
            <pluginManagement>
                <plugins>
                    <!-- Add Maven coordinates for> maven-war-plugin -->
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-war-plugin</artifactId>
                        <version>3.3.2</version>
                    </plugin>
                </plugins>
            </pluginManagement>
        </build>
    
    </project>

## Configuração do Spring Security<span id="springsecurit_config"></span>

No pacote `dominio.springsecurity.config`, comece a criar a classe chamada `SecurityWebApplicationInitializer`, mas antes de finalizar, vá em *Superclass* e procure por `AbstractSecurityWebApplicationInitializer`:

    package dominio.springsecurity.config;
    
    import org.springframework.security.web.context.AbstractSecurityWebApplicationInitializer;
    
    public class SecurityWebApplicationInitializer extends AbstractSecurityWebApplicationInitializer {
    
    }

Nesse mesmo pacote, repita o mesmo procedimento com a criação da classe chamada `MeuSecurityConfig` em que você selecionará a *Superclass* `WebSecurityConfigurerAdapter`:

    package dominio.springsecurity.config;
    
    import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;

    public class MeuSecurityConfig extends WebSecurityConfigurerAdapter {
    
    }

Nessa última classe adicione as anotações `@Configuration` e `@EnableWebSecurity` e dentro da classe clique com o botão direito do mouse => `Source` => `Override/Implement methods`. Selecione:

* configure(AuthenticationManagerBuilder)

Deixaremos nosso arquivo `MeuSecurityConfig.java` assim:

    package dominio.springsecurity.config;
    
    import org.springframework.context.annotation.Configuration;
    import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
    import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
    import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
    import org.springframework.security.core.userdetails.User;
    import org.springframework.security.core.userdetails.User.UserBuilder;
    
    @Configuration
    @EnableWebSecurity
    public class MeuSecurityConfig extends WebSecurityConfigurerAdapter {
    
        @Override
        protected void configure(AuthenticationManagerBuilder auth) throws Exception {
            
            // Adicionaremos alguns usuários em hard code mode para teste
            
            UserBuilder usuarios = User.withDefaultPasswordEncoder(); // Sim, withDefaultPasswordEncoder está marcado como obsoleto, mas serve para o nosso teste
            
            auth.inMemoryAuthentication()
                .withUser(usuarios.username("João").password("12345").roles("FUNCIONARIO"))
                .withUser(usuarios.username("Maria").password("12345").roles("GERENTE"))
                .withUser(usuarios.username("Thiago").password("12345").roles("DIRETOR"));
        }
    
    }

Tente rodar como servidor. *Todo o código está correto, se ocorrer qualquer erro e você tiver certeza que seguiu os passos corretamente, tente selecionar o servidor do Tomcat (na aba `Servers`) e selecione `Clean...`*

Você verá uma tela de login criada pelo próprio Spring.

## Tela de login customizada<span id="springsecurit_login"></span>

Abra o arquivo `MeuSecurityConfig.java`, depois do método existente lá, clique com o botão direito do mouse sobre o editor de texto => `Source` => `Override/Implement Methods...`. Selecione `configure(HttpSecurity)`.

    package dominio.springsecurity.config;
    
    import org.springframework.context.annotation.Configuration;
    import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
    import org.springframework.security.config.annotation.web.builders.HttpSecurity;
    import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
    import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
    import org.springframework.security.core.userdetails.User;
    import org.springframework.security.core.userdetails.User.UserBuilder;
    
    @Configuration
    @EnableWebSecurity
    public class MeuSecurityConfig extends WebSecurityConfigurerAdapter {
    
        @Override
        protected void configure(AuthenticationManagerBuilder auth) throws Exception {
            
            UserBuilder usuarios = User.withDefaultPasswordEncoder();
            
            auth.inMemoryAuthentication()
                .withUser(usuarios.username("João").password("12345").roles("FUNCIONARIO"))
                .withUser(usuarios.username("Maria").password("12345").roles("GERENTE"))
                .withUser(usuarios.username("Thiago").password("12345").roles("DIRETOR"));
        }
    
        @Override
        protected void configure(HttpSecurity http) throws Exception { // Configuramos os caminhos web aqui
            http.authorizeRequests()
                .anyRequest().authenticated() // Toda requisição ao aplicativo deve ser autenticado
                .and()
                .formLogin().loginPage("/paginaDeLogin") // O parâmetro desta linha e da próxima tem que ser compatível com os nomes do Controller
                .loginProcessingUrl("/autenticaUsuario")
                .permitAll(); // Até porque o ususário precisa pelo menos ter acesso à página de login...
        }
        
    }

Vá no pacote `dominio.springsecurity.controller` e crie a classe `LoginController`:

    package dominio.springsecurity.controller;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.GetMapping;
    
    @Controller
    public class LoginController {
    
        @GetMapping("/paginaDeLogin")
        public String paginaDeLogin() {
            return "login";
        }
    }

Agora crie o arquivo `login.jsp` na pasta `webapp/WEB-INF/view`:

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Página de Login</title>
    </head>
    <body>
        <h3>Página de login</h3>
        
        <form:form action="${pageContext.request.contextPath}/autenticaUsuario" method="POST">
        
            <p>
                <!-- Você tem que usar exatamente esse valor para o name -->
                Nome de usuário: <input type="text" name="username" />
            </p>
            
            <p>
                <!-- Você tem que usar exatamente esse valor para o name -->
                Senha: <input type="password" name="password" />
            </p>
            <!-- Não usamos o <.form.:.input./> (coloquei pontos porque, mesmo dentro de um comentário, estava bagunçando com o Spring) porque só usamos essa tag do Spring quando usamos o Spring MVC Data Binding com @ModelAttribute -->
            <input type="submit" value="Login" />
        
        </form:form>
        
    </body>
    </html>

**Pronto, você já pode testar!**

Só um toque, o Spring já faz muita coisa por você, então se você fizer login, fecha a aba e abrir de novo (ainda que você tenha reiniciado o servidor), você já virá logado. Nesses casso, você pode ir testando através do uso de janelas anônimas. 

Nossa página de login não apresenta mensagens de erro quando inserimos logins ou senhas incorretos, vamos corrigir isso.

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
    
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Página de Login</title>
    </head>
    <body>
        <h3>Página de login</h3>
        
        <form:form action="${pageContext.request.contextPath}/autenticaUsuario" method="POST">
        
            <c:if test="${param.error != null}">
                <i>Login ou senha inválidos</i>
            </c:if>
        
            <p>
                <!-- Você tem que usar exatamente esse valor para o name -->
                Nome de usuário: <input type="text" name="username" />
            </p>
            
            <p>
                <!-- Você tem que usar exatamente esse valor para o name -->
                Senha: <input type="password" name="password" />
            </p>
            <!-- Não usamos o <.form.:.input./> (coloquei pontos porque, mesmo dentro de um comentário, estava bagunçando com o Spring) porque só usamos essa tag do Spring quando usamos o Spring MVC Data Binding com @ModelAttribute -->
            <input type="submit" value="Login" />
        
        </form:form>
        
    </body>
    </html>

## Logout<span id="springsecurit_logout"></span>

**MeuSecurityConfig.java**

    package dominio.springsecurity.config;
    
    import org.springframework.context.annotation.Configuration;
    import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
    import org.springframework.security.config.annotation.web.builders.HttpSecurity;
    import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
    import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
    import org.springframework.security.core.userdetails.User;
    import org.springframework.security.core.userdetails.User.UserBuilder;
    
    @Configuration
    @EnableWebSecurity
    public class MeuSecurityConfig extends WebSecurityConfigurerAdapter {
    
        @Override
        protected void configure(AuthenticationManagerBuilder auth) throws Exception {
            
            UserBuilder usuarios = User.withDefaultPasswordEncoder();
            
            auth.inMemoryAuthentication()
                .withUser(usuarios.username("João").password("12345").roles("FUNCIONARIO"))
                .withUser(usuarios.username("Maria").password("12345").roles("GERENTE"))
                .withUser(usuarios.username("Thiago").password("12345").roles("DIRETOR"));
        }
    
        @Override
        protected void configure(HttpSecurity http) throws Exception {
            http.authorizeRequests()
                .anyRequest().authenticated()
                .and()
                    .formLogin().loginPage("/paginaDeLogin")
                    .loginProcessingUrl("/autenticaUsuario")
                    .permitAll()
                .and()
                    .logout()
                    .permitAll();
            
        }
        
    }

Quando mandamos dados para a URL padrão `/logout`, o método *GET* é desabilitado por padrão.

**login.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
    
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <title>Página de Login</title>
    </head>
    <body>
        <h3>Página de login</h3>
        
        <form:form action="${pageContext.request.contextPath}/autenticaUsuario" method="POST">
        
            <c:if test="${param.error != null}">
                <i>Login ou senha inválidos</i>
            </c:if>
            
            <c:if test="${param.logout != null}">
                <i>Você foi deslogado</i>
            </c:if>
        
            <p>
                Nome de usuário: <input type="text" name="username" />
            </p>
            
            <p>
                Senha: <input type="password" name="password" />
            </p>
            
            <input type="submit" value="Login" />
        
        </form:form>
        
    </body>
    </html>

**home.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring Security</title>
    </head>
    <body>
    
        <p>Olá mundo</p>
        
        <form:form action="${pageContext.request.contextPath}/logout" method="POST">
            <input type="submit" value="Logout" />
        </form:form>
    
    </body>
    </html>

## *Cross Site Request Forgery*<span id="springsecurit_csrf"></span>

*Cross Site Request Forgery* (ou simplesmente CSRF – se pronuncia como *see surf* –, como é comumente referenciado), é um ataque de segurança em que um site malicioso te engana para que você execute uma ação em uma aplicação web em que você está logado.

Quando usamos a proteção CSRF, devemos usar POST em vez de GET e sempre adicionar o *token* do CSRF na submissão do formulário. O `<form:form>` automaticamente adiciona esse *token*.

## Id de usuário e *role*<span id="springsecurit_userroles"></span>

Vamos pôr o ID e *roles* para serem exibidos na página:

**pom.xml**

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>dominio</groupId>
        <artifactId>springsecurity</artifactId>
        <version>0.0.1-SNAPSHOT</version>
        <packaging>war</packaging>
    
        <name>springsecurity</name>
    
        <properties>
            <springframework.version>5.3.19</springframework.version>
            <springsecurity.version>5.6.3</springsecurity.version>
    
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
        </properties>
    
        <dependencies>
    
            <!-- Spring Framework -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-webmvc</artifactId>
                <version>${springframework.version}</version>
            </dependency>
    
            <!-- Spring Security -->
            <dependency>
                <groupId>org.springframework.security</groupId>
                <artifactId>spring-security-web</artifactId>
                <version>${springsecurity.version}</version>
            </dependency>
    
            <dependency>
                <groupId>org.springframework.security</groupId>
                <artifactId>spring-security-config</artifactId>
                <version>${springsecurity.version}</version>
            </dependency>
            
            <dependency>
                <groupId>org.springframework.security</groupId>
                <artifactId>spring-security-taglibs</artifactId>
                <version>${springsecurity.version}</version>
            </dependency>
    
            <!-- Servlet, JSP and JSTL support -->
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>javax.servlet-api</artifactId>
                <version>3.1.0</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet.jsp</groupId>
                <artifactId>javax.servlet.jsp-api</artifactId>
                <version>2.3.1</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>jstl</artifactId>
                <version>1.2</version>
            </dependency>
    
            <!-- to compensate for java 9+ not including jaxb -->
            <dependency>
                <groupId>javax.xml.bind</groupId>
                <artifactId>jaxb-api</artifactId>
                <version>2.3.0</version>
            </dependency>
    
            <dependency>
                <groupId>junit</groupId>
                <artifactId>junit</artifactId>
                <version>3.8.1</version>
                <scope>test</scope>
            </dependency>
    
        </dependencies>
    
        <!-- Add support for Maven WAR Plugin -->
    
        <build>
            <finalName>springsecurity</finalName>
            <pluginManagement>
                <plugins>
                    <!-- Add Maven coordinates for> maven-war-plugin -->
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-war-plugin</artifactId>
                        <version>3.3.2</version>
                    </plugin>
                </plugins>
            </pluginManagement>
        </build>
    
    </project>

**home.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <%@ taglib prefix="security" uri="http://www.springframework.org/security/tags" %>
    
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring Security</title>
    </head>
    <body>
    
        <p>Olá mundo</p>
        
        <hr>
        
        <p>
            Nome de usuário: <security:authentication property="principal.username" />
        </p>
        <p>
            <i>Role</i>: <security:authentication property="principal.authorities" />
        </p>
        
        <hr>
        
        <form:form action="${pageContext.request.contextPath}/logout" method="POST">
            <input type="submit" value="Logout" />
        </form:form>
    
    </body>
    </html>

## Restrição de acesso baseado em *roles*<span id="springsecurit_restrictaccessrole"></span>

Atualize os seguintes arquivos:

**MeuSecurityConfig.java**

    package dominio.springsecurity.config;
    
    import org.springframework.context.annotation.Configuration;
    import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
    import org.springframework.security.config.annotation.web.builders.HttpSecurity;
    import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
    import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
    import org.springframework.security.core.userdetails.User;
    import org.springframework.security.core.userdetails.User.UserBuilder;
    
    @Configuration
    @EnableWebSecurity
    public class MeuSecurityConfig extends WebSecurityConfigurerAdapter {
    
        @Override
        protected void configure(AuthenticationManagerBuilder auth) throws Exception {
            
            UserBuilder usuarios = User.withDefaultPasswordEncoder();
            
            auth.inMemoryAuthentication()
                .withUser(usuarios.username("Marcos").password("12345").roles("FUNCIONARIO"))
                .withUser(usuarios.username("Maria").password("12345").roles("FUNCIONARIO", "GERENTE"))
                .withUser(usuarios.username("Thiago").password("12345").roles("FUNCIONARIO", "ADMINISTRADOR"));
        }
    
        @Override
        protected void configure(HttpSecurity http) throws Exception {
            http.authorizeRequests()
                .antMatchers("/").hasRole("FUNCIONARIO")
                .antMatchers("/lideres/**").hasRole("GERENTE")
                .antMatchers("/sistema/**").hasRole("ADMINISTRADOR")
                .and()
                    .formLogin().loginPage("/paginaDeLogin")
                    .loginProcessingUrl("/autenticaUsuario")
                    .permitAll()
                .and()
                    .logout()
                    .permitAll();
            
        }
        
    }

**MeuController.java**

    package dominio.springsecurity.controller;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.GetMapping;
    
    @Controller
    public class MeuController {
        
        @GetMapping("/")
        public String mostrarHome() {        
            return "home";        
        }
        
        @GetMapping("/lideres")
        public String mostrarLiders() {        
            return "lideres";        
        }
        
        @GetMapping("/sistema")
        public String mostrarSistema() {        
            return "sistema";        
        }
    
    }

**home.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <%@ taglib prefix="security" uri="http://www.springframework.org/security/tags" %>
    
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring Security</title>
    </head>
    <body>
    
        <p>Olá mundo</p>
        
        <hr>
        
        <p>
            Nome de usuário: <security:authentication property="principal.username" />
        </p>
        <p>
            <i>Role</i>: <security:authentication property="principal.authorities" />
        </p>
        
        <p>
            <a href="${pageContext.request.contextPath}/lideres">Reunião da gerência</a>
        </p>
        
        <p>
            <a href="${pageContext.request.contextPath}/sistema">Administração do sistema</a>
        </p>
        
        <hr>
        
        <form:form action="${pageContext.request.contextPath}/logout" method="POST">
            <input type="submit" value="Logout" />
        </form:form>
    
    </body>
    </html>

Dentro da pasta `webapp/WEB-INF/view`, crie os arquivos:

**lideres.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Reunião da gerência</title>
    </head>
    <body>
    
        <h1>Reunião da gerência</h1>
        
        <a href="${pageContext.request.contextPath}/">Retornar à página inicial</a>
    
    </body>
    </html>

**sistema.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Administração do sistema</title>
    </head>
    <body>
    
        <h1>Administração do sistema</h1>
        
        <a href="${pageContext.request.contextPath}/">Retornar à página inicial</a>
        
    </body>
    </html>

Faça testes com os 3 usuários. Quando você acessa uma página não autorizada, o próprio Spring promoverá uma página explicando o erro.

### Página customizada de acesso negado<span id="springsecurit_restrictaccessrole_accessdenied"></span>

**MeuSecurityConfig.java**

    package dominio.springsecurity.config;
    
    import org.springframework.context.annotation.Configuration;
    import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
    import org.springframework.security.config.annotation.web.builders.HttpSecurity;
    import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
    import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
    import org.springframework.security.core.userdetails.User;
    import org.springframework.security.core.userdetails.User.UserBuilder;
    
    @Configuration
    @EnableWebSecurity
    public class MeuSecurityConfig extends WebSecurityConfigurerAdapter {
    
        @Override
        protected void configure(AuthenticationManagerBuilder auth) throws Exception {
            
            UserBuilder usuarios = User.withDefaultPasswordEncoder();
            
            auth.inMemoryAuthentication()
                .withUser(usuarios.username("Marcos").password("12345").roles("FUNCIONARIO"))
                .withUser(usuarios.username("Maria").password("12345").roles("FUNCIONARIO", "GERENTE"))
                .withUser(usuarios.username("Thiago").password("12345").roles("FUNCIONARIO", "ADMINISTRADOR"));
        }
    
        @Override
        protected void configure(HttpSecurity http) throws Exception {
            http.authorizeRequests()
                .antMatchers("/").hasRole("FUNCIONARIO")
                .antMatchers("/lideres/**").hasRole("GERENTE")
                .antMatchers("/sistema/**").hasRole("ADMINISTRADOR")
                .and()
                    .formLogin().loginPage("/paginaDeLogin")
                    .loginProcessingUrl("/autenticaUsuario")
                    .permitAll()
                .and()
                    .logout()
                    .permitAll()
                .and()
                    .exceptionHandling()
                    .accessDeniedPage("/acessoNegado");
        }
        
    }

**LoginController.java**

    package dominio.springsecurity.controller;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.GetMapping;
    
    @Controller
    public class LoginController {
    
        @GetMapping("/paginaDeLogin")
        public String paginaDeLogin() {
            return "login";
        }
        
        @GetMapping("/acessoNegado")
        public String paginaacessoNegado() {
            return "acessonegado";
        }
    }

Dentro da pasta `webapp/WEB-INF/view`, crie o arquivo:

**acessonegado.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Acesso Negado</title>
    </head>
    <body>
        <h1>Acesso negado</h1>
        
        <p>Você não tem permissão para acessar esta página</p>
        
        <a href="${pageContext.request.contextPath}/">Retornar à página inicial</a>
    </body>
    </html>

### Exibição de conteúdo baseado nos *roles*<span id="springsecurit_restrictaccessrole_contentroles"></span>

Não faz sentido mostra os links "*Reunião da gerência*" e "*Administração do sistema*" para o usuário que não tem o direito de acesso a eles, então vamos corrigir isso.

Felizmente só precisamos editar 1 único arquivo:

**home.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <%@ taglib prefix="security" uri="http://www.springframework.org/security/tags" %>
    
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring Security</title>
    </head>
    <body>
    
        <p>Olá mundo</p>
        
        <hr>
        
        <p>
            Nome de usuário: <security:authentication property="principal.username" />
        </p>
        <p>
            <i>Role</i>: <security:authentication property="principal.authorities" />
        </p>
        
        <security:authorize access="hasRole('GERENTE')">
    	    <p>
    	        <a href="${pageContext.request.contextPath}/lideres">Reunião da gerência</a>
    	    </p>
        </security:authorize>
        
        <security:authorize access="hasRole('ADMINISTRADOR')">
    	    <p>
    	        <a href="${pageContext.request.contextPath}/sistema">Administração do sistema</a>
    	    </p>
        </security:authorize>
        
        <hr>
        
        <form:form action="${pageContext.request.contextPath}/logout" method="POST">
            <input type="submit" value="Logout" />
        </form:form>
    
    </body>
    </html>

## Autenticação de banco de dados JDBC<span id="springsecurit_jdbc"></span>

Nossos usuários estavam *hard coded* no aplicativo, vamos usar um banco de dados no lugar. O padrão é que você forneça duas tabelas, uma chamada `users` e outra chamada `authorities`. Exatamente esses nomes de tabelas e colunas:

    drop database if exists `springsecurity`;
    create database `springsecurity`;
    
    use `springsecurity`;

    create table users(
        username varchar(50) not null primary key,
        password varchar(50) not null,
        enabled boolean not null
    );
    
    create table authorities (
        username varchar(50) not null,
        authority varchar(50) not null,
        constraint fk_authorities_users foreign key(username) references users(username)
    );
    create unique index ix_auth_username on authorities (username,authority);

    insert into users values
        ("marcos", "{noop}12345", 1),
        ("maria", "{noop}12345", 1),
        ("thiago", "{noop}12345", 1);

    insert into authorities values
        ("marcos", "ROLE_FUNCIONARIO"),
        ("maria", "ROLE_FUNCIONARIO"),
        ("thiago", "ROLE_FUNCIONARIO"),
        ("maria", "ROLE_GERENTE"),
        ("thiago", "ROLE_ADMINISTRADOR");

`authorities` é o mesmo que *roles*.

Quando inserimos os usuários, podemos escolher como guardar as senhas:

| ID     | Descrição                      |
| ------ | ---------                      |
| noop   | Senhas em *plain text*         |
| bcrypt | *hashing* de senhas com BCrypt |

De início usamos `noop`.

Vamos editar agora o arquivo `pom.xml`:

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>dominio</groupId>
        <artifactId>springsecurity</artifactId>
        <version>0.0.1-SNAPSHOT</version>
        <packaging>war</packaging>
    
        <name>springsecurity</name>
    
        <properties>
            <springframework.version>5.3.19</springframework.version>
            <springsecurity.version>5.6.3</springsecurity.version>
    
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
        </properties>
    
        <dependencies>
    
            <!-- Spring Framework -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-webmvc</artifactId>
                <version>${springframework.version}</version>
            </dependency>
    
            <!-- Spring Security -->
            <dependency>
                <groupId>org.springframework.security</groupId>
                <artifactId>spring-security-web</artifactId>
                <version>${springsecurity.version}</version>
            </dependency>
    
            <dependency>
                <groupId>org.springframework.security</groupId>
                <artifactId>spring-security-config</artifactId>
                <version>${springsecurity.version}</version>
            </dependency>
    
            <dependency>
                <groupId>org.springframework.security</groupId>
                <artifactId>spring-security-taglibs</artifactId>
                <version>${springsecurity.version}</version>
            </dependency>
    
            <!-- Add MySQL and C3P0 support -->
            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>8.0.29</version>
            </dependency>
    
            <dependency>
                <groupId>com.mchange</groupId>
                <artifactId>c3p0</artifactId>
                <version>0.9.5.5</version>
            </dependency>
    
            <!-- Servlet, JSP and JSTL support -->
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>javax.servlet-api</artifactId>
                <version>3.1.0</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet.jsp</groupId>
                <artifactId>javax.servlet.jsp-api</artifactId>
                <version>2.3.1</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>jstl</artifactId>
                <version>1.2</version>
            </dependency>
    
            <!-- to compensate for java 9+ not including jaxb -->
            <dependency>
                <groupId>javax.xml.bind</groupId>
                <artifactId>jaxb-api</artifactId>
                <version>2.3.0</version>
            </dependency>
    
            <dependency>
                <groupId>junit</groupId>
                <artifactId>junit</artifactId>
                <version>3.8.1</version>
                <scope>test</scope>
            </dependency>
    
        </dependencies>
    
        <!-- Add support for Maven WAR Plugin -->
    
        <build>
            <finalName>springsecurity</finalName>
            <pluginManagement>
                <plugins>
                    <!-- Add Maven coordinates for> maven-war-plugin -->
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-war-plugin</artifactId>
                        <version>3.3.2</version>
                    </plugin>
                </plugins>
            </pluginManagement>
        </build>
    
    </project>

O C3P0 lida com o *Connection Pool*, fornece uma forma conveniente para o gerenciamento conexões de bancos de dados. Ele cria um *pool* de conexões, também lida cmo a limpeza de *Statements* e *ResultSets* após o uso, o que garante que o uso de recursos seja otimizado e que bloqueios evitáveis não ocorram. Esta biblioteca se integra muito bem com diversos drivers JDBC.

Dentro da pasta `src/main/resources`, crie o arquivo `persistence-mysql.properties` com o seguinte conteúdo:

    #
    # JDBC connection properties
    #
    jdbc.driver=com.mysql.cj.jdbc.Driver
    jdbc.url=jdbc:mysql://localhost:3306/springsecurity?useSSL=false&serverTimezone=UTC
    jdbc.user=estudante
    jdbc.password=estudante
    
    #
    # Connection pool properties
    #
    connection.pool.initialPoolSize=5
    connection.pool.minPoolSize=5
    connection.pool.maxPoolSize=20
    connection.pool.maxIdleTime=3000

A propósito, a pasta `src/main/resources` é justamente onde você guarda os arquivos de propriedades e configurações do aplicativo.

Edite o arquivo `MinhaAppConfig.java`:

    package dominio.springsecurity.config;
    
    import java.beans.PropertyVetoException;
    import java.util.logging.Logger;
    
    import javax.sql.DataSource;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.ComponentScan;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.context.annotation.PropertySource;
    import org.springframework.core.env.Environment;
    import org.springframework.web.servlet.ViewResolver;
    import org.springframework.web.servlet.config.annotation.EnableWebMvc;
    import org.springframework.web.servlet.view.InternalResourceViewResolver;
    
    import com.mchange.v2.c3p0.ComboPooledDataSource;
    
    @Configuration
    @EnableWebMvc
    @ComponentScan(basePackages="dominio.springsecurity")
    @PropertySource("classpath:persistence-mysql.properties") // Os arquivos de src/main/resources são automaticamente copiados para o classpath durante a build do Maven
    public class MinhaAppConfig {
        
        @Autowired // Environment env é autowired porque este Bean é automaticamente criado pelo Spring
        private Environment env; // env reterá os dados lidos pelo arquivo .properties
        
        private Logger logger = Logger.getLogger(getClass().getName()); // Não é obrigatório, é só para diagnóstico
            
        @Bean
        public ViewResolver viewResolver () {
            
            InternalResourceViewResolver viewResolver = new InternalResourceViewResolver();
            
            viewResolver.setPrefix("/WEB-INF/view/");
            viewResolver.setSuffix(".jsp");
            
            return viewResolver;
        }
        
        @Bean
        public DataSource securityDataSource() {
            
            // Cria um connection pool
            ComboPooledDataSource securityDataSource = new ComboPooledDataSource();
            
            // Define a classe de driver do JDBC
            try {
                securityDataSource.setDriverClass(env.getProperty("jdbc.driver"));
            } catch (PropertyVetoException e) {
                throw new RuntimeException(e);
            }
            
            // Faz log do connection props, só para termos certeza que estamos lendo dados do arquivo properties
            logger.info(">>> jdbc.url: " + env.getProperty("jdbc.driver"));
            logger.info(">>> jdbc.user: " + env.getProperty("jdbc.user"));
            
            // Define o connection props do banco de dados
            securityDataSource.setJdbcUrl(env.getProperty("jdbc.url"));
            securityDataSource.setUser(env.getProperty("jdbc.user"));
            securityDataSource.setPassword(env.getProperty("jdbc.password"));
            
            // Define o connection pool props
            securityDataSource.setInitialPoolSize(getIntProperty("connection.pool.initialPoolSize"));
            securityDataSource.setMinPoolSize(getIntProperty("connection.pool.minPoolSize"));
            securityDataSource.setMaxPoolSize(getIntProperty("connection.pool.maxPoolSize"));
            securityDataSource.setMaxIdleTime(getIntProperty("connection.pool.maxIdleTime"));
            
            return securityDataSource;
        }
        
        // Método para nos ajudar a ler o environment property e convertê-lo para int
        private  int getIntProperty(String propName) {
            String propVal = env.getProperty(propName);
            int intPropVal = Integer.parseInt(propVal);
            return intPropVal;
        }
    
    }

E edite o arquivo `MeuSecurityConfig.java`:

    package dominio.springsecurity.config;
    
    import javax.sql.DataSource;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
    import org.springframework.security.config.annotation.web.builders.HttpSecurity;
    import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
    import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
    import org.springframework.security.core.userdetails.User;
    import org.springframework.security.core.userdetails.User.UserBuilder;
    
    @Configuration
    @EnableWebSecurity
    public class MeuSecurityConfig extends WebSecurityConfigurerAdapter {
        
        @Autowired
        private DataSource securityDataSource;
    
        @Override
        protected void configure(AuthenticationManagerBuilder auth) throws Exception {
            
            // Fala para o Spring Security para usar a autenticação JDBC com nossa fonte de dados
            auth.jdbcAuthentication().dataSource(securityDataSource);
        }
    
        @Override
        protected void configure(HttpSecurity http) throws Exception {
            http.authorizeRequests()
                .antMatchers("/").hasRole("FUNCIONARIO")
                .antMatchers("/lideres/**").hasRole("GERENTE")
                .antMatchers("/sistema/**").hasRole("ADMINISTRADOR")
                .and()
                    .formLogin().loginPage("/paginaDeLogin")
                    .loginProcessingUrl("/autenticaUsuario")
                    .permitAll()
                .and()
                    .logout()
                    .permitAll()
                .and()
                    .exceptionHandling()
                    .accessDeniedPage("/acessoNegado");
        }
        
    }

### Encriptação de senha<span id="springsecurit_jdbc_crypt"></span>

A melhor prática é armazenar as senhas de forma criptografada. Vamos modificar nosso banco de dados:

    drop database if exists `springsecurity`;
    create database `springsecurity`;
    
    use `springsecurity`;
    
    drop table if exists `users`;
    create table users(
        username varchar(50) not null primary key,
        password varchar(68) not null,
        enabled boolean not null
    );
    
    create table authorities (
        username varchar(50) not null,
        authority varchar(50) not null,
        constraint fk_authorities_users foreign key(username) references users(username)
    );
    create unique index ix_auth_username on authorities (username,authority);
    
    insert into users values
        ("marcos", "{bcrypt}$2a$10$oZgySAH78tJ4VRQg9T8NCubIhwmI0k2KQBvATLSqrxY8HnJxcYXdu", 1),
        ("maria", "{bcrypt}$2a$10$oZgySAH78tJ4VRQg9T8NCubIhwmI0k2KQBvATLSqrxY8HnJxcYXdu", 1),
        ("thiago", "{bcrypt}$2a$10$oZgySAH78tJ4VRQg9T8NCubIhwmI0k2KQBvATLSqrxY8HnJxcYXdu", 1);
    
    insert into authorities values
        ("marcos", "ROLE_FUNCIONARIO"),
        ("maria", "ROLE_FUNCIONARIO"),
        ("thiago", "ROLE_FUNCIONARIO"),
        ("maria", "ROLE_GERENTE"),
        ("thiago", "ROLE_ADMINISTRADOR");

68 caracteres porque a `{bcrypt}` tem 8 caracteres e a encriptação da senha sempre tem 60 caracteres.

Já essa encriptação das senhas "12345" foi obtida por [este site](https://www.bcryptcalculator.com/).

E... é só isso, não precisamos editar mais nada 🙂

## BÔNUS: O projeto final<span id="springsecurit_final"></span>

No Eclipse, mude para a perspectiva do Java EE.

`File` => `New` => `Maven Project`

Marque a opção para criar um projeto simples. Clique em `Next`

Em *Group Id* ponha `dominio`

Em *Artifact Id* ponha `springsecurity`

Abra o MySQL e use a seguinte série de comandos:

    drop database if exists `springsecurity`;
    create database `springsecurity`;
    
    use `springsecurity`;
    
    drop table if exists `users`;
    create table users(
        username varchar(50) not null primary key,
        password varchar(68) not null,
        enabled boolean not null
    );
    
    create table authorities (
        username varchar(50) not null,
        authority varchar(50) not null,
        constraint fk_authorities_users foreign key(username) references users(username)
    );
    create unique index ix_auth_username on authorities (username,authority);
    
    insert into users values
        ("marcos", "{bcrypt}$2a$10$oZgySAH78tJ4VRQg9T8NCubIhwmI0k2KQBvATLSqrxY8HnJxcYXdu", 1),
        ("maria", "{bcrypt}$2a$10$oZgySAH78tJ4VRQg9T8NCubIhwmI0k2KQBvATLSqrxY8HnJxcYXdu", 1),
        ("thiago", "{bcrypt}$2a$10$oZgySAH78tJ4VRQg9T8NCubIhwmI0k2KQBvATLSqrxY8HnJxcYXdu", 1);
    
    insert into authorities values
        ("marcos", "ROLE_FUNCIONARIO"),
        ("maria", "ROLE_FUNCIONARIO"),
        ("thiago", "ROLE_FUNCIONARIO"),
        ("maria", "ROLE_GERENTE"),
        ("thiago", "ROLE_ADMINISTRADOR");

Edite o arquivo `pom.xml` para que ele fique assim:

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>dominio</groupId>
        <artifactId>springsecurity</artifactId>
        <version>0.0.1-SNAPSHOT</version>
        <packaging>war</packaging>
    
        <name>springsecurity</name>
    
        <properties>
            <springframework.version>5.3.19</springframework.version>
            <springsecurity.version>5.6.3</springsecurity.version>
    
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
        </properties>
    
        <dependencies>
    
            <!-- Spring Framework -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-webmvc</artifactId>
                <version>${springframework.version}</version>
            </dependency>
    
            <!-- Spring Security -->
            <dependency>
                <groupId>org.springframework.security</groupId>
                <artifactId>spring-security-web</artifactId>
                <version>${springsecurity.version}</version>
            </dependency>
    
            <dependency>
                <groupId>org.springframework.security</groupId>
                <artifactId>spring-security-config</artifactId>
                <version>${springsecurity.version}</version>
            </dependency>
    
            <dependency>
                <groupId>org.springframework.security</groupId>
                <artifactId>spring-security-taglibs</artifactId>
                <version>${springsecurity.version}</version>
            </dependency>
    
            <!-- Add MySQL and C3P0 support -->
            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>8.0.29</version>
            </dependency>
    
            <dependency>
                <groupId>com.mchange</groupId>
                <artifactId>c3p0</artifactId>
                <version>0.9.5.5</version>
            </dependency>
    
            <!-- Servlet, JSP and JSTL support -->
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>javax.servlet-api</artifactId>
                <version>3.1.0</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet.jsp</groupId>
                <artifactId>javax.servlet.jsp-api</artifactId>
                <version>2.3.1</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>jstl</artifactId>
                <version>1.2</version>
            </dependency>
    
            <!-- to compensate for java 9+ not including jaxb -->
            <dependency>
                <groupId>javax.xml.bind</groupId>
                <artifactId>jaxb-api</artifactId>
                <version>2.3.0</version>
            </dependency>
    
            <dependency>
                <groupId>junit</groupId>
                <artifactId>junit</artifactId>
                <version>3.8.1</version>
                <scope>test</scope>
            </dependency>
    
        </dependencies>
    
        <!-- Add support for Maven WAR Plugin -->
    
        <build>
            <finalName>springsecurity</finalName>
            <pluginManagement>
                <plugins>
                    <!-- Add Maven coordinates for> maven-war-plugin -->
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-war-plugin</artifactId>
                        <version>3.3.2</version>
                    </plugin>
                </plugins>
            </pluginManagement>
        </build>
    
    </project>

Na pasta `src/main/java`, crie o pacote `dominio.springsecurity.config` e dentro dele crie as classes:

**MeuSecurityConfig.java**

    package dominio.springsecurity.config;
    
    import javax.sql.DataSource;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
    import org.springframework.security.config.annotation.web.builders.HttpSecurity;
    import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
    import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
    import org.springframework.security.core.userdetails.User;
    import org.springframework.security.core.userdetails.User.UserBuilder;
    
    @Configuration
    @EnableWebSecurity
    public class MeuSecurityConfig extends WebSecurityConfigurerAdapter {
        
        @Autowired
        private DataSource securityDataSource;
    
        @Override
        protected void configure(AuthenticationManagerBuilder auth) throws Exception {
            
            // Fala para o Spring Security para usar a autenticação JDBC com nossa fonte de dados
            auth.jdbcAuthentication().dataSource(securityDataSource);
        }
    
        @Override
        protected void configure(HttpSecurity http) throws Exception {
            http.authorizeRequests()
                .antMatchers("/").hasRole("FUNCIONARIO")
                .antMatchers("/lideres/**").hasRole("GERENTE")
                .antMatchers("/sistema/**").hasRole("ADMINISTRADOR")
                .and()
                    .formLogin().loginPage("/paginaDeLogin")
                    .loginProcessingUrl("/autenticaUsuario")
                    .permitAll()
                .and()
                    .logout()
                    .permitAll()
                .and()
                    .exceptionHandling()
                    .accessDeniedPage("/acessoNegado");
        }
        
    }

**MinhaAppConfig.java**

    package dominio.springsecurity.config;
     
    import java.beans.PropertyVetoException;
    import java.util.logging.Logger;
    
    import javax.sql.DataSource;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.ComponentScan;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.context.annotation.PropertySource;
    import org.springframework.core.env.Environment;
    import org.springframework.web.servlet.ViewResolver;
    import org.springframework.web.servlet.config.annotation.EnableWebMvc;
    import org.springframework.web.servlet.view.InternalResourceViewResolver;
    
    import com.mchange.v2.c3p0.ComboPooledDataSource;
    
    @Configuration
    @EnableWebMvc
    @ComponentScan(basePackages="dominio.springsecurity")
    @PropertySource("classpath:persistence-mysql.properties") // Os arquivos de src/main/resources são automaticamente copiados para o classpath durante a build do Maven
    public class MinhaAppConfig {
        
        @Autowired // Environment env é autowired porque este Bean é automaticamente criado pelo Spring
        private Environment env; // env reterá os dados lidos pelo arquivo .properties
        
        private Logger logger = Logger.getLogger(getClass().getName()); // Não é obrigatório, é só para diagnóstico
            
        @Bean
        public ViewResolver viewResolver () {
            
            InternalResourceViewResolver viewResolver = new InternalResourceViewResolver();
            
            viewResolver.setPrefix("/WEB-INF/view/");
            viewResolver.setSuffix(".jsp");
            
            return viewResolver;
        }
        
        @Bean
        public DataSource securityDataSource() {
            
            // Cria um connection pool
            ComboPooledDataSource securityDataSource = new ComboPooledDataSource();
            
            // Define a classe de driver do JDBC
            try {
                securityDataSource.setDriverClass(env.getProperty("jdbc.driver"));
            } catch (PropertyVetoException e) {
                throw new RuntimeException(e);
            }
            
            // Faz log do connection props, só para termos certeza que estamos lendo dados do arquivo properties
            logger.info(">>> jdbc.url: " + env.getProperty("jdbc.driver"));
            logger.info(">>> jdbc.user: " + env.getProperty("jdbc.user"));
            
            // Define o connection props do banco de dados
            securityDataSource.setJdbcUrl(env.getProperty("jdbc.url"));
            securityDataSource.setUser(env.getProperty("jdbc.user"));
            securityDataSource.setPassword(env.getProperty("jdbc.password"));
            
            // Define o connection pool props
            securityDataSource.setInitialPoolSize(getIntProperty("connection.pool.initialPoolSize"));
            securityDataSource.setMinPoolSize(getIntProperty("connection.pool.minPoolSize"));
            securityDataSource.setMaxPoolSize(getIntProperty("connection.pool.maxPoolSize"));
            securityDataSource.setMaxIdleTime(getIntProperty("connection.pool.maxIdleTime"));
            
            return securityDataSource;
        }
        
        // Método para nos ajudar a ler o environment property e convertê-lo para int
        private  int getIntProperty(String propName) {
            String propVal = env.getProperty(propName);
            int intPropVal = Integer.parseInt(propVal);
            return intPropVal;
        }
    
    }

**SecurityWebApplicationInitializer.java**

    package dominio.springsecurity.config;
    
    import org.springframework.security.web.context.AbstractSecurityWebApplicationInitializer;
    
    public class SecurityWebApplicationInitializer extends AbstractSecurityWebApplicationInitializer {
    
    }

**MeuSpringMvcDispatcherServletInitializer.java**

    package dominio.springsecurity.config;
    
    import org.springframework.web.servlet.support.AbstractAnnotationConfigDispatcherServletInitializer;
    
    public class MeuSpringMvcDispatcherServletInitializer extends AbstractAnnotationConfigDispatcherServletInitializer {
    
        @Override
        protected Class<?>[] getRootConfigClasses() { // Não teremos arquivos de configuração root no nosso projeto
            // TODO Auto-generated method stub
            return null;
        }
    
        @Override
        protected Class<?>[] getServletConfigClasses() {
    
            return new Class[] {MinhaAppConfig.class};
        }
    
        @Override
        protected String[] getServletMappings() {
    
            return new String[] { "/" };
        }
    
    }

Na pasta `src/main/java`, crie o pacote `dominio.springsecurity.controller` e dentro dele crie as classes:

**MeuController.java**

    package dominio.springsecurity.controller;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.GetMapping;
    
    @Controller
    public class MeuController {
        
        @GetMapping("/")
        public String mostrarHome() {        
            return "home";        
        }
        
        @GetMapping("/lideres")
        public String mostrarLiders() {        
            return "lideres";        
        }
        
        @GetMapping("/sistema")
        public String mostrarSistema() {        
            return "sistema";        
        }
    
    }

**LoginController.java**

    package dominio.springsecurity.controller;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.GetMapping;
    
    @Controller
    public class LoginController {
    
        @GetMapping("/paginaDeLogin")
        public String paginaDeLogin() {
            return "login";
        }
        
        @GetMapping("/acessoNegado")
        public String paginaacessoNegado() {
            return "acessonegado";
        }
    }

Na pasta `src/main/resources`, crie o arquivo abaixo:

**persistence-mysql.properties**

    #
    # JDBC connection properties
    #
    jdbc.driver=com.mysql.cj.jdbc.Driver
    jdbc.url=jdbc:mysql://localhost:3306/springsecurity?useSSL=false&serverTimezone=UTC
    jdbc.user=estudante
    jdbc.password=estudante
    
    #
    # Connection pool properties
    #
    connection.pool.initialPoolSize=5
    connection.pool.minPoolSize=5
    connection.pool.maxPoolSize=20
    connection.pool.maxIdleTime=3000

Dentro da pasta `webapp`, caso não exista, crie a pasta `WEB-INF` e dentro desta última a pasta `view`. Dentro da pasta `view`, crie os seguintes arquivos JSP:

**login.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
    
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <title>Página de Login</title>
    </head>
    <body>
        <h3>Página de login</h3>
        
        <form:form action="${pageContext.request.contextPath}/autenticaUsuario" method="POST">
        
            <c:if test="${param.error != null}">
                <i>Login ou senha inválidos</i>
            </c:if>
            
            <c:if test="${param.logout != null}">
                <i>Você foi deslogado</i>
            </c:if>
        
            <p>
                Nome de usuário: <input type="text" name="username" />
            </p>
            
            <p>
                Senha: <input type="password" name="password" />
            </p>
            
            <input type="submit" value="Login" />
        
        </form:form>
        
    </body>
    </html>

**home.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    <%@ taglib prefix="security" uri="http://www.springframework.org/security/tags" %>
    
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring Security</title>
    </head>
    <body>
    
        <p>Olá mundo</p>
        
        <hr>
        
        <p>
            Nome de usuário: <security:authentication property="principal.username" />
        </p>
        <p>
            <i>Role</i>: <security:authentication property="principal.authorities" />
        </p>
        
        <security:authorize access="hasRole('GERENTE')">
    	    <p>
    	        <a href="${pageContext.request.contextPath}/lideres">Reunião da gerência</a>
    	    </p>
        </security:authorize>
        
        <security:authorize access="hasRole('ADMINISTRADOR')">
    	    <p>
    	        <a href="${pageContext.request.contextPath}/sistema">Administração do sistema</a>
    	    </p>
        </security:authorize>
        
        <hr>
        
        <form:form action="${pageContext.request.contextPath}/logout" method="POST">
            <input type="submit" value="Logout" />
        </form:form>
    
    </body>
    </html>

**lideres.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Reunião da gerência</title>
    </head>
    <body>
    
        <h1>Reunião da gerência</h1>
        
        <a href="${pageContext.request.contextPath}/">Retornar à página inicial</a>
    
    </body>
    </html>

**sistema.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Administração do sistema</title>
    </head>
    <body>
    
        <h1>Administração do sistema</h1>
        
        <a href="${pageContext.request.contextPath}/">Retornar à página inicial</a>
        
    </body>
    </html>

**acessonegado.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Acesso Negado</title>
    </head>
    <body>
        <h1>Acesso negado</h1>
        
        <p>Você não tem permissão para acessar esta página</p>
        
        <a href="${pageContext.request.contextPath}/">Retornar à página inicial</a>
    </body>
    </html>



# Spring REST<span id="springrest"></span>

*<b>Re</b>presentational <b>S</b>tate <b>T</b>ransfer* (REST), ou “Transferência Representacional de Estado” em português, é um estilo de arquitetura de software que define um conjunto de restrições a serem usadas para a criação de serviços Web, é uma abordagem leve para a comunicação entre aplicações, como um aplicativo que exibe o tempo *(clima)* atual de uma cidade e consulta os dados armazenados em um servidor. 

Tanto no lado do servidor quanto no do cliente, podemos utilizar qualquer linguagem de programação. Até mesmo o formato pode ser qualquer um, como XML ou JSON, sendo que este último é o mais utilizado por ser mais moderno. Em resumo, a diferença entre um aplicativo web e uma API REST é que a resposta de um aplicativo da web é uma visualização do nosso conhecido conjunto de HTML, CSS e JavaScript enquanto a API REST apenas retorna dados em forma de JSON ou XML.

No nosso estudo, criaremos um aplicativo CRM que pega dados de um serviço CRM feito em Spring Rest. CRM = Customer Relationship Manager

*A propósito, se você quiser encontrar APIs, você pode visitar o site [ProgrammableWeb](https://www.programmableweb.com/).*

Ainda sobre conceitos, você precisa saber que geralmente os termos abaixo são sinônimos:

REST API = REST Web Services = REST Services

RESTful API = RESTful Web Services = RESTful Services

Até mesmo REST e RESTful são praticamente a mesma coisa, uma API RESTful é aquela que se adere à arquitetura REST.

## JSON Data Binding<span id="springrest_jsondatabinding"></span>

Em nosso projeto, faremos o processo de "*JSON Binding*", que consiste no processo de converter dados JSON em um POJO Java. Esse processo pode receber outros nomes, como: "*Mapping*", "*Serialization*"/"*Deserialization*", "*Marshalling*"/"*Unmarshalling*".

No Eclipse, mude para a perspectiva do Java EE.

`File` => `New` => `Maven Project`

Marque a opção para criar um projeto simples. Clique em `Next`

Em *Group Id* ponha `dominio`

Em *Artifact Id* ponha `springrest`

Seu arquivo `pom.xml` deverá ficar assim:

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>dominio</groupId>
        <artifactId>springrest</artifactId>
        <version>0.0.1-SNAPSHOT</version>
        <packaging>jar</packaging>
    
        <properties>
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
        </properties>
    
        <dependencies>
    
            <dependency>
                <groupId>com.fasterxml.jackson.core</groupId>
                <artifactId>jackson-databind</artifactId>
                <version>2.13.3</version>
            </dependency>
    
        </dependencies>
    </project>

*Não se esqueça e atualizar o projeto Maven.*

Na raiz do seu projeto, crie a pasta `dados` e dentro deles crie os seguintes arquivos JSON:

**exemplo-simples.json**

    {
    	"id": 23,
    	"nome": "Lúcio",
    	"sobrenome": "Ribeiro",
    	"ativo": true
    }

**exemplo-completo.json**

    {
    	"id": 23,
    	"nome": "Lúcio",
    	"sobrenome": "Ribeiro",
    	"ativo": true,
    	"endereco": {
    		"rua": "Rua Graveteiros",
    		"cidade": "Belo Horizonte",
    		"estado": "Minas Gerais",
    		"cep": "31950-210",
    		"pais": "Brasil"
    	},
    	"linguagens" : ["Java", "C++", "Python", "Javascript"]
    }

Na pasta `src/main/java`, crie o pacote `dominio.jackson.json` e dentro deste pacote crie as seguintes classes:

**Estudante.java**

    package dominio.jackson.json;
    
    public class Estudante {
        
        private int id;
        private String nome;
        private String sobrenome;
        private boolean ativo;
        
        public Estudante () {
            
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public boolean isAtivo() {
            return ativo;
        }
    
        public void setAtivo(boolean ativo) {
            this.ativo = ativo;
        }
        
    }

**Driver.java**

    package dominio.jackson.json;
    
    import java.io.File;
    
    import com.fasterxml.jackson.databind.ObjectMapper;
    
    public class Driver {
    
        public static void main(String[] args) {
            
            try {
                
                ObjectMapper mapper = new ObjectMapper();
                
                Estudante estudante = mapper.readValue(new File("dados/exemplo-simples.json"), Estudante.class);
                
                System.out.println("Nome completo: " + estudante.getNome() + " " + estudante.getSobrenome());
                
            } catch (Exception e) {
                e.printStackTrace();
            }
    
        }
    
    }

Você já pode testar o aplicativo.

Agora vamos usar um dado mais complexo, com objeto aninhado e *array*:

Como temos um objeto aninhado, vamos criar sua classe junto com as outras:

**Endereco.java**

    package dominio.jackson.json;
    
    public class Endereco {
        
        private String rua;
        private String cidade;
        private String estado;
        private String cep;
        private String pais;
        
        public Endereco () {
            
        }
    
        public String getRua() {
            return rua;
        }
    
        public void setRua(String rua) {
            this.rua = rua;
        }
    
        public String getCidade() {
            return cidade;
        }
    
        public void setCidade(String cidade) {
            this.cidade = cidade;
        }
    
        public String getEstado() {
            return estado;
        }
    
        public void setEstado(String estado) {
            this.estado = estado;
        }
    
        public String getCep() {
            return cep;
        }
    
        public void setCep(String cep) {
            this.cep = cep;
        }
    
        public String getPais() {
            return pais;
        }
    
        public void setPais(String pais) {
            this.pais = pais;
        }
    
    }

E atualizamos as classes existentes:

**Estudante.java**

    package dominio.jackson.json;
    
    public class Estudante {
        
        private int id;
        private String nome;
        private String sobrenome;
        private boolean ativo;
        
        private Endereco endereco;
        private String[] linguagens;
        
        public Estudante () {
            
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public boolean isAtivo() {
            return ativo;
        }
    
        public void setAtivo(boolean ativo) {
            this.ativo = ativo;
        }
    
        public Endereco getEndereco() {
            return endereco;
        }
    
        public void setEndereco(Endereco endereco) {
            this.endereco = endereco;
        }
    
        public String[] getLinguagens() {
            return linguagens;
        }
    
        public void setLinguagens(String[] linguagens) {
            this.linguagens = linguagens;
        }
        
    }

**Driver.java**

    package dominio.jackson.json;
    
    import java.io.File;
    
    import com.fasterxml.jackson.databind.ObjectMapper;
    
    public class Driver {
    
        public static void main(String[] args) {
            
            try {
                
                ObjectMapper mapper = new ObjectMapper();
                
                Estudante estudante = mapper.readValue(new File("dados/exemplo-completo.json"), Estudante.class); // Observe que mudei o arquivo...
                
                System.out.println("Nome completo: " + estudante.getNome() + " " + estudante.getSobrenome());
                System.out.println("Endereço: " + estudante.getEndereco().getRua() + ", " + estudante.getEndereco().getCidade());
                System.out.print("Linguagens:");
                for (String tempLang : estudante.getLinguagens()) {
                    System.out.print(" " + tempLang);
                }
                
            } catch (Exception e) {
                e.printStackTrace();
            }
    
        }
    
    }

Você já pode testar o aplicativo.

Uma questão é que, se uma nova propriedade for adicionada ao JSON e não atualizarmos nosso código, haverá um erro na hora da exceção, ainda que não usemos essa nova propriedade. Faça um teste, adicione uma nova propriedade ao arquivo JSON e tente rodar o programa novamente.

Para que não dê erro, basta usar a *annotation* `@JsonIgnoreProperties(ignoreUnknown=true)` sobre a classe usada como POJO.

    package dominio.jackson.json;
    
    import com.fasterxml.jackson.annotation.JsonIgnoreProperties;
    
    @JsonIgnoreProperties(ignoreUnknown=true)
    public class Estudante {
        
        private int id;
        private String nome;
        private String sobrenome;
        private boolean ativo;

    [...]

## Conceitos básicos<span id="springrest_basicconcepts"></span>

Vamos entender como funcionam os métodos HTTP em operações CRUD.

| Método | Operação CRUD                      |
| ------ | ---------------------------------- |
| POST   | Cria uma nova entidade             |
| GET    | Lê uma ou mais entidades           |
| PUT    | Atualiza uma entidade já existente |
| DELETE | Deleta uma entidade já existente   |

O aplicativo manda um *request* para o servidor e o servidor manda de volta um *ressponse*.

Um *request* é composto por:

* Request line: o comando HTTP

* Header variables: metadados do *request*

* Message body: conteúdos da mensagem

Um *response* é composto por:

* Response line: protocolo do servidor ou *[status code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)*

* Header variables: metadados do *response*

* Message body: conteúdos da mensagem

Também é importante conhecer os conteúdos MIME *(<b>M</b>ultipurpose <b>I</b>nternet <b>M</b>ail-<b>E</b>xtension)*, é a descrição do formato de mensagem, o *"Content-Type"*. Exemplos de MIME: `text/html`, `text/plain`, `application/json`, `application/xml`.

Precisaremos de um client tool para enviar *requests* para o serviço web REST, alguns exemplos são curl, Postman, etc, usaremos este último. Você pode usar sites como [JSON Test](http://www.jsontest.com/) ou [{JSON} Placeholder](https://jsonplaceholder.typicode.com/) para testar o Postman.

## REST Controller<span id="springrest_restcontroller"></span>

O Spring MVC provê suporte para o Spring REST.

OK, crie um projeto Maven cujo *Artefact Id* será `springrest` e nosso arquivo `pom.xml` será este:

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>dominio</groupId>
        <artifactId>springrest</artifactId>
        <version>1.0</version>
        <packaging>war</packaging>
    
        <properties>
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
        </properties>
    
        <dependencies>
    
            <!-- Add Spring MVC and REST support -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-webmvc</artifactId>
                <version>5.3.20</version>
            </dependency>
    
            <!-- Add Jackson for JSON converters -->
            <dependency>
                <groupId>com.fasterxml.jackson.core</groupId>
                <artifactId>jackson-databind</artifactId>
                <version>2.13.3</version>
            </dependency>
    
            <!-- Add Servlet support for 
                 Spring's AbstractAnnotationConfigDispatcherServletInitializer -->
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>javax.servlet-api</artifactId>
                <version>4.0.1</version>
            </dependency>
    
        </dependencies>
        
        <!-- Add support for Maven WAR Plugin -->
    
        <build>
            <finalName>springrest</finalName>
            <pluginManagement>
                <plugins>
                    <!-- Add Maven coordinates for> maven-war-plugin -->
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-war-plugin</artifactId>
                        <version>3.3.2</version>
                    </plugin>
                </plugins>
            </pluginManagement>
        </build>
    </project>

Na pasta `src/main/java`, crie o pacote `dominio.spring.config` e dentro dele crie as classes:

**AppConfig.java**

    package dominio.spring.config;
    
    import org.springframework.context.annotation.ComponentScan;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.web.servlet.config.annotation.EnableWebMvc;
    
    @Configuration
    @EnableWebMvc
    @ComponentScan("dominio.spring")
    public class AppConfig {
    
    }

**AppSpringMvcDispatcherServletInitializer.java**

    package dominio.spring.config;
    
    import org.springframework.web.servlet.support.AbstractAnnotationConfigDispatcherServletInitializer;
    
    public class AppSpringMvcDispatcherServletInitializer extends AbstractAnnotationConfigDispatcherServletInitializer {
    
        @Override
        protected Class<?>[] getRootConfigClasses() {
            // TODO Auto-generated method stub
            return null;
        }
    
        @Override
        protected Class<?>[] getServletConfigClasses() {
            return new Class[] {AppConfig.class};
        }
    
        @Override
        protected String[] getServletMappings() {
            return new String[] {"/"};
        }
    
    }

Agora crie o pacote `dominio.spring.rest` e crie a classe `TestRestController`:

    package dominio.spring.rest;
    
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    @RestController
    @RequestMapping("/teste")
    public class TestRestController {
    
        @GetMapping("/ola")
        public String dizerOla() {
            return "Olá";
        }
    }

`@RestController` é uma extensão de `@Controller`, mais precisamente uma combinação do `@Controller` e `@ResponseBody`.

Rode como servidor. Naturalmente que você terá um erro 404 porque ainda não temos uma página inicial, mas o endereço [http://localhost:8080/springrest/teste/ola](http://localhost:8080/springrest/teste/ola) funcionará. Tente abrrir esse endereço no Postman para você ver o resultado.

Por uma questão de conveninência, vamos adicionar uma página inicial. Na pasta `src/main/webapp`, crie o arquivo `index.jsp`

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring REST Demo</title>
    </head>
    <body>
    
    <p>Na verdade, os testes estão sendo feitos neste <a href="${pageContext.request.contextPath}/teste/ola">link</a></p>
    
    </body>
    </html>

Você verá que o Eclipse está apresentando algumas mensagens de erro para o arquivo JSP, então vamos adicionar mais uma dependência ao nosso projeto, mais precisamente o `javax.servlet.jsp-api`. De novo, observe que essa parte, inclusive essa dependência, não é obrigatório, é só por uma questão de conveniência.

Veja como ficou o arquivo `pom.xml` atualizado.

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>dominio</groupId>
        <artifactId>springrest</artifactId>
        <version>1.0</version>
        <packaging>war</packaging>
    
        <properties>
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
        </properties>
    
        <dependencies>
    
            <!-- Add Spring MVC and REST support -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-webmvc</artifactId>
                <version>5.3.20</version>
            </dependency>
    
            <!-- Add Jackson for JSON converters -->
            <dependency>
                <groupId>com.fasterxml.jackson.core</groupId>
                <artifactId>jackson-databind</artifactId>
                <version>2.13.3</version>
            </dependency>
    
            <!-- Add Servlet support for 
                 Spring's AbstractAnnotationConfigDispatcherServletInitializer -->
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>javax.servlet-api</artifactId>
                <version>4.0.1</version>
            </dependency>
    
            <!-- Add support for JSP ... get rid of Eclipse error -->
            <dependency>
                <groupId>javax.servlet.jsp</groupId>
                <artifactId>javax.servlet.jsp-api</artifactId>
                <version>2.3.3</version>
            </dependency>
    
        </dependencies>
    
        <!-- Add support for Maven WAR Plugin -->
    
        <build>
            <finalName>springrest</finalName>
            <pluginManagement>
                <plugins>
                    <!-- Add Maven coordinates for> maven-war-plugin -->
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-war-plugin</artifactId>
                        <version>3.3.2</version>
                    </plugin>
                </plugins>
            </pluginManagement>
        </build>
    </project>

## Coletar POJO como JSON<span id="springrest_pojojson"></span>

Crie o pacote `dominio.spring.entity` e dentro dele a classe `Estudante`:

    package dominio.spring.entity;
    
    public class Estudante {
        
        private String nome;
        private String sobrenome;
        
        public Estudante() {
            
        }
        
        public Estudante(String nome, String sobrenome) {
            this.nome = nome;
            this.sobrenome = sobrenome;
        }
    
        public String getNome() {
            return nome;
        }
    
        public void setNome(String nome) {
            this.nome = nome;
        }
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
        
    }

No pacote `dominio.spring.rest`, crie a classe `EstudanteRestController`:

    package dominio.spring.rest;
    
    import java.util.ArrayList;
    import java.util.List;
    
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.spring.entity.Estudante;
    
    @RestController
    @RequestMapping("/api")
    public class EstudanteRestController {
        
        // Define o endpoint para "/estudantes", retorna  alista de todos os estudantes
        @GetMapping("/estudantes")
        public List<Estudante> getEstudantes() {
            
            List<Estudante> estudantes = new ArrayList<>();
            
            estudantes.add(new Estudante("Júnior", "Galvão"));
            estudantes.add(new Estudante("Virgínia", "Araújo"));
            estudantes.add(new Estudante("Gleize", "Smith"));
            estudantes.add(new Estudante("Rui", "Tavares"));
            
            return estudantes;
        }
    
    }

Rode o projeto como servidor. Se você quiser o link para agilizar, [aqui está](http://localhost:8080/springrest/api/estudantes).

No plano de fundo, o Spring faz uso do Jackson para converter os POJOs em JSON.

Pela conveniência, podemos editar nosso arquivo JSP:

**index.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Spring REST Demo</title>
    </head>
    <body>
    
    <ul>
        <li><a href="${pageContext.request.contextPath}/teste/ola">/teste/ola</a></li>
        <li><a href="${pageContext.request.contextPath}/api/estudantes">/api/estudantes</a></li>
    </ul>
    
    </body>
    </html>

Se por acaso for mostrado menos que 4 estudantes, isso será devido a um bug de *caching* do Eclipse, uma possível solução é você adicionar um `?` no final da URL.

## @PathVariable<span id="springrest_pathvariable"></span>

Através de *Path Variables*, podemos recuperar um único estudante pelo id *(`api/estudantes/{id}`)*

Como precisaremos usar algumas anotações ainda não suportadas pelo nosso arquivo `pom.xml` atual, vamos atualizar nosso arquivo:

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>dominio</groupId>
        <artifactId>springrest</artifactId>
        <version>1.0</version>
        <packaging>war</packaging>
    
        <properties>
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
        </properties>
    
        <dependencies>
    
            <!-- Add Spring MVC and REST support -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-webmvc</artifactId>
                <version>5.3.20</version>
            </dependency>
    
            <!-- Add Jackson for JSON converters -->
            <dependency>
                <groupId>com.fasterxml.jackson.core</groupId>
                <artifactId>jackson-databind</artifactId>
                <version>2.13.3</version>
            </dependency>
    
            <!-- Add Servlet support for 
                 Spring's AbstractAnnotationConfigDispatcherServletInitializer -->
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>javax.servlet-api</artifactId>
                <version>4.0.1</version>
            </dependency>
    
            <!-- Add support for JSP ... get rid of Eclipse error -->
            <dependency>
                <groupId>javax.servlet.jsp</groupId>
                <artifactId>javax.servlet.jsp-api</artifactId>
                <version>2.3.3</version>
            </dependency>
    
            <!-- Add Jackson for some annotations like @PostConstruct -->
            <dependency>
                <groupId>javax.annotation</groupId>
                <artifactId>javax.annotation-api</artifactId>
                <version>1.3.2</version>
            </dependency>
    
        </dependencies>
    
        <!-- Add support for Maven WAR Plugin -->
    
        <build>
            <finalName>springrest</finalName>
            <pluginManagement>
                <plugins>
                    <!-- Add Maven coordinates for> maven-war-plugin -->
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-war-plugin</artifactId>
                        <version>3.3.2</version>
                    </plugin>
                </plugins>
            </pluginManagement>
        </build>
    </project>

Agora edite o arquivo `EstudanteRestController.java`...

    package dominio.spring.rest;
    
    import java.util.ArrayList;
    import java.util.List;
    
    import javax.annotation.PostConstruct;
    
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.spring.entity.Estudante;
    
    @RestController
    @RequestMapping("/api")
    public class EstudanteRestController {
        
        private List<Estudante> estudantes;
        
        // Define @PostConstruct para carregar os dados dos estudantes apenas uma vez, apenas um refatoramento do código para deixar as coisas mais simples
        @PostConstruct
        public void carregarDados() {
            
            estudantes = new ArrayList<>();
            
            estudantes.add(new Estudante("Júnior", "Galvão"));
            estudantes.add(new Estudante("Virgínia", "Araújo"));
            estudantes.add(new Estudante("Gleize", "Smith"));
            estudantes.add(new Estudante("Rui", "Tavares"));
        }
        
        // Define endpoint para /estudantes
        @GetMapping("/estudantes")
        public List<Estudante> getEstudantes() {
            
            return estudantes;
        }
    
        // Define endpoint para /estudantes/id
        @GetMapping("/estudantes/{estudanteId}")
        public Estudante getEstudante(@PathVariable int estudanteId) {
            
            return estudantes.get(estudanteId);
        }
    }

...e você já pode rodar o aplicativo como servidor. Saiba que o Id começa em 0, portanto `api/estudantes/2`, por exemplo, te levará para a estudante Gleize.

## Exception Handling<span id="springrest_exceptionhandling"></span>

O que acontece se eu tentar acessar um id de estudante que não existe? Dará erro 400 ou 500 a depender do que você inserir lá.

Crie novas classes no pacote `dominio.spring.rest`:

**EstudanteErrorResponse.java**

    package dominio.spring.rest;
    
    public class EstudanteErrorResponse {
        
        private int status;
        private String message;
        private long timeStamp;
        
        public EstudanteErrorResponse () {
            
        }
    
        public EstudanteErrorResponse(int status, String message, long timeStamp) {
            this.status = status;
            this.message = message;
            this.timeStamp = timeStamp;
        }
    
        public int getStatus() {
            return status;
        }
    
        public void setStatus(int status) {
            this.status = status;
        }
    
        public String getMessage() {
            return message;
        }
    
        public void setMessage(String message) {
            this.message = message;
        }
    
        public long getTimeStamp() {
            return timeStamp;
        }
    
        public void setTimeStamp(long timeStamp) {
            this.timeStamp = timeStamp;
        }
    }

**EstudanteNotFoundException.java**

Para facilitar a construção dessa classe, você teria clicado com o botão direito do mouse sobre a tela de edição => `Source` => `Generate Constructors from Superclass`, você escolherá apenas 3, como você pode ver no código abaixo:

    package dominio.spring.rest;
    
    public class EstudanteNotFoundException extends RuntimeException {
    
        private static final long serialVersionUID = 1L;
    
        public EstudanteNotFoundException(String message, Throwable cause) {
            super(message, cause);
        }
    
        public EstudanteNotFoundException(String message) {
            super(message);
        }
    
        public EstudanteNotFoundException(Throwable cause) {
            super(cause);
        }
    
    }

E edite o arquivo abaixo:

**EstudanteRestController.java**

    package dominio.spring.rest;
    
    import java.util.ArrayList;
    import java.util.List;
    
    import javax.annotation.PostConstruct;
    
    import org.springframework.http.HttpStatus;
    import org.springframework.http.ResponseEntity;
    import org.springframework.web.bind.annotation.ExceptionHandler;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.spring.entity.Estudante;
    
    @RestController
    @RequestMapping("/api")
    public class EstudanteRestController {
        
        private List<Estudante> estudantes;
        
        // Define @PostConstruct para carregar os dados dos estudantes apenas uma vez, apenas um refatoramento do código para deixar as coisas mais simples
        @PostConstruct
        public void carregarDados() {
            
            estudantes = new ArrayList<>();
            
            estudantes.add(new Estudante("Júnior", "Galvão"));
            estudantes.add(new Estudante("Virgínia", "Araújo"));
            estudantes.add(new Estudante("Gleize", "Smith"));
            estudantes.add(new Estudante("Rui", "Tavares"));
        }
        
        // Define endpoint para /estudantes
        @GetMapping("/estudantes")
        public List<Estudante> getEstudantes() {
            
            return estudantes;
        }
    
        // Define endpoint para /estudantes/{estudanteId}
        @GetMapping("/estudantes/{estudanteId}")
        public Estudante getEstudante(@PathVariable int estudanteId) {
            
            if ((estudanteId >= estudantes.size()) || (estudanteId < 0)) {
                throw new EstudanteNotFoundException("ID de estudante não encontrado - " + estudanteId);
            }
            
            return estudantes.get(estudanteId);
        }
        
        // Adiciona um gerenciador de exceções
        @ExceptionHandler
        public ResponseEntity<EstudanteErrorResponse> handleException(EstudanteNotFoundException e) {
            
            EstudanteErrorResponse error = new EstudanteErrorResponse();
            
            error.setStatus(HttpStatus.NOT_FOUND.value());
            error.setMessage(e.getMessage());
            error.setTimeStamp(System.currentTimeMillis());
            
            return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
        }
    }

Agora, quando você for acessar um ID cujo número não esteja dentro do limite de IDs disponíveis, você receberá um JSON com a mensagem de erro.

`ResponseEntity` é uma extensão de `HttpEntity`. `HttpEntity` representa um HTTP *request* ou *response* que contém *headers* e *body*, o `ResponseEntity` adiciona *status code*.

Mas nosso código tem um problema, se adicionarmos uma letra em vez de número no lugar do ID, teremos um erro 400.

    package dominio.spring.rest;
    
    import java.util.ArrayList;
    import java.util.List;
    
    import javax.annotation.PostConstruct;
    
    import org.springframework.http.HttpStatus;
    import org.springframework.http.ResponseEntity;
    import org.springframework.web.bind.annotation.ExceptionHandler;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.spring.entity.Estudante;
    
    @RestController
    @RequestMapping("/api")
    public class EstudanteRestController {
        
        private List<Estudante> estudantes;
        
        // Define @PostConstruct para carregar os dados dos estudantes apenas uma vez, apenas um refatoramento do código para deixar as coisas mais simples
        @PostConstruct
        public void carregarDados() {
            
            estudantes = new ArrayList<>();
            
            estudantes.add(new Estudante("Júnior", "Galvão"));
            estudantes.add(new Estudante("Virgínia", "Araújo"));
            estudantes.add(new Estudante("Gleize", "Smith"));
            estudantes.add(new Estudante("Rui", "Tavares"));
        }
        
        // Define endpoint para /estudantes
        @GetMapping("/estudantes")
        public List<Estudante> getEstudantes() {
            
            return estudantes;
        }
    
        // Define endpoint para /estudantes/{estudanteId}
        @GetMapping("/estudantes/{estudanteId}")
        public Estudante getEstudante(@PathVariable int estudanteId) {
            
            if ((estudanteId >= estudantes.size()) || (estudanteId < 0)) {
                throw new EstudanteNotFoundException("ID de estudante não encontrado - " + estudanteId);
            }
            
            return estudantes.get(estudanteId);
        }
        
        // Adiciona um gerenciador de exceções
        @ExceptionHandler
        public ResponseEntity<EstudanteErrorResponse> handleException(EstudanteNotFoundException e) {
            
            EstudanteErrorResponse error = new EstudanteErrorResponse();
            
            error.setStatus(HttpStatus.NOT_FOUND.value());
            error.setMessage(e.getMessage());
            error.setTimeStamp(System.currentTimeMillis());
            
            return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
        }
        
     // Adiciona outro gerenciador de exceções que pega QUALQUER exceção
        @ExceptionHandler
        public ResponseEntity<EstudanteErrorResponse> handleException(Exception e) {
            
            EstudanteErrorResponse error = new EstudanteErrorResponse();
            
            error.setStatus(HttpStatus.BAD_REQUEST.value());
            error.setMessage(e.getMessage());
            error.setTimeStamp(System.currentTimeMillis());
            
            return new ResponseEntity<>(error, HttpStatus.BAD_REQUEST);
        }
    }

Uma coisa que precisa sr dita é que esse gerenciamento de exceções serve apenas para um REST controller em específico, não dá para reutilizar em outros controllers (que são muitos em projetos grandes). Para resolver isso podemos utilizar gerenciadores de exceções globais.

Crie uma nova classe no pacote `dominio.spring.rest`:

**EstudanteRestExceptionHandler.java**

    package dominio.spring.rest;
    
    import org.springframework.http.HttpStatus;
    import org.springframework.http.ResponseEntity;
    import org.springframework.web.bind.annotation.ControllerAdvice;
    import org.springframework.web.bind.annotation.ExceptionHandler;
    
    @ControllerAdvice
    public class EstudanteRestExceptionHandler {
        
     // Adiciona um gerenciador de exceções
        @ExceptionHandler
        public ResponseEntity<EstudanteErrorResponse> handleException(EstudanteNotFoundException e) {
            
            EstudanteErrorResponse error = new EstudanteErrorResponse();
            
            error.setStatus(HttpStatus.NOT_FOUND.value());
            error.setMessage(e.getMessage());
            error.setTimeStamp(System.currentTimeMillis());
            
            return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
        }
        
     // Adiciona outro gerenciador de exceções que pega QUALQUER exceção
        @ExceptionHandler
        public ResponseEntity<EstudanteErrorResponse> handleException(Exception e) {
            
            EstudanteErrorResponse error = new EstudanteErrorResponse();
            
            error.setStatus(HttpStatus.BAD_REQUEST.value());
            error.setMessage(e.getMessage());
            error.setTimeStamp(System.currentTimeMillis());
            
            return new ResponseEntity<>(error, HttpStatus.BAD_REQUEST);
        }
    
    }

Repare que ele tem os métodos que lidam com as exceções, isso signica que essesmétodos não são mais necessários no controller:

**EstudanteRestController.java**

    package dominio.spring.rest;
    
    import java.util.ArrayList;
    import java.util.List;
    
    import javax.annotation.PostConstruct;
    
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.spring.entity.Estudante;
    
    @RestController
    @RequestMapping("/api")
    public class EstudanteRestController {
        
        private List<Estudante> estudantes;
        
        // Define @PostConstruct para carregar os dados dos estudantes apenas uma vez, apenas um refatoramento do código para deixar as coisas mais simples
        @PostConstruct
        public void carregarDados() {
            
            estudantes = new ArrayList<>();
            
            estudantes.add(new Estudante("Júnior", "Galvão"));
            estudantes.add(new Estudante("Virgínia", "Araújo"));
            estudantes.add(new Estudante("Gleize", "Smith"));
            estudantes.add(new Estudante("Rui", "Tavares"));
        }
        
        // Define endpoint para /estudantes
        @GetMapping("/estudantes")
        public List<Estudante> getEstudantes() {
            
            return estudantes;
        }
    
        // Define endpoint para /estudantes/{estudanteId}
        @GetMapping("/estudantes/{estudanteId}")
        public Estudante getEstudante(@PathVariable int estudanteId) {
            
            if ((estudanteId >= estudantes.size()) || (estudanteId < 0)) {
                throw new EstudanteNotFoundException("ID de estudante não encontrado - " + estudanteId);
            }
            
            return estudantes.get(estudanteId);
        }
    
    }

## CRUD<span id="springrest_crud"></span>

Teremos o seguinte esquema no nosso projeto:

| Método HTTP | Caminho                  | CRUD                          |
| ----------- | ------------------------ | ----------------------------- |
| POST        | api/clientes             | Cria um novo cliente          |
| GET         | api/clientes             | Lê uma lista de clientes      |
| GET         | api/clientes/{clienteId} | Lê um único cliente           |
| PUT         | api/clientes             | Atualiza um cliente existente |
| DELETE      | api/clientes/{clienteId} | Deleta um cliente existente   |

É má prática usar caminhos como `api/deletarcliente` ou `api/criarcliente`, prefira usar os *methods*.

Crie o projeto como projeto Maven. Criarei meu projeto Maven com *Group Id* como `dominio` e *Artefact Id* como `springmvchb`.

Vamos ao banco de dados, use o seguinte comando:

    CREATE DATABASE IF NOT EXISTS `cliente_web`;
    USE `cliente_web`;
    
    DROP TABLE IF EXISTS `cliente`;
    CREATE TABLE `cliente` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=latin1;
    
    LOCK TABLES `cliente` WRITE;
    
    INSERT INTO `cliente` VALUES 
    	(1,'Marcelino','Travolta','marcelino@gmail.com'),
    	(2,'Cuca','Beludo','culudo@gmail.com'),
    	(3,'Paula','Barbosa','paulinha@gmail.com'),
    	(4,'Oscar','Alho','alho@gmail.com'),
    	(5,'Maria','Freitas','maria@gmail.com');
    
    UNLOCK TABLES;

Agora vejamos nosso arquivo `pom.xml`:

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>dominio</groupId>
        <artifactId>springmvchb</artifactId>
        <version>1.0.0</version>
        <packaging>war</packaging>
    
        <properties>
            <springframework.version>5.3.20</springframework.version>
            <hibernate.version>5.6.9.Final</hibernate.version>
            <mysql.connector.version>8.0.29</mysql.connector.version>
            <c3p0.version>0.9.5.5</c3p0.version>
    
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
        </properties>
    
        <dependencies>
    
            <!-- Spring Framework -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-webmvc</artifactId>
                <version>${springframework.version}</version>
            </dependency>
    
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-tx</artifactId>
                <version>${springframework.version}</version>
            </dependency>
    
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-orm</artifactId>
                <version>${springframework.version}</version>
            </dependency>
    
            <dependency>
                <groupId>com.fasterxml.jackson.core</groupId>
                <artifactId>jackson-databind</artifactId>
                <version>2.13.3</version>
            </dependency>
    
            <dependency>
                <groupId>org.hibernate</groupId>
                <artifactId>hibernate-core</artifactId>
                <version>${hibernate.version}</version>
            </dependency>
    
            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>${mysql.connector.version}</version>
            </dependency>
    
            <dependency>
                <groupId>com.mchange</groupId>
                <artifactId>c3p0</artifactId>
                <version>${c3p0.version}</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>javax.servlet-api</artifactId>
                <version>3.1.0</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet.jsp</groupId>
                <artifactId>javax.servlet.jsp-api</artifactId>
                <version>2.3.1</version>
            </dependency>
    
            <!-- to compensate for java 9+ not including jaxb -->
            <dependency>
                <groupId>javax.xml.bind</groupId>
                <artifactId>jaxb-api</artifactId>
                <version>2.3.0</version>
            </dependency>
    
        </dependencies>
    
        <!-- Add support for Maven WAR Plugin -->
        <build>
            <finalName>springmvchb</finalName>
                <plugins>
                    <!-- Add Maven coordinates for> maven-war-plugin -->
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-war-plugin</artifactId>
                        <version>3.3.2</version>
                    </plugin>
                </plugins>
        </build>
    </project>

`spring-webmvc` inclui suporte ao REST, `spring-tx` (Spring Transaction) porque usaremos o Hibernate no plano de fundo, `spring-orm` contém classes que dão suporte para utilizar Hibernate, `jackson-databind` para converter POJO em JSON, `hibernate-core` que é nossa ferramenta ORM e armazenar dados no banco de dados, `mysql-connector-java`, a implementação do banco de dados, `c3p0` para fazer a conexão com o *polling* que gerencia a conexão com o banco de dados pra gente, `javax.servlet-api` que Spring MVC usará no plano de fundo, `javax.servlet.jsp-api` porque usaremos algumas páginas JSP,`jstl`

Na pasta `src/main/resources`, crie o arquivo abaixo:

**persistence-mysql.properties**

    #
    # JDBC connection properties
    #
    jdbc.driver=com.mysql.cj.jdbc.Driver
    jdbc.url=jdbc:mysql://localhost:3306/cliente_web?useSSL=false&serverTimezone=UTC
    jdbc.user=estudante
    jdbc.password=estudante
    
    #
    # Connection pool properties
    #
    connection.pool.initialPoolSize=5
    connection.pool.minPoolSize=5
    connection.pool.maxPoolSize=20
    connection.pool.maxIdleTime=3000
    
    #
    # Hibernate properties
    #
    hibernate.dialect=org.hibernate.dialect.MySQLDialect
    hibernate.show_sql=true
    hibernate.packagesToScan=dominio.springmvchb.entity

*A propósito, tenha certeza que o banco de dados MySQL foi incializado...*

Crie os seguintes pacotes:

* `dominio.springmvchb.config`

* `dominio.springmvchb.dao`

* `dominio.springmvchb.entity`

* `dominio.springmvchb.service`

* `dominio.springmvchb.rest`

No pacote `dominio.springmvchb.config`, crie os arquivos:

**AppConfig.java**

    package dominio.springmvchb.config;
    
    import java.beans.PropertyVetoException;
    import java.util.Properties;
    import java.util.logging.Logger;
    
    import javax.sql.DataSource;
    
    import org.hibernate.SessionFactory;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.ComponentScan;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.context.annotation.PropertySource;
    import org.springframework.core.env.Environment;
    import org.springframework.orm.hibernate5.HibernateTransactionManager;
    import org.springframework.orm.hibernate5.LocalSessionFactoryBean;
    import org.springframework.transaction.annotation.EnableTransactionManagement;
    import org.springframework.web.servlet.config.annotation.EnableWebMvc;
    import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;
    
    import com.mchange.v2.c3p0.ComboPooledDataSource;
    
    @Configuration
    @EnableWebMvc
    @EnableTransactionManagement
    @ComponentScan(basePackages="dominio.springmvchb")
    @PropertySource("classpath:persistence-mysql.properties")
    public class AppConfig implements WebMvcConfigurer {
        
        @Autowired
        private Environment env;
        
        private Logger logger = Logger.getLogger(getClass().getName());
        
    
        @Bean
        public DataSource myDataSource() {
            
            ComboPooledDataSource myDataSource = new ComboPooledDataSource();
    
            try {
                myDataSource.setDriverClass(env.getProperty("jdbc.driver"));       
            }
            catch (PropertyVetoException exc) {
                throw new RuntimeException(exc);
            }
            
            logger.info(">> jdbc.url=" + env.getProperty("jdbc.url"));
            logger.info(">> jdbc.user=" + env.getProperty("jdbc.user"));
            
            myDataSource.setJdbcUrl(env.getProperty("jdbc.url"));
            myDataSource.setUser(env.getProperty("jdbc.user"));
            myDataSource.setPassword(env.getProperty("jdbc.password"));
            
            myDataSource.setInitialPoolSize(getIntProperty("connection.pool.initialPoolSize"));
            myDataSource.setMinPoolSize(getIntProperty("connection.pool.minPoolSize"));
            myDataSource.setMaxPoolSize(getIntProperty("connection.pool.maxPoolSize"));     
            myDataSource.setMaxIdleTime(getIntProperty("connection.pool.maxIdleTime"));
    
            return myDataSource;
        }
        
        private Properties getHibernateProperties() {
    
            // set hibernate properties
            Properties props = new Properties();
    
            props.setProperty("hibernate.dialect", env.getProperty("hibernate.dialect"));
            props.setProperty("hibernate.show_sql", env.getProperty("hibernate.show_sql"));
            
            return props;
        }
    
        
        private int getIntProperty(String propName) {
            
            String propVal = env.getProperty(propName);
            
            int intPropVal = Integer.parseInt(propVal);
            
            return intPropVal;
        }   
        
        @Bean
        public LocalSessionFactoryBean sessionFactory(){
            
            LocalSessionFactoryBean sessionFactory = new LocalSessionFactoryBean();
            
            sessionFactory.setDataSource(myDataSource());
            sessionFactory.setPackagesToScan(env.getProperty("hibernate.packagesToScan"));
            sessionFactory.setHibernateProperties(getHibernateProperties());
            
            return sessionFactory;
        }
        
        @Bean
        @Autowired
        public HibernateTransactionManager transactionManager(SessionFactory sessionFactory) {
            
            // setup transaction manager based on session factory
            HibernateTransactionManager txManager = new HibernateTransactionManager();
            txManager.setSessionFactory(sessionFactory);
    
            return txManager;
        }
    }

**MeuSpringMvcDispatcherServletInitializer.java**

    package dominio.springmvchb.config;
    
    import org.springframework.web.servlet.support.AbstractAnnotationConfigDispatcherServletInitializer;
    
    public class MeuSpringMvcDispatcherServletInitializer extends AbstractAnnotationConfigDispatcherServletInitializer {
    
        @Override
        protected Class<?>[] getRootConfigClasses() { // Não teremos arquivos de configuração root no nosso projeto
            // TODO Auto-generated method stub
            return null;
        }
    
        @Override
        protected Class<?>[] getServletConfigClasses() {
    
            return new Class[] {AppConfig.class};
        }
    
        @Override
        protected String[] getServletMappings() {
    
            return new String[] { "/" };
        }
    
    }

No pacote `dominio.springmvchb.dao`, crie os arquivos:

**ClienteDAO.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteDAO {
        
        public List<Cliente> getClientes();
        
        public void saveCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
        public void deleteCliente(int oId);
    
    }

**ClienteDAOImpl.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.query.Query;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.springmvchb.entity.Cliente;
    
    @Repository
    public class ClienteDAOImpl implements ClienteDAO {
        
        @Autowired
        private SessionFactory sessionFactory;
                
        @Override
        public List<Cliente> getClientes() {
            
            Session currentSession = sessionFactory.getCurrentSession();
                    
            Query<Cliente> theQuery = currentSession.createQuery("from Cliente order by nome", Cliente.class);
            
            // execute query and get result list
            List<Cliente> clientes = theQuery.getResultList();
                    
            // return the results
            return clientes;
        }
    
        @Override
        public void saveCliente(Cliente oCliente) {
    
            Session currentSession = sessionFactory.getCurrentSession();
            
            currentSession.saveOrUpdate(oCliente);
            
        }
    
        @Override
        public Cliente getCliente(int oId) {
    
            // get the current hibernate session
            Session currentSession = sessionFactory.getCurrentSession();
            
            // now retrieve/read from database using the primary key
            Cliente oCliente = currentSession.get(Cliente.class, oId);
            
            return oCliente;
        }
    
        @Override
        public void deleteCliente(int oId) {
    
            // get the current hibernate session
            Session currentSession = sessionFactory.getCurrentSession();
            
            // delete object with primary key
            Query theQuery = currentSession.createQuery("delete from Cliente where id=:clienteId");
            theQuery.setParameter("clienteId", oId);
            
            theQuery.executeUpdate();       
        }
    
    }

No pacote `dominio.springmvchb.entity`, crie os arquivos:

**Cliente.java**

    package dominio.springmvchb.entity;
    
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="cliente")
    public class Cliente {
        
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        public int id;
        
        @Column(name="nome")
        public String nome;
        
        @Column(name="sobrenome")
        public String sobrenome;
        
        @Column(name="email")
        public String email;
        
        public Cliente () {
            
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        @Override
        public String toString() {
            return "Cliente [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email + "]";
        }
    
    }

No pacote `dominio.springmvchb.service`, crie os arquivos:

**ClienteService.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteService {
        
        public List<Cliente> getClientes();
        
        public void saveCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
        public void deleteCliente(int oId);
    
    }

**ClienteServiceImpl.java**

    package dominio.springmvchb.service;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    import org.springframework.transaction.annotation.Transactional;
    
    import dominio.springmvchb.dao.ClienteDAO;
    import dominio.springmvchb.entity.Cliente;
    
    @Service
    public class ClienteServiceImpl implements ClienteService {
        
        @Autowired
        private ClienteDAO clienteDAO;
    
        @Override
        @Transactional
        public List<Cliente> getClientes() {
            return clienteDAO.getClientes();
        }
    
        @Override
        @Transactional
        public void saveCliente(Cliente oCliente) {
            clienteDAO.saveCliente(oCliente);        
        }
    
        @Override
        @Transactional
        public Cliente getCliente(int oId) {
            return clienteDAO.getCliente(oId);
        }
    
        @Override
        @Transactional
        public void deleteCliente(int oId) {
            clienteDAO.deleteCliente(oId);  
            
        }
    
    }

No pacote `dominio.springmvchb.rest`, crie o arquivo:

**ClienteRestController.java**

    package dominio.springmvchb.rest;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @RestController
    @RequestMapping("/api")
    public class ClienteRestController {
        
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/clientes")
        public List<Cliente> getClientes() {
            return clienteService.getClientes();
        }
    
    }

Na pasta `src/main/webapp`, crie o arquivo `index.jsp`:

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Página inicial - REST</title>
    </head>
    <body>
    
        <p>Páginas JSP não são necessárias para REST, isto aqui é apenas para conveniência</p>
        
        <br>
        
        <ul>
            <li><a href="${pageContext.request.contextPath}/api/clientes">api/clientes</a></li>
        </ul>
    
    </body>
    </html>

### Leitura de um único cliente<span id="springrest_crud_r1"></span>

Simplesmente edite o arquivo `ClienteRestController.java`:

    package dominio.springmvchb.rest;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @RestController
    @RequestMapping("/api")
    public class ClienteRestController {
        
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/clientes")
        public List<Cliente> getClientes() {
            return clienteService.getClientes();
        }
        
        @GetMapping("/clientes/{clienteId}")
        public Cliente getCliente(@PathVariable int clienteId) {
            
            Cliente oCliente = clienteService.getCliente(clienteId);
            
            return oCliente;
        }
    
    }

### Exception Handling<span id="springrest_crud_exceptionhandling"></span>

No pacote `dominio.springmvchb.rest`, crie o arquivo:

**ClienteErrorResponse.java**

    package dominio.springmvchb.rest;
    
    public class ClienteErrorResponse {
        
        private int status;
        private String message;
        private long timeStamp;
        
        public ClienteErrorResponse () {
            
        }
    
        public ClienteErrorResponse(int status, String message, long timeStamp) {
            this.status = status;
            this.message = message;
            this.timeStamp = timeStamp;
        }
    
        public int getStatus() {
            return status;
        }
    
        public void setStatus(int status) {
            this.status = status;
        }
    
        public String getMessage() {
            return message;
        }
    
        public void setMessage(String message) {
            this.message = message;
        }
    
        public long getTimeStamp() {
            return timeStamp;
        }
    
        public void setTimeStamp(long timeStamp) {
            this.timeStamp = timeStamp;
        }
        
    }

Comece a criar a classe chamada `ClienteNotFoundException`, em *Superclass* procure por `RuntimeException` e marque a opção `Constructors from superclass`

    package dominio.springmvchb.rest;
    
    public class ClienteNotFoundException extends RuntimeException {
    
        private static final long serialVersionUID = 1L;
    
        public ClienteNotFoundException() {
            
        }
    
        public ClienteNotFoundException(String message) {
            super(message);
        }
    
        public ClienteNotFoundException(Throwable cause) {
            super(cause);
        }
    
        public ClienteNotFoundException(String message, Throwable cause) {
            super(message, cause);
        }
    
        public ClienteNotFoundException(String message, Throwable cause, boolean enableSuppression,
                boolean writableStackTrace) {
            super(message, cause, enableSuppression, writableStackTrace);
        }
    
    }

Atualize o controller `ClienteRestController`:

    package dominio.springmvchb.rest;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @RestController
    @RequestMapping("/api")
    public class ClienteRestController {
        
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/clientes")
        public List<Cliente> getClientes() {
            return clienteService.getClientes();
        }
        
        @GetMapping("/clientes/{clienteId}")
        public Cliente getCliente(@PathVariable int clienteId) {
            
            Cliente oCliente = clienteService.getCliente(clienteId);
            
            if (oCliente == null) {
                throw new ClienteNotFoundException("Cliente não encontrado - " + clienteId);
            }
            
            return oCliente;
        }
    
    }

Crie o nosso exception handler chamado `ClienteRestExceptionHandler`:

    package dominio.springmvchb.rest;
    
    import org.springframework.http.HttpStatus;
    import org.springframework.http.ResponseEntity;
    import org.springframework.web.bind.annotation.ControllerAdvice;
    import org.springframework.web.bind.annotation.ExceptionHandler;
    
    @ControllerAdvice
    public class ClienteRestExceptionHandler {
    
        @ExceptionHandler
        public ResponseEntity<ClienteErrorResponse> handleException(ClienteNotFoundException exc) {
            
            ClienteErrorResponse error = new ClienteErrorResponse(
                    HttpStatus.NOT_FOUND.value(),
                    exc.getMessage(),
                    System.currentTimeMillis());
            
            return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
        }
        
        @ExceptionHandler
        public ResponseEntity<ClienteErrorResponse> handleException(Exception exc) {
            
            ClienteErrorResponse error = new ClienteErrorResponse(
                    HttpStatus.BAD_REQUEST.value(),
                    exc.getMessage(),
                    System.currentTimeMillis());
            
            return new ResponseEntity<>(error, HttpStatus.BAD_REQUEST);
        }
        
    }

### Adição de um cliente<span id="springrest_crud_c"></span>

Atualize o arquivo `ClienteRestController.java`:

    package dominio.springmvchb.rest;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.RequestBody;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @RestController
    @RequestMapping("/api")
    public class ClienteRestController {
        
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/clientes")
        public List<Cliente> getClientes() {
            return clienteService.getClientes();
        }
        
        @GetMapping("/clientes/{clienteId}")
        public Cliente getCliente(@PathVariable int clienteId) {
            
            Cliente oCliente = clienteService.getCliente(clienteId);
            
            if (oCliente == null) {
                throw new ClienteNotFoundException("Cliente não encontrado - " + clienteId);
            }
            
            return oCliente;
        }
        
        @PostMapping("/clientes")
        public Cliente addCliente(@RequestBody Cliente oCliente) {
            
            oCliente.setId(0); // Deixei um comentário explicando porque o ID foi definido como 0
            
            clienteService.saveCliente(oCliente); // Usamos @RequestBody para acessar o request body como um POJO
            
            return oCliente;
            
        }
    
    }

A *annotation* `@RequestBody` vincula o POJO ao parâmetro do método. No controller REST, explicitamente definimos o ID do cliente como 0 porque o DAO no backend usa o método Hibernate `session.saveOrUpdate(..)`, se a *primary key* está *empty* (*null* ou 0), o sistema INSERT um novo cliente, caso contrário UPDATE um cliente existente.

Agora você já pode testar, basta rodar o aplicativo como servidor e abrir o POstman para realizar a operação de POST. Selecione POST, ponha a URL com `api/clientes`, clique na aba *body*, selecione *raw*, na mesma barra escolha *JSON* (o padrão será *Text*). O conteúdo será:

    {
        "nome" : "Juliana",
        "sobrenome" : "Couto",
        "email" : "ju@gmail.com"
    }

Clique no botão *Send*. Se tudo deu xerto, repare que até o banco de dados MySQL foi atualizado.

### Atualização de um cliente<span id="springrest_crud_u"></span>

Atualize o arquivo `ClienteRestController.java`:

    package dominio.springmvchb.rest;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.PutMapping;
    import org.springframework.web.bind.annotation.RequestBody;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @RestController
    @RequestMapping("/api")
    public class ClienteRestController {
        
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/clientes")
        public List<Cliente> getClientes() {
            return clienteService.getClientes();
        }
        
        @GetMapping("/clientes/{clienteId}")
        public Cliente getCliente(@PathVariable int clienteId) {
            
            Cliente oCliente = clienteService.getCliente(clienteId);
            
            if (oCliente == null) {
                throw new ClienteNotFoundException("Cliente não encontrado - " + clienteId);
            }
            
            return oCliente;
        }
        
        @PostMapping("/clientes")
        public Cliente addCliente(@RequestBody Cliente oCliente) {
            
            oCliente.setId(0);
            
            clienteService.saveCliente(oCliente);
            
            return oCliente;
            
        }
        
        @PutMapping("/clientes")
        public Cliente updateCliente(@RequestBody Cliente oCliente) {
            
            clienteService.saveCliente(oCliente);
            
            return oCliente;
            
        }
    
    }

No Postman, você usará o PUT agora. Do resto você repetirá o mesmo procedimento. Vamos dizer que quero editar o cliente cujo ID é 1:

    {
        "id" : 1,
        "nome" : "Hugo",
        "sobrenome" : "Castro",
        "email" : "hugo@gmail.com"
    }

### Deleção de um cliente<span id="springrest_crud_d"></span>

Atualize o arquivo `ClienteRestController.java`:

    package dominio.springmvchb.rest;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.web.bind.annotation.DeleteMapping;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.PutMapping;
    import org.springframework.web.bind.annotation.RequestBody;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @RestController
    @RequestMapping("/api")
    public class ClienteRestController {
        
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/clientes")
        public List<Cliente> getClientes() {
            return clienteService.getClientes();
        }
        
        @GetMapping("/clientes/{clienteId}")
        public Cliente getCliente(@PathVariable int clienteId) {
            
            Cliente oCliente = clienteService.getCliente(clienteId);
            
            if (oCliente == null) {
                throw new ClienteNotFoundException("Cliente não encontrado - " + clienteId);
            }
            
            return oCliente;
        }
        
        @PostMapping("/clientes")
        public Cliente addCliente(@RequestBody Cliente oCliente) {
            
            oCliente.setId(0);
            
            clienteService.saveCliente(oCliente);
            
            return oCliente;
            
        }
        
        @PutMapping("/clientes")
        public Cliente updateCliente(@RequestBody Cliente oCliente) {
            
            clienteService.saveCliente(oCliente);
            
            return oCliente;
            
        }
        
        @DeleteMapping("/clientes/{clienteId}")
        public String deleteCliente(@PathVariable int clienteId) {
            
            Cliente clienteTemp = clienteService.getCliente(clienteId);
            
            if (clienteTemp == null) {
                throw new ClienteNotFoundException("Cliente não encontrado - " + clienteId);
            }
            
            clienteService.deleteCliente(clienteId);
            
            return "Foi deletado o cliente cujo ID é " + clienteId;
            
        }
    
    }

Nesta vez será diferente no Postman, escolha a opção DELETE e apenas envie o link com a ID do cliente que você quer deletar, por exemplo [http://localhost:8080/springmvchb/api/clientes/2](http://localhost:8080/springmvchb/api/clientes/2).

## BÔNUS: O projeto final<span id="springrest_final"></span>

Crie o projeto como projeto Maven. Criarei meu projeto Maven com *Group Id* como `dominio` e *Artefact Id* como `springmvchb`.

Vamos ao banco de dados, use o seguinte comando:

Se você ainda não tiver o usuário `estudante`

    CREATE USER 'estudante'@'localhost' IDENTIFIED BY 'estudante';
    GRANT ALL PRIVILEGES ON * .* TO 'estudante'@'localhost';

O comando de fato:

    CREATE DATABASE IF NOT EXISTS `cliente_web`;
    USE `cliente_web`;
    
    DROP TABLE IF EXISTS `cliente`;
    CREATE TABLE `cliente` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=latin1;
    
    LOCK TABLES `cliente` WRITE;
    
    INSERT INTO `cliente` VALUES 
    	(1,'Marcelino','Travolta','marcelino@gmail.com'),
    	(2,'Cuca','Beludo','culudo@gmail.com'),
    	(3,'Paula','Barbosa','paulinha@gmail.com'),
    	(4,'Oscar','Alho','alho@gmail.com'),
    	(5,'Maria','Freitas','maria@gmail.com');
    
    UNLOCK TABLES;

Agora vejamos nosso arquivo `pom.xml`:

    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>dominio</groupId>
        <artifactId>springmvchb</artifactId>
        <version>1.0.0</version>
        <packaging>war</packaging>
    
        <properties>
            <springframework.version>5.3.20</springframework.version>
            <hibernate.version>5.6.9.Final</hibernate.version>
            <mysql.connector.version>8.0.29</mysql.connector.version>
            <c3p0.version>0.9.5.5</c3p0.version>
    
            <maven.compiler.source>17</maven.compiler.source>
            <maven.compiler.target>17</maven.compiler.target>
        </properties>
    
        <dependencies>
    
            <!-- Spring Framework -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-webmvc</artifactId>
                <version>${springframework.version}</version>
            </dependency>
    
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-tx</artifactId>
                <version>${springframework.version}</version>
            </dependency>
    
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-orm</artifactId>
                <version>${springframework.version}</version>
            </dependency>
    
            <dependency>
                <groupId>com.fasterxml.jackson.core</groupId>
                <artifactId>jackson-databind</artifactId>
                <version>2.13.3</version>
            </dependency>
    
            <dependency>
                <groupId>org.hibernate</groupId>
                <artifactId>hibernate-core</artifactId>
                <version>${hibernate.version}</version>
            </dependency>
    
            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>${mysql.connector.version}</version>
            </dependency>
    
            <dependency>
                <groupId>com.mchange</groupId>
                <artifactId>c3p0</artifactId>
                <version>${c3p0.version}</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>javax.servlet-api</artifactId>
                <version>3.1.0</version>
            </dependency>
    
            <dependency>
                <groupId>javax.servlet.jsp</groupId>
                <artifactId>javax.servlet.jsp-api</artifactId>
                <version>2.3.1</version>
            </dependency>
    
            <!-- to compensate for java 9+ not including jaxb -->
            <dependency>
                <groupId>javax.xml.bind</groupId>
                <artifactId>jaxb-api</artifactId>
                <version>2.3.0</version>
            </dependency>
    
        </dependencies>
    
        <!-- Add support for Maven WAR Plugin -->
        <build>
            <finalName>springmvchb</finalName>
                <plugins>
                    <!-- Add Maven coordinates for> maven-war-plugin -->
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-war-plugin</artifactId>
                        <version>3.3.2</version>
                    </plugin>
                </plugins>
        </build>
    </project>

Na pasta `src/main/resources`, crie o arquivo:

**persistence-mysql.properties**

    #
    # JDBC connection properties
    #
    jdbc.driver=com.mysql.cj.jdbc.Driver
    jdbc.url=jdbc:mysql://localhost:3306/cliente_web?useSSL=false&serverTimezone=UTC
    jdbc.user=estudante
    jdbc.password=estudante
    
    #
    # Connection pool properties
    #
    connection.pool.initialPoolSize=5
    connection.pool.minPoolSize=5
    connection.pool.maxPoolSize=20
    connection.pool.maxIdleTime=3000
    
    #
    # Hibernate properties
    #
    hibernate.dialect=org.hibernate.dialect.MySQLDialect
    hibernate.show_sql=true
    hibernate.packagesToScan=dominio.springmvchb.entity

Na pasta `src/main/webapp`, crie o arquivo:

**index.jsp**

    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Página inicial - REST</title>
    </head>
    <body>
    
        <p>Páginas JSP não são necessárias para REST, isto aqui é apenas para conveniência</p>
        
        <br>
        
        <ul>
            <li><a href="${pageContext.request.contextPath}/api/clientes">api/clientes</a></li>
        </ul>
    
    </body>
    </html>

Crie os seguintes pacotes:

* `dominio.springmvchb.config`

* `dominio.springmvchb.dao`

* `dominio.springmvchb.entity`

* `dominio.springmvchb.service`

* `dominio.springmvchb.rest`

No pacote `dominio.springmvchb.config`, crie os arquivos:

**AppConfig.java**

    package dominio.springmvchb.config;
    
    import java.beans.PropertyVetoException;
    import java.util.Properties;
    import java.util.logging.Logger;
    
    import javax.sql.DataSource;
    
    import org.hibernate.SessionFactory;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.ComponentScan;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.context.annotation.PropertySource;
    import org.springframework.core.env.Environment;
    import org.springframework.orm.hibernate5.HibernateTransactionManager;
    import org.springframework.orm.hibernate5.LocalSessionFactoryBean;
    import org.springframework.transaction.annotation.EnableTransactionManagement;
    import org.springframework.web.servlet.config.annotation.EnableWebMvc;
    import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;
    
    import com.mchange.v2.c3p0.ComboPooledDataSource;
    
    @Configuration
    @EnableWebMvc
    @EnableTransactionManagement
    @ComponentScan(basePackages="dominio.springmvchb")
    @PropertySource("classpath:persistence-mysql.properties")
    public class AppConfig implements WebMvcConfigurer {
        
        @Autowired
        private Environment env;
        
        private Logger logger = Logger.getLogger(getClass().getName());
        
    
        @Bean
        public DataSource myDataSource() {
            
            ComboPooledDataSource myDataSource = new ComboPooledDataSource();
    
            try {
                myDataSource.setDriverClass(env.getProperty("jdbc.driver"));       
            }
            catch (PropertyVetoException exc) {
                throw new RuntimeException(exc);
            }
            
            logger.info(">> jdbc.url=" + env.getProperty("jdbc.url"));
            logger.info(">> jdbc.user=" + env.getProperty("jdbc.user"));
            
            myDataSource.setJdbcUrl(env.getProperty("jdbc.url"));
            myDataSource.setUser(env.getProperty("jdbc.user"));
            myDataSource.setPassword(env.getProperty("jdbc.password"));
            
            myDataSource.setInitialPoolSize(getIntProperty("connection.pool.initialPoolSize"));
            myDataSource.setMinPoolSize(getIntProperty("connection.pool.minPoolSize"));
            myDataSource.setMaxPoolSize(getIntProperty("connection.pool.maxPoolSize"));     
            myDataSource.setMaxIdleTime(getIntProperty("connection.pool.maxIdleTime"));
    
            return myDataSource;
        }
        
        private Properties getHibernateProperties() {
    
            // set hibernate properties
            Properties props = new Properties();
    
            props.setProperty("hibernate.dialect", env.getProperty("hibernate.dialect"));
            props.setProperty("hibernate.show_sql", env.getProperty("hibernate.show_sql"));
            
            return props;
        }
    
        
        private int getIntProperty(String propName) {
            
            String propVal = env.getProperty(propName);
            
            int intPropVal = Integer.parseInt(propVal);
            
            return intPropVal;
        }   
        
        @Bean
        public LocalSessionFactoryBean sessionFactory(){
            
            LocalSessionFactoryBean sessionFactory = new LocalSessionFactoryBean();
            
            sessionFactory.setDataSource(myDataSource());
            sessionFactory.setPackagesToScan(env.getProperty("hibernate.packagesToScan"));
            sessionFactory.setHibernateProperties(getHibernateProperties());
            
            return sessionFactory;
        }
        
        @Bean
        @Autowired
        public HibernateTransactionManager transactionManager(SessionFactory sessionFactory) {
            
            // setup transaction manager based on session factory
            HibernateTransactionManager txManager = new HibernateTransactionManager();
            txManager.setSessionFactory(sessionFactory);
    
            return txManager;
        }
    }

**MeuSpringMvcDispatcherServletInitializer.java**

    package dominio.springmvchb.config;
    
    import org.springframework.web.servlet.support.AbstractAnnotationConfigDispatcherServletInitializer;
    
    public class MeuSpringMvcDispatcherServletInitializer extends AbstractAnnotationConfigDispatcherServletInitializer {
    
        @Override
        protected Class<?>[] getRootConfigClasses() { // Não teremos arquivos de configuração root no nosso projeto
            // TODO Auto-generated method stub
            return null;
        }
    
        @Override
        protected Class<?>[] getServletConfigClasses() {
    
            return new Class[] {AppConfig.class};
        }
    
        @Override
        protected String[] getServletMappings() {
    
            return new String[] { "/" };
        }
    
    }

No pacote `dominio.springmvchb.dao`, crie os arquivos:

**ClienteDAO.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import dominio.springmvchb.entity.Cliente;
    
    public interface ClienteDAO {
        
        public List<Cliente> getClientes();
        
        public void saveCliente(Cliente oCliente);
    
        public Cliente getCliente(int oId);
    
        public void deleteCliente(int oId);
    
    }

**ClienteDAOImpl.java**

    package dominio.springmvchb.dao;
    
    import java.util.List;
    
    import org.hibernate.Session;
    import org.hibernate.SessionFactory;
    import org.hibernate.query.Query;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.springmvchb.entity.Cliente;
    
    @Repository
    public class ClienteDAOImpl implements ClienteDAO {
        
        @Autowired
        private SessionFactory sessionFactory;
                
        @Override
        public List<Cliente> getClientes() {
            
            Session currentSession = sessionFactory.getCurrentSession();
                    
            Query<Cliente> theQuery = currentSession.createQuery("from Cliente order by nome", Cliente.class);
            
            // execute query and get result list
            List<Cliente> clientes = theQuery.getResultList();
                    
            // return the results
            return clientes;
        }
    
        @Override
        public void saveCliente(Cliente oCliente) {
    
            Session currentSession = sessionFactory.getCurrentSession();
            
            currentSession.saveOrUpdate(oCliente);
            
        }
    
        @Override
        public Cliente getCliente(int oId) {
    
            // get the current hibernate session
            Session currentSession = sessionFactory.getCurrentSession();
            
            // now retrieve/read from database using the primary key
            Cliente oCliente = currentSession.get(Cliente.class, oId);
            
            return oCliente;
        }
    
        @Override
        public void deleteCliente(int oId) {
    
            // get the current hibernate session
            Session currentSession = sessionFactory.getCurrentSession();
            
            // delete object with primary key
            Query theQuery = currentSession.createQuery("delete from Cliente where id=:clienteId");
            theQuery.setParameter("clienteId", oId);
            
            theQuery.executeUpdate();       
        }
    
    }

No pacote `dominio.springmvchb.entity`, crie o arquivo:

**Cliente.java**

    package dominio.springmvchb.entity;
    
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="cliente")
    public class Cliente {
        
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        public int id;
        
        @Column(name="nome")
        public String nome;
        
        @Column(name="sobrenome")
        public String sobrenome;
        
        @Column(name="email")
        public String email;
        
        public Cliente () {
            
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        @Override
        public String toString() {
            return "Cliente [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email + "]";
        }
    
    }

No pacote `dominio.springmvchb.rest`, crie os arquivos:

**ClienteRestController.java**

    package dominio.springmvchb.rest;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.web.bind.annotation.DeleteMapping;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.PutMapping;
    import org.springframework.web.bind.annotation.RequestBody;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.springmvchb.entity.Cliente;
    import dominio.springmvchb.service.ClienteService;
    
    @RestController
    @RequestMapping("/api")
    public class ClienteRestController {
        
        @Autowired
        private ClienteService clienteService;
        
        @GetMapping("/clientes")
        public List<Cliente> getClientes() {
            return clienteService.getClientes();
        }
        
        @GetMapping("/clientes/{clienteId}")
        public Cliente getCliente(@PathVariable int clienteId) {
            
            Cliente oCliente = clienteService.getCliente(clienteId);
            
            if (oCliente == null) {
                throw new ClienteNotFoundException("Cliente não encontrado - " + clienteId);
            }
            
            return oCliente;
        }
        
        @PostMapping("/clientes")
        public Cliente addCliente(@RequestBody Cliente oCliente) {
            
            oCliente.setId(0);
            
            clienteService.saveCliente(oCliente);
            
            return oCliente;
            
        }
        
        @PutMapping("/clientes")
        public Cliente updateCliente(@RequestBody Cliente oCliente) {
            
            clienteService.saveCliente(oCliente);
            
            return oCliente;
            
        }
        
        @DeleteMapping("/clientes/{clienteId}")
        public String deleteCliente(@PathVariable int clienteId) {
            
            Cliente clienteTemp = clienteService.getCliente(clienteId);
            
            if (clienteTemp == null) {
                throw new ClienteNotFoundException("Cliente não encontrado - " + clienteId);
            }
            
            clienteService.deleteCliente(clienteId);
            
            return "Foi deletado o cliente cujo ID é " + clienteId;
            
        }
    
    }

**ClienteErrorResponse.java**

    package dominio.springmvchb.rest;
    
    public class ClienteErrorResponse {
        
        private int status;
        private String message;
        private long timeStamp;
        
        public ClienteErrorResponse () {
            
        }
    
        public ClienteErrorResponse(int status, String message, long timeStamp) {
            this.status = status;
            this.message = message;
            this.timeStamp = timeStamp;
        }
    
        public int getStatus() {
            return status;
        }
    
        public void setStatus(int status) {
            this.status = status;
        }
    
        public String getMessage() {
            return message;
        }
    
        public void setMessage(String message) {
            this.message = message;
        }
    
        public long getTimeStamp() {
            return timeStamp;
        }
    
        public void setTimeStamp(long timeStamp) {
            this.timeStamp = timeStamp;
        }
        
    }

**ClienteNotFoundException.java**

    package dominio.springmvchb.rest;
    
    public class ClienteNotFoundException extends RuntimeException {
    
        private static final long serialVersionUID = 1L;
    
        public ClienteNotFoundException() {
            
        }
    
        public ClienteNotFoundException(String message) {
            super(message);
        }
    
        public ClienteNotFoundException(Throwable cause) {
            super(cause);
        }
    
        public ClienteNotFoundException(String message, Throwable cause) {
            super(message, cause);
        }
    
        public ClienteNotFoundException(String message, Throwable cause, boolean enableSuppression,
                boolean writableStackTrace) {
            super(message, cause, enableSuppression, writableStackTrace);
        }
    
    }

**ClienteRestExceptionHandler.java**

    package dominio.springmvchb.rest;
    
    import org.springframework.http.HttpStatus;
    import org.springframework.http.ResponseEntity;
    import org.springframework.web.bind.annotation.ControllerAdvice;
    import org.springframework.web.bind.annotation.ExceptionHandler;
    
    @ControllerAdvice
    public class ClienteRestExceptionHandler {
    
        @ExceptionHandler
        public ResponseEntity<ClienteErrorResponse> handleException(ClienteNotFoundException exc) {
            
            ClienteErrorResponse error = new ClienteErrorResponse(
                    HttpStatus.NOT_FOUND.value(),
                    exc.getMessage(),
                    System.currentTimeMillis());
            
            return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
        }
        
        @ExceptionHandler
        public ResponseEntity<ClienteErrorResponse> handleException(Exception exc) {
            
            ClienteErrorResponse error = new ClienteErrorResponse(
                    HttpStatus.BAD_REQUEST.value(),
                    exc.getMessage(),
                    System.currentTimeMillis());
            
            return new ResponseEntity<>(error, HttpStatus.BAD_REQUEST);
        }
        
    }

# Spring Boot<span id="springboot"></span>

Finalmente chegamos no Spring Boot!!! 🎉🎉🎉

Bom, não é trivial o trabalho de criar uma aplicação Spring, temos que ver qual arquétipo do Maven utilizar, quais dependências usar, que tipo de configuração *(XML ou Java)* a ser utilizada e como instalar o servidor *(Tomcat, JBoss, etc) *.

Spring Boot facilita tudo minimizando a quantidade de configuração manual, nem sequer precisamos instalar um servidor separadamente, será gerado um arquivo JAR com seu código e o Tomcat. Mas você pode fazer o *deploy* como um arquivo WAR para que este seja rodade num servidor externo.
 
O Spring Boot não substitui as tecnologias que estudamos até aqui, na verdade, ele as usa, dentro dele tem Spring Core, Spring AOP, Spring MVC, Spring REST, etc.

Apesar do time do Spring oferecer o [Spring Tool Suite (STS)](https://spring.io/tools/), você pode desenvolver mesmo com o bloco de notas.

## Spring Initializr<span id="springboot_initializr"></span>

É um site *(aqui o [link](https://start.spring.io/)* que permite criar um projeto Spring rapidamente, nos permitindo selecionar as dependências, criar um projeto Maven/Gradle e importar o projeto para a IDE.

*Quando você configurar seu projeto no site, escolha a última versão do Spring Boot, mas evite as marcadas como `(SNAPSHOT)` porque elas são versões alfa/beta*

*Em `Dependencies`, podemos simplesmente digitar "web" que aparecerá a opção `Spring Web` que é a que queremos.*

*Apenas como referência, deixei o nome do meu projeto como `demo` mesmo.*

Com tudo definido, clicamos em `Download` ou `Generate`, baixamos um arquivo ZIP, extraimos o conteúdo desse arquivo e importamos o conteúdo como um projeto Maven/Gradle.

No Eclipse: `File` => `Import` => `Existing Maven Projects` => Selecione a pasta que você descompactou do récem baixado arquivo ZIP

Espere um pouquinho para o Maven baixar as dependências. Pode demorar um bocadinho...

Quando tudo estiver carregado, **rode o arquivo java com o método main como Java Application**, não precisa ser mais como servidor porque o Sprign Boot já inclui seu próprio servidor. Outra coisa que não sei se você prestou atenção, **é para rodar o arquivo .java, não a pasta do projeto**!!!

Você pode ir até o endereço [http://localhost:8080/](http://localhost:8080/) ver  que o servidor está funcionando.

Vamos ver como ficou o `pom.xml` gerado no projeto:

    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    	<modelVersion>4.0.0</modelVersion>
    	<parent>
    		<groupId>org.springframework.boot</groupId>
    		<artifactId>spring-boot-starter-parent</artifactId>
    		<version>3.0.0-M3</version>
    		<relativePath/> <!-- lookup parent from repository -->
    	</parent>
    	<groupId>dominio</groupId>
    	<artifactId>demo</artifactId>
    	<version>0.0.1-SNAPSHOT</version>
    	<name>demo</name>
    	<description>Demo project for Spring Boot</description>
    	<properties>
    		<java.version>17</java.version>
    	</properties>
    	<dependencies>
    		<dependency>
    			<groupId>org.springframework.boot</groupId>
    			<artifactId>spring-boot-starter-web</artifactId>
    		</dependency>
    
    		<dependency>
    			<groupId>org.springframework.boot</groupId>
    			<artifactId>spring-boot-starter-test</artifactId>
    			<scope>test</scope>
    		</dependency>
    	</dependencies>
    
    	<build>
    		<plugins>
    			<plugin>
    				<groupId>org.springframework.boot</groupId>
    				<artifactId>spring-boot-maven-plugin</artifactId>
    			</plugin>
    		</plugins>
    	</build>
    	<repositories>
    		<repository>
    			<id>spring-milestones</id>
    			<name>Spring Milestones</name>
    			<url>https://repo.spring.io/milestone</url>
    			<snapshots>
    				<enabled>false</enabled>
    			</snapshots>
    		</repository>
    	</repositories>
    	<pluginRepositories>
    		<pluginRepository>
    			<id>spring-milestones</id>
    			<name>Spring Milestones</name>
    			<url>https://repo.spring.io/milestone</url>
    			<snapshots>
    				<enabled>false</enabled>
    			</snapshots>
    		</pluginRepository>
    	</pluginRepositories>
    
    </project>

*<span style="color: red;">Cometi um vacilo e baixei a versão (M3), essa não é a versão que eu deveria ter baixado, mas tudo bem...</span>*

Vamos ver essas dependências.`spring-boot-starter-web` é uma coleção de dependências do Maven que são compatíveis, contém: spring-web, spring-webmvc, hibernate-validator, json, tomcat, etc. Vejamos o que tem nos principais Spring Boot Starters:

| Nome                    | Descrição                                |
| ----------------------- | ---------------------------------------- |
| spring-boot-starter-web | Criação de aplicativos web, inclui validação e REST; usa Tomcat como servidor padrão |
| spring-boot-starter-security | Adiciona suporte ao Spring Security |
| spring-boot-starter-data-jpa | Adiciona suporte ao JPA e Hibernate |

Você pode ver mais [aqui](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#using.build-systems.starters).

Se você quiser ver as dependências com detalhes, no Eclipse, abra o arquivo `pom.xml` e clique na aba *Dependency Hierarchy*

A propósito, o `spring-boot-starter-parent` define a versão do Spring Boot, por isso que o resto das dependências não tem versão, porque isso já foi definido pela versão do Spring Boot selecionada.

E o Spring Boot criou um pacote `dominio.demo` com a classe principal `DemoApplication.java` *(que tem esse nome porque deixei no padrão, se você tivesse gerado seu projeto com o nome "Meuprograma", o nome completo do arquivo seria `dominio.meuprograma.MeuprogramaApplication`)*

    package dominio.demo;
    
    import org.springframework.boot.SpringApplication;
    import org.springframework.boot.autoconfigure.SpringBootApplication;
    
    @SpringBootApplication
    public class DemoApplication {
    
    	public static void main(String[] args) {
    		SpringApplication.run(DemoApplication.class, args);
    	}
    
    }

A *annotation* `@SpringBootApplication` habilita auto-configuração (`@EnableAutoConfiguration`), escaneamento de componentes (`@ComponentScan`) e configurações adicionais (`@Configuration`). O Spring Boot automaticamente escaneia subpacotes, mas para escanear pacotes em outros lugares você precisa declará-los explicitamente.

Também temos outras novidades, que são os arquivos `mvnw` (`mvnw` e `mvnw.cmd`): `mvnw` é pra Linux ou Mac e `mvnw.cmd` é pra Windows, ele serve para baixar a versão correta do Maven caso você não tenha esta instalada.  Esses arquivos são desnecessários se você já tiver o Maven instalado no seu computador.

Isso aqui é importante: Nunca use a pasta `src/main/webapp` se a aplicação for empacotada em JAR, porque isso só funciona no empacotamento WAR.

## Uma página inicial bem simples<span id="springboot_simplehome"></span>

Crie o pacote `dominio.demo.rest` *(é a última vez que falo isso, estou assumindo aqui que o nome do seu projeto é `demo`, se for diferente vá adaptando os códigos que eu for lhe passando)*. Neste pacote, crie a seguinte classe:

**AppRestController.java**

    package dominio.demo.rest;
    
    import java.time.LocalDateTime;
    
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    @RestController
    public class AppRestController {
        
        @GetMapping("/")
        public String olaMundo() {
            return "Olá Mundo! Hora no servidor é " + LocalDateTime.now();
        }
    
    }

## Spring Boot Dev Tools<span id="springboot_devtools"></span>

Quando editamos algo no código de um projeto feito com Spring Boot, temos que reiniciar a aplicação manualmente. Para deixar as coisas mais automáticas é usar  `spring-boot-devtools`:

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
    </dependency>

## Spring Boot Actuator<span id="springboot_actuator"></span>

Para monitorar a aplicação, checar seu *status* e métricas, podemos usar o Spring Boot Actuator, com ele os *REST Endpoints* são adicionados automaticamente.

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-actuator</artifactId>
    </dependency>

Eis os *endpoint* prefixados com `/actuator`

| Nome     | Descrição                                               |
| -------- | ------------------------------------------------------- |
| /health  | Informação da saúde/status da sua aplicação             |
| /info    | Informação sobre o projeto                              |
| /metrics | Mostra diversas informações de métrica da sua aplicação |

*Há mais. Mas saiba que apenas `/health` é exposto por padrão, para exibir TUDO precisamos adicionar a linha `management.endpoints.web.exposure.include=*` no arquivo `application.properties`. Para exibir alguns poucos, pode ser assim `management.endpoints.web.exposure.include=health,info`*

*O endpoint `/info` também requer, no arquivo `application.properties`, a linha `management.info.env.enabled=true`*

*Para excluir, usamos a linha `management.endpoints.web.exposure.exclude=<escreva-aqui-os-endpoints-a-serem-excluídos>`*

Meu arquivo .properties ficou assim:

    management.endpoints.web.exposure.include=*
    management.info.env.enabled=true
    
    info.app.name=Demo
    info.app.description=Uma aplicação interessante
    info.app.version=1.0.0

Com o aplicativo rodando, você pode testar o `/health` acessando este link [http://localhost:8080/actuator/health](http://localhost:8080/actuator/health).

Quanto ao /info, ele lê informações do arquivo `application.properties`

## Segurança<span id="springboot_security"></span>

Não queremos que tudo fique exposto. Pra resolver esse problema, começamos adicionando a dependência do Spring Security  no `pom.xml`.

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-security</artifactId>
    </dependency>

*Eu tive problemas com o Maven (o arquivo `pom.xml` acusava que tinha algo errado)porque eu tinha caracteres especiais ('ç', 'ã'), no arquivo properties, o que estava causando erro.*

    management.endpoints.web.exposure.include=*
    management.info.env.enabled=true
    
    info.app.name=Demo
    info.app.description=Uma aplicacao interessante
    info.app.version=1.0.0

Quando tento acessar, por exemplo, http://localhost:8080/actuator/beans](http://localhost:8080/actuator/beans), será-me pedido um login e uma senha; por *default* o login é `user` e a senha é dada nos *console logs*. Mas no arquivo properties posso definir o usuário e senha, por exemplo:

    spring.security.user.name=henrique
    spring.security.user.password=12345

## Como rodar aplicativos do Spring Boot via linha de comando<span id="springboot_commandline"></span>

Veremos como rodar uma aplicação do Spring Boot sem a ajuda de uma IDE. O passo-a-passo:

1. Fecha a IDE

2. Empacota o aplicativo usando `mvnw package`

3. Roda o aplicativo com o comando `java -jar` ou `mvnw spring-boot:run` *(um desses dois)*

Vamos dizer que estou com o terminal ou prompt de comando aberto na pasta do meu projeto, no Linux ou MacOS rodo o comando `./mvnw package`, enquanto no Windows o comando é `mvnw package` *(se você já tiver o Maven instalado no seu sistema, simplesmente use o comando `mvn package`)*. O arquivo JAR será gerado na pasta `target`. No meu caso aqui, o nome do meu arquivo é `demo-0.0.1-SNAPSHOT.jar`, se o seu for diferente, procure modificar o nome do comando que passarei a seguir. Bom, entre na pasta `target` e rode um dos comandos abaixo:

* `java -jar demo-0.0.1-SNAPSHOT.jar`

* A outra opção seria permanecer na pasta onde se encontram os arquivos *mvnw* e usar o comando `mvnw spring-boot:run` puro.

## Application Properties<span id="springboot_applicationproperties"></span>

Se você ainda estiver usando o projeto anterior ou uma cópia deste, você pode agora remover as dependências relativas ao `spring-boot-starter-actuator` e `spring-boot-starter-security`.

**application.properties**

    treinador.nome=Lucas
    time.nome=Bota Fogo

**AppRestController.java**

    package dominio.demo.rest;
    
    import org.springframework.beans.factory.annotation.Value;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    @RestController
    public class AppRestController {
        
        @Value("${treinador.nome}")
        private String treinador;
        
        @Value("${time.nome}")
        private String time;
        
        @GetMapping("/")
        public String olaMundo() {
            return "O nome do treinador é " + treinador + " e seu time é o " + time;
        }
    
    }

Este só foi um exemplo simples, você pode ver a lista de propriedades [aqui](https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html)

Um exemplo é o `server.port`, se escrevo por exemplo

    server.port=7071

O link da minha aplicação será [http://localhost:7071/](http://localhost:7071/)

## REST API com Hibernate<span id="springboot_resthibernate"></span>

Ajeite o banco de dados:

    CREATE DATABASE IF NOT EXISTS `empregadodb`;
    USE `empregadodb`;
    
    DROP TABLE IF EXISTS `empregado`;
    
    CREATE TABLE `empregado` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;
    
    
    INSERT INTO `empregado` VALUES 
    	(1,'Marcelino','Travolta','marcelino@gmail.com'),
    	(2,'Cuca','Beludo','culudo@gmail.com'),
    	(3,'Paula','Barbosa','paulinha@gmail.com'),
    	(4,'Oscar','Alho','alho@gmail.com'),
    	(5,'Maria','Freitas','maria@gmail.com');

No Spring Initializr, coloquei o *Group* como `dominio` e o *Artifact/Name* como `crudhb`. Na parte das dependências, selecionei `Spring Web`, `Spring Boot DevTools` `Spring Data JPA`, `MySQL Driver`

Aqui está o `pom.xml` do projeto

    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    	<modelVersion>4.0.0</modelVersion>
    	<parent>
    		<groupId>org.springframework.boot</groupId>
    		<artifactId>spring-boot-starter-parent</artifactId>
    		<version>2.7.0</version>
    		<relativePath/> <!-- lookup parent from repository -->
    	</parent>
    	<groupId>dominio</groupId>
    	<artifactId>crudhb</artifactId>
    	<version>0.0.1-SNAPSHOT</version>
    	<name>crudhb</name>
    	<description>Demo project for Spring Boot</description>
    	<properties>
    		<java.version>17</java.version>
    	</properties>
    	<dependencies>
    		<dependency>
    			<groupId>org.springframework.boot</groupId>
    			<artifactId>spring-boot-starter-data-jpa</artifactId>
    		</dependency>
    		<dependency>
    			<groupId>org.springframework.boot</groupId>
    			<artifactId>spring-boot-starter-web</artifactId>
    		</dependency>
    
    		<dependency>
    			<groupId>org.springframework.boot</groupId>
    			<artifactId>spring-boot-devtools</artifactId>
    			<scope>runtime</scope>
    			<optional>true</optional>
    		</dependency>
    		<dependency>
    			<groupId>mysql</groupId>
    			<artifactId>mysql-connector-java</artifactId>
    			<scope>runtime</scope>
    		</dependency>
    		<dependency>
    			<groupId>org.springframework.boot</groupId>
    			<artifactId>spring-boot-starter-test</artifactId>
    			<scope>test</scope>
    		</dependency>
    	</dependencies>
    
    	<build>
    		<plugins>
    			<plugin>
    				<groupId>org.springframework.boot</groupId>
    				<artifactId>spring-boot-maven-plugin</artifactId>
    			</plugin>
    		</plugins>
    	</build>
    
    </project>

*No meu caso, assim que eu importei o projeto e as dependências foram baixadas, eu recebi a seguinte mensagem de erro:*

    Failed to execute goal org.apache.maven.plugins:maven-surefire-plugin:2.22.2:test (default-test) on project crudhb: There are test failures.

Resolvi o problema simplesmente clicando com o botão direito do mouse sobre o projeto= > `Maven` => Update Project...`

Vamos começar com os dados do nosso banco de dados:

**application.properties**

    # JDBC Properties
    
    spring.datasource.url=jdbc:mysql://localhost:3306/empregadodb?useSSL=false&serverTimezone=UTC
    spring.datasource.username=estudante
    spring.datasource.password=estudante

O Spring Boot configura tão bem as coisas que até o nome de classe do driver JDBC é automaticamente detectado por meio da URL.

Crie o pacote `dominio.crudhb.entity` e dentro deste crie a classe `Empregado`:

    package dominio.crudhb.entity;
    
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="empregado")
    public class Empregado {
        
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="nome")
        private String nome;
        
        @Column(name="sobrenome")
        private String sobrenome;
        
        @Column(name="email")
        private String email;
        
        public Empregado() {
            
        }
    
        public Empregado(String nome, String sobrenome, String email) {
            this.nome = nome;
            this.sobrenome = sobrenome;
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        @Override
        public String toString() {
            return "Empregado [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email + "]";
        }
    
    }

Crie o pacote `dominio.crudhb.dao` e dentro dele os arquivos:

**EmpregadoDAO.java**

    package dominio.crudhb.dao;
    
    import java.util.List;
    
    import dominio.crudhb.entity.Empregado;
    
    public interface EmpregadoDAO {
        
        public List<Empregado> findAll();
        
        public Empregado findById(int theId);
        
        public void save(Empregado empregado);
        
        public void deleteById(int theId);
    
    }

**EmpregadoDAOHibernateImpl.java**

    package dominio.crudhb.dao;
    
    import java.util.List;
    
    import javax.persistence.EntityManager;
    
    import org.hibernate.Session;
    import org.hibernate.query.Query;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.crudhb.entity.Empregado;
    
    @Repository
    public class EmpregadoDAOHibernateImpl implements EmpregadoDAO {
        
        private EntityManager entityManager;
        
        @Autowired
        public EmpregadoDAOHibernateImpl(EntityManager entityManager) { // Este EntityManager entityManager aplica a dieia do Instructor INjection
            this.entityManager = entityManager;
        }
    
        @Override
        public List<Empregado> findAll() {
            
            Session currentSession = entityManager.unwrap(Session.class); // Parece ser redundante a criação de um objeto Session em cada método, mas é que se eu declarar como "global", isso afetará o session pool e trará o problema de return too many connection
            
            Query<Empregado> theQuery = currentSession.createQuery("from Empregado", Empregado.class);
            
            List<Empregado> empregados = theQuery.getResultList();
    
            return empregados;
        }
    
        @Override
        public Empregado findById(int theId) {
            
            Session currentSession = entityManager.unwrap(Session.class);
            
            Empregado empregado = currentSession.get(Empregado.class, theId);
            
            return empregado;
        }
    
        @Override
        public void save(Empregado empregado) {
            
            Session currentSession = entityManager.unwrap(Session.class);
            
            currentSession.saveOrUpdate(empregado); // Se o ID for 0, ele cria um novo, caso contrário será uma operação de update
            
        }
    
        @Override
        public void deleteById(int theId) {
            
            Session currentSession = entityManager.unwrap(Session.class);
            
            Query theQuery = currentSession.createQuery("delete from Empregado where id=:EmpregadoId");
            theQuery.setParameter("EmpregadoId", theId);
            theQuery.executeUpdate();
                    
        }
        
    }

*Repare que usamos as classes nativas do Hibernate*

O `EntityManager` é automaticamente criado pelo Sring Boot. Outro ponto a se considerar é que quando a classe tem apenas 1 *constructor*, o `@Autowired` é opcional.

A implementação do DAO não necessita da *annotation* `@Transactional` porque ela será utilizada no *service*.

Crie o pacote `dominio.crudhb.service` e dentro dele os arquivos:

**EmpregadoService.java**

    package dominio.crudhb.service;
    
    import java.util.List;
    
    import dominio.crudhb.entity.Empregado;
    
    public interface EmpregadoService {
        
        public List<Empregado> findAll();
        
        public Empregado findById(int theId);
        
        public void save(Empregado empregado);
        
        public void deleteById(int theId);
    
    }

**EmpregadoServiceImpl.java**

    package dominio.crudhb.service;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    import org.springframework.transaction.annotation.Transactional;
    
    import dominio.crudhb.dao.EmpregadoDAO;
    import dominio.crudhb.entity.Empregado;
    
    @Service
    public class EmpregadoServiceImpl implements EmpregadoService {
        
        private EmpregadoDAO empregadoDAO;
        
        @Autowired
        public EmpregadoServiceImpl(EmpregadoDAO empregadoDAO) {
            this.empregadoDAO = empregadoDAO;
        }
    
        @Override
        @Transactional
        public List<Empregado> findAll() {
            return empregadoDAO.findAll();
        }
    
        @Override
        @Transactional
        public Empregado findById(int theId) {
            return empregadoDAO.findById(theId);
        }
    
        @Override
        @Transactional
        public void save(Empregado empregado) {
            empregadoDAO.save(empregado);
        }
    
        @Override
        @Transactional
        public void deleteById(int theId) {
            empregadoDAO.deleteById(theId);
        }
    
    }

Crie o pacote `dominio.crudhb.rest` com o arquivo:

**EmpregadoRestController.java**

    package dominio.crudhb.rest;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.web.bind.annotation.DeleteMapping;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.PutMapping;
    import org.springframework.web.bind.annotation.RequestBody;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import dominio.crudhb.entity.Empregado;
    import dominio.crudhb.service.EmpregadoService;
    
    @RestController
    @RequestMapping("/api")
    public class EmpregadoRestController {
        
        private EmpregadoService empregadoService;
        
        @Autowired
        public EmpregadoRestController(EmpregadoService empregadoService) {
            this.empregadoService = empregadoService;
        }
        
        @GetMapping("/empregados")
        public List<Empregado> findAll() {
            return empregadoService.findAll();
        }
        
        @GetMapping("/empregados/{empregadoId}")
        public Empregado getEmpregado(@PathVariable int empregadoId) {
            
            Empregado empregado = empregadoService.findById(empregadoId);
            
            if (empregado == null) {
                throw new RuntimeException("Empregado não encontrado - " + empregadoId);
            }
            
            return empregado;
        }
        
        @PostMapping("/empregados/")
        public Empregado postEmpregado(@RequestBody Empregado empregado) {
            
            empregado.setId(0);
            
            empregadoService.save(empregado);
            
            return empregado;
        }
        
        @PutMapping("/empregados/")
        public Empregado putEmpregado(@RequestBody Empregado empregado) {
            
            empregadoService.save(empregado);
            
            return empregado;
        }
        
        @DeleteMapping("/empregados/{empregadoId}")
        public String deleteEmpregado(@PathVariable int empregadoId) {
            
            Empregado empregado = empregadoService.findById(empregadoId);
            
            if (empregado == null) {
                throw new RuntimeException("Empregado não encontrado - " + empregadoId);
            }
            
            empregadoService.deleteById(empregadoId);
            
            return "Empregado " + empregadoId + " deletado";
        }
    
    }

Agora você já pode executar o aplicativo e ver se os dados aaprecem no link [http://localhost:8080/api/empregados](http://localhost:8080/api/empregados)

Você já sabe como fazer o CRUD com o Postman, fizemos isso no capítulo de [Spring REST](#springrest_final).

## REST API com JPA<span id="springboot_restjpa"></span>

Esta é uma continuação do subcapítulo anterior.

Bom, como você já deve saber, ao usar JPA, não ficamos presos a uma implementação, o que deixa o código mais portável e flexível. Vejamos a comparação entre JPA e Hibernate:

| Ação                         | Método do Hibernate          | Método JPA                     |
| ---------------------------- | ---------------------------- | ------------------------------ |
| Criar/salvar nova entidade   | session.save(...)            | entityManager.persist(...)     |
| Recuperar entidade por ID    | session.get(...) / load(...) | entityManager.find(...)        |
| Recuperar lista de entidades | session.createQuery(...)     | entityManager.createQuery(...) |
| Salvar ou atualizar entidade | session.saveOrUpdate(...)    | entityManager.merge(...)       |
| Deletar entidade             | session.delete(...)          | entityManager.remove(...)      |

Crie uma nova classe no pacote `dominio.crudhb.dao`:

**EmpregadoDAOJpaImpl.java**

    package dominio.crudhb.dao;
    
    import java.util.List;
    
    import javax.persistence.EntityManager;
    import javax.persistence.Query;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Repository;
    
    import dominio.crudhb.entity.Empregado;
    
    @Repository
    public class EmpregadoDAOJpaImpl implements EmpregadoDAO {
        
        private EntityManager entityManager;
        
        @Autowired
        public EmpregadoDAOJpaImpl(EntityManager entityManager) {
            this.entityManager = entityManager;
        }
    
        @Override
        public List<Empregado> findAll() {
            
            Query theQuery = entityManager.createQuery("from Empregado"); // O JPA usa a linguagem JPQL para lidar com o SQL
            // A propósito, repare que desta vez usei o Query do javax.persistence
            
            List<Empregado> empregados = theQuery.getResultList();
            
            return empregados;
        }
    
        @Override
        public Empregado findById(int theId) {
            
            Empregado empregado = entityManager.find(Empregado.class, theId);
            
            return empregado;
        }
    
        @Override
        public void save(Empregado empregado) {
            
            Empregado dbEmpregado = entityManager.merge(empregado); // Se o ID for 0, ele cria um novo, caso contrário será uma operação de update
            dbEmpregado.setId(dbEmpregado.getId());
        }
    
        @Override
        public void deleteById(int theId) {
            
            Query theQuery = entityManager.createQuery("delete from Empregado where id=:empregadoId");
            theQuery.setParameter("empregadoId", theId);
            theQuery.executeUpdate();
    
        }
    
    }

Se você tentar executar a aplicação agora, reparará que dará erro porque temos dois *beans* para alimentar `EmpregadoServiceImpl`, precisamos resolver esse conflito. É só alterar o construtor de `EmpregadoServiceImpl` através da *annotation* `@Qualifier`, em que colocamos o nome da classe, mas com a primeira letra em minúsculo:

    package dominio.crudhb.service;
    
    import java.util.List;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.beans.factory.annotation.Qualifier;
    import org.springframework.stereotype.Service;
    import org.springframework.transaction.annotation.Transactional;
    
    import dominio.crudhb.dao.EmpregadoDAO;
    import dominio.crudhb.entity.Empregado;
    
    @Service
    public class EmpregadoServiceImpl implements EmpregadoService {
        
        private EmpregadoDAO empregadoDAO;
        
        @Autowired
        public EmpregadoServiceImpl(@Qualifier("empregadoDAOJpaImpl") EmpregadoDAO empregadoDAO) {
            this.empregadoDAO = empregadoDAO;
        }
    
        @Override
        @Transactional
        public List<Empregado> findAll() {
            return empregadoDAO.findAll();
        }
    
        @Override
        @Transactional
        public Empregado findById(int theId) {
            return empregadoDAO.findById(theId);
        }
    
        @Override
        @Transactional
        public void save(Empregado empregado) {
            empregadoDAO.save(empregado);
        }
    
        @Override
        @Transactional
        public void deleteById(int theId) {
            empregadoDAO.deleteById(theId);
        }
    
    }

## Spring Data<span id="springboot_data"></span>

Vimos como criar um DAO para `Empregado`, mas e se quisermos criar um DAO para outra entidade como `Cliente`, `Fornecedor`, etc? Teremos que repetir esse código todo de novo?

### Spring Data JPA<span id="springboot_data_jpa"></span>

Com o Spring Data JPA, você coloca sua entidade e chave primária, que o Spring vai te dar a implementação do CRUD como se fosse mágica. Ele até traz os métodos que usamos como `findAll`, `getById`, `delete` e [outros](https://docs.spring.io/spring-data/jpa/docs/current/api/org/springframework/data/jpa/repository/JpaRepository.html).

O *bloilerplate* é drasticamente reduzido.

Bom, podemos tranquilamente deletar todos os arquivos DAO porque não precisaremos mais deles. Manteremos o pacote `dominio.crudhb.dao` e nele criaremos a interface `EmpregadoRepository`:

    package dominio.crudhb.dao;
    
    import org.springframework.data.jpa.repository.JpaRepository;
    
    import dominio.crudhb.entity.Empregado;
    
    public interface EmpregadoRepository extends JpaRepository<Empregado, Integer> {
        
        // Só isso, mais nada :-)
    
    }

Agora precisamos atualizar o arquivo `EmpregadoServiceImpl`:

    package dominio.crudhb.service;
    
    import java.util.List;
    import java.util.Optional;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    
    import dominio.crudhb.dao.EmpregadoRepository;
    import dominio.crudhb.entity.Empregado;
    
    @Service
    public class EmpregadoServiceImpl implements EmpregadoService {
        
        private EmpregadoRepository empregadoRepository;
        
        @Autowired
        public EmpregadoServiceImpl(EmpregadoRepository empregadoRepository) {
            this.empregadoRepository = empregadoRepository;
        }
    
        @Override
        public List<Empregado> findAll() {
            return empregadoRepository.findAll();
        }
    
        @Override
        public Empregado findById(int theId) {
            Optional<Empregado> result = empregadoRepository.findById(theId);
            
            Empregado empregado = null;
            
            if (result.isPresent()) {
                empregado = result.get();
            }
            else {
                throw new RuntimeException("Não foi encontrado um empreago com o ID " + theId);
            }
            
            return empregado;
        }
    
        @Override
        public void save(Empregado empregado) {
            empregadoRepository.save(empregado);
        }
    
        @Override
        public void deleteById(int theId) {
            empregadoRepository.deleteById(theId);
        }
    
    }

A *annotation* `@Transactional` não é mais necessária porque JpaRepository provê essa funcionalidade.

### Spring Data REST<span id="springboot_data_rest"></span>

Nós vimos como criar uma API REST para `Empregado`, mas e se precisarmos criar uma API REST para outra entidade? O Spring Data REST nos ajudará nisso e ele ainda criará os *endpoints* pra gente!

Em essência, você só precisa de 3 coisas:

* A entidade, que no caso é `Empregado`

* Um JpaRepository: `EmpregadoRepository extends JpaRepository`

* A dependência no Maven: `spring-boot-starter-data-rest`

Já temos 2 itens dessa lista, só falta adicionar Spring Data REST ao nosso arquivo `pom.xml`

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-rest</artifactId>
    </dependency>

<hr>

**Como era antes?**

*Controller* REST de `Empregado` ⇔ *Service* de `Empregado` ⇔ Repositório de `Empregado` (Spring Data JPA) ⇔ Banco de dados

**Agora**

Spring Data REST para `/empregado` ⇔ Repositório de `Empregado` (Spring Data JPA) ⇔ Banco de dados

<hr>

Os *endpoints do Spring Data REST são compatíveis com o HATEOAS (Hypermedia as the Engine of Application State)

Com a dependência adicionada, podemos tranquilamente deletar os pacotes relacionados ao *controller* (que, no caso aqui, está no pacote `.rest`) e *service* junto com seus arquivos dentro.

Pronto, é só isso, pode testar sua aplicação 🙂

Uma coisa engraçada é que o caminho criado pelo Spring Data REST para ver todos os itens da lista não foi [http://localhost:8080/empregados](http://localhost:8080/empregados), mas sim [http://localhost:8080/empregadoes](http://localhost:8080/empregadoes). Isso porque Spring Data REST assume que estamos inserindo uma palavra em inglês. Na verdade, até mesmo dentro da língua inglesa haverá problemas, porque o Spring Data REST é muito simplista e não saberá, por exemplo, que o plural de "*goose*" é "*geese*", mas isso pode ser facilmente resolvido com uma *annotation* na classe `EmpregadoRepository`.

    package dominio.crudhb.dao;
    
    import org.springframework.data.jpa.repository.JpaRepository;
    import org.springframework.data.rest.core.annotation.RepositoryRestResource;
    
    import dominio.crudhb.entity.Empregado;
    
    @RepositoryRestResource(path="empregados")
    public interface EmpregadoRepository extends JpaRepository<Empregado, Integer> {
        
        // Só isso, mais nada :-)
    
    }

A propósito, podemos inserir prefixos para o caminho da nossa API, é só atualizarmos nosso arquivo .properties.

    # JDBC Properties
    
    spring.datasource.url=jdbc:mysql://localhost:3306/empregadodb?useSSL=false&serverTimezone=UTC
    spring.datasource.username=estudante
    spring.datasource.password=estudante
    
    # Spring Data REST properties
    
    spring.data.rest.base-path=/api

Agora você poderá acessar pelo link [http://localhost:8080/api/empregados](http://localhost:8080/api/empregados)

Fique sabendo que há outras propriedades para configurar o Spring Data REST como `spring.data.rest.default-page-size`.

### BÔNUS: O projeto final<span id="springboot_data_final"></span>

Essa versão é relativamente simplificada, talvez seja interessante refazer o projeto que começa no capítulo [REST API com Hibernate](#springboot_resthibernate)

Ajeite o banco de dados:

    CREATE DATABASE IF NOT EXISTS `empregadodb`;
    USE `empregadodb`;
    
    DROP TABLE IF EXISTS `empregado`;
    
    CREATE TABLE `empregado` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;
    
    
    INSERT INTO `empregado` VALUES 
    	(1,'Marcelino','Travolta','marcelino@gmail.com'),
    	(2,'Cuca','Beludo','culudo@gmail.com'),
    	(3,'Paula','Barbosa','paulinha@gmail.com'),
    	(4,'Oscar','Alho','alho@gmail.com'),
    	(5,'Maria','Freitas','maria@gmail.com');

No Spring Initializr, coloquei o *Group* como `dominio` e o *Artifact/Name* como `crudhb`. Na parte das dependências, selecionei `Spring Web`, `Spring Boot DevTools` `Spring Data JPA`, `REST Repositories`, `MySQL Driver`. 

**CrudhbApplication.java** *(gerado pelo próprio Spring Boot)*

    package dominio.crudhb;
    
    import org.springframework.boot.SpringApplication;
    import org.springframework.boot.autoconfigure.SpringBootApplication;
    
    @SpringBootApplication
    public class CrudhbApplication {
    
    	public static void main(String[] args) {
    		SpringApplication.run(CrudhbApplication.class, args);
    	}
    
    }

**pom.xml** *(gerado pelo próprio Spring Boot, mas o código abaixo em específico foi manualmente editado por mim durante a criação do aplicativo)*

    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    	<modelVersion>4.0.0</modelVersion>
    	<parent>
    		<groupId>org.springframework.boot</groupId>
    		<artifactId>spring-boot-starter-parent</artifactId>
    		<version>2.7.0</version>
    		<relativePath/> <!-- lookup parent from repository -->
    	</parent>
    	<groupId>dominio</groupId>
    	<artifactId>crudhb</artifactId>
    	<version>0.0.1-SNAPSHOT</version>
    	<name>crudhb</name>
    	<description>Demo project for Spring Boot</description>
    	<properties>
    		<java.version>17</java.version>
    	</properties>
    	<dependencies>
    		<dependency>
    			<groupId>org.springframework.boot</groupId>
    			<artifactId>spring-boot-starter-data-jpa</artifactId>
    		</dependency>
    		<dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-data-rest</artifactId>
            </dependency>
    		<dependency>
    			<groupId>org.springframework.boot</groupId>
    			<artifactId>spring-boot-starter-web</artifactId>
    		</dependency>
    
    		<dependency>
    			<groupId>org.springframework.boot</groupId>
    			<artifactId>spring-boot-devtools</artifactId>
    			<scope>runtime</scope>
    			<optional>true</optional>
    		</dependency>
    		<dependency>
    			<groupId>mysql</groupId>
    			<artifactId>mysql-connector-java</artifactId>
    			<scope>runtime</scope>
    		</dependency>
    		<dependency>
    			<groupId>org.springframework.boot</groupId>
    			<artifactId>spring-boot-starter-test</artifactId>
    			<scope>test</scope>
    		</dependency>
    	</dependencies>
    
    	<build>
    		<plugins>
    			<plugin>
    				<groupId>org.springframework.boot</groupId>
    				<artifactId>spring-boot-maven-plugin</artifactId>
    			</plugin>
    		</plugins>
    	</build>
    
    </project>

**application.properties** *(gerado vazio pelo próprio Spring Boot)*

    # JDBC Properties
    
    spring.datasource.url=jdbc:mysql://localhost:3306/empregadodb?useSSL=false&serverTimezone=UTC
    spring.datasource.username=estudante
    spring.datasource.password=estudante

Crie os pacotes abaixo:

* `dominio.crudhb.dao`

* `dominio.crudhb.entity`

No pacote `dominio.crudhb.entity`, crie o arquivo:

**Empregado.java**

    package dominio.crudhb.entity;
    
    import javax.persistence.Column;
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.Table;
    
    @Entity
    @Table(name="empregado")
    public class Empregado {
        
        @Id
        @GeneratedValue(strategy=GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
        
        @Column(name="nome")
        private String nome;
        
        @Column(name="sobrenome")
        private String sobrenome;
        
        @Column(name="email")
        private String email;
        
        public Empregado() {
            
        }
    
        public Empregado(String nome, String sobrenome, String email) {
            this.nome = nome;
            this.sobrenome = sobrenome;
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        @Override
        public String toString() {
            return "Empregado [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email + "]";
        }
    
    }

No pacote `dominio.crudhb.dao`, crie o arquivo:

**EmpregadoRepository.java**

    package dominio.crudhb.dao;
    
    import org.springframework.data.jpa.repository.JpaRepository;
    import org.springframework.data.rest.core.annotation.RepositoryRestResource;
    
    import dominio.crudhb.entity.Empregado;
    
    @RepositoryRestResource(path="empregados")
    public interface EmpregadoRepository extends JpaRepository<Empregado, Integer> {
        
        // Só isso, mais nada :-)
    
    }

# Thymeleaf<span id="thymeleaf"></span>

Thymeleaf *(pronunciamos "Thyme" como "time" mesmo)* é um *template engine* do Java, é um projeto sem relação com o Spring, ele pode ser usado sem o Spring, mas os dois sçao comumente usados juntos.

Em um aplicativo web, o Thymeleaf é processado no servidor, é muito similar ao JSP, mas a diferença é que o Thymeleaf também pode ser utilizado em um ambiente não-web, como templates de e-mail, CSV e PDF.

Eis a dependência Maven do Thymeleaf no `pom.xml`

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-thymeleaf</artifactId>
    </dependency>

No Spring Boot, os templates do Thymeleaf ficam na pasta `src/main/resources/templates`. No arquivo HTML, precisamos substituir a tag `<html>` pela linha logo abaixo...

    <html xmlns:th="http://www.thymeleaf.org">

...para que possamos usar as expressões do Thymeleaf.

Vamos criar um projeto simples, no Spring Initializr, coloquei o *Group* como `dominio` e o *Artifact/Name* como `leaf`. Na parte das dependências, selecionei `Spring Web`, `Spring Boot DevTools` e `Thymeleaf` *(você já entende que estamos colocando o `Spring Boot DevTools` apenas por uma questão de conveniência)*.

Crie o pacote `dominio.leaf.controller` com o arquivo:

**AppController.java**

    package dominio.leaf.controller;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.GetMapping;
    
    @Controller
    public class AppController {
    
        @GetMapping("/oi")
        public String digaOi(Model model) {
            model.addAttribute("data", new java.util.Date());
    
            return "ola"; // Por conta do Thymeleaf, já se presumpõe que há o arquivo src/main/resources/templates/ola.html
        }
    
    }

Na pasta `src/main/resources/static`, crie a pasta `css`, e dentro desta o arquivo:

**demo.css**

    body {
        color: red;
        font-weight: bold;
    }

Na pasta `src/main/resources/templates`, crie o arquivo:

**ola.html**

    <!DOCTYPE html>
    <html xmlns:th="http://www.thymeleaf.org">
    <head>
        <meta charset="UTF-8">
        <title>Olá</title>
        <link rel="stylesheet" th:href="@{/css/demo.css}" />
    </head>
    <body>
    
        <p>Olá mundo</p>
    
        <p th:text="'O horário no servidor é ' + ${data}" />
    </body>
    </html>

O símbolo `@` em `@{/css/demo.css}` se refere ao caminho de contexto da sua aplicação.

## Tabelas<span id="thymeleaf_tables"></span>

Podemos reutilizar os arquivos do projeto anterior ou criar um novo dozero, tanto faz.

Crie o pacote `dominio.leaf.model` *(assumo aqui que você manteve os mesmos nomes do projeto anterior...)* e dentro dele a classe:

**Empregado.java**

    package dominio.leaf.model;
    
    public class Empregado {
    
        private int id;
        private String nome;
        private String sobrenome;
        private String email;
    
        public Empregado() {
    
        }
    
        public Empregado(int id, String nome, String sobrenome, String email) {
            this.id = id;
            this.nome = nome;
            this.sobrenome = sobrenome;
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        @Override
        public String toString() {
            return "Empregado{" +
                    "id=" + id +
                    ", nome='" + nome + '\'' +
                    ", sobrenome='" + sobrenome + '\'' +
                    ", email='" + email + '\'' +
                    '}';
        }
    }

Crie o pacote `dominio.leaf.controller` e crie o arquivo:

**EmpregadoController.java**

    package dominio.leaf.controller;
    
    import dominio.leaf.model.Empregado;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    
    import javax.annotation.PostConstruct;
    import java.util.ArrayList;
    import java.util.List;
    
    @Controller
    @RequestMapping("/empregados")
    public class EmpregadoController {
    
        private List<Empregado> empregados;
    
        @PostConstruct
        private void loadData() {
            Empregado emp1 = new Empregado(1, "Diana", "Tavares", "diana@terra.com.br");
            Empregado emp2 = new Empregado(1, "Mario", "Andrade", "andrade@terra.com.br");
            Empregado emp3 = new Empregado(1, "Carla", "Guimarães", "cg@hotmail.com.br");
    
            empregados = new ArrayList<>();
    
            empregados.add(emp1);
            empregados.add(emp2);
            empregados.add(emp3);
        }
    
        @GetMapping("/lista")
        public String listaEmpregados(Model modelo) {
            modelo.addAttribute("empregadosAtt", empregados);
            return "lista";
        }
    }

Usaremos o [Bootstrap](https://getbootstrap.com/) para o CSS do nosso projeto. Você pode baixar o arquivo para usar localmente *(que você já sabe como fazer)* ou carregar a folha de estilos de forma remota, usarei esta segunda opção nesta vez, até para simplificar pra gente.

    <!DOCTYPE html>
    <html xmlns:th="http://www.thymeleaf.org">
    <head>
        <meta charset="UTF-8">
        <title>Lista de Epregados</title>
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css">
    
    </head>
    <body>
        <div class="container">
            <h3>Lista de Empregados</h3>
    
            <table class="table table-dark">
                <thead>
                <tr>
                    <th>Nome</th>
                    <th>Sobrenome</th>
                    <th>E-mail</th>
                </tr>
                </thead>
                <tbody>
                <tr th:each="EmpregadoTemp : ${empregadosAtt}" class="table-active">
                    <td th:text="${EmpregadoTemp.nome}" />
                    <td th:text="${EmpregadoTemp.sobrenome}" />
                    <td th:text="${EmpregadoTemp.email}" />
                </tr>
                </tbody>
            </table>
        </div>
    </body>
    </html>

## Projeto completo CRUD: Thymeleaf + Spring Boot<span id="thymeleaf_crudfinal"></span>

Vamos criar um projeto simples, no Spring Initializr, coloquei o *Group* como `dominio` e o *Artifact/Name* como `leafcrud`. Na parte das dependências, selecionei `Spring Web`, `Spring Data JPA`, `MySQL Driver` e `Thymeleaf`.

No banco de dados:

    CREATE DATABASE IF NOT EXISTS `empregadodb`;
    USE `empregadodb`;
    
    DROP TABLE IF EXISTS `empregado`;
    
    CREATE TABLE `empregado` (
      `id` int(11) NOT NULL AUTO_INCREMENT,
      `nome` varchar(45) DEFAULT NULL,
      `sobrenome` varchar(45) DEFAULT NULL,
      `email` varchar(45) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;
    
    
    INSERT INTO `empregado` VALUES 
    	(1,'Marcelino','Travolta','marcelino@gmail.com'),
    	(2,'Cuca','Beludo','culudo@gmail.com'),
    	(3,'Paula','Barbosa','paulinha@gmail.com'),
    	(4,'Oscar','Alho','alho@gmail.com'),
    	(5,'Maria','Freitas','maria@gmail.com');

De volta à IDE:

**application.properties**

    # JDBC Properties
    
    spring.datasource.url=jdbc:mysql://localhost:3306/empregadodb?useSSL=false&serverTimezone=UTC
    spring.datasource.username=estudante
    spring.datasource.password=estudante

Crie o pacote `dominio/leafcrud/entity` com a classe:

**Empregado.java**

    package dominio.leafcrud.entity;
    
    import javax.persistence.*;
    
    @Entity
    @Table(name="empregado")
    public class Empregado {
    
        @Id
        @GeneratedValue(strategy= GenerationType.IDENTITY)
        @Column(name="id")
        private int id;
    
        @Column(name="nome")
        private String nome;
    
        @Column(name="sobrenome")
        private String sobrenome;
    
        @Column(name="email")
        private String email;
    
        public Empregado() {
    
        }
    
        public Empregado(String nome, String sobrenome, String email) {
            this.nome = nome;
            this.sobrenome = sobrenome;
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
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public String getEmail() {
            return email;
        }
    
        public void setEmail(String email) {
            this.email = email;
        }
    
        @Override
        public String toString() {
            return "Empregado [id=" + id + ", nome=" + nome + ", sobrenome=" + sobrenome + ", email=" + email + "]";
        }
    
    }

Crie o pacote `dominio.leaf.dao` com a interface:

**EmpregadoRepository.java**

    package dominio.leafcrud.dao;
    
    import dominio.leafcrud.entity.Empregado;
    import org.springframework.data.jpa.repository.JpaRepository;
    
    import java.util.List;
    
    public interface EmpregadoRepository extends JpaRepository<Empregado, Integer> {
    
    }

Crie o pacote `dominio.leaf.service` com os arquivos:

**EmpregadoService.java**

    package dominio.leafcrud.service;
    
    import dominio.leafcrud.entity.Empregado;
    
    import java.util.List;
    
    public interface EmpregadoService {
        public List<Empregado> findAll();
    
        public Empregado findById(int theId);
    
        public void save(Empregado empregado);
    
        public void deleteById(int theId);
    }

**EmpregadoServiceImpl.java**

    package dominio.leafcrud.service;
    
    import dominio.leafcrud.dao.EmpregadoRepository;
    import dominio.leafcrud.entity.Empregado;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;
    
    import java.util.List;
    import java.util.Optional;
    
    @Service
    public class EmpregadoServiceImpl implements EmpregadoService {
    
        private EmpregadoRepository empregadoRepository;
    
        @Autowired
        public EmpregadoServiceImpl(EmpregadoRepository empregadoRepository) {
            this.empregadoRepository = empregadoRepository;
        }
    
        @Override
        public List<Empregado> findAll() { return empregadoRepository.findAll(); }
    
        @Override
        public Empregado findById(int theId) {
            Optional<Empregado> result = empregadoRepository.findById(theId);
    
            Empregado empregado = null;
    
            if (result.isPresent()) {
                empregado = result.get();
            }
            else {
                throw new RuntimeException("Não foi encontrado um empreago com o ID " + theId);
            }
    
            return empregado;
        }
    
        @Override
        public void save(Empregado empregado) {
            empregadoRepository.save(empregado);
        }
    
        @Override
        public void deleteById(int theId) {
            empregadoRepository.deleteById(theId);
        }
    }

Crie o pacote `dominio.leaf.controller` com a classe:

**EmpregadoController.java**

    package dominio.leafcrud.controller;
    
    import dominio.leafcrud.entity.Empregado;
    import dominio.leafcrud.service.EmpregadoService;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.*;
    
    import java.util.List;
    
    @Controller
    @RequestMapping("/empregados")
    public class EmpregadoController {
    
        private EmpregadoService empregadoService;
    
        public EmpregadoController(EmpregadoService empregadoService) {
            this.empregadoService = empregadoService;
        }
    
        @GetMapping("/lista")
        public String listaEmpregados(Model modelo) {
            List<Empregado> empregados = empregadoService.findAll();
            modelo.addAttribute("empregados", empregados);
    
            return "empregados/lista";
        }
    
        @GetMapping("/cadastroForm")
        public String cadastroForm(Model modelo) {
            Empregado empregado = new Empregado();
            modelo.addAttribute("empregado", empregado);
    
            return "empregados/form";
        }
    
        @PostMapping("/salvar")
        public String salvarEmpregado(@ModelAttribute("empregado") Empregado empregado) {
        // Esse @ModelAttribute("empregado") se comunica com o th:object="${empregado} do arquivo form.html
    
            empregadoService.save(empregado);
    
            return "redirect:/empregados/lista";
        }
    
        @GetMapping("/atualizacaoForm")
        public String atualizacaoForm(@RequestParam("empregadoId") int theId, Model modelo) {
    
            Empregado empregado = empregadoService.findById(theId);
    
            modelo.addAttribute("empregado", empregado);
    
            return "empregados/form";
        }
    
        @GetMapping("/deletar")
        public String deletar(@RequestParam("empregadoId") int theId) {
    
            empregadoService.deleteById(theId);
    
            return "redirect:/empregados/lista";
        }
    }

Na pasta `src/main/resources/static`, crie o arquivo:

**index.html**

    <meta http-equiv="refresh" content="0; URL='empregados/lista'" />

Na pasta `src/main/resources/templates/empregados`, crie os arquivos:

**lista.html**

    <!DOCTYPE html>
    <html xmlns:th="http://www.thymeleaf.org">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Lista de Epregados</title>
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css">
    </head>
    <body>
    <div class="container">
        <h3>Lista de Empregados</h3>
    
        <a th:href="@{cadastroForm}" class="btn btn-primary btn-sm mb-3">Cadastrar empregado</a>
    
        <table class="table">
            <thead class="table-dark">
            <tr>
                <th>Nome</th>
                <th>Sobrenome</th>
                <th>E-mail</th>
                <th>Ações</th>
            </tr>
            </thead>
            <tbody>
            <tr th:each="empregadoTemp : ${empregados}" class="table-light">
                <td th:text="${empregadoTemp.nome}" />
                <td th:text="${empregadoTemp.sobrenome}" />
                <td th:text="${empregadoTemp.email}" />
                <td>
                    <a th:href="@{/empregados/atualizacaoForm(empregadoId=${empregadoTemp.id})}" class="btn btn-info btn-sm">Atualizar</a>
                    <a th:href="@{/empregados/deletar(empregadoId=${empregadoTemp.id})}" class="btn btn-danger btn-sm"
                    onclick="if (!(confirm('Você tem certeza que quer deletar este empregado?'))) return false;">Deletar</a>
                </td>
            </tr>
            </tbody>
        </table>
    </div>
    </body>
    </html>

**form.html**

    <!DOCTYPE html>
    <html xmlns:th="http://www.thymeleaf.org">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Formulário</title>
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css">
    </head>
    <body>
        <div class="container">
    
            <h3>Página de cadastro</h3>
    
            <form action="#" th:action="@{/empregados/salvar}" th:object="${empregado}" method="POST">
            <!-- Esse ${empregado} tem que ser o mesmo do modelo.addAttribute("empregado", empregado); do controller -->
    
                <input type="hidden" th:field="*{id}" />
                <!-- Este formulário escondido é para lidar com o update -->
    
                <input type="text" th:field="*{nome}" class="form-control mb-4 col-4" placeholder="Nome">
                <!-- *{nome} seleciona a propriedade do objeto referenciado em th:object, que no caso chama o método empregado.getNome()-->
    
                <input type="text" th:field="*{sobrenome}" class="form-control mb-4 col-4" placeholder="Sobrenome">
    
                <input type="text" th:field="*{email}" class="form-control mb-4 col-4" placeholder="E-mail">
    
                <button type="submit" class="btn btn-info col-2">Salvar</button>
                <!-- Quando clicamos nesse botão, são chamados os métodos empregado.setNome(), empregado.setSobrenome(), etc -->
    
            </form>
    
            <hr>
    
            <a th:href="@{/empregados/lista}">Retornar para a lista</a>
        </div>
    </body>
    </html>

# BÔNUS: Calculadora<span id="calculator"></span>

Crie um projeto pelo Spring Initializr com `Spring Web`. Assumirei que o *Group* será `dominio` e o *Artifact/Name* como `calc`:

Crie o pacote `dominio.dto`, e dentro dele a classe:

**CalculatorDTO.java**

    package dominio.calc.dto;
    
    import com.fasterxml.jackson.annotation.JsonProperty;
    
    public class CalculatorDTO {
    
        private Double num1;
        private Double num2;
        private Double num3;
        @JsonProperty("num41")
        private Double num4;
    
        public Double getNum1() {
            return num1;
        }
    
        public void setNum1(Double num1) {
            this.num1 = num1;
        }
    
        public Double getNum2() {
            return num2;
        }
    
        public void setNum2(Double num2) {
            this.num2 = num2;
        }
    
        public Double getNum3() {
            return num3;
        }
    
        public void setNum3(Double num3) {
            this.num3 = num3;
        }
    
        public Double getNum4() {
            return num4;
        }
    
        public void setNum4(Double num4) {
            this.num4 = num4;
        }
    }

Crie o pacote `dominio.controller`, e dentro dele a classe:

**CalculatorController.java**

    package dominio.calc.controller;
    
    import dominio.calc.dto.CalculatorDTO;
    import org.springframework.http.HttpStatus;
    import org.springframework.http.ResponseEntity;
    import org.springframework.web.bind.annotation.*;
    
    @RestController
    @RequestMapping("/api/v1/calculator")
    public class CalculatorController {
    
        @GetMapping("/add")
        public Double add(@RequestParam("num1") Double num1, @RequestParam("num2") Double num2){
            return num1 + num2;
        }
    
        @GetMapping("/sub/{num1}/{num2}")
        public Double sub(@PathVariable("num1") Double num1, @PathVariable("num2") Double num2) {
    
            Double result = null;
            if (num1 > num2) {
                result = num1 - num2;
            }
            else {
                result = num2 - num1;
            }
            return result;
    
        }
    
        @PostMapping("/mul")
        public Double multiply(@RequestBody CalculatorDTO calculatorDTO) {
            Double result = null;
            result = calculatorDTO.getNum1() * calculatorDTO.getNum2() * calculatorDTO.getNum3() * calculatorDTO.getNum4();
            return result;
        }
    
        // Uma alternativa de código que manda um HttpStatus 201 em vez de 200
        /*@PostMapping("/mul")
        public ResponseEntity multiply(@RequestBody CalculatorDTO calculatorDTO) {
            Double result = null;
            result = calculatorDTO.getNum1() * calculatorDTO.getNum2() * calculatorDTO.getNum3() * calculatorDTO.getNum4();
            ResponseEntity<Double> responseEntity = new ResponseEntity<>(result, HttpStatus.CREATED);
            return responseEntity;
        }*/
    }

No Postman, use este *body* abaixo, no método POST, para o link `http://localhost:8080/api/v1/calculator/mul`

    {
        "num1" : 5.0,
        "num2" : 2.0,
        "num3" : 1.0,
        "num41" : 6.3
    }

# BÔNUS: RPC API<span id="rpc"></span>

O que muita gente chama de REST API *(e a maior parte do que fizemos até agora...)* são [RPC](https://pt.wikipedia.org/wiki/Chamada_de_procedimento_remoto).

O que você verá agora não é muito diferente do que vimos, mas este é bem interessante:

**SQL**

    CREATE TABLE aluno (
        id SERIAL PRIMARY KEY,
        nome VARCHAR(255) NOT NULL,
        sobrenome VARCHAR(255) NOT NULL,
        ano INT NOT NULL
    );
    
    CREATE TABLE atividade (
        id SERIAL PRIMARY KEY,
        aluno_id INT NOT NULL,
        descricao VARCHAR(255) NOT NULL,
        CONSTRAINT aluno_id FOREIGN KEY (aluno_id) REFERENCES aluno(id)
    );
    
    INSERT INTO aluno (nome, sobrenome, ano) VALUES ('João', 'Macedo', '6');
    INSERT INTO aluno (nome, sobrenome, ano) VALUES ('Paula', 'Cristina', '6');
    INSERT INTO aluno (nome, sobrenome, ano) VALUES ('Ricardo', 'Andrade', '6');
    INSERT INTO aluno (nome, sobrenome, ano) VALUES ('Amélia', 'Duarte', '6');
    
    INSERT INTO atividade (aluno_id, descricao) VALUES (1, 'Pintura de bonecos');
    INSERT INTO atividade (aluno_id, descricao) VALUES (2, 'Pintura de bonecos');
    INSERT INTO atividade (aluno_id, descricao) VALUES (3, 'Pintura de bonecos');
    INSERT INTO atividade (aluno_id, descricao) VALUES (4, 'Pintura de bonecos');
    INSERT INTO atividade (aluno_id, descricao) VALUES (1, 'Dança na rua');
    INSERT INTO atividade (aluno_id, descricao) VALUES (3, 'Dança na rua');
    INSERT INTO atividade (aluno_id, descricao) VALUES (1, 'Resolução de quebra-cabeças');
    INSERT INTO atividade (aluno_id, descricao) VALUES (2, 'Resolução de quebra-cabeças');
    INSERT INTO atividade (aluno_id, descricao) VALUES (3, 'Resolução de quebra-cabeças');
    INSERT INTO atividade (aluno_id, descricao) VALUES (4, 'Resolução de quebra-cabeças');

*Se você estiver no Windows, use o pgAdmin.*

Na criação do projeto Spring Boot, pegue as dependências: Spring Web, PostgreSQL Driver e Spring data JPA.

**application.properties**

    spring.datasource.url=jdbc:postgresql://localhost:5432/<banco_de_dados>
    spring.datasource.username=<usuário>
    spring.datasource.password=<senha>

Crie o pacote `entity` com as seguintes classes:

**Aluno.java**

    package br.com.hmslima.escola.entity;
    
    import javax.persistence.*;
    import java.util.List;
    
    @Entity
    @Table(name="aluno")
    public class Aluno {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        @Column(name="id")
        private Long id;
    
        @Column(name="nome")
        private String nome;
    
        @Column(name="sobrenome")
        private String sobrenome;
    
        @Column(name="ano")
        private int ano;
    
        @OneToMany(mappedBy = "aluno",
                   fetch = FetchType.LAZY)
        private List<Atividade> atividades;
    
        public Aluno() {
        }
    
        public Aluno(String nome, String sobrenome, int ano, List<Atividade> atividades) {
            this.nome = nome;
            this.sobrenome = sobrenome;
            this.ano = ano;
            this.atividades = atividades;
        }
    
        public Long getId() {
            return id;
        }
    
        public void setId(Long id) {
            this.id = id;
        }
    
        public String getNome() {
            return nome;
        }
    
        public void setNome(String nome) {
            this.nome = nome;
        }
    
        public String getSobrenome() {
            return sobrenome;
        }
    
        public void setSobrenome(String sobrenome) {
            this.sobrenome = sobrenome;
        }
    
        public int getAno() {
            return ano;
        }
    
        public void setAno(int ano) {
            this.ano = ano;
        }
    
        public List<Atividade> getAtividades() {
            return atividades;
        }
    
        public void setAtividades(List<Atividade> atividades) {
            this.atividades = atividades;
        }
    }

**Atividade.java**

    package br.com.hmslima.escola.entity;
    
    import com.fasterxml.jackson.annotation.JsonIgnore;
    
    import javax.persistence.*;
    
    @Entity
    @Table(name="atividade")
    public class Atividade {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        @Column(name="id")
        private Long id;
    
        @ManyToOne
        @JoinColumn(name="aluno_id")
        @JsonIgnore // Sem esta linha, geraria um loop infinito, repetição/repetições infinita. Ou era isso ou deveria usar DTOs
        private Aluno aluno;
    
        @Column(name="descricao")
        private String descricao;
    
        public Atividade () {
        }
    
        public Atividade(Aluno aluno, String descricao) {
            this.aluno = aluno;
            this.descricao = descricao;
        }
    
        public Long getId() {
            return id;
        }
    
        public void setId(Long id) {
            this.id = id;
        }
    
        public Aluno getAluno() {
            return aluno;
        }
    
        public void setAluno(Aluno aluno) {
            this.aluno = aluno;
        }
    
        public String getDescricao() {
            return descricao;
        }
    
        public void setDescricao(String descricao) {
            this.descricao = descricao;
        }
    }

Crie o pacote `repository` com as seguintes interfaces:

**AlunoRepository.java**

    package br.com.hmslima.escola.repository;
    
    import br.com.hmslima.escola.entity.Aluno;
    import org.springframework.data.jpa.repository.JpaRepository;
    
    public interface AlunoRepository extends JpaRepository<Aluno, Long>{

    }

**AtividadeRepository.java**

    package br.com.hmslima.escola.repository;
    
    import br.com.hmslima.escola.entity.Atividade;
    import org.springframework.data.jpa.repository.JpaRepository;
    
    public interface AtividadeRepository extends JpaRepository<Atividade, Long> {
    }

Crie o pacote `service` com as seguintes classes:

**AlunoService.java**

    package br.com.hmslima.escola.service;
    
    import br.com.hmslima.escola.entity.Aluno;
    import br.com.hmslima.escola.exception.AlunoNotFoundExeption;
    import br.com.hmslima.escola.repository.AlunoRepository;
    import org.springframework.beans.factory.annotation.Autowired;
    
    import org.springframework.stereotype.Service;
    
    import javax.transaction.Transactional;
    import java.util.List;
    import java.util.Optional;
    
    @Service
    @Transactional
    public class AlunoService {
    
        private AlunoRepository alunoRepository;
    
        @Autowired
        public AlunoService(AlunoRepository alunoRepository) {
            this.alunoRepository = alunoRepository;
        }
    
        public Aluno findAluno(Long id) {
            return alunoRepository.findById(id).orElseThrow(() -> new AlunoNotFoundExeption(id));
        }
    
        public List<Aluno> findAllAlunos() {
            return alunoRepository.findAll();
        }
    
        public Aluno addAluno(Aluno aluno) {
    
            aluno.setId(0L);
            return alunoRepository.save(aluno);
        }
    
        public Aluno updateAluno(Aluno aluno) {
            return alunoRepository.save(aluno);
        }
    
        public void deleteAluno(Long id) {
            alunoRepository.deleteById(id);
        }
    }

**AtividadeService.java**

    package br.com.hmslima.escola.service;
    
    import br.com.hmslima.escola.entity.Aluno;
    import br.com.hmslima.escola.entity.Atividade;
    import br.com.hmslima.escola.repository.AlunoRepository;
    import br.com.hmslima.escola.repository.AtividadeRepository;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.http.ResponseEntity;
    import org.springframework.stereotype.Service;
    
    import javax.transaction.Transactional;
    import java.util.List;
    import java.util.Optional;
    
    @Service
    @Transactional
    public class AtividadeService {
    
        private AlunoRepository alunoRepository;
        private AtividadeRepository atividaRepository;
    
        @Autowired
        public AtividadeService(AlunoRepository alunoRepository, AtividadeRepository atividaRepository) {
            this.alunoRepository = alunoRepository;
            this.atividaRepository = atividaRepository;
        }
    
        public List<Atividade> findAtividades(Long aluno_id) {
    
            Optional<Aluno> aluno = alunoRepository.findById(aluno_id);
    
            return aluno.get().getAtividades();
        }
    
        public ResponseEntity<Object> addAtividade(Long aluno_id, Atividade atividade) {
    
            Optional<Aluno> aluno = alunoRepository.findById(aluno_id);
    
            atividade.setAluno(aluno.get());
    
            atividaRepository.save(atividade);
    
            if (aluno.isPresent()) {
                return ResponseEntity.accepted().body("Atividade adicionada com sucesso");
            }
            else {
                return ResponseEntity.unprocessableEntity().body("Aluno não encontrado");
            }
        }
    
        public ResponseEntity<Object> updateAtividade(Long aluno_id, Long atividade_id, Atividade atividade) {
    
            Optional<Aluno> aluno = alunoRepository.findById(aluno_id);
    
            if (aluno.isPresent()) {
    
                List<Atividade> atividades = aluno.get().getAtividades();
    
                atividade.setId(atividade_id);
                atividade.setAluno(aluno.get());
    
                boolean fazParte = false;
    
                for (Atividade atividadeTemp : atividades) {
                    if (atividadeTemp.getId().equals(atividade_id)) {
                        fazParte = true;
                    }
                }
    
                if (fazParte) {
                    atividaRepository.save(atividade);
                }
                else {
                    return ResponseEntity.unprocessableEntity().body("Atividade não encontrada");
                }
    
                return ResponseEntity.accepted().body("Atividade atualizada com sucesso");
            }
            else {
                return ResponseEntity.unprocessableEntity().body("Aluno não encontrado");
            }
        }
    
        public ResponseEntity<Object> deleteAtividade(Long aluno_id, Long atividade_id) {
    
            Optional<Aluno> aluno = alunoRepository.findById(aluno_id);
            List<Atividade> atividades = aluno.get().getAtividades();
            boolean sucesso = false;
    
            for (Atividade atividadeTemp : atividades) {
                if (atividadeTemp.getId().equals(atividade_id)) {
                    atividaRepository.deleteById(atividade_id);
                    sucesso = true;
                }
            }
    
            if (sucesso) {
                return ResponseEntity.accepted().body("Atividade deletada com sucesso");
            }
            else {
                return ResponseEntity.unprocessableEntity().body("Aluno ou atividade não existe");
            }
        }
    }

Crie o pacote `exception` e crie a classe:

**AlunoNotFoundExeption.java**

    package br.com.hmslima.escola.exception;
    
    public class AlunoNotFoundExeption extends RuntimeException{
    
        public AlunoNotFoundExeption(Long id) {
            super("Não foi possível encontrar o aluno " + id);
        }
    }

Crie o pacote `controller` e crie a classe:

**AlunoController.java**

    package br.com.hmslima.escola.controller;
    
    import br.com.hmslima.escola.entity.Aluno;
    import br.com.hmslima.escola.entity.Atividade;
    import br.com.hmslima.escola.service.AlunoService;
    import br.com.hmslima.escola.service.AtividadeService;
    import org.springframework.http.HttpStatus;
    import org.springframework.http.ResponseEntity;
    import org.springframework.web.bind.annotation.*;
    
    import java.util.List;
    
    @RestController
    @CrossOrigin
    @RequestMapping("/api/alunos")
    public class AlunoController {
    
        private AlunoService alunoService;
        private AtividadeService atividadeService;
    
        public AlunoController(AlunoService alunoService, AtividadeService atividadeService) {
            this.alunoService = alunoService;
            this.atividadeService = atividadeService;
        }
    
        @GetMapping("/find/{id}")
        public ResponseEntity<Aluno> findAluno(@PathVariable("id") Long id) {
            Aluno aluno = alunoService.findAluno(id);
            return new ResponseEntity<>(aluno, HttpStatus.OK);
        }
    
        @GetMapping("/all")
        public ResponseEntity<List<Aluno>> findAllAlunos() {
            List<Aluno> alunos = alunoService.findAllAlunos();
            return new ResponseEntity<>(alunos, HttpStatus.OK);
        }
    
        @PostMapping("/add")
        public ResponseEntity<Aluno> addAluno(@RequestBody Aluno aluno) {
            Aluno newAluno = alunoService.addAluno(aluno);
            return new ResponseEntity<>(newAluno, HttpStatus.CREATED);
        }
    
        @PutMapping("/update")
        public ResponseEntity<Aluno> updateAluno(@RequestBody Aluno aluno) {
            Aluno updatedAluno = alunoService.updateAluno(aluno);
            return new ResponseEntity<>(updatedAluno, HttpStatus.OK);
        }
    
        @DeleteMapping("/delete/{id}")
        public ResponseEntity<?> deleteAluno(@PathVariable("id") Long id) {
            alunoService.deleteAluno(id);
            return new ResponseEntity<>(HttpStatus.OK);
        }
    
        @GetMapping("/{id}/atividades/all")
        public ResponseEntity<List<Atividade>> findAtividades(@PathVariable("id") Long id) {
            List<Atividade> atividades = atividadeService.findAtividades(id);
            return new ResponseEntity<>(atividades, HttpStatus.OK);
        }
    
        @PostMapping("/{id}/atividades/add")
        public ResponseEntity addAtividade(@PathVariable("id") Long id, @RequestBody Atividade atividade) {
            return atividadeService.addAtividade(id, atividade);
        }
    
        @PutMapping("/{id}/atividades/update/{a_id}")
        public ResponseEntity addAtividade(@PathVariable("id") Long id,
                                           @PathVariable("a_id") Long a_id,
                                           @RequestBody Atividade atividade) {
            return atividadeService.updateAtividade(id, a_id, atividade);
        }
    
        @DeleteMapping("/{id}/atividades/delete/{a_id}")
        public ResponseEntity deleteAtividade(@PathVariable("id") Long id, @PathVariable("a_id") Long a_id) {
            return atividadeService.deleteAtividade(id, a_id);
        }
    }
