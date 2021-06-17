# Store Procedures
Los store procedures son procedimientos de [[SQL]] que se guardan en la base de datos para ser accesados directamente después.
Pueden tener parámetros, controlar el flujo de ejecución (IF, ELSE, WHILE), pueden llamar otros procedimientos o funciones.

Más referencia en: https://www.mysqltutorial.org/mysql-stored-procedure-tutorial.aspx

## Sintaxis básica
```sql
CREATE PROCEDURE procedure_name(parameter_list)
BEGIN
   statements;
END //
```

## Parámetros
Existen dos tipos: IN, OUT y una combinación de ambos: INOUT.
La sintaxis básica de los parámetros es: 
```sql
[IN | OUT | INOUT] parameter_name datatype[(length)]
```
### Ejemplo de store procedure con parámetros
```sql
DELIMITER $$

CREATE PROCEDURE GetOrderCountByStatus (
	IN  orderStatus VARCHAR(25),
	OUT total INT
)
BEGIN
	SELECT COUNT(orderNumber)
	INTO total
	FROM orders
	WHERE status = orderStatus;
END$$

DELIMITER ;
```
Nótese que deben tener un tipo, justo como se hace al crear una tabla.
## IF Statement
Sintaxis básica del IF statement:
```sql
IF condition THEN
   statements;
ELSEIF elseif-condition THEN
   elseif-statements;
...
ELSE
   else-statements;
END IF;
```
Nótese que conditions son las mismas condiciones que un `WHERE`.
## Ejemplo de cómo crear store procedures básicos en [[MySQL]]
```sql
DELIMITER $$

CREATE PROCEDURE GetCustomers()
BEGIN
	SELECT 
		customerName, 
		city, 
		state, 
		postalCode, 
		country
	FROM
		customers
	ORDER BY customerName;    
END$$
DELIMITER ;
```
Una vez guardado este procedimiento se puede acceder así:
```sql
CALL GetCustomers();
```
