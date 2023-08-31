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

Instead of prepending `PMCON\` to the username, you can add the domain `@domain` to the end of the username.