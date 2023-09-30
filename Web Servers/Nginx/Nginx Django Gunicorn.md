#django #gunicorn
In the site-available config, add the following code:
```
server {
	listen 80;
	server_name 192.168.100.152;

	location / {
		include proxy_params;
		proxy_pass http://unix:/run?gunicorn.sock;
	}
}
```

This file is the configuration when you create the gunicorn socket service managed by systemd.

### Enable Gunicorn and Nginx on startup

`sudo systemctl start gunicorn.socket`
`sudo systemctl enable gunicorn.socket`
`sudo systemctl reload nginx`