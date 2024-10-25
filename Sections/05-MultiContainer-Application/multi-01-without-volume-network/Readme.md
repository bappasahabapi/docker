# Three Container [lecture 87]

-    Database `MongoDB ` | mongodb-container
        - Data must be persisted
        - Access should be limited
-    Backend `Nodejs Rest API` | backend-container
        - Data must be persisted
        - Live Source code update
-    Fronted `React` -frontend-container
        - Live Source code update
        
---

- **in short:**


    - **Network**
        - `docker network create goals-net `
        <!-- - `docker run --name mongodb-container --network goals-net mongo` -->
        - `docker run --name mongodb-container -v data:/data/db --rm --network goals-net mongo` | data persistence
        - `docker run --name mongodb-container -v data:/data/db --rm --network goals-net -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=secret mongo`  


        - `docker build -t backend-img .` 
        <!-- - `docker run --name backend-container --rm --network goals-net backend-img` -->
        - `docker run --name backend-container --rm -p 80:80 --network goals-net backend-img`
        - `docker build -t frontend-img .`
        - `docker run --name frontend-container --rm -p 3000:3000 --network goals-net -it frontend-img`






- **Without Network:**
    - **MongoDB**
        - `docker run --name mongodb-container -p 27017:27017  mongo `
    - **Backend:** 
        - `docker build -t backend-img .` 
        - `docker run --name backend-container --rm -p 80:80 backend-img`
    - **Frontend:** 
        - `docker build -t frontend-img .`
        - `docker run --name frontend-container --rm -p 3000:3000 -it frontend-img`


## A. Using npm [Optional Part]

<details>
<summary>Backend & Fronted Setup</summary>

```bash
cd backend
npm install
brew services start mongodb-community@7.0
node app.js

cd frontend
npm install
npm run dev

```

</details> 

## B. Using Docker [Not use Network and working by publishing port]


<details>
<summary> Step by Backend & Fronted Setup</summary>

First run the docker desktop app.

**1.Dockerizing the MongoDB Service:**
-  'mongodb://localhost:27017/course-goals', 
    -  `docker run --name mongodb-container -p 27017:27017  mongo `
    
**2.Dockerizing the Backend:**
- Create the image: `docker build -t backend-img .`
- Create container based on the image: `docker run --name backend-container --rm backend-img`
     -  'mongodb://localhost:27017/course-goals', change to 
     -  '**mongodb://host.docker.internal:27017/course-goals**', | this can fixed mongodb connection but not work like the fortend. To fix this define a port
     - `docker run --name backend-container --rm -p 80:80 backend-img`

**3.Dockerizing the Fronted:**
-Create the image: `docker build -t frontend-img .`
- Create container based on the image: `docker run --name frontend-container --rm -p 3000:3000 --it frontend-img`

</details> 