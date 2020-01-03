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

## Other Spring Security Related Configuration
Login page, default success URL after login, default success URL after logout, failure URL for unsuccessful login URL, token validity and token storage repository configured inside WebSecurityConfigurerAdapter.


## Localization
WebMvcConfigurer interface of Spring Servlet Library implemented to provide local change interceptor. 
Resource bundle for messages.properties created for 2 different languages and thyemeleaf `th:text="#{message}` text attributes used.All the rest for the localization is being handled by the framework. As the local changes by user or default browser settings, proper text message is selected from resource bundle messages.properties file

## Package structure 
Classes are divided to packages according to logical functionalities they fullfill. 
- assemblers : Converts retrieved entities after CRUD operations to DTOs.
- config : Spring MVC, Security and Localization related configuration classes that inherited or implemented
- controllers : Spring MVC and Rest Controllers to expose back-end REST services for HTML forms and AJAX calls
- dto : Data Transfer Objects for exchanging data between front-end and back-end via web services
- entity : Hibernate JPA entities as database objects
- enums : Enumarated values used for assigning to class fields of dto and entity


![Package Structure](https://lh3.googleusercontent.com/I1MgrsgpUfUTKkRf-8fAdKi89z3F5j0Ut9ghA_Jnf49mQ5N0g0vPONZDqpzlhTFjuqxRw5AeTqc_0EXD_MmeL2DNOdJLmGVKd1yflzUOXca7eLCRT7pJ8hUhbRvMbRTu4yAvTTMRafhRJADyTVe3V9oSpJy3wPzXmzN9NndoPmS9daKUjlFidLApT5XAfMtL_XRWOz1e_PanvqDwukOjyZiiBo-kl4-2ZNMNnBLNqSVGTs52gnmfa5uqRXoEt_71jYu7i92wlI2IP6UBVs-f0AdFdm5C-5L-zpFljZnoNuwbXoNfVO9eA64cUMhRMO_wiRfZ40kVLrs5xKJtoRtrVUPEj2BcnW5ysUdtu8m12BGE6eo4Ld7bpQuDkzosv7HLocJ4pJZIK4zdz1F26z9hhSuo1o64X0jhtfzVB_4EfaTDTornhUCCF0zhPveeWY4IsUi7JMyQ1ww-H1iAbM54PgWAoUzGbFF41loDH2QTrU2Q2G4vXWX2iLZsdKA59yv6a1DMoBfc9MGghhQl0zd-_GEU5X4xe6pp9F5tDHfR6V5IPBVxKah5mJPsYtQtDRvwlopvWin2Cetfa7oebsqSejoMXGtrLR6CBFnxa71-XzKkxs4hJQkoKfZDtxlGxHES_7_1mV49iTF15N7DNSu80A129JhVhUCzN2AbejudzYDjC5YjCsV4NUbsgKGVgWxuUJ1BRlVAdkcshYrk5c9cpjRMdNMkecCvK517vlTtP8MO2xA=w334-h511-no "Packages")














