Docker has commands to make certain actions for working with PHP extensions easier.
These can be commands to install and enable the extensions:
1. Install Command: `docker-php-ext-install`
2. Enable Command: `docker-php-ext-enable`

### Notes
When install some modules, it seems you may have to use `apt` to get the initial files and then use `docker-php-ext-*` to configure it.

### PHP-ODBC
Use the following commands to install the package
1. `apt-get install unixodbc unixodbc-dev -y`
2. `docker-php-ext-configure pdo_odbc --with-pdo-odbc=unixODBC,/usr`
3. `docker-php-ext-install pdo_odbc`

### Installing LDAP
[[APACHE Configuration]]

### Installing `sqlsvr`
The following are the steps/commands required;
1. This command updates the package manager and installs `gnupg2` which is used for encryption: `apt-get update && apt-get install -y gnupg2`
2. This command is used to add the Microsoft GPG key to the APT keyring: `curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -`
3. This command is used to download the configuration file for Microsoft SQL Server: `curl https://packages.microsoft.com/config/ubuntu/20.04/prod.list > /etc/apt/sources.list.d/mssql-release.list`
4. Command to update APT again: `apt-get update`
5. This command downloads the Microsoft ODBC Drive: `ACCEPT_EULA=Y apt-get -y --no-install-recommends install msodbcsql17 unixodbc-dev `
6. This command is used to download the PHP package with a specific version: `pecl install sqlsrv:5.8.0 pdo_sqlsrv:5.8.0`
7. This command is used to enable the packages: `docker-php-ext-enable sqlsrv pdo_sqlsrv`

### Setup a connection in PHP
The following script is used to setup a connection to a SQL Server database in the host machine.
```php
$serverName = "10.2.12.185"; //serverName\instanceName

// Since UID and PWD are not specified in the $connectionInfo array,
// The connection will be attempted using Windows Authentication.
$connectionInfo = array("UID" => "username", "PWD" => "password", "Database"=>"crm_version_test");
$conn = sqlsrv_connect( $serverName, $connectionInfo);

if( $conn ) {
     echo "Connection established.<br />";
}else{
     echo "Connection could not be established.<br />";
     die( print_r( sqlsrv_errors(), true));
}
```