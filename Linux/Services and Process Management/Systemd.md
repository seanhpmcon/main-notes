#sockets
Define the socket configuration in the gunicorn.socket file like
```
[Unit]
Description=gunicorn socket

[Socket]
ListenStream=/run/gunicorn.sock

[Install]
WantedBy=sockets.target
```

`socket.target` is a special systemd target unit that represents the point in the system startup process when socket activation can begin. Targets in systemd serve as synchronization points and dependencies for units (services, sockets, timers, etc.). The `socket.target` target serves as a point of synchronization for socket activation.

Define the gunicorn.service file to configure the service like:
```
[Unit]
Description=gunicorn daemon
Requires=gunicorn.socket
After=network.target

[Service]
User=sean
Group=www-data
WorkingDirectory=/home/sean/Documents/python-prac
ExecStart=/home/sean/Documents/python-prac/venv/bin/gunicorn --workers 3 --bind unix:/run/gunicorn.sock test_prac.wsgi:application

[Install]
WantedBy=multi-user.target
```