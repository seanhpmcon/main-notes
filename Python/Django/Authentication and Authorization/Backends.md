The Remote User Backends is to authenticate to external data sources by using the web servers (Apache, Nginx etc.) functionality to add authentication headers to the request. The authentication can happen using kerberos, ldap etc. and the web server would set the header variable allowing django to create a user based on that value.