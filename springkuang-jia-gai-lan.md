# Spring Framework Overview

# Spring框架概览

Spring makes it easy to create Java enterprise applications. It provides everything you need to embrace the Java language in an enterprise environment, with support for Groovy and Kotlin as alternative languages on the JVM, and with the flexibility to create many kinds of architectures depending on an application’s needs. As of Spring Framework 5.0, Spring requires JDK 8+ \(Java SE 8+\) and provides out-of-the-box support for JDK 9 already.

Spring简化了Java企业级应用的创建。它提供企业环境Java开发的一切需要，支持Groovy和Kotlin作为虚拟机上的替代语言，可以根据应用的需要灵活的创建多种体系结构。对于Spring Framework5.0而言，Spring需要JDK8及以上版本，同时提供了对JDK9开箱即用的支持。

Spring supports a wide range of application scenarios. In a large enterprise, applications often exist for a long time and have to run on a JDK and application server whose upgrade cycle is beyond developer control. Others may run as a single jar with the server embedded, possibly in a cloud environment. Yet others may be standalone applications \(such as batch or integration workloads\) that do not need a server.

Spring支持广泛的应用场景。在大企业中，一个应用程序通常存在很长时间，以致只能运行在更新周期超出了开发者控制的JDK和应用服务器上。也有一些应用作为单一的jar和服务器嵌入，可能运行在云环境中。其他的可能是独立的应用（例如批处理和集成工作负载），不需要服务器。

Spring is open source. It has a large and active community that provides continuous feedback based on a diverse range of real-world use cases. This has helped Spring to successfully evolve over a very long time.

Spring是开源的。拥有庞大的活跃的社区，提供基于不同范围的真实例子的持续贡献反馈。这帮助Spring成功发展了很长时间。

## 1. What We Mean by "Spring" {#overview-spring}

# 1.Spring是什么

The term "Spring" means different things in different contexts. It can be used to refer to the Spring Framework project itself, which is where it all started. Over time, other Spring projects have been built on top of the Spring Framework. Most often, when people say "Spring", they mean the entire family of projects. This reference documentation focuses on the foundation: the Spring Framework itself.

术语“Spring”在不同的地方有不同的意思。它习惯指Spring Framework项目本身，这也是最开始的意思。随着时间的过去，其他的Spring项目在Spring Framework的基础上创建了。大部分时候人们说的“Spring”是指整个Spring家族的项目。这个参考文档关注基础的Spring Framework本身。

The Spring Framework is divided into modules. Applications can choose which modules they need. At the heart are the modules of the core container, including a configuration model and a dependency injection mechanism. Beyond that, the Spring Framework provides foundational support for different application architectures, including messaging, transactional data and persistence, and web. It also includes the Servlet-based Spring MVC web framework and, in parallel, the Spring WebFlux reactive web framework.

Spring Framework分为几个模块。应用可以选择需要的模块。核心模块是核心容器（core container）,包括配置模型和依赖注入机制。除此之外，Spring Framework 为不同的应用结构提供了基础支持，包括消息传递，事务化数据和持久化及web。还包括基于Servlet的web框架Spring MVC ，以及响应式web框架Spring WebFlux。

A note about modules: Spring’s framework jars allow for deployment to JDK 9’s module path \("Jigsaw"\). For use in Jigsaw-enabled applications, the Spring Framework 5 jars come with "Automatic-Module-Name" manifest entries which define stable language-level module names \("spring.core", "spring.context" etc\) independent from jar artifact names \(the jars follow the same naming pattern with "-" instead of ".", e.g. "spring-core" and "spring-context"\). Of course, Spring’s framework jars keep working fine on the classpath on both JDK 8 and 9.

模块的注意事项：Spring框架的jar包允许部署在JDK9的模块路径（“Jigsaw”）。

## 2. History of Spring and the Spring Framework {#overview-history}

Spring came into being in 2003 as a response to the complexity of the early[J2EE](https://en.wikipedia.org/wiki/Java_Platform,_Enterprise_Edition)specifications. While some consider Java EE and Spring to be in competition, Spring is, in fact, complementary to Java EE. The Spring programming model does not embrace the Java EE platform specification; rather, it integrates with carefully selected individual specifications from the EE umbrella:

* Servlet API \([JSR 340](https://jcp.org/en/jsr/detail?id=340)\)

* WebSocket API \([JSR 356](https://www.jcp.org/en/jsr/detail?id=356)\)

* Concurrency Utilities \([JSR 236](https://www.jcp.org/en/jsr/detail?id=236)\)

* JSON Binding API \([JSR 367](https://jcp.org/en/jsr/detail?id=367)\)

* Bean Validation \([JSR 303](https://jcp.org/en/jsr/detail?id=303)\)

* JPA \([JSR 338](https://jcp.org/en/jsr/detail?id=338)\)

* JMS \([JSR 914](https://jcp.org/en/jsr/detail?id=914)\)

* as well as JTA/JCA setups for transaction coordination, if necessary.

The Spring Framework also supports the Dependency Injection \([JSR 330](https://www.jcp.org/en/jsr/detail?id=330)\) and Common Annotations \([JSR 250](https://jcp.org/en/jsr/detail?id=250)\) specifications, which application developers may choose to use instead of the Spring-specific mechanisms provided by the Spring Framework.

As of Spring Framework 5.0, Spring requires the Java EE 7 level \(e.g. Servlet 3.1+, JPA 2.1+\) as a minimum - while at the same time providing out-of-the-box integration with newer APIs at the Java EE 8 level \(e.g. Servlet 4.0, JSON Binding API\) when encountered at runtime. This keeps Spring fully compatible with e.g. Tomcat 8 and 9, WebSphere 9, and JBoss EAP 7.

Over time, the role of Java EE in application development has evolved. In the early days of Java EE and Spring, applications were created to be deployed to an application server. Today, with the help of Spring Boot, applications are created in a devops- and cloud-friendly way, with the Servlet container embedded and trivial to change. As of Spring Framework 5, a WebFlux application does not even use the Servlet API directly and can run on servers \(such as Netty\) that are not Servlet containers.

Spring continues to innovate and to evolve. Beyond the Spring Framework, there are other projects, such as Spring Boot, Spring Security, Spring Data, Spring Cloud, Spring Batch, among others. It’s important to remember that each project has its own source code repository, issue tracker, and release cadence. See[spring.io/projects](https://spring.io/projects)for the complete list of Spring projects.

## 3. Design Philosophy {#overview-philosophy}

When you learn about a framework, it’s important to know not only what it does but what principles it follows. Here are the guiding principles of the Spring Framework:

* Provide choice at every level. Spring lets you defer design decisions as late as possible. For example, you can switch persistence providers through configuration without changing your code. The same is true for many other infrastructure concerns and integration with third-party APIs.

* Accommodate diverse perspectives. Spring embraces flexibility and is not opinionated about how things should be done. It supports a wide range of application needs with different perspectives.

* Maintain strong backward compatibility. Spring’s evolution has been carefully managed to force few breaking changes between versions. Spring supports a carefully chosen range of JDK versions and third-party libraries to facilitate maintenance of applications and libraries that depend on Spring.

* Care about API design. The Spring team puts a lot of thought and time into making APIs that are intuitive and that hold up across many versions and many years.

* Set high standards for code quality. The Spring Framework puts a strong emphasis on meaningful, current, and accurate Javadoc. It is one of very few projects that can claim clean code structure with no circular dependencies between packages.

## 4. Feedback and Contributions {#overview-feedback}

For how-to questions or diagnosing or debugging issues, we suggest using StackOverflow, and we have a[questions page](https://spring.io/questions)that lists the suggested tags to use. If you’re fairly certain that there is a problem in the Spring Framework or would like to suggest a feature, please use the[JIRA issue tracker](https://jira.spring.io/browse/spr).

If you have a solution in mind or a suggested fix, you can submit a pull request on[Github](https://github.com/spring-projects/spring-framework). However, please keep in mind that, for all but the most trivial issues, we expect a ticket to be filed in the issue tracker, where discussions take place and leave a record for future reference.

For more details see the guidelines at the[CONTRIBUTING](https://github.com/spring-projects/spring-framework/blob/master/CONTRIBUTING.adoc), top-level project page.

## 5. Getting Started {#overview-getting-started}

If you are just getting started with Spring, you may want to begin using the Spring Framework by creating a[Spring Boot](https://projects.spring.io/spring-boot/)-based application. Spring Boot provides a quick \(and opinionated\) way to create a production-ready Spring-based application. It is based on the Spring Framework, favors convention over configuration, and is designed to get you up and running as quickly as possible.

You can use[start.spring.io](https://start.spring.io/)to generate a basic project or follow one of the["Getting Started" guides](https://spring.io/guides), such as[Getting Started Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/). As well as being easier to digest, these guides are very task focused, and most of them are based on Spring Boot. They also cover other projects from the Spring portfolio that you might want to consider when solving a particular problem.

