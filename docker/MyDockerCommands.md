# Images
* docker.io/library/spring-6-auth-server:0.0.1-SNAPSHOT
* docker.io/library/spring-6-rest-mvc:0.0.1-SNAPSHOT
* docker.io/library/spring-6-cloud-gateway:0.0.1-SNAPSHOT
* docker.io/library/reactivemongo:0.0.1-SNAPSHOT
* docker.io/library/spring-6-reactive:0.0.1-SNAPSHOT

# Docker Commands


Use Spring Boot Maven Plugin to build a Docker image:

```shell
./mvnw clean package spring-boot:build-image
```

Run Auth Server
```shell
docker run -d -p 9000:9000 --name auth-server spring-6-auth-server:0.0.1-SNAPSHOT
```

Run MySQL
```shell
docker run --name mysql -d -e MYSQL_USER=restadmin -e MYSQL_PASSWORD=password -e MYSQL_DATABASE=restdb -e MYSQL_ROOT_PASSWORD=password mysql:8
```

Run MongoDB
```shell
docker run --name mongo-db -d -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=example -p 27017:27017 mongo
```

Run Rest MVC
```shell
docker run --name rest-mvc -d -p 8081:8080 -e SPRING_PROFILES_ACTIVE=docker -e SPRING_SECURITY_OAUTH2_RESOURCESERVER_JWT_ISSUER_URI=http://auth-server:9000 --link auth-server:auth-server --link mysql:mysql spring-6-rest-mvc:0.0.1-SNAPSHOT
```
Run Reactive
'''shell
docker run --name reactive -d -p 8082:8080 -e SPRING_PROFILES_ACTIVE=docker --link auth-server:auth-server spring-6-reactive:0.0.1-SNAPSHOT
'''

Run Reactive Mongo
```shell
docker run --name reactive-mongo -d -p 8083:8080 -e SPRING_PROFILES_ACTIVE=docker --link auth-server:auth-server --link mongo-db:mongo-db reactivemongo:0.0.1-SNAPSHOT
```

Run Gateway
```shell
docker run --name gateway -d -p 8080:8080 -e SPRING_PROFILES_ACTIVE=docker --link auth-server:auth-server --link rest-mvc:rest-mvc --link reactive:reactive --link reactive-mongo:reactive-mongo spring-6-cloud-gateway:0.0.1-SNAPSHOT
```

Remove Container
```shell
docker rm gateway
```

Remove Container
```shell
docker rm gateway
```

Show logs for Rest MVC
```shell
docker logs -f rest-mvc
```










