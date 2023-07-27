### Installing 2022 SQL Server Container

The command to pull and start the container is as follows
```shell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong@Passw0rd>" -p 1437:1433 --name sql_server1 --hostname sql_server1 -d mcr.microsoft.com/mssql/server:2022-latest
```
NOTE: password needs to have 1 uppercase, 1 number and 1 special character
NOTE: the user for the database above would be 'sa'

#LinkedServers
Manage linked servers in SQL Server Management Studio since DBeaver doesn't have the fields displayed for it to work

Aliasing Linked server tables by the LinkServerName.Database.dbo.Table