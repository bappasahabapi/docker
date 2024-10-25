# Buiding our custom node image
<!-- - 28 -->
1. Build the image
       
         docker build .

2. Run the image as container 
        
        docker run -p localPort:dockerPort Image

3. Stop the containre

        docker stop contaner name or,
        docker stop contaner id


- First Create the **Dockerfile**
```dockerfile
FROM node

WORKDIR /app

# COPY . .
COPY . /app

# install packages 
RUN npm install


EXPOSE 80

# RUN node server.js
CMD [ "node","server.js" ]
```

--- 
- Then create the custom image based on docker file
    - `docker build .` 
        - sha256:35dd35922270dfb24b2463b9428a76a7e2680144ea58b929ebcd8521bdfc8645  
    - docker run sha256:35dd35922270dfb24b2463b9428a76a7e2680144ea58b929ebcd8521bdfc8645 
    - `docker ps` | only show the running image 
    - To Stop the docker run
        - **docker stop CONTAINER ID** |` docker stop b12564086507 `
        
- This will not work untill we expose the port `3000:80`
- here 3000 is our local machine port and 80 is docker exposed port
-  **docker run -p localPort:dockerPort Image**
    - Run: `docker run -p 3000:80 sha256:35dd35922270dfb24b2463b9428a76a7e2680144ea58b929ebcd8521bdfc8645 ` 
    - Run: `docker run -p 3000:80 35dd35922270 ` 
- sotp the running container 
    - **docker stop NAMES** | `docker stop quirky_wozniak`
    

# Commands

docker --help

######    🔥 Stop and Restart Container 

**set names to the container**
- `docker run -p 3000:80 -d --rm --name goalsapp 328bc813964506`

** 🔥  Attached deattached container**

- `docker ps --help` 
- `docker start cranky_boyd`   | NAME: cranky_boyd , this way terminal is not blocking 
- `docker log container_id`


**🔥 Deleting container**
- `docker rm container_name` | Remove single container
- `docker rm container_name1 container_name2` | Remove multiple container
- `docker container prune` | Remove all stop container at a time
- `--rm` Automatically remove the container and its associated anonymous volumes when it exits
    -` docker run -p 3000:80 -d --rm 35dd` 


**🔥 copy container**
- docker cp dummy/. quirky_wozniak:/test
- docker cp quirky_wozniak:/test dummy


**🔥 Deleting Images**

- `docker images`
- `docker image inspect 35dd35922270`  | More about particular image

```powershell
❯ docker images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
<none>       <none>    f4947ed3bae0   29 minutes ago   1.02GB
<none>       <none>    c261479411b6   4 hours ago      1.12GB
<none>       <none>    d30ae0582d61   4 hours ago      1.12GB
<none>       <none>    7aaee69eea1a   4 hours ago      1.12GB
<none>       <none>    35dd35922270   5 hours ago      1.12GB
<none>       <none>    e0bf6e8cd8ca   24 hours ago     863MB
```


# docker-03-python

First create a Dockerfile

then create the image file 
- docker build .
- sha256:f4947ed3bae06d37dea52fab155769815d645e2840a7cf9715d7048841f0acef

- docker run -i -t sha256:f4947ed3bae06d37dea52fab155769815d645e2840a7cf9715d7048841f0acef
- docker run -i -t f49   
- docker start -a f49
- docker start -a -i 692


