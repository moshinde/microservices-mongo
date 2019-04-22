# microservices-mongo

There are two microservcies user-service and stock-service. User-service handles user data and stock symbol.
The other microservice is stock service contains stock data.

1. Create namepsaces for database and other microservices

kubectl create namespace db-namespace

kubectl create namespace user-app-namespace

kubectl create namespace stock-app-namespace

2. Create mongo db pod in db-namespace(Refer mongo-pod.yml)

kubectl create -f mongo-pod.yml

3. Create user microservice deployment in user-app-namespace (refer user-service/user-deployment.yml)

kubectl create -f user-deployment.yml

4. Create stock microservice deployment in stock-app-namespace (refer stock-service/stock-deployment.yml)

kubectl create -f stock-deployment.yml

Environment variable USER_SERVICE_HOST is a host of user-deployment and which is used in stock-service as environment variable

5. To get service urls if the minikube is used.

minikube service mongo-service --namespace=db-namespace --url

minikube service user-app-service --namespace=user-app-namespace --url

minikube service stock-app-service --namespace=stock-app-namespace --url

To get the service urls from production based kubernetes environment check the namespaces created and use the port to create link and access it.
