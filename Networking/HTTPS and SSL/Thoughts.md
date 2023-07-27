### Web App Architecture

Client - Load Balancer - Reverse Proxy - Frontend server - Reverse Proxy - Backend API server

When setting up the web services above, the reverse proxies would be configured with SSL encryption and the connection between the Reverse Proxy and the servers can be unencrypted.