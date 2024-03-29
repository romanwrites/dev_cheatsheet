# Spring

# Why use constructor injection over setter injection
From [Spring docs](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-setter-injection)

```
... it is a good rule of thumb to use constructors for mandatory dependencies and setter methods or configuration methods for optional dependencies.

The Spring team generally advocates constructor injection, as it lets you implement application components as immutable objects and ensures that required dependencies are not null. Furthermore, constructor-injected components are always returned to the client (calling) code in a fully initialized state. As a side note, a large number of constructor arguments is a bad code smell, implying that the class likely has too many responsibilities and should be refactored to better address proper separation of concerns.

Setter injection should primarily only be used for optional dependencies that can be assigned reasonable default values within the class. Otherwise, not-null checks must be performed everywhere the code uses the dependency. One benefit of setter injection is that setter methods make objects of that class amenable to reconfiguration or re-injection later. Management through JMX MBeans is therefore a compelling use case for setter injection.
```

## Tests ignore logging level in application.yml
I used `lombok` annotation `@Slf4j`. And set log level in `application.yml`.  Tests ignored it.  
So I add file [`logback-test.xml`](files/logback-test.xml) to src/test/resources  


## Guides
* [🇷🇺 Сгенерировать liquibase миграции](https://sysout.ru/rabota-s-liquibase/). Пункт 2
* [Throttling in java spring boot](https://golb.hplar.ch/2019/08/rate-limit-bucket4j.html)
* [Three interceptors in spring](https://programmer.group/three-interceptors-in-spring.html)
