# spring-boot-admin
Spring Boot Admin is an application to manage and monitor your Spring Boot Applications.

##Register the client app
Add spring-boot-admin-starter-client dependency to the pom.xml file

```
<dependency>
      <groupId>de.codecentric</groupId>
      <artifactId>spring-boot-admin-starter-client</artifactId>
      <version>x.y.z</version>
</dependency>
```

Enable the spring-boot-admin Client by configuring the URL of the Spring Boot Admin Server in your application.yml
```
spring:
  boot:
    admin:
      client:
        url: http://localhost:8888
        username: username
        password: password
        instance:
          name: the-name-of-your-api
          management-base-url: management-base-url
          service-base-url: ${spring.boot.admin.client.instance.management-base-url}
```

With the exposure of all endpoints we have the maximum view.
```
management:
  endpoints:
    web:
      exposure:
        include: '*'
```

Optional: Base url for computing the management-url to register with. The path is inferred at runtime, and appended to the base url. 
```
spring:
  boot:
    admin:
      client:
        instance:
          name: the-name-of-your-api
          management-base-url: management-base-url
          service-base-url: ${spring.boot.admin.client.instance.management-base-url}
```

Optional: In that case you will have Spring Security on the classpath, and you can disable management security like this:

```
management:
  security: 
    enabled: false
```