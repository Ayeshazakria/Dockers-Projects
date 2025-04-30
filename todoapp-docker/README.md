# A sample todo app in react. </br>
It has the Dockerfile which is multi-staged.</br>
Its images are pushed to DOCKER-HUB.

Below are the steps to run this simple docker multi-staged project</br>

Clone the below sample repository, or you can use any web application that you have </br>
**git clone https://github.com/piyushsachdeva/todoapp-docker.git** </br>

cd into the directory </br>

cd todoapp-docker/ </br>

Create an empty file with the name Dockerfile </br>

**sudo vim  Dockerfile** </br>

**FROM node:18-alpine AS installer</br>**

**WORKDIR /app</br>**

**COPY package*.json ./</br>**

**RUN npm install</br>**
 
**COPY . .</br>**

**RUN npm run build</br>**

**FROM nginx:latest AS deployer </br>**

**COPY --from=installer /app/build /usr/share/nginx/html</br>**

Build the docker image using the application code and Dockerfile</br>

**docker build -t todoapp-docker .</br>**

Verify the image has been created and stored locally using the below command:</br>

**docker images</br>**

Create a public repository on hub.docker.com and push the image to remote repo</br>

**docker login</br>**

**docker tag todoapp-docker:latest username/new-reponame:tagname</br>**

**docker images</br>**

**docker push username/new-reponame:tagname</br>**

To pull the image to another environment, you can use the below command</br>

**docker pull username/new-reponame:tagname</br>**

To start the docker container, use the below command</br>

**docker run -dp 3000:80 username/new-reponame:tagname</br>**

Verify your app. If you have followed the above steps correctly, your app should be listening on localhost:3000</br>

To enter(exec) into the container, use the below command</br>

**docker exec -it containername sh</br>*8

or</br>

**docker exec -it containerid sh</br>**

To view docker logs</br>

**docker logs containername</br>**
or</br>

**docker logs containerid</br>**

To view the content of Docker container</br>

**docker inspect</br>**

Cleanup the old docker images from local repo using below command:</br>

**docker image rm image-id </br>**

![Image](https://github.com/user-attachments/assets/f6969df4-3b1a-4ddb-bba6-1675c1ecaa63)
