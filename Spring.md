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