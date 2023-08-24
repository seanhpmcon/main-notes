### Using Python and SQLalchemy
When authenticating to a sql server database with sqlalchemy, you can provide the username and password in the string or use windows authentication by adding `trusted_connection=yes` to the connection string.
See here for further explanation on windows authentication [[Using Window's Login User to Authenticate with other Services]]

Even with `trusted_connection=yes`, `ODBC Driver 18 for SQL Server` required an SSL certificate.