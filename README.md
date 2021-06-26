# Commands:

- dotnet new webapi -n Catalog
- dotnet dev-certs https --trust
- dotnet add package MongoDB.Driver
- docker run -d --rm --name mongo -p 27017:27017 -v mongodb_data:/data/db -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=123456789 mongo
- dotnet user-secrets init
- dotnet user-secrets set MongoDbSettings:Password 123456789

# VSCode Extensions:

- MongoDB for VSCode
