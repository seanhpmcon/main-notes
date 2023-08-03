### Installing PHP LDAP
`apt-get update && apt-get install libldap2-dev -y && rm -rf /var/lib/apt/lists/* && docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/ && docker-php-ext-install ldap`
Add `extension=ldap` to the file