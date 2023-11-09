When creating a custom backend to handle LDAP authentication:

1. Create the Custom Auth Backend
2. Add it to the settings.py file
3. Change the login redirect url which is set to `accounts/profile/` by default

Issues:
The create user function saves the user in the database. This is because I got an unique constraint error when logging into the app a second time as I have the functionality to create a new user everything someone logs in.

### Resources
https://stackoverflow.com/questions/54549903/django-authentication-ldap-full-example
https://medium.com/@itsayushbansal/ldap-authentication-with-django-a2b4f00c9a04
https://pypi.org/project/django-auth-ldap/

*Adding Custom Groups to Django LDAP*
https://groups.google.com/g/netbox-discuss/c/ku2oiKLQkAU
https://forum.djangoproject.com/t/mapping-ldap-attributes-to-extended-user-model/1994

From the Django app tutorial, once you set up as the boiler plate, the user would need to log in with their username and password and Django would check the credentials against AD. Extend the Django user model to incorporate more groups.