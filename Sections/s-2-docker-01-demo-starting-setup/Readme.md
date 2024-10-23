# Docker command

-  Run desktop docker First
-  go to the project root: 
    - `docker build .`
- `docker ps`
- docker run -p 3000:3000 image
    - ex: `docker run -p 3000:3000 e0bf6e8cd8ca`
- - `docker  stop quirky_wozniak` | docker stop NAMES





#   Run the project 

- open desktop docker

- `docker build .` | this will create an image 
    - sha256:e0bf6e8cd8cad092081fc5c52ee42b54c87aa51c9f727558bfb590f2c132ce6a  
- `docker run -p 3000:3000 sha256:e0bf6e8cd8cad092081fc5c52ee42b54c87aa51c9f727558bfb590f2c132ce6a`
- 
- To Stop the container:
- `docker ps`
    
```dockerfile
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                    NAMES
79d3e5b939cf   e0bf6e8cd8ca   "docker-entrypoint.s…"   2 minutes ago   Up 2 minutes   0.0.0.0:3000->3000/tcp   quirky_wozniak
```

- `docker  stop quirky_wozniak` | docker stop NAMES