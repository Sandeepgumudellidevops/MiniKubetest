# Pre-Requisites

minikube or any kubernetes cluster

# Run `hello.py` directly and Test
```python3 hello.py```

then open `127.0.0.1:8080` on browser this should give results like:

Hello World from host "------". with your host 

# Docarize and Test

```docker build -t hello-world-basic:v1 .```
This create the image

docker run -d -p 8080:8080 hello-world-basic:v1
 This runs the program in docker container exposing 8080 port.

then open 127.0.0.1:8080 on browser this should give results like:

`Hello World from host "------".` with your host 

# Running in minikube

```eval $(minikube docker-env)```


```docker build -t hello-world-basic:v1 .```
 This will run steps mentioned in Dockerfile. Like pulling Python image, expose to port 8080 installing flask as mentioned in requirements file.

```kubectl create -f deployment.yaml```
 This needs to be run on minikube or your local k8 cluster to create deployment. Deployment uses docker image that built on above step and creates deployemnt on k8 cluster. As we mentioned replicas 3 it will create 3 pods running with same docker image.

```kubectl expose deployment hello-world-basic --type=LoadBalancer --port=8080```
This will create service with loadbalancer type.

```kubectl get services```
Gives the service information all the serrvices. `hello-world-basic` will be assigned with port. loadbalncer url which need to be opened in broweser to test it.

if using minikube run this command.
```minikube service hello-world-basic```