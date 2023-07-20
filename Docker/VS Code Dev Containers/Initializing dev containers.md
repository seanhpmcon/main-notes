### Node Containers
Create a docker container with a volume mapping to the `/usr/src/app` directory and port mapping to desired ports

### C++ Containers
`docker run -it --name cpp-conatiner-name -v ${PWD}:/projects mcr.microsoft.com/devcontainers/cpp:ubuntu`

### Nextjs in Node Containers
`docker run -it --name nextjs-container-name -p 3000:3000 -v ${PWD}:/workspace node`