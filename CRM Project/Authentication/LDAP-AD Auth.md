# How does LDAP work to authenticate a user from active directory on a web app?

#php #ldap

LDAP (Lightweight Directory Access Protocol) is a protocol used to access and authenticate against directory services, including Active Directory (AD). Here's an overview of how LDAP works to authenticate a user from AD in a web application:

1. Establish Connection: The web application establishes a connection to the AD server using the LDAP protocol. This typically involves specifying the server address (hostname or IP) and the LDAP port (default is 389 for non-SSL connections).

2. Bind Operation: Once the connection is established, the application performs a "bind" operation to authenticate itself with the AD server. This involves providing a distinguished name (DN) and password that has sufficient privileges to search for and retrieve user information. The DN typically identifies a service account or an administrative user.

3. Search for User: After the bind operation is successful, the application can search for the user's entry in the AD directory. This is typically done by specifying search criteria, such as the user's username or email address. The application constructs an LDAP query and submits it to the server.

4. Retrieve User Information: If the search is successful, the server returns the user's entry, which contains various attributes such as username, email, group memberships, and more. The application can extract the necessary information to perform authentication and authorization.

5. Verify Credentials: To authenticate the user, the application compares the supplied password (from the login form) with the password stored in the user's entry in AD. This comparison can be performed locally within the application or by requesting the AD server to perform the password comparison.

6. Authentication Result: Based on the comparison result, the application determines whether the user's credentials are valid. If the comparison succeeds, the user is authenticated, and the application can proceed with granting access or performing further authorization checks.

It's important to note that LDAP authentication against AD typically requires secure communication, especially when transmitting passwords. This can be achieved by using LDAPS (LDAP over SSL/TLS) on port 636 or by using STARTTLS to upgrade a regular LDAP connection to a secure connection.

The specifics of implementing LDAP authentication in a web application depend on the programming language or framework being used. There are LDAP client libraries available for various languages that simplify the process of connecting to an LDAP server and performing authentication operations.

It's recommended to consult the documentation and resources provided by the LDAP client library or framework you're using to get detailed implementation guidance and best practices specific to your environment.

LDAP PHP implementation example - https://riptutorial.com/ldap/example/19797/setting-up-php-to-work-with-ldap

```php
<?php

// LDAP server settings
$ldapServer = 'ldap://your-ldap-server';
$ldapBaseDn = 'dc=example,dc=com';

// LDAP user credentials
$ldapUsername = 'ldap-username';
$ldapPassword = 'ldap-password';

// Connect to LDAP server
$ldapConn = ldap_connect($ldapServer);
if (!$ldapConn) {
    die('Failed to connect to LDAP server');
}

// Bind to LDAP server using the user credentials
$ldapBind = ldap_bind($ldapConn, $ldapUsername, $ldapPassword);
if (!$ldapBind) {
    die('LDAP bind failed');
}

// LDAP search
$ldapFilter = '(uid=your-username)';
$ldapSearch = ldap_search($ldapConn, $ldapBaseDn, $ldapFilter);
if (!$ldapSearch) {
    die('LDAP search failed');
}

$ldapEntries = ldap_get_entries($ldapConn, $ldapSearch);
if ($ldapEntries['count'] == 1) {
    // User found in LDAP
    $userDn = $ldapEntries[0]['dn'];
    // Perform any additional actions or authentication checks
    // ...
    echo 'User authenticated successfully';
} else {
    // User not found in LDAP or multiple entries found
    echo 'Invalid credentials';
}

// Close LDAP connection
ldap_close($ldapConn);
?>
```

## Christian LDAP PHP test connection script

```php
<?php

// using ldap bind
$ldaprdn  = 'PMCON\cltest';     // ldap rdn or dn
$ldappass = 'Password1';  // associated password

// connect to ldap server
$ldapconn = ldap_connect("ldap://ttbrcdc001.ad.pmcon.co.tt")
    or die("Could not connect to LDAP server.");

if ($ldapconn) {

    // binding to ldap server
    $ldapbind = ldap_bind($ldapconn, $ldaprdn, $ldappass);

    // verify binding
    if ($ldapbind) {
        echo "LDAP bind successful...";
    } else {
        echo "LDAP bind failed...";
    }

}

?>
```
