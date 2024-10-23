# Backed:

<!-- - docker run --name mongodb-container mongo   -->
<!-- - `docker run --name mongodb-container --rm -p 27017:27017 mongo` -->

### Making a Network:

💡 Create Custom Network 
- `docker network create ts-docker-net`

💡🚢 MongoDB Container:
-  `docker run --name mongodb-container --rm --network ts-docker-net mongo`


💡🚢 Dockerized Node Express/Backend Image:
- `docker build -t ts-docker-backend:v5 .`   
- `docker run --name ts-docker-backend-container --rm --network ts-docker-net --env-file .env -w //app -v ts-docker-logs://app/logs -v "//$(pwd)"://app -v //app/node_modules -p 5000:5000 ts-docker-backend:v5`


💡🚢 Dockerized NextJS/React/Frontend Image:

- `docker build -t ts-docker-frontend:v5 .`
<!-- - `docker run --name ts-docker-frontend-container --rm -p 3000:3000 --env-file .env.local --network ts-docker-net ts-docker-frontend:v5` -->
- `❯ docker run --name ts-docker-frontend-container --rm -p 3000:3000 --env-file .env.local -w //app -v "//$(pwd)"://app -v //app/node_modules --network ts-docker-net ts-docker-frontend:v5`



