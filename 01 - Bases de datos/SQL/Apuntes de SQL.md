## WHERE
Es una cláusula para filtrar registros

>[!INFO] Sintaxis
>```SQL
>SELECT column1,column2 FROM table_name
>WHERE condition
>//Nota : `WHERE` también se utiliza en `UPDATE` , `DELETE` , `ETC`.
>```

>[!EXAMPLE] EJEMPLOS
>```SQL
>SELECT * FROM Customers
>WHERE CustomersID = 1;
>//Nota : Los campos numéricos no necesitan comillas
>
>SELECT * FROM Customers
>WHERE CustomersID > 80;
>
>SELECT * FROM Customers
>WHERE Country = 'Mexico';
>//Nota: Los campos de texto usamos comillas.
>```

### 1.1 Operadores con claúsula WHERE
- `=` : Igual
- `>` : Mayor que
- `<` : Menor que 
- `>=` : Mayor o igual
- `<=` : Menor o igual
- `<>` : Diferente de *En otros lenguajes es !=*
- `BETWEEN` : Entre un rango determinado
- `LIKE` : Buscar un patrón
- `IN` : Para especificar múltiples valores posibles para una columna.

# PARTITION BY
Nos permite individualizar cada fila del grupo, mediante las funciones de ventana.

>[!INFO] SINTAXIS
>```SQL
>SELECT
>	columna1,
>	columna2,
>	funcion_agregada() OVER (PARTITION BY columnaX)
>FROM
> 	tabla
>```

>[!EXAMPLE] EJEMPLO 1
>```SQL
>CREATE Database Empresa; 
>USE Empresa; 
>create table empleado ( 
>	id INT PRIMARY KEY AUTO_INCREMENT, 
>	nombre varchar(100), 
>	departamento VARCHAR(100), 
>	salario INT 
>); 
>
>INSERT INTO empleado (nombre, departamento, salario) VALUES 
>	('Ana', 'Marketing', 5000), 
>	('Juan', 'Marketing', 6000), 
>	('Luis', 'Ventas', 4500), 
>	('María', 'Ventas', 5500), 
>	('Carlos', 'IT', 7000), 
>	('Sofía', 'IT', 8000);
>	 
>select 
>		nombre, 
>		departamento, 
>		salario, 
>		AVG(salario) over(Partition by departamento) as promedio_departamento 
>FROM empleado;
>```

Esto nos devolvería:

```
| nombre | departamento | salario | promedio_departamento |
| ------ | ------------ | ------- | --------------------- |
| Ana    | Marketing    | 5000    | 5500                  |
| Juan   | Marketing    | 6000    | 5500                  |
| Luis   | Ventas       | 4500    | 5000                  |
| María  | Ventas       | 5500    | 5000                  |
| Carlos | IT           | 7000    | 7500                  |
| Sofía  | IT           | 8000    | 7500                  |
```


