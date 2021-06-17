# SQL Server
Base de datos SQL de Windows (ew).
## Instalación en MacOs
Se instala utilizando un contenedor de Docker. Seguir pasos en: https://database.guide/how-to-install-sql-server-on-a-mac/

## Acceso en GUI
Se puede acceder desde Azure Data Studio: https://docs.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver15

### Crear una nueva base de datos desde Azure Data Studio
Se corre el siguiente comando:
```
Syntax:- 
-- Create a new database called 'DatabaseName'
-- Connect to the 'master' or Any database to run this snippet
USE master  
GO
-- Create the new database if it does not exist already
IF NOT EXISTS (
    SELECT [name]
        FROM sys.databases
        WHERE [name] = N'DatabaseName'
)
CREATE DATABASE DatabaseName
GO
```
Recordando cambiar `DatabaseName` al nombre de la nueva base de datos.

## Diferencias con [[MySQL]]
Lista de todas las diferencias: http://troels.arvin.dk/db/rdbms/

## Scripts utiles
- Drop all tables:
```sql
DECLARE @Sql NVARCHAR(500) DECLARE @Cursor CURSOR

SET @Cursor = CURSOR FAST_FORWARD FOR
SELECT DISTINCT sql = 'ALTER TABLE [' + tc2.TABLE_SCHEMA + '].[' +  tc2.TABLE_NAME + '] DROP [' + rc1.CONSTRAINT_NAME + '];'
FROM INFORMATION_SCHEMA.REFERENTIAL_CONSTRAINTS rc1
LEFT JOIN INFORMATION_SCHEMA.TABLE_CONSTRAINTS tc2 ON tc2.CONSTRAINT_NAME =rc1.CONSTRAINT_NAME

OPEN @Cursor FETCH NEXT FROM @Cursor INTO @Sql

WHILE (@@FETCH_STATUS = 0)
BEGIN
Exec sp_executesql @Sql
FETCH NEXT FROM @Cursor INTO @Sql
END

CLOSE @Cursor DEALLOCATE @Cursor
GO

EXEC sp_MSforeachtable 'DROP TABLE ?'
GO
```

