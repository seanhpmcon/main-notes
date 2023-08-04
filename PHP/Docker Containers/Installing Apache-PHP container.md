Run the following command to setup and run an Apache-PHP container:
````console
docker run -d -p host-port:80 --name my-apache-php-app-name -v "$PWD":/var/www/html php:7.2-apache
````