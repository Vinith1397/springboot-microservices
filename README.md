
## Overview of the Project

- **Goal**: To demonstrate the integration of machine learning capabilities into a Java application using a microservices architecture.
- **Technology Stack**: Utilizes Spring Boot for microservices and Apache Spark ML for machine learning tasks.

## Components of the Project

The project comprises several microservices, each fulfilling a distinct role in the machine learning workflow:

### 1. income-predictor-dto (Data Transfer Objects)

- Defines the data objects for transferring data within the application, including inputs to the machine learning model and the generated predictions.

### 2. income-predictor-ml (Machine Learning)

- The core machine learning component that uses Apache Spark ML to process input data, train a machine learning model, and generate predictions.

### 3. income-predictor-service

- Exposes RESTful endpoints for accessing machine learning functionalities, acting as an intermediary between the `income-predictor-ml` and other services or clients.

### 4. income-predictor-vaadin

- The web interface for user interaction, built with Vaadin. Allows users to input data for predictions and view the results.

## How It Works

- **Compilation and Running Process**: Uses Maven for building and managing project dependencies. Each component is compiled into a `.jar` file.

- **Running the Applications**: Each service (`income-predictor-ml`, `income-predictor-service`, and `income-predictor-vaadin`) is run separately but works together to process user inputs and display predictions.

- **Interactions**:
  - Users input data through the `income-predictor-vaadin` web interface.
  - The web application forwards this data to the `income-predictor-service`.
  - The service communicates with the `income-predictor-ml` to process the data with the machine learning model and generate predictions.
  - Predictions are sent back to be displayed in the web interface.

## Simple Terms Explanation

This project can be likened to a sophisticated, automated system capable of making predictions based on provided data. Imagine it as a highly advanced robot in a factory inspecting products (input data) and predicting which ones will be successful (the predictions). The project showcases how to construct and organize the robot's "brain" (machine learning component) and its communication methods with the external world (through microservices and a web interface), utilizing Java and Apache Spark ML.


## Quick start

This section can help you to start the solution without a deep knowledge of the different technologies used. Please follow the instructions and PR if more information is needed.

### Maven

A very simple process if you know Maven and Java, this is the recommended way if you want to explore or improve the project after the quick start.

#### Prerrequisites

##### Java

You need a JDK installed to compile all the projects, you can download the latest version from [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html), [OpenJDK](http://openjdk.java.net/install/) or [Azul Zulu (not tested)](https://www.azul.com/downloads/zulu/)

You can check that Java is available with the command below:

_java -version_

##### Maven

You also need Apache Maven installed. You can find installation instructions [here](https://maven.apache.org/download.cgi)

You can check your maven installation with the command below:

_mvn -version_

##### Spark

You can download Apache Spark [here](https://spark.apache.org/downloads.html). Please select the package type prebuild for Hadoop. Please note that you will need the installation path in the compilation and running process.

#### Process

##### Compilation

1. Clone project in a local directory and enter into microservices-ml folder.
2. Go to income-predictor-dto project.
3. Into this project run _mvn clean install_ execution should finish with a _BUILD SUCCESS_ message
4. Go to income-predictor-ml project.
5. Edit the application.properties file and change _spark_home, models_path_ and _dataset_file_ to the ones in your local machine.
6. Into this project run _mvn clean install_ execution should finish with a _BUILD SUCCESS_ message.
7. Go to income-predictor-service project.
8. Edit the application.properties file and change _spark_home, models_path_ and _dataset_file_ to the ones in your local machine.
9. Into this project run _mvn clean install_ execution should finish with a _BUILD SUCCESS_ message.
10. Go to income-predictor-vaadin project.
11. Into this project run _mvn clean install_ execution should finish with a _BUILD SUCCESS_ message.
12. Now all artifacts are generated and ready to be executed.

##### Running

We need to run all three applications to have the solution working, to do so we only need to follow the instructions below:

1. Go to _income-predictor-ml/target_
1. Check that the file _income-predictor-ml-0.0.1-SNAPSHOT.jar_ exists. If not you should follow the steps described in __Compilation__ section.
1. Run the project using the command _java -jar income-predictor-ml-0.0.1-SNAPSHOT.jar_, application should now connect to spark hadoop and read input file and create a model using this data.
1. Go to _income-predictor-service/target_
1. Check that the file _income-predictor-service-0.0.1-SNAPSHOT.jar_ exists. If not you should follow the steps described in __Compilation__ section.
1. Run the project using the command _java -jar income-predictor-service-0.0.1-SNAPSHOT.jar_, now service application should be availabe at port 8082.
1. Go to _income-predictor-vaadin/target_
1. Check that the file _income-predictor-vaadin-0.0.1-SNAPSHOT.jar_ exists. If not you should follow the steps described in __Compilation__ section.
1. Run the project using the command _java -jar income-predictor-vaadin-0.0.1-SNAPSHOT.jar_, now web application should be available at port 8080.
1. You can open your browser and go to [http://localhost:8080](http://localhost:8080) to check the solution.

![alt Screen](https://github.com/oscuroweb/microservices-ml/blob/master/images/Capture.png)

### Docker

TBD

#### Prerrequisites

##### Docker

#### Process

## Topology

![alt Topology](https://github.com/oscuroweb/microservices-ml/blob/master/images/Topology.png)

This solution has three different projects:

- income-predictor-dto
- income-predictor-service
- income-predictor-ml
- income-predictor-vaadin

You can see below a description for each project.

### income-predictor-dto

![alt income-predictor-dto project class diagram](https://github.com/oscuroweb/microservices-ml/blob/master/images/DTO-Diagram.png)

This project includes all Data Transfer Objects needed in the solution, it also includes all the types needed to process the input file.

### income-predictor-ml

![alt income-predictor-ml project class diagram](https://github.com/oscuroweb/microservices-ml/blob/master/images/ML-Diagram.png)

The Machine-Learning project itself, implements the algo.

### income-predictor-service

![alt income-predictor-service project class diagram](https://github.com/oscuroweb/microservices-ml/blob/master/images/Service-Diagram.png)

Service that exposes the different endpoints to be consumed.

### income-predictor-vaadin

![alt income-predictor-service project class diagram](https://github.com/oscuroweb/microservices-ml/blob/master/images/Vaadin-Diagram.png)

Web application that shows the results.



