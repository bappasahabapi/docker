




---
# 05-Docker Multi Container 

### Docker Network


💡 `docker network create ts-docker-net`

### No Image Build Needed For Mongo. Just Pull it From DockerHub

### Mongo DB Container

<aside>
💡

> docker run --name mongodb --rm -v ts-docker-db:/data/db --network ts-docker-net -e MONGO_INITDB_ROOT_USERNAME=ts-docker -e MONGO_INITDB_ROOT_PASSWORD=ts-docker mongo
> 
</aside>

### No Dockerfile Needed

### Node Express/Backend Image

<aside>
💡

docker build -t ts-docker-bakcend:v5 .

</aside>

### Node-Express/Backend Container

<aside>
💡

> docker run --name ts-docker-backend-container --rm --network ts-docker-net --env-file .env -w //app -v ts-docker-logs://app/logs -v "//$(pwd)"://app -v //app/node_modules -p 5000:5000 ts-docker-backend:v5
> 
</aside>

[Dockerfile [Nodejs]](https://www.notion.so/Dockerfile-Nodejs-128a868a7e95817d8acfe560dda3a694?pvs=21)

### NextJS/React/Frontend Image

<aside>
💡

docker build -t ts-docker-frontend:v5 .

</aside>

### NextJS/React/Frontend Container

<aside>
💡

> docker run --name ts-docker-frontend-conatiner --rm -p 3000:3000 --env-file .env.local -w //app -v "//$(pwd)"://app -v //app/node_modules --network ts-docker-net -e WATCHPACK_POLLING=true ts-docker-frontend:v5
> 
</aside>

[Dockerfile [NextJS/React/Frontend]](https://www.notion.so/Dockerfile-NextJS-React-Frontend-128a868a7e9581a08ba3f8f0929dc8b2?pvs=21)