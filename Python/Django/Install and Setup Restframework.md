Packages to install:
1. `pip install django`
2. `pip install djangorestframework`
3. install the required database drivers/packages

### Setup
Setup a Django project -> `django-=admin startproject project-name .` 
The dot (.) builds the project ion the working directory without creating a new folder.

### Configure the installed apps
add the names of the apps used to the INSTALLED_APPS list like 'rest_framework'

### Configure the models
Build the models from scratch when starting with a new database or
use `python manage.py inspectdb > models.py`

### Create Admin SuperUser
Run the following command `python manage.py createsuperuser` and enter the required information
Create an admin.py file and import the models you want displayed in the admin page there

### Access the development server outside the container
Set the `ALLOWED_HOSTS = ['**']` property in the setting.py file

