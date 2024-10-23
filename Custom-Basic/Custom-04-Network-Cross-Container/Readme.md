# 

- `docker build -t ts-docker:v4 .`
- `docker run -p 5000:5000 --name ts-container --rm -w /app -v ts-docker-logs:/app/logs -v "/$(pwd)":/app -v /app/node_modules --env-file .env ts-docker:v4`
- `docker container stop ts-container`


## Remote MongoDB Connection
.env remote connection:
```bash
NODE_ENV="development"
PORT=5000

CLOUDINARY_CLOUD_NAME="dtx9sibea"
CLOUDINARY_API_KEY="516412222127372"
CLOUDINARY_API_SECRET="SG9bfoZ8TwWg_U5RlTQXM_R-YssT"

DB_URL=mongodb+srv://mac-admin:Tx2803SPifFX46PH@cluster0.nnn0vgn.mongodb.net/ts-doker-db?retryWrites=true&w=majority
```

## Local Connections:
- `brew services start mongodb-community@7.0`   | `brew services stop mongodb-community@7.0`
-   



 
.env
```bash
NODE_ENV="development"
PORT=5000

CLOUDINARY_CLOUD_NAME="dtx9sibea"
CLOUDINARY_API_KEY="516412222127372"
CLOUDINARY_API_SECRET="SG9bfoZ8TwWg_U5RlTQXM_R-YssT"

# DB_URL=mongodb://host.docker.internal:27017
DB_URL=mongodb://host.docker.internal:27017/ts-docker-db
```

## Contaner to Container Connections 

**mongodb** container to **ts-container** connections

- `docker pull mongo`
-  `docker run --name mongodb --rm mongo`
- `docker container inspect mongodb`
    - "IPAddress": "172.17.0.2",
- `docker run -p 5000:5000 --name ts-container --rm -w /app -v ts-docker-logs:/app/logs -v "/$(pwd)":/app -v /app/node_modules --env-file .env ts-docker:v4`


.env

```bash
NODE_ENV="development"
PORT=5000

CLOUDINARY_CLOUD_NAME="dtx9sibea"
CLOUDINARY_API_KEY="516412222127372"
CLOUDINARY_API_SECRET="SG9bfoZ8TwWg_U5RlTQXM_R-YssT"
# Way-1
DB_URL=mongodb://172.17.0.2:27017/ts-docker-db
```


# 02-Creating Container Network

## A.
- `docker run --network my_network`
- `docker network create ts-docker-network`
    - custom Network: 05e0142c7cab25094db4616015fb8b008a73fadd09c3f2eaed50af035841136e
- `docker network ls`

```bash
❯ docker network ls
NETWORK ID     NAME                DRIVER    SCOPE
e52446175805   bridge              bridge    local
10d9a017524d   host                host      local
969c2bcfc6f4   none                null      local
05e0142c7cab   ts-docker-network   bridge    local
```

## B. Run two container in same network

- `docker run --name mongodb --rm --network ts-docker-network mongo`
- `docker run -p 5000:5000 --name ts-container --rm -w /app -v ts-docker-logs:/app/logs -v "/$(pwd)":/app -v /app/node_modules --env-file .env --network ts-docker-network ts-docker:v4`

 And then change the `.env` file to 

```powershell
# Way-2: give the container name [container name here is mongodb]
DB_URL=mongodb://mongodb:27017
```

