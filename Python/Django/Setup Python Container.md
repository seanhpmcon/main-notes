#pythoncontainer
Docker command:
```shell
docker run -it --name container-name -v "$PWD":/usr/src/myapp python
```

Docker Command for Web Server builds to map a port
```shell
docker run -it --name container-name -p host-port:container-port -v "$PWD":/usr/src/myapp python
```