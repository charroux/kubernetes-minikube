# kubernetes-minikube

## Download this project
This project contains a web service coded in Java, but the language doesn't matter. This project has already been built and the binary version is there:

First of all, download the project: git clone https://github.com/charroux/kubernetes

Then move to the sud directory with cd kubernetes/MyService where a DockerFile is.

## Test this project using Docker
Build the docker image: docker build -t my-service .

Check the image: docker images

Start the container: docker run -p 4000:8080 -t my-service

8080 is the port of the web service, while 4000 is the port for accessing the container. Test the web service using a web browser: http://localhost:4000 It displays hello.

Ctr-c to stop the Web Service.

Check the containerID: docker ps

Stop the container: docker stop containerID

## Publish the image to the Docker Hub
Retreive the image ID: docker images

Tag the docker image: docker tag imageID yourDockerHubName/imageName:version

Example: docker tag 1dsd512s0d myDockerID/my-service:1

Login to docker hub: docker login

Push the image to the docker hub: docker push yourDockerHubName/imageName:version

Example: docker push myDockerID/my-service:1

## Create a deploymet

https://minikube.sigs.k8s.io/docs/start/


kubectl get nodes

kubectl create deployment myservice --image=efrei/my-service:2 

kubectl expose deployment myservice --type=NodePort --port=8080

kubectl get pod

wait until running state

minikube service myservice --url

kubectl delete services myservice

kubectl delete deployment myservice