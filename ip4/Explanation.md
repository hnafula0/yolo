CHOICE ON THE BASE IMAGE
Backend and client base images are alpine image because I require something small to work with.
Database image is mongodb which will be downloaded from the mongoDB page.

DOCKERFILE DIRECTIVES USED IN THE CREATION AND RUNNING OF EACH CONTAINER
BACKEND
1. CREATION OF A DOCKERFILE
-FROM node:alpine - Base image that results to a small application
-WORKDIR - The working directory of the container
-COPY - Copies files of the package.json file
-RUN - runs installation of npm in the layer
-EXPOSE - Informs docker to listen to port 8080 at runtime

2. BUILD IMAGE
docker build -t backend

3. RUN CONTAINER 
docker run --name backend-container --rm -p 8080:8080 -it backend

CLIENT
1. CREATION OF A DOCKERFILE
-FROM node:alpine - Base image that results to a small application
-WORKDIR - The working directory of the container
-COPY - Copies files of the package.json file
-RUN - runs installation of npm in the layer
-EXPOSE - Informs docker to listen to port 3000 at runtime

2. BUILD IMAGE
docker build -t client

3. RUN CONTAINER 
docker run --name client-container --rm -p 3000:3000 -it client

MONGODB
Type docker run mongo on terminal
RUN A CONTAINER
docker run --name mongodb --rm -d -p 27017:27017 mongo

GIT WORKFLOW USED TO ACHIEVE THE TASK
Create a YAML file
Identify version used 
Identify services used

GOOD PRACTICES
FROM - Specifies base image in which we are building from
WORKDIR - Working directory of the container
COPY - Copies files into the image you are building
RUN - Runs a new command in a new layer
EXPOSE - Informs docker thta the container listens on the speicified network port at runtime
CMD - Specifies the instruction that is to be executed when a docker container starts

**ORCHESTRATION
Creating a kubernetes cluster using minikube
**

Install kubectl
Install minikube
Use minikube start command to create a cluster
Create a folder to hold resource definition YAML files created
Create a deployment resource for backend
Define a service which makes a pod accessible to users ouside the cluster
Create a resource deployment for frontend
Define a service
Define the database tier
Submit resource definitions to kubernetes using the command kubectl apply -f <folder>
Watch pods using the command kubectl get pods --watch
Access service using the command minikube service yolo --url
