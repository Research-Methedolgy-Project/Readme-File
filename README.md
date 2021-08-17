# When and How to migrate from Monolithic to Microservice Architecture?
    Yashkumar Parikh
    Lakehead University - Computer Science
    Email: parikhy@lakeheadu.ca

## Research Methodology 

These Projects are created while researching on topic "When and How to migrate from Monolithic to Microservice Architecture?". An application is created and then the applications' Monolith architecture is replaced by Microservice architecture. 

# Monolith Application Repository
1. [Ecommerce Project](https://www.google.comhttps://github.com/Research-Methedolgy-Project/Ecommerce_Project)

# Microservice Applications Repositories
1. [API Gateway](https://github.com/Research-Methedolgy-Project/Api_Gateway)
2. [Product Service](https://github.com/Research-Methedolgy-Project/Product_Service)
3. [Order Service](https://github.com/Research-Methedolgy-Project/Order_Service)
4. [Cart Service](https://github.com/Research-Methedolgy-Project/Cart_Service)

## Table of Contents

1. [Project Description](#project-description)
2. [This project includes the following things](#this-project-includes-the-following-things)
3. [Architecture followed](#architecture-followed)
4. [Project Related Terminologies](#project-related-terminologies)
5. [Install](#install)
6. [Swagger URL](#swagger-url)
7. [Project Status](#project-status)
8. [Road-map](#road-map)
9. [Contributors](#contributors)
10. [Contact Details](#contact-details)


## Project Description

This website is designed for selling products online. Users can register them selfs into the website, filter and search for different products category-wise, add products to the cart and order the item. 

## This project includes the following things
1. Spring Security Configured.
2. MySQL Configured.
3. Liquibase Configured.
4. Ehcache Configured.
5. Two different env Configured (Dev and Prod).
6. Spring actuator Configured.
7. Logging Configured (Through AOP).
8. Pre-made User and Authority Class with CRUD Rest endpoints ready.
9. Swagger Configured.

## Architecture followed
    
    In this Monolith Project and Services, we have used service layer architecture
    with MVC architecture. 
    
    A service layer architecture includes a service layer in the
    the application where we need to write business logic and acts as
    a bridge between higher-level layer (controller) and lower level
    layer (Repository).
    
## Project Related Terminologies
    
    Controller: It is the same as a Controller concept in the MVC application 
                in which controller is a front face of the application 
                that is where we expose our application endpoints and
                which is a place that handles the request and the response for the 
                application.
                
    DTO: It represents the request or response objects that are exposed to the 
         HTTP Client. It is a simple POJO class that is used in the controller, the service and is not used in the Repository. It is used so that we can only expose those fields [localhost:8080/swagger-ui.html](localhost:8080/swagger-ui.html)

         from the domain class which are required by the HTTP Client specific to 
         application requirement.
         
    Domain: It is a simple POJO class that is used by the Repository and acts as an Entity (Model in MVC)
            in this application. It is used in Service, Repository and is not exposed to the Controller.
            It can also be used to represent a table in ORM like Hibernate.
            
    Mapper: It is used to convert DTO to Domain/Entity and Domain/Entity to DTO. This is generally used in
            Service where we convert DTO to Domain and Domain DTO while interacting with Controller and Repository.
         
    Repository: It is an interface that is used to deal with the data source of the application and acts as a bridge between our application and the data source where we store application data.
                It provides methods for the creation and manipulation of the data stored in the data source. It is 
                a data access layer for our application.
    
    Service: The layer of the application where we write our business logic and which acts as a bridge between the controller and repository. Here basically we perform the following 
             actions and other actions can also be performed specifically to application requirements:
                1. Conversion of DTO to Domain and Domain to DTO.
                2. Business logic of the application API.
                3. Acts as a bridge between Controller and Repository.
                4. Accepting the Request from the Controller.
                5. Return Response to the Controller.
                
              In services we use the concept of interface and implementation class for each service to
              provide loose coupling in the application.
              
              
              
## Install

To run on local follow the given steps:

    1. git clone repo_link.
    2. Import as Gradle project in IntelliJ.
    3. Create a schema in the DB server with the name mentioned in 
       the application-dev.yml file in the data source URL.
    4. if Linux user run ./gradlew clean and then ./gradlew -Plocal.
    5. if windows user run gradlew  clean and then gradlew -Plocal.
    
Every repository has a specific Readme.Md file, you can also look at it for more information.  

### Swagger URL

For API documentation and testing swagger is configured in every application and services. Only change the port in the following URL,
[localhost:8080/swagger-ui.html](http:\\localhost:8080/swagger-ui.html)


## Project Status
We have successfully moved from Monolith architecture to Microservice architecture.


## Road-map
We are planning to release a new version which includes Payment Gateway integration, Order Tracking, etc. 

## Contributors

[Yash Parikh](https://github.com/yparikh8036)

## Contact Details

Anyone has any questions or wants to contribute to the project then write an email at parikhy@lakeheadu.ca.
