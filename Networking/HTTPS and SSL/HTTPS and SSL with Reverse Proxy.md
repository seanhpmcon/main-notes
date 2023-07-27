SSL is terminated at the proxy server. So you install your SSL certificates on the proxy server.

Then your proxy server can make a secure (SSL) or unsecure connection (HTTP) connection to your web server.

Since the proxy server and web server are usually located on a private network, you can use a self-generated certificate to make the connection to the internal web server from the proxy server.

To give you an example of my setup. I have an Nginx proxy server in front of my Apache web server.

1. On the Nginx server, install your certificates you purchase from a certificate authority on the web. Also generate a self signed certificate on the Nginx server.
2. On Apache, generate a self-signed certificate.
3. Configure your web sites on Apache to accept both SSL connections (using the certificate you generated in step 2) and normal http connections.
4. On the Nginx server, proxy to the Apache server using [http://apache.server.ip](http://apache.server.ip/ "apache.server.ip").
5. If you require high security (you don’t trust your private network), then on the Nginx server, proxy to the Apache server using https://apache.server.ip