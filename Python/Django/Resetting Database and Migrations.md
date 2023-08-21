To reset everything, and start by generating a new database and migration follow the steps below:
1. Go through each of your projects apps migration folder and remove everything inside, except the `__init__.py` file.
	1. `find . -path "*/migrations/*.py" -not -name "__init__.py" -delete` (for Unix).
	2. `find . -path "*/migrations/*.pyc" -delete` (for Unix).
2. Drop the current database, or delete the db.sqlite3 if it is your case.
3. Create the initial migrations and generate the database schema.
	1. `python manage.py makemigrations`
	2. `python manage.py migrate`

For more information, visit -> https://simpleisbetterthancomplex.com/tutorial/2016/07/26/how-to-reset-migrations.html