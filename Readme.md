# Howto

(Didn't cover with the minikube tutorial. But remind that kubectl ***doesn't expose*** a service to external when using with minikube)

1. Apply the MongoDB secret, which contain a username and a password

```
kubectl apply -f mongodb-secret.yaml
```

2. Apply the MongoDB deployment (service is included)

```
kubectl apply -f mongo.yaml
```

3. Apply the Mongo Express ConfigMap, which contain database url

```
kubectl apply -f me-configmap.yaml
```

4. Apply the Mongo Express deployment (yes, service is included)

```
kubectl apply -f me.yaml
```

5. Because Mongo Express container is using NodePort, expose the service using minikube (Thanks to Digital Ocean for waste my precious 3-4 hrs. due to LoadBalance issue)

```
minikube service me-service
```

6. Forward port using kubectl (Thanks again, Digital Ocean)

```
kubectl forward-port --address localhost,0.0.0.0 <port>:8081
```
