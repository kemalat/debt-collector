# debt-collector
This demo application developed using Spring MVC, Security and JPA frameworks at back-end side. Front-end side is based on javascript and JQuery library.

## Maven
Maven dependency and jar plugins used to prevent fat jar generation. All required librariers copied under the lib directory under the build path and only application classes are compressed as application jar to make it smaller.

## data.sql file
When project is run with this file on the classpath, Spring will pick data.sql and use it for populating the database. In this project data.sql file consisting user, roles and user_role tables and their data. Actually schema.sql file can be also used to create database table structure if you don not want to rely on Hibernate for table creation/update via entities. 

## Thymeleaf Template Directory
Thymeleaf template engine is used for our Spring Boot application. Spring Boot provides a default location where it expects to find our templates.By default, Spring Boot looks for our templates in src/main/resources/templates. This path can be overriden with below property line. in application.properties:
```
spring.thymeleaf.prefix=classpath:/templates/
```

## Role Based Access Control and Authorization
Role based user access control and authorization implemented using Spring Security. User data and roles are being stored in MySQL database. UserDetailsService interface of Spring Framework Security library implemented to provide CustomUserDetailsService which interrogates MySQL database tables for user and role data using custom JpaRepository.

  * WebSecurityConfigurerAdapter abstract class extended as Web Security Config to set web service paths access rights according to user roles. Files under /static/assets , /static/error and /static/vendors directories has full permission since even without user authentication is access required to show HTML content properly. Rest services that are only exposed to users with Admin role located under the /admin path , for other user roles Rest service root path set to /user

## Localization
WebMvcConfigurer interface of Spring Servlet Library implemented to provide local change interceptor. 
Resource bundle for messages.properties created for 2 different languages and thyemeleaf `th:text="#{message}` text attributes used.All the rest for the localization is being handled by the framework. As the local changes by user or default browser settings, proper text message is selected from resource bundle messages.properties file












