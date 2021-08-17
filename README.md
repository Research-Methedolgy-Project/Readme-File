# When and How to migrate from Monolithic to Microservice Architecture?
    Yashkumar Parikh
    Lakehead University - Computer Science
    Email: parikhy@lakeheadu.ca

## Research Methodology 

This Projects are created while doing research about the topic. One Monolith application is created and then the Monolith architechture is replaced by Microservice architechture. 

# Monolith Application Repository:
1. [Ecommerce Project](https://www.google.comhttps://github.com/Research-Methedolgy-Project/Ecommerce_Project)

# Microservice Applications Repositories:
1. [API Gateway](https://github.com/Research-Methedolgy-Project/Api_Gateway)
2. [Product Service](https://github.com/Research-Methedolgy-Project/Product_Service)
3. [Order Service](https://github.com/Research-Methedolgy-Project/Order_Service)
4. [Cart Service](https://github.com/Research-Methedolgy-Project/Cart_Service)

## Project Description

This website is designed for selling products online. Users can register them selfs into the website, filter and search for different products category wise, add product in cart and Order the item. 

## This project include the following things:
1. Spring Security Configured.
2. MySQL Configured.
3. Liquibase Configured.
4. Ecache Configured.
5. Two different env Configured (Dev and Prod).
6. Spring actuator Configured.
7. Logging Configured (Through AOP).
8. Pre-made User and Authority Class with CRUD Rest end points ready.
9. Swagger Configured.

## Architecture followed:
    
    In this Monolith Project and Services we have used service layer architecture
    with MVC architecture. 
    
    A service layer architecture includes a service layer in the
    application where we need to write business logic and acts as
    a bridge between higer level layer (controller) and lower level
    layer (Repository).
    
## Project Related Terminologies:
    
    Controller: It is same as a Controller concept in the MVC application 
                in which controller is a front face of the applicaiton 
                that is where we expose our application endpoints and
                which is a place that handles the request and the response for the 
                applicaiton.
                
    DTO: It represents the request or response objects that is basically exposed to the 
         Http Client. It is simple POJO class which is used in the controller, the service 
         and is not used in the Repository. It is used so that we can only expose those fields 
         from the domain class which are actually required by the Http Client specific to 
         applicaiton requirement.
         
    Domain: It is a simple POJO class that is used by the Repository and acts as an Entity (Model in MVC)
            in this applicaiton. It is used in Service, Repository and is not exposed to the Controller.
            It can also be used to represent an table in ORM like Hibernate.
            
    Mapper: It is used to convert DTO to Domain/Entity and Domain/Entity to DTO. This is generally used in
            Service where we convert DTO to Domain and Domain DTO while interacting with Controller and Respository.
         
    Repository: It is a interface that is used to deal with our data source of the application and acts
                as a bridge between our application and data source where we store applicaiton data.
                It provides methods for creation and manuplication of the data stored in data source. It is 
                basically a data access layer for our application.
    
    Service: The layer of the applicaiton where we write our business logic and which 
             acts as a bridge between the contoller and repository. Here basically we perform following 
             actions and other actions can also be performed specific to application requirements:
                1. Conversion of DTO to Domain and Domain to DTO.
                2. Business logic of the applicaiton api.
                3. Acts as a bridge between Controller and Repository.
                4. Accepting the Request from the Controller.
                5. Return Response to the Controller.
                
              In services we use concept of interface and implementation class for each service to
              provide loose coupling in the applicaiton.
              
              
              
## Project Details

To run on local follow the given steps:

    1. git clone repo_link.
    2. Import as gradle project in Intellji.
    3. Create a schema in db server with the name mentioned in 
       the application-dev.yml file in the datasource url.
    4. if linux user run ./gradlew clean and then ./gradlew -Plocal.
    5. if windows user run gradlew clean and then gradlew -Plocal.
    
Every repository has a specific Readne.Md file, you can also look at it for more information.    
    
## Contact Details

Anyone have any questions or wants to contribute to the project then write an email at parikhy@lakeheadu.ca.
