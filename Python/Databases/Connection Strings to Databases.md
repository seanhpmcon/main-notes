#databases
### SQLAlchemy
`mssql+pyodbc://QPPSL-WS-13/crm_version_test?trusted_connection=yes&driver=SQL+Server+Native+Client+11.0`

### PYODBC
```python
conn_str = ("Driver={ODBC Driver 17 for SQL Server};"

            "Server=QPPSL-WS-13;"

            "Database=crm_version_test;"

            "Trusted_Connection=yes;")

conn = pyodbc.connect(conn_str)

cursor = conn.cursor()
```