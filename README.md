# sflcore

## This project include the following things:
1. Spring Security Configured.
2. MySQL Configured.
3. Liquibase Configured.
4. Auditing Configured.
5. Ecache Configured.
6. Two different env Configured (Dev and Prod).
7. Spring actuator Configured.
8. Logging Configured (Through AOP).
9. Pre-made User and Authority Class with CRUD Rest end points ready.
10. Swagger Configured.
11. Sonar SunflowerLab Profile Passed.

## Architecture followed:
    
    In this base project we have used service layer architecture
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

### Swagger URL:
[https://ec2-18-219-86-32.us-east-2.compute.amazonaws.com:8080/swagger-ui.html](https://ec2-18-219-86-32.us-east-2.compute.amazonaws.com:8080/swagger-ui.html)

To run on local follow the given steps:

    1. git clone repo_link.
    2. Import as gradle project in Intellji.
    3. Copy application-dev.xml to application-local.xml
    3. Create a schema in db server with the name mentioned in 
       the application-local.yml file in the datasource url.
    4. if linux user run ./gradlew clean and then ./gradlew -Plocal.
    5. if windows user run gradlew clean and then gradlew -Plocal.

Base project have two env one is dev for development purpose and production for production server.

To start clean your application simply run:

    ./gradlew clean --> Linux/Mac Users
       
      gradlew clean --> Windows Users

To start your application in dev env simply run:
    
    ./gradlew --> Linux/Mac Users
    
      gradlew --> Windows Users

To check common configurations check **application.yml**.
To check db and other configurations for dev profile check **application-dev.yml**.
To check db and other configurations for prod profile check **application-prod.yml**.


For db just create schema in your db server and run the application tables would be create 
and loaded with dummy data. 

## Building for production

### Packaging as jar

To build the final jar and optimize the sflcore application for production, run:

    ./gradlew -Pprod clean bootJar

To ensure everything worked, run:

    java -jar build/libs/*.jar

Refer to [Using JHipster in production][] for more details.

### Packaging as war

To package your application as a war in order to deploy it to an application server, run:

    ./gradlew -Pprod -Pwar clean bootWar

## Testing

To launch your application's tests, run:

    ./gradlew test integrationTest jacocoTestReport

For more information, refer to the [Running tests page][].

### Code quality

Sonar is used to analyse code quality. You can start a local Sonar server (accessible on http://localhost:9001) with:

```
docker-compose -f src/main/docker/sonar.yml up -d
```

You can run a Sonar analysis with using the [sonar-scanner](https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner) or by using the gradle plugin.

Then, run a Sonar analysis:

```
./gradlew -Pprod clean check jacocoTestReport sonarqube
```

## Using Docker to simplify development (optional)

You can use Docker to improve your JHipster development experience. A number of docker-compose configuration are available in the [src/main/docker](src/main/docker) folder to launch required third party services.

For example, to start a mysql database in a docker container, run:

    docker-compose -f src/main/docker/mysql.yml up -d

To stop it and remove the container, run:

    docker-compose -f src/main/docker/mysql.yml down

You can also fully dockerize your application and all the services that it depends on.
To achieve this, first build a docker image of your app by running:

    ./gradlew bootJar -Pprod jibDockerBuild

Then run:

    docker-compose -f src/main/docker/app.yml up -d
