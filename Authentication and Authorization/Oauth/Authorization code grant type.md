Below is the steps in the authorization code grant flow:
1. The user click on the login button which sends them to the login page.
2. All the third part Identity Providers would be listed here as button where the link is the link to the login page of IdP.
3. When the user authenticates, the IdP sends a response which redirects the user to the redirect URI specified with the code grant. This is because the response after the user authenticates with the Authentication provider has a location header that redirects the user.
4. this response is sent to the server and the server takes the code and creates a request to send back to the IdP token endpoint to get the access/ID tokens.