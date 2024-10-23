[CheetSheet](Canva.com/design/DAFyWfnXhAk/iFVa2Wsh9n79Wzk51MGn5Q/edit)

- **docker run -p 5000:5000 -d --rm --name custom1 bfb6487a0917**   
-  **docker run -p myPort:dockerExposePort imageId**   
    -  `docker run -p 5000:5000 bfb6487a0917`  


# Working Command for this project:

- **docker run -p 5000:5000 --name custom1 bfb6487a0917**
- **docker container start custom1** 
- **docker container stop custom1** 


## Image & Container Naming

- `docker build -t docker-ts:20-bappa-v1 .`
- `docker run -p 5000:5000 -d --rm docker-ts:20-bappa-v1` | Image Naming
- `docker run -p 5000:5000 -d --rm --name docker-app docker-ts:20-bappa-v1` | Give Custom Name to container and image

```bash
❯ docker images
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
<none>       <none>    bfb6487a0917   21 hours ago   1.15GB
```
```bash
❯ docker build -t docker-ts:20-bappa-v1 .
❯ docker images

REPOSITORY   TAG           IMAGE ID       CREATED          SIZE
docker-ts    20-bappa-v1   a4e9c51c293c   11 seconds ago   1.19GB
<none>       <none>        bfb6487a0917   21 hours ago     1.15GB
```
```bash
❯ docker run -p 5000:5000 -d --rm --name docker-app docker-ts:20-bappa-v1

d8ef25116e40bea65aa1d1db2afa1da8d4a3568c75801705553e8d9f900b063f

❯ docker ps

CONTAINER ID   IMAGE                   COMMAND                  CREATED          STATUS          PORTS                    NAMES
d8ef25116e40   docker-ts:20-bappa-v1   "docker-entrypoint.s…"   17 seconds ago   Up 17 seconds   0.0.0.0:5000->5000/tcp   docker-app
```




No need to install node module for given `npm install`
- `docker run --help`
# 1.First Create the  Dockerfile



```dockerfile
FROM node:20

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 5000

CMD ["npm", "run", "dev"]

```




# 2. Make a Image file based on the Dockerfile instruction

- Run the **docker desktop app** first in your system and ensure that I am logged in.
- Open the terminal in the project folder and run the commads
    - `docker build .`
- Below five layer will execute after given `docker build .` command
    
```dockerfile
FROM node:20

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .
```

