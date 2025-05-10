```SQL
SELECT nombre FROM producto WHERE precio >= ALL(SELECT);
```


Esto compara el precio de producto , con todos los precios de producto) , pero este operador '>=' impone a que se cumple esta condición.

ALL : Se utiliza para encontrar maximos.

```SQL
SELECT nombre FROM fabricante WHERE id=ANY (SELECT id_fabricante FROM producto);
```

// Esto compara si el id aparece en id_fabricante en producto .

ANY :  Analiza valores

//Lo de abajo va en el examen (CASE WHEN)

```SQL
CREATE TABLE HORAS_USUARIO(Usuario INT UNSIGNED, Hora_Entrada DATETIME, Hora_Salida DATETIME);
```

//Esto hay que usarlo cuando existen casos distintos. Como por ejemplo este example donde si hago la diferencia de horas me salía negativo por lo que no es valido.

```SQL
 INSERT INTO USUARIO VALUES (1,'21:00','02:00'); 
	 SELECT 
			 CASE 
				 WHEN Hora_Salida < Hora_Entrada THEN TIMESTAMPDIFF(MINUTE,
					 Hora_Entrada, Hora_Salida + INTERVAL 1 DAY) 
				 ELSE TIMESTAMPDIFF(MINUTE, Hora_Entrada, Hora_Salida) END AS
					Diferencia_Minutos FROM HORAS_USUARIO;
```