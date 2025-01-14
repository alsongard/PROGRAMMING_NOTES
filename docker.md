To start of docker daemon use the following command:
``sudo systemctl start docker``
``sudo systemctl stop docker``
``sudo systemctl stop docker.socket``
run the command to confirm if its running:
``docker ps`` : (result)
``CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES``
if not running get message:
``Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?``


**Docker images:**
- docker image is a template for creating an environment of your choice.
- template for creating an environment of your choice, 
- Snapshot
- Has everything needed to run your apps.


**Container:**  
- Running instance of an image
In or example : nginx
Check on website to get nginx image
tag: latest

To see list of  images on machine 
``docker images``

## Docker containers
#### get an image from
[link]( https://hub.docker.com)
docker hub is a registry. It's a place we can download images. 
``docker pull nginx``
``docker images``
nginx is a web server software, reverse proxy and load parameter. 

run a container from nginx image:

``docker run -d nginx:latest`` : used to run a docker image and add tag which is displayed on ``docker pull ImageName``. Adding the flag -d (means detatched). 
``docker container ls ``: gives information about the running docker images
``docker ps`` : used to check runnign containers/images


## HOW TO USE CONTAINERS
```
 docker container ls        
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS              PORTS     NAMES
331c0005d348   nginx:latest   "/docker-entrypoint.…"   About a minute ago   Up About a minute   80/tcp    pedantic_bardeen
```
Issue request to our container
``localhost:8080``

To specify a port for our container use:
Syntax : ``docker run -d -p 8080:80 dockerName:tag`` 
Command : ``docker run -d -p 8080:80 nginx:latest``
One can also use different ports other than 8080 such as 3000

To stop a running image:
``docker stop idName``
The idname is given when running ``docker run -d -p 8080:80 ImageName``
host machine which is running docker on port 8080 on the protocol 80

Exposing Mutliple Ports:
To use multiple ports use:
``docker -d -p 8080:80 -p 3000:80 ImageName:tag``

``docker ps`` : check which images are running, it simply shows the running containers
Also to run docker yuo can use:
``docker run ImageName`` : ``docker run -d nginx:latest``

To run on multiple ports:
``docker run -d -p 8080:80 -p 3000:80 nginx:latest``

Once you created a container from an image it will exist until removed although it can be stopped.
```
docker stop containerId | containerName
```

To run the container again:
``docker start containerId | containerName``
To check all images in the container, you use :
``docker ps -a``

To remove a specific image use:
``docker rm containerId``
``docker rm containerName``

``docker ps -aq``
the  flag ``(-a)`` means all both running and  not running and ``(-q)`` displays only the containerId.

To remove all images
``docker rm -f $(docker ps -aq)``
The command above return all ids of the containers in machine
### How to name containers
``docker ps -a `` : display containers

``docker run --name website -d -p 8080:80 nginx:latest``
The output of ``docker ps``:
```
└─$ docker ps                                           
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                   NAMES
3146fe65875d   nginx:latest   "/docker-entrypoint.…"   3 seconds ago   Up 2 seconds   0.0.0.0:8080->80/tcp, :::8080->80/tcp   website
```

``docker stop website``

``docker exec it postgres_df psql u postgres -d movies_db``

How to select a better preview format:
```
docker ps -a --format="ID\t{{.ID}}\nNAME\t{{.Names}}\nPORTS\t{{.Ports}}\nCREATED\t{{.CreatedAt}}\nCOMMAND\t{{.Command}}\nSTATUS\t{{.Status}}\n"
```

To export you simply:
```
export FORMAT="ID\t{{.ID}}\nNAME\t{{.Names}}\nPORTS\t{{.Ports}}\nCREATED\t{{.CreatedAt}}\nCOMMAND\t{{.Command}}\nSTATUS\t{{.Status}}\n"
docker ps --format=$FORMAT
```


## DOCKER VOLUMES
docker volumes allow us to share data,files and folders. Volumes allow us to share data between host and containers and also between containers.

if data/files are stored in a directory in local machine to host them on the docker container use the following syntax:
``docker run  --name bootstrap /some/content:/usr/share/nginx/html:ro  -d -p 5000:80 nginx 
The ``ro`` stands for read only
any changes made to the file in the docker will be reflected to the original file in the local machine and vice versa.
Make changes to the file in the docker container do the following:
```
docker exec -it website bash
```


**How to share volumes between containers**
share folder or data between 2 containers
``docker run --name new-website  --volumes-from previosDocker -d -p 8081:80 nginx:latest`` 

## Docker file
How to build your own images by using dockerfile. 
dockerfile is a list of steps of how to create images.

Add dockerfile in a directory with your file contents:
Dockerfile contents
```
# images your going to import or use
FROM nginx:latest 
# adding current directory files to nginx directory for hosting files
ADD . /usr/share/nginx/html
```

Run:
```
docker run build --tag free:latest

docker run --name codecamp -d -p 8080:80 free:latest
```
Go to : *localhost:8080*

## building an API using nodejs
create a directory: **user-service-api**
```
npm init .
npm install express --save
```

Add the following to index.js file or create:
```
const express = require("express");
const app = express();

app.get("/", (request, response)=>{
	response.send("<h1>Welcome to Express API in docker</h1>");
})

app.listen(5000, ()=>{
	console.log("listening on port 5000");
})

```

Create a Dockerfile :
```
FROM node:latest
ADD . /app
WORKDIR . /app/
RUN npm install
CMD node index.js
```

run the command on terminal:
``docker build --tag user-api:latest .``
the period character(.) represents the current directory

Create a container based on the image:
``docker run --name user-service-api -d -p 3000:5000 user-api:latest``

## .dockerignore
Add the following:
```
node_modules/
Dockerfile
.git
```

## caching and layers
```

FROM node:latest
WORKDIR . /app/
ADD package*.json /app/
RUN npm install
ADD . /app/
CMD node index.js
```


## ALPINE
