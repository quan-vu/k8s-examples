# Deploy Knote app with Nodejs, MongoDB on Kubernetes

Start Minikube

```shell
minikube start
```

Deploy to Kubernetes Cluster

```shell
kubectl apply -f k8s-practices/knote-js/kube
```

Get list of services

```shell
kubectl get svc
```

NAME         TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
knote        LoadBalancer   10.106.178.101   <pending>     80:31546/TCP   49s
kubernetes   ClusterIP      10.96.0.1        <none>        443/TCP        32h
mongo        ClusterIP      10.102.92.111    <none>        27017/TCP      48s


## Exposes LoadBalancer in Minikube

```shell
minikube service knote
```

|-----------|-------|-------------|-----------------------------|
| NAMESPACE | NAME  | TARGET PORT |             URL             |
|-----------|-------|-------------|-----------------------------|
| default   | knote |             | http://192.168.39.244:31546 |
|-----------|-------|-------------|-----------------------------|
🎉  Opening service default/knote in default browser...


## Forward MongoDB Port

```shell
kubectl get pods | grep mongo
kubectl port-forward mongo-f7d8b86bd-mjwzb 27017:27017
```

Connect to mongodb use command:

```shell
mongo mongodb://localhost:27017
show dbs;

admin   0.000GB
config  0.000GB
dev     0.000GB
local   0.000GB

```

## Docker

Build your won docker image

```shell
docker image build -t <your_docker_hub_account>/0.0.1 .
```


