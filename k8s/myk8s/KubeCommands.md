Display all K8s resources in the default namespace
```bash
kubectl get all
```

Create Deployment for Mongo
```bash
kubectl create deployment mongo-db --image=mongo --dry-run=client -o yaml > mongo-deployment.yaml
```

Apply Deployment
```bash
kubectl apply -f mongo-deployment.yaml
```

Create Mongo Service
```bash
kubectl create service clusterip mongo-db --tcp=27017:27017 --dry-run=client -o yaml > mongo-service.yaml
```

Apply Service for Mongo
```bash
kubectl apply -f mongo-service.yaml
```

Create Deployment for MySQL
```bash
kubectl create deployment mysql --image=mysql:8 --dry-run=client -o yaml > mysql-deployment.yaml
```

Apply Deployment for MySQL
```bash
kubectl apply -f mysql-deployment.yaml
```

Create MySQL Service
```bash
kubectl create service clusterip mysql --tcp=3306:3306 --dry-run=client -o yaml > mysql-service.yaml
```

Create Deployment for Auth-Server
```bash
kubectl create deployment auth-server --image=spring-6-auth-server:0.0.1-SNAPSHOT --dry-run=client -o yaml > auth-server-deployment.yaml
```

Apply Deployment for Auth-Server
```bash
kubectl apply -f auth-servergo-deployment.yaml
```

Create Service for Auth-Server
```bash
kubectl create service clusterip auth-server --tcp=9000:9000 --dry-run=client -o yaml > auth-server-service.yaml
```

Apply Service for Auth-Server
```bash
kubectl apply -f auth-server-service.yaml
```

Create Deployment for Rest MVC
```bash
kubectl create deployment rest-mvc --image=spring-6-rest-mvc:0.0.1-SNAPSHOT --dry-run=client -o yaml > rest-mvc-deployment.yaml
```

Apply Deployment for Rest MVC
```bash
kubectl apply -f rest-mvc-deployment.yaml
```

Create Service for Rest MVC
```bash
kubectl create service clusterip rest-mvc --tcp=8081:8080 --dry-run=client -o yaml > rest-mvc-service.yaml
```

Apply Service for Rest MVC
```bash
kubectl apply -f rest-mvc-service.yaml
```

Create Deployment for reactive
```bash
kubectl create deployment reactive --image=spring-6-reactive:0.0.1-SNAPSHOT --dry-run=client -o yaml > reactive-deployment.yaml
```

Apply Deployment for reactive
```bash
kubectl apply -f reactive-deployment.yaml
```
Create Service for reactive
```bash
kubectl create service clusterip reactive --tcp=8082:8080 --dry-run=client -o yaml > reactive-service.yaml
```
Apply Service for reactive
```bash
kubectl apply -f reactive-service.yaml
```

Create Deployment for reactive-mongo
```bash
kubectl create deployment reactive-mongo --image=reactivemongo:0.0.1-SNAPSHOT --dry-run=client -o yaml > reactive-mongo-deployment.yaml
```

Apply Deployment for reactive-mongo
```bash
kubectl apply -f reactive-mongo-deployment.yaml
```

Create Service for reactive-mongo
```bash
kubectl create service clusterip reactive-mongo --tcp=8083:8080 --dry-run=client -o yaml > reactive-mongo-service.yaml
```
Apply Service for reactive-mongo
```bash
kubectl apply -f reactive-mongo-service.yaml
```

Create Deployment for reactive-mongo
```bash
kubectl create deployment gateway --image=spring-6-cloud-gateway:0.0.1-SNAPSHOT --dry-run=client -o yaml > gateway-deployment.yaml
```

Apply Deployment for gateway
```bash
kubectl apply -f gateway-deployment.yaml
```

Create Service for gateway
```bash
kubectl create service clusterip gateway --tcp=8080:8080 --dry-run=client -o yaml > gateway-service.yaml
```
Apply Service for gateway
```bash
kubectl apply -f reactive-mongo-service.yaml
```

Port Forward for gateway
```bash
kubectl port-forward service/gateway 8080:8080
```

