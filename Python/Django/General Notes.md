### Installed apps
List all the app to be built in the settengs.py file in the INSTALLED_APPS list

### Databases
make migrations, Create models or create models from an existing database by using the command `python manage.py inspectdb --database=your_existing_schema > your_app_name/models.py` and modify the models.py file to suit.

### Serializers
Create serializers to be used to turn complex Django objects into python datatypes which can be easily converted to JSON.
When serializing raw SQL queries, create nested serializers for all the fields in the query.

### Resource Links
1. How to connect Django to an existing database -> https://rafed.github.io/devra/posts/database/how-to-connect-django-to-existing-database/
2. How to use Django with an existing database -> https://djangoadventures.com/how-to-integrate-django-with-existing-database/