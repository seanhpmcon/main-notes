### Configuring the `default.conf` file
To configure nginx as a reverse proxy, configure the location in the `default.conf` file with the following line:
```conf
	proxy_set_header Host $host;
	proxy_set_header X-Real-IP $remote_addr;
	proxy_pass http://localhost:3000;
```

[[Let's Encrypt Certs]]