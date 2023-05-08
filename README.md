# Cinema Service
A simple imitation of the backend of a cinema app. Using Spring and Hibernate

![Logo](logo.jpeg)

## Navigation
- [Installation and Deployment](#installation-and-deployment)
- [Features](#features)
- [Technology](#technology)
- [Author](#author)

## Installation and Deployment
- Install IntelliJ IdEA;
- Clone project to your local machine;
- Configure your Mysql database and db.properties;
- Build the project using Maven: mvn clean install;
- Deploy the WAR file to a servlet container such as Tomcat or other;
- After deploying the project, you can use the web application using the link http://localhost:8080/ and PostMan

## Features
- Registration of users;
- Authentication;
- Authorization
  - Unregistered Users
    - Can register (POST /register).
  - Users with the "USER" Role
    - Can access the list of cinema halls, movies, and available sessions (GET /cinema-halls, /movies, /movie-sessions/available).
    - Can view their own orders (GET /orders).
    - Can complete orders (POST /orders/complete).
    - Can add sessions to their shopping cart (PUT /shopping-carts/movie-sessions).
    - Can retrieve information about their shopping cart (GET /shopping-carts/by-user).
  - Users with the "ADMIN" Role
    - Can access the list of cinema halls, movies, and available sessions (GET /cinema-halls, /movies, /movie-sessions/available).
    - Can add cinema halls, movies, and sessions (POST /cinema-halls, /movies, /movie-sessions).
    - Can update session information (PUT /movie-sessions/{id}).
    - Can delete sessions (DELETE /movie-sessions/{id}).
    - Can retrieve information about users by email (GET /users/by-email).
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

## Author
Volodymyr Prysiazhniuk