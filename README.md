# Kubernetes Assignement
This project serves as an illustration of fundamental Kubernetes concepts and principles.


## Prerequisites
Before you begin, make sure your system meets the following prerequisites:

 -Docker is installed.
 -Kubernetes CLI (kubectl) is installed.
 -Minikube is installed
 
These prerequisites should be installed on your system to ensure a smooth and successful setup and execution of the project.

## Installation

1. Clone the repository:

```shell
    git clone https://github.com/inficareAbhishek/Microservices-Kubernates.git
```

2. Change the project  directory to the clone repository:

```shell
    cd Microservices-Kubernates
```
3. Once you moved into the step number 2 directory then you will find the below folder/files:
  a. APIConfig
  b. DataBaseConfig
  c. README.md
  d. springboot-microservice-postgres-db-master // Actual source code
  
4. Deploy the required resources:

```shell
    # execute below command for database
   kubectl apply -f DatabaseConfig/databaseSecret.yaml
   kubectl apply -f DatabaseConfig/databaseConfig.yaml
   kubectl apply -f DatabaseConfig/databaseDeployment.yaml
   kubectl apply -f databaseCreation.yaml
```

```shell
    # execute below command for API
   kubectl apply -f APIConfig/apiSecrets.yaml
   kubectl apply -f APIConfig/apiConfig.yaml
   kubectl apply -f APIConfig/apiDeployment.yaml
```

5. Check for the service
 ```shell
   kubectl get po
 ```

6. move to APIConfig directory and run below command

   ```shell
   kubectl apply -f apiSecrets.yaml
   kubectl apply -f apiConfig.yaml
   kubectl apply -f apiDeployment.yaml
   ```

## Usage

1. Get the services:
``` shell

   kubectl get services
```

2. copy the "api-service" received from the 5th step and paste it on the below command

```shell
    minikube service api-service --url 
```
3. copy the URL received from the 6th step and paste it with appending employees like below:
``` shell
   http://127.0.0.1:49677/employees
 ```
 Above might give empty result, so please hit the below post url on the postman with the body given:
 http://127.0.0.1:49677/employees/save
 
 {
    "name": "Test12345",
    "role": "emp1",
    "age": "36"
}

## Cleanup
Please ensure to clean up the process initiated with the below commands:

``` shell
   kubectl delete all --all
   minikube stop
```
