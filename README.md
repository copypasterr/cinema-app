# Cinema Service
A simple imitation of the backend of a cinema app. Using Spring and Hibernate

![Logo](logo.jpeg)

## Navigation
- [How to run](#how-to-run)
- [Features](#features)
- [Technology](#technology)
- [Structure](#structure)
- [Author](#author)

## How to run
- Install IntelliJ IdEA;
- Clone project to your local machine;
- Configure your Mysql database and `db.properties`;
- Build the project using Maven: `mvn clean install`;
- Deploy the WAR file to a servlet container such as Tomcat or other;
- After deploying the project, you can use the web application using the link `http://localhost:8080/` and PostMan
- Default credentials:
  - For admin login: `admin@i.ua`, password: `admin123`
  - For user login: `user@gmail.com`, password: `user!213`

## Features
- Registration of users;
- Authentication;
- Authorization
  - Unregistered Users
    - Can register (`POST /register`).
  - Users with the "USER" Role
    - Can access the list of cinema halls, movies, and available sessions (`GET /cinema-halls`, `/movies`, `/movie-sessions/available`).
    - Can view their own orders (`GET /orders`).
    - Can complete orders (`POST /orders/complete`).
    - Can add sessions to their shopping cart (`PUT /shopping-carts/movie-sessions`).
    - Can retrieve information about their shopping cart (`GET /shopping-carts/by-user`).
  - Users with the "ADMIN" Role
    - Can access the list of cinema halls, movies, and available sessions (`GET /cinema-halls`, `/movies`, `/movie-sessions/available`).
    - Can add cinema halls, movies, and sessions (`POST /cinema-halls`, `/movies`, `/movie-sessions`).
    - Can update session information (`PUT /movie-sessions/{id}`).
    - Can delete sessions (`DELETE /movie-sessions/{id}`).
    - Can retrieve information about users by email (`GET /users/by-email`).
  - All other requests require user authentication. The login form and HTTP authentication are available for all users. CSRF protection is disabled.

## Technology
- Java v.17.0.5
- Maven v.3.8.7
- Spring v.5.3.20
- Hibernate v.5.6.14.Final
- MySql v.8.0.22 
- Java Servlets v.4.0.1
- Jackson core v.2.14.1
- Javax annotation v.1.3.2
- Tomcat v.9.0.50

## Structure
This project utilizes the Layered Architectural Pattern, also known as Layered Design. This pattern helps to separate the application into several abstraction layers, each with specific responsibilities. In this case, the application is divided into levels such as controllers, services, DAO, models, and others. 

The Layered Architectural Pattern promotes modularity, maintainability, and testability of the application. By separating concerns into distinct layers, the code becomes more organized and easier to understand, thus enhancing the overall quality of the project.

1. config: This package contains configuration classes for application, such as Spring configuration, Hibernate configuration, security configuration.

2. controller: This package holds the controllers, which handle HTTP requests and responses. They are responsible for processing user inputs, invoking services, and returning appropriate views or responses.

3. dao (Data Access Object): This package contains classes that interact with the database directly. DAOs are responsible for CRUD operation in the database using Hibernate.

4. dto (Data Transfer Object): This package contains classes that serve as data carriers between different layers of the application.

5. exception: This package contains custom exception classes.

6. lib: This package houses email and password validators along with their annotations. These validators ensure that user-provided data is valid and meets the application's requirements.

7. model: This package contains the domain model classes or entities, which represent the core business objects of your application. These classes are typically annotated with Hibernate/JPA annotations to map them to the database.

8. security: This package includes the CustomUserDetailsService that implements the UserDetailsService interface. CustomUserDetailsService finds a user by their email and converts the user object into a UserDetails object, utilized by Spring Security for authentication and authorization.

9. service: This package contains service classes that implement the business logic of your application. Services are responsible for coordinating tasks, such as invoking DAOs, performing validations, and applying business rules.

10. util: Package with helper class DateTimePatternUtil to define the time format.

Author
Volodymyr Prysiazhniuk
