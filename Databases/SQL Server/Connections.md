#sqlserver
### Connection to a SQL Server instance using IP and Port number
To connect to a SQL Server database using an IP address and port number in Microsoft SQL Server Management Studio (SSMS), follow these steps:

1. **Open SQL Server Management Studio:**
   Launch Microsoft SQL Server Management Studio. You can usually find it in your Start menu or as a standalone application.

2. **Connect to Server:**
   On the initial connection screen, you'll see a field labeled "Server name." This is where you specify the server's IP address and port number.

   - Enter the IP address followed by a comma and the port number, like this: `xxx.xxx.xxx.xxx,portNumber`.
   - For example: `192.168.1.100,1433` if the IP address is 192.168.1.100, and the port is 1433 (the default SQL Server port).

3. **Choose Authentication Method:**
   Select the appropriate authentication method for your SQL Server instance. You can choose between Windows Authentication or SQL Server Authentication. Provide the required credentials.

   - **Windows Authentication:** If you choose Windows Authentication, SSMS will use your Windows login credentials.
   - **SQL Server Authentication:** If you choose SQL Server Authentication, enter a valid SQL Server username and password for the server.

4. **Click "Connect":**
   After entering the server name, port number, and authentication details, click the "Connect" button to establish the connection to the SQL Server database.

5. **Access the Database:**
   Once the connection is established, you'll be able to access and manage the databases on the SQL Server instance through SSMS.

Please ensure that the SQL Server instance is configured to allow connections over the specified IP address and port. Additionally, consider any firewall and network settings that might affect connectivity to the SQL Server. If you're dealing with a remote SQL Server, you may need to configure the SQL Server to listen on the specified IP address and port and allow access from the client machine's IP address.