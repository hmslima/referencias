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

    CREATE DATABASE  IF NOT EXISTS `cliente_web`;
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

Agora criaremos um *servlet* neste pacote básico para testar a conexão. Clique no pacote, `New` => `Servlet`, chamarei o arquivo de `ServletDbTeste`, dê `Next` até você chegar numa janela onde você tem algumas opções para deixar marcadas, deixe apenas marcados Inherited abstract methods` e `doGet`.

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

Como não quero me repetir: se você ainda não tem os arquivos JAR configurados, vá até o início deste capítulo e depois volte aqui.

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

# Programação orientada a aspecto<span id="aop"></span>

Programação orientada a aspecto *(ou “Aspect-oriented programming” (AOP), em inglês)*