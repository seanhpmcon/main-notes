### Middleware
Create the middleware, `AuthCheck.php` which would be applied to all routes in the app besides the login routes.

### Controller
Create the Login Controller `Login.php` to authenticate the user using LDAP.

### Blade Template
Create the template `login.blade.php` for the login page.

### Route
Create the route for the login page and add the middleware to the routes that need protecting. This is done in the main `web.php` file.