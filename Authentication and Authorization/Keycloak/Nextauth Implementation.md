### Redirect URIs
`http://localhost:8030/api/auth/callback/keycloak`

Use the IP of WSL instead of localhost for local development

### Confidential Setting
Set to on to get the client secrets for the app

### Example of request URL to the IdP
`http://localhost:8099/realms/crm-auth/protocol/openid-connect/auth?client_id=crmclient&scope=openid&response_type=code&state=fj8o3n7bdy1op5&redirect_uri=http://localhost/`

### Connection Issues
[[Connection issues]]