### Installing PHP LDAP
`apt-get update && apt-get install libldap2-dev -y && rm -rf /var/lib/apt/lists/* && docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/ && docker-php-ext-install ldap`
Add `extension=ldap` to the file

### Configuring Apache to look for the `index.php` file
To configure the apache server to serve the `index.php` file first, in the `dir.conf` file in the `/etc/apache2/mods-enabled` folder, add `index.php` to the front of the `DirectoryIndex` directive like:
```php
<IfModule mod_dir.c>
    DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
```
