**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [Spring](#spring)

	* [Configuração](#spring_config)

	* [Primeiro projeto (com configuração XML)](#spring_primeiroprojetoxml)

		* [Projeto com dependências](#spring_primeiroprojetoxml_dependencias)

	* [Inversão de controle e Injeção de Dependência](#spring_iocinj)

	* [Primeiro projeto (com Java Annotations)](#spring_primeiroprojetojavaannotations)


# Introdução<span id="intro"></span>

Leia o [README](README.md).

# Spring<span id="spring"></span>

Spring é um framework completo que fornece uma estrutura para criar aplicações Java. Esse framework é constituído de módulos agrupados em *Core Container*, *Data Access/Integration*, *Web*, *AOP (Aspect Oriented Programming)*, *Instrumentation* e *Test*.

Por exemplo, dentro do *Data Access/Integration* (Integração/Acesso aos Dados), temos o JDBC, ORM, OXM, JMS e Transactions. Já esse ORM, provê integração a APIs como JPA, JDO, Hibernate e iBatis.

O nosso projeto terá a seguinte estrutura, a aplicação conversa com o *Resource Layer (rest controllers)*, este por sua vez conversa com *Service Layer* e este último conversa com *Data Access Layer (data repositories)*.

## Configuração<span id="spring_config"></span>

Usaremos o Eclipse EE. É bem simples, crie um novo `Java Project`, mas **não** crie um `module-info.java` pra ele!

Baixe o [Tomcat](https://tomcat.apache.org/). Se você for usar o Spring 5.x, fique sabendo que essa versão só é compatível com a versão 9 do Tomcat. Mude para o modo de perspectiva do Java EE, na parte de baixo clique na aba `Servers` e clique no link para criar um novo servidor. Depois de configurar você pode voltar para a perspectiva normal do Java.

Acesse o site do [JFrog](https://repo.spring.io/ui/) e siga este caminho: `Artifactory` => `Artifacts` => `libs-release` => `org` => `springframework` => `spring` => Escolha a versão mais recente => `spring-x.x.x-dist.zip` *(sendo `x.x.x` a versão)*. Baixe e descompacte o arquivo .zip, crie uma pasta `lib` no seu projeto, cole os arquivos jar lá e adicione-os ao seu projeto: clique com o botão direito do mouse sobre o nome do projeto => `Build Path` => `Configure Build Path` => Vá na aba `Libraries` => Selecione `Class Path` => `Add JARs...` => Procure os arquivos JARs na pasta `lib` do seu projeto => Aplique as mudanças

## Primeiro projeto (com configuração XML)<span id="spring_primeiroprojetoxml"></span>

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

### Projeto com dependências<span id="spring_primeiroprojetoxml_dependencias"></span>

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

## Inversão de controle e Injeção de Dependência<span id="spring_iocinj"></span>

Na minha opinião, fica masi fácil explicar esses conceitos após você ter sido exposto(a) ao Spring. Vamos ver como seria nosso projeto se ele fosse escrito em Java puro:

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

## Primeiro projeto (com Java Annotations)<span id="spring_primeiroprojetojavaannotations"></span>

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