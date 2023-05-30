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
Set environment**

Activate cloud shell
Confirm that you are already authenticated and your project is set to your project ID
Set default zone and project configuration

**Create a GKE cluster**

Ensure proper apis are enabled using the command gcloud services enable container.googleapis.com
Create your cluster using the command gcloud container clusters create yolo-cluster --num-nodes 3

**Clone source repository**
Git clone then change to the appropriate repository

**Create docker container**
Enable cloudbuild api by running command gcloud services enable cloudbuild.googleapis.com
Start the build process using the command gcloud builds submit --tag 

**Deploy container to GKE**

Deploy the app using the command kubectl create deployment

**Expose GKE deployment**
Run the following command to expose the website to the internet kubectl expose deployment yolo --type=LoadBalancer --port 80 --target-port 8080

Find the external IP that GKE provisioned for your application by inspecting the service using the command kubectl get service

**Scale GKE deployment**
Run the following command to scale your deployment replicas kubectl scale deployment yolo --replicas=3

**Clean Up**
Delete git repository
Delete container registry images
Delete cloud build artifacts from cloud storage
Delete GKE cluster
Delete GKE service


