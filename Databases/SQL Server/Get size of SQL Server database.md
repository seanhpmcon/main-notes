```sql
SELECT
    DB_NAME(database_id) AS DatabaseName,
    SUM(size * 8 / 1024.0) AS SizeInMB
FROM sys.master_files
WHERE type = 0 -- Data files
GROUP BY database_id;
```