### Building and starting a new container
Use the command `docker run --name mongodb -p 27017:27017 -v D:/mongo_container_data/data:/data/db mongo` to start the container and replace the name, port and volume mount with the variables you intend to use.

### Rebuilding from an old container's data
When rebuilding a new image using the same data from the previous image, ensure to map the volume where the database data is store (/data/db inside the conatiner) to the external volume mapping which, in the case of the container above would be D:/mongo_container_data/data.