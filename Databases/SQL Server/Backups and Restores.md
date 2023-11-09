When restoring, ensure a few things are in place:
1. The `.bak` file is in the correct folder.
2. The user has permission to access and restore using that `.bak` file. (Not sure if the user who created the `.bak` file needs to be the one to restore due to permissions)
3. In the Options setting check, the first and last boxes.

### Transfer one database data to another
Using Export data functionality (SQL Server Import and Export Wizard):
1. Start with the target database being empty. (Not sure if this needs to be, when importing to a database with data already, id error were being thrown, not sure if there was a unique constrain issue.)
2. Right click on the database.
3. Under tasks, select Export Data.
4. Follow the SQL Server Import and Export Wizard to transfer the data.