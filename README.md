# Pre-Requisites

minikube or any kubernetes cluster

# Running in minikube

```eval $(minikube docker-env)

docker build -t hello-world-basic:v1 .

kubectl create -f deployment.yaml

kubectl expose deployment hello-world-basic --type=LoadBalancer --port=8080

minikube service hello-world-basic
