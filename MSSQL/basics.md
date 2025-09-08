# MSSQL Command Line Guide for Linux

This guide shows how to perform basic tasks using **sqlcmd** on Linux.

---

## 1. Connect to SQL Server
```bash
sqlcmd -S localhost -U SA -P 'YourPassword123'
```
- `-S` → server name or IP (use `localhost,1433` if custom port)  
- `-U` → username  
- `-P` → password  

---

## 2. Switch to a Database
```sql
USE MyDatabase;
GO
```

---

## 3. View All Databases
```sql
SELECT name FROM sys.databases;
GO
```

---

## 4. View All Tables in Current Database
```sql
SELECT table_name 
FROM information_schema.tables 
WHERE table_type='BASE TABLE';
GO
```

---

## 5. View Table Columns
```sql
EXEC sp_help 'MyTable';
GO
```
or
```sql
SELECT column_name, data_type 
FROM information_schema.columns 
WHERE table_name = 'MyTable';
GO
```

---

## 6. Select Rows from a Table
```sql
SELECT TOP 10 * FROM MyTable;
GO
```

---

## 7. Insert a Row
```sql
INSERT INTO MyTable (Column1, Column2)
VALUES ('Value1', 'Value2');
GO
```

---

## 8. Update a Row
```sql
UPDATE MyTable
SET Column1 = 'NewValue'
WHERE Column2 = 'Value2';
GO
```

---

## 9. Delete a Row
```sql
DELETE FROM MyTable
WHERE Column1 = 'Value1';
GO
```

---

## 10. Exit `sqlcmd`
```sql
QUIT
```

---

## 🔹 Tips
- Use `:help` inside `sqlcmd` for command shortcuts.
- To run a `.sql` script file:
  ```bash
  sqlcmd -S localhost -U SA -P 'YourPassword123' -d MyDatabase -i script.sql
  ```
- To output query results to a file:
  ```bash
  sqlcmd -S localhost -U SA -P 'YourPassword123' -d MyDatabase -Q "SELECT * FROM MyTable" -o output.txt
  ```
