
    brew services start mongodb-community@7.0 
- docker compose up -d
- docker compose down

##    Create Network
```bash
docker network create goals-net 
```


##   1. Run MongoDB Container

```bash
docker run --name mongodb \
  -e MONGO_INITDB_ROOT_USERNAME=max \
  -e MONGO_INITDB_ROOT_PASSWORD=secret \
  -v data:/data/db \
  --rm \
  -d \
  --network goals-net \
  mongo


```

##   2. Build Node API Image

\---------------------

`docker build -t goals-node .`

\---------------------

###    Run Node API Container

\---------------------

docker run --name goals-backend \\

\-e MONGODB\_USERNAME=max \\

\-e MONGODB\_PASSWORD=secret \\

\-v logs:/app/logs \\

\-v /Users/maximilianschwarzmuller/development/teaching/udemy/docker-complete/backend:/app \\

\-v /app/node\_modules \\

\--rm \\

\-d \\

\--network goals-net \\

\-p 80:80 \\

goals-node

\---------------------

##   3. Build React SPA Image

\---------------------

`docker build -t goals-react .`

\---------------------

###    Run React SPA Container

\---------------------

docker run --name goals-frontend \\

\-v /Users/maximilianschwarzmuller/development/teaching/udemy/docker-complete/frontend/src:/app/src \\

\--rm \\

\-d \\

\-p 3000:3000 \\

\-it \\

goals-react

\---------------------

Stop all Containers

\---------------------

docker stop mongodb goals-backend goals-frontend