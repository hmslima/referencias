**Autor:** Henrique Matheus da Silva Lima

# Índice

* [Introdução](#intro)

* [Spring](#spring)

	* [Configuração](#spring_config)

	* [Primeiro projeto](#spring_primeiropro)

		* [Com configuração XML](#spring_primeiropro_xml)

			* [Projeto com dependências](#spring_primeiropro_xml_dependencias)

		* [Inversão de controle e Injeção de Dependência](#spring_primeiropro_iocinj)

		* [Com Java Annotations](#spring_primeiropro_javaannotations)

			* [@Qualifier](#spring_primeiropro_javaannotations_qualifier)

		* [Sem configuração XML](#spring_primeiropro_semxml)

			* [@Bean](#spring_primeiropro_semxml_bean)

	* [@Bean vs @Component](#spring_beanxcomponent)


# Introdução<span id="intro"></span>

Leia o [README](README.md).

# Spring<span id="spring"></span>

Spring é um framework completo que fornece uma estrutura para criar aplicações Java. Esse framework é constituído de módulos agrupados em *Core Container*, *Data Access/Integration*, *Web*, *AOP (Aspect Oriented Programming)*, *Instrumentation* e *Test*.

Por exemplo, dentro do *Data Access/Integration* (Integração/Acesso aos Dados), temos o JDBC, ORM, OXM, JMS e Transactions. Já esse ORM, provê integração a APIs como JPA, JDO, Hibernate e iBatis.

## Configuração<span id="spring_config"></span>

Usaremos o Eclipse EE. É bem simples, crie um novo `Java Project`, mas **não** crie um `module-info.java` pra ele!

Baixe o [Tomcat](https://tomcat.apache.org/). Se você for usar o Spring 5.x, fique sabendo que essa versão só é compatível com a versão 9 do Tomcat. Mude para o modo de perspectiva do Java EE, na parte de baixo clique na aba `Servers` e clique no link para criar um novo servidor. Depois de configurar você pode voltar para a perspectiva normal do Java.

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

### Inversão de controle e Injeção de Dependência<span id="spring_primeiropro_iocinj"></span>

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


