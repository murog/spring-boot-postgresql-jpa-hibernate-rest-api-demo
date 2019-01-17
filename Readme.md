

## what is your application?
Java application can be compiled down to one executable file (ex: .jar, .war). In our case, we will be creating a jar file that will be saved to a directory called __target__.
This can be done from your IDE (ex: Intellij, Eclipse).
```bash
$ mvn clean install
$ ls target 
< there should be a bunch of files>
classes
generated-sources
generated-test-sources
maven-archiver
maven-status
postgres-demo-0.0.1-SNAPSHOT.jar
postgres-demo-0.0.1-SNAPSHOT.jar.original
surefire-reports
test-classes
```
to run you application from the command line
```bash
$ java -jar target/postgres-demo-0.0.1-SNAPSHOT.jar
```
## what does your application need to run?

- java 8
    - maven
- database (ex: postgres)
    - database table 
    - databese username
    
You can check this information in the application.

To find the java version, check the pom.xml
```bash
$ cat pom.xml
< lots of stuff will be in here>
...    
    <name>postgres-demo</name>
    <description>Demo project for Spring Boot</description>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.0.1.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <java.version>1.8</java.version>
    </properties>
...
```

```bash
$ cat src/main/resources/application.properties
## Spring DATASOURCE (DataSourceAutoConfiguration & DataSourceProperties)
spring.datasource.url=jdbc:postgresql://localhost:5432/postgres_demo
spring.datasource.username=
spring.datasource.password=

# The SQL dialect makes Hibernate generate better SQL for the chosen database
spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.PostgreSQLDialect

# Hibernate ddl auto (create, create-drop, validate, update)
spring.jpa.hibernate.ddl-auto = update
```

In this example, our application uses a postgres database called _postgres_demo_.  There is no username or password defined. 




---------
## Spring Boot, PostgreSQL, JPA, Hibernate REST API Demo

## Tutorial

Check out the complete tutorial on the CalliCoder blog -

[Spring Boot, PostgreSQL, JPA, Hibernate RESTful CRUD API Example](https://www.callicoder.com/spring-boot-jpa-hibernate-postgresql-restful-crud-api-example/)

## Steps to Setup

**1. Clone the repository**

```bash
git clone https://github.com/callicoder/spring-boot-postgresql-jpa-hibernate-rest-api-demo.git
```

**2. Configure PostgreSQL**

First, create a database named `postgres_demo`. Then, open `src/main/resources/application.properties` file and change the spring datasource username and password as per your PostgreSQL installation.

**3. Run the app**

Type the following command from the root directory of the project to run it -

```bash
mvn spring-boot:run
```

Alternatively, you can package the application in the form of a JAR file and then run it like so -

```bash
mvn clean package
java -jar target/postgres-demo-0.0.1-SNAPSHOT.jar
```
