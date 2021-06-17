# Stored Procedures
Son procedimientos que ya están almacenados en la base de datos.

Bastante bien explicado en: https://www.w3schools.com/SQL/sql_stored_procedures.asp

## Ver todas las stored procedures
```sql
SELECT \*

FROM \[GymTec\].INFORMATION\_SCHEMA.ROUTINES

WHERE ROUTINE\_TYPE \= 'PROCEDURE'

AND LEFT(ROUTINE\_NAME, 3) NOT IN ('sp\_', 'xp\_', 'ms\_')
```

---
Ir a [[SQL Server]]