# Commands:

- dotnet new webapi -n Catalog
- dotnet dev-certs https --trust
- dotnet add package MongoDB.Driver
- dotnet add package AspNetCore.HealthChecks.MongoDb
- docker run -d --rm --name mongo -p 27017:27017 -v mongodb_data:/data/db -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=123456789 mongo
- docker stop mongo
- dotnet user-secrets init
- dotnet user-secrets set MongoDbSettings:Password 123456789

# Docker build:

- docker build -t catalog:v1 .
- docker network create net5
- docker network ls
- docker run -d --rm --name mongo -p 27017:27017 -v mongodb_data:/data/db -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=123456789 --network=net5 mongo

- docker run -it --rm -p 8089:80 -e MongoDbSettings:Host=mongo -e MongoDbSettings:Password=123456789 --network=net5 catalog:v1

# Push to Dockerhub:

- docker tag catalog:v1 nhatvu148/catalog:v1
- docker push nhatvu148/catalog:v1
- docker rmi catalog:v1 nhatvu148/catalog:v1
- docker run -it --rm -p 8089:80 -e MongoDbSettings:Host=mongo -e MongoDbSettings:Password=123456789 --network=net5 nhatvu148/catalog:v1

- docker build -t nhatvu148/catalog:v2 .
- docker push nhatvu148/catalog:v2

# Kubernetes:

- kubectl config current-context
- kubectl create secret generic catalog-secrets --from-literal=mongodb-password='123456789'
- kubectl apply -f k8s/
- kubectl get deployments
- kubectl get pods
- kubectl get statefulsets
- kubectl logs catalog-deployment-86db5967b4-bksrm #pod id

- kubectl get pods -w #watch mode
- kubectl delete pod catalog-deployment-86db5967b4-bksrm

- kubectl scale deployments/catalog-deployment --replicas=3

- kubectl logs catalog-deployment-756886c7df-8x8h5 -f #watch logs

# Unit Test:

- dotnet new xunit -n Catalog.UnitTests

# VSCode Extensions:

- MongoDB for VSCode
