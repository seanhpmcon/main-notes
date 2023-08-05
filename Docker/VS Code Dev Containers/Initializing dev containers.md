### Node Containers
Create a docker container with a volume mapping to the `/usr/src/app` directory and port mapping to desired ports

### C++ Containers
`docker run -it --name cpp-conatiner-name -v ${PWD}:/projects mcr.microsoft.com/devcontainers/cpp:ubuntu`

### Nextjs in Node Containers
`docker run -it --name nextjs-container-name -p 3000:3000 -v ${PWD}:/workspace node`

### Nginx Containers
`docker run --name nginx-instance -p 8001:80 -v ${PWD}:/workspace nginx`

### Apache-PHP Containers
[[Installing Apache-PHP container]]

### Python Containers
[[Setup Python Container]]