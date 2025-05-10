# Script de ciudades
```SQL
CREATE DATABASE ciudades;
USE ciudades;
CREATE TABLE cities (city VARCHAR (25) , state VARCHAR(2), price_to_income_ratio DECIMAL(3,1), mortgage_as_pct_of_income DECIMAL(5,1), homeowner_pct TINYINT UNSIGNED , population INT UNSIGNED);

INSERT INTO cities VALUES('Santa Barbara','CA',13.3,103.7,53,88000),('Brooklyn','NY',11.2,89.9,30,2533862),
('Queens','NY',11.1,91.3,45,2271000),
('New York','NY',10.4,85.9,24,8468000),
('Oakland','CA',9.4,77.5,41,433800),
('Sunnyvale','CA',9.3,76.5,45,152300),
('San Diego','CA',8.2,66.3,54,1382000),
('San Francisco','CA',9.2,73.2,38,815200),
('Long Beach','CA',8.5,69.6,41,456000),
('Buffalo','NY',6.5,53,43,276800);

```
## Ejercicios 

//YA LO CREE EN EL XAMPP con la de ciudades

1)Obtener para cada ciudad si tiene densidad baja, media o alta, teniendo en cuenta que se considera densidad baja a ciudades con población inferior a 500000 habitantes, densidad media a ciudades

```SQL
//TRATA DE CLASIFICAR CIUDADES
 SELECT city FROM cities WHERE population < 500000;
Si hago esto estaría bien si solo me pidiesen una cosa. Lo que quiero es que para cada ciudad me diga la densidad que tiene cada una. Me pide que saque cada ciudad y la clasifique.
SELECT city, "Densidad Baja" FROM cities WHERE population < 500000;
Con esto me sale pero solo de una parte de las ciudades.
TENEMOS QUE HACER EL CASE WHEN

SELECT 
city,
population, 
CASE
 WHEN population < 500000 THEN 'Low'
 WHEN population >= 500000 and population < 1500000 THEN 'Medium'
WHEN population >= 1500000 THEN 'High'
END as population_level
FROM cities;

//CON ESTO YA ME SALE TODO CORRECTO CON EL CASE WHEN
```


![[Pasted image 20250213093836.png]]

2) Obtener la población media para cada uno de los tipos de densidad de población

Si hago:
SELECT AVG(population) FROM cities WHERE population < 500000//Estaria bien si solo me piden de una, pero yo quiero la de todas. Juntar los tres tipos de población.
Nos lleva al caso de usar un CASE WHEN con un GROUP BY

```SQL
SELECT
 CASE
  WHEN population < 500000 THEN 'Densidad Baja'
  WHEN population >= 500000 and population < 1500000 THEN 'Densidad Media'
  WHEN population >= 1500000 THEN 'Densidad Alta'
  END AS population_level,
  AVG(population) as average_population
  FROM cities
 GROUP BY
 CASE
   WHEN population < 500000 THEN 'Low'
   WHEN population >= 500000 and population < 1500000 THEN 'Medium'
   WHEN population >= 1500000 THEN 'High'
END
```



![[Pasted image 20250213093904.png]]

Resumen de código:
```SQL
SELECT
 CASE
  WHEN population < 500000 THEN 'Densidad Baja'
  WHEN population >= 500000 and population < 1500000 THEN 'Densidad Media'
  ELSE 'Densidad Alta'
  END AS population_level, 
  AVG(population) as average_population 
  FROM cities
 GROUP BY population_level;
//MAS RESUMIDO¡¡¡ EN VEZ DE COPIAR TODO EL GROUP BY CASE WHEN solo pongo GROUP BY population_level

```

3)Obtener cuantas ciudades tienen densidad baja, media y alta
//FACIL SOLO SUTITUIMOS EL AVG CON EL COUNT¡¡¡

```SQL
SELECT
 CASE
  WHEN population < 500000 THEN 'Densidad Baja'
  WHEN population >= 500000 and population < 1500000 THEN 'Densidad Media'
  ELSE 'Densidad Alta'
  END AS population_level, 
  COUNT(population) as "Numero de ciudades" 
  FROM cities
 GROUP BY population_level;
```

1) Obtener de cada producto su información y su categoría , teniendo en cuenta que 
- la sudadera, la chaqueta y el hersei pertenecen a prendas de exterior.
- 

```SQL
SELECT *,

  CASE WHEN description LIKE '%sweater%'
         OR description LIKE '%blazer%'
         OR description LIKE '%jacket%' THEN  'Outerwear'
       WHEN description LIKE `'%dress%'`
         OR description LIKE '%jumpsuit%' THEN  'Dresses'
       WHEN description LIKE `'%shirt%'`
         OR description LIKE '%blouse%' THEN 'Tops'
  END as product_category
FROM products
```

nota : DISTINT , PARTITION entrará en el examen
nota : la diferencia con WHERE y CASE WHEN , que CASE WHEN nos permite clasificar y devolver , en cambio , WHERE solo devuelve.

nota : el partition by permite
```SQL
SELECT COUNT(*) "Nª de ciudades", state ,city from cities GROUP by state;
```

Podemos poner alias de esta manera **"Alias"**.

**GROUP BY** : no permite acceder individualmente a cada fila del grupo , ala vez , poner un dato agregado.
**partition by** permiten individualizar cada fila del grupo 

nota importante : cuando se usa un group by , todo lo que consultemos , tiene que estar en el group  by o tiene ser una función de tabla o agregada (SUM , CONT , AVG , ...)de grupo .esto es regla de oro.

```SQL
SELECT
    train.id,
    train.model,
    route.name,
    route.from_city,
    route.to_city,
    COUNT(*) OVER (PARTITION BY train.id ORDER BY train.id) AS routes,
    COUNT(*) OVER () AS routes_total
FROM train
INNER JOIN journey ON journey.train_id = train.id
INNER JOIN route ON journey.route_id = route.id;
```
**PARTITION** : Permite individualizar cada fila del grupo.

Aprender PARTITION BY con copilot

## PARTITION BY
Nos permite individualizar de cada fila del grupo. 
