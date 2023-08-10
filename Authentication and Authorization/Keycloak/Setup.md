Create the Keycloak docker file to build the image:
```Dockerfile
FROM quay.io/keycloak/keycloak:latest as builder

# Enable health and metrics support
ENV KC_HEALTH_ENABLED=true
ENV KC_METRICS_ENABLED=true

# Configure a database vendor
ENV KC_DB=mssql

WORKDIR /opt/keycloak
# for demonstration purposes only, please make sure to use proper certificates in production instead
RUN keytool -genkeypair -storepass password -storetype PKCS12 -keyalg RSA -keysize 2048 -dname "CN=server" -alias server -ext "SAN:c=DNS:localhost,IP:127.0.0.1" -keystore conf/server.keystore
RUN /opt/keycloak/bin/kc.sh build 

FROM quay.io/keycloak/keycloak:latest
COPY --from=builder /opt/keycloak/ /opt/keycloak/

# change these values to point to a running postgres instance
ENV KC_DB=keycloak_db
ENV KC_DB_URL=10.2.12.185:1433
ENV KC_DB_USERNAME=keycloak
ENV KC_DB_PASSWORD=Superguy#1
ENV KC_HOSTNAME=keycloak_host
ENTRYPOINT ["/opt/keycloak/bin/kc.sh"]
```

To run keycloak in development mode without the created image above, use:
`docker run --name pmconkeycloak -p 8019:8080 -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=superguy1 quay.io/keycloak/keycloak:latest start-dev`

When setting up the client in keycloak, set the Client authentication to 'on' to get the client secret.