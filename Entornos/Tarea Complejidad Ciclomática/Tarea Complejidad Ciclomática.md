# Ejercicio 1

Otorgar una beca universitaria basándose en los criterios de edad, renta familiar y nota del expediente de bachillerato.

![[{7CF36923-1694-47E8-943E-E8061FA935BE}.png]]
![[Pasted image 20250511081839.png | 900]]
![[Pasted image 20250511081907.png | 300]]

## Datos para el calculo de complejidad

- **N.º de aristas:** 11
- **N.º de nodos:** 9
- **N.º de regiones:** 4

## Cálculo de complejidad ciclomática V(G) con las 3 fórmulas


- **V(G):** 4
- **V(G):** 11 - 9 + 2 = 4
- **V(G):** 4

# Caminos independientes

- **Camino 1:** 1,2,6,7
- **Camino 2:** 1,2,3,4,6,7
- **Camino 3:** 1,2,3,4,5,7
- **Camino 4:** 1,2,3,5,7

# Tabla


| N.ª de Caso | Valores de entrada                                                             | Resultado esperado                                                                      |
| :---------: | ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------- |
|      1      | **-Edad:** 31<br>**-RentaFamilia:** 15000<br>**-ExpedienteBachillerato:** 9.2  | *Beca no otorgada*<br>(Supera el limite de edad)                                        |
|      2      | **-Edad:** 25<br>**-RentaFamilia:** 25000<br>**-ExpedienteBachillerato:** 7.3  | *Beca no otorgada*<br>(Supera el límite de renta y no cumple con la nota sobresaliente) |
|      3      | **-Edad:** 27<br>**-RentaFamilia:** 21000 <br>**-ExpedienteBachillerato:** 9.5 | *Beca otorgada*<br>(Supero el límite de renta, pero cumple con la nota sobresaliente)   |
|      4      | **-Edad:** 23<br>**-RentaFamilia:** 17000<br>**-ExpedienteBachillerato:** 9.7  | *Beca otorgada*<br>(Cumple con todos lo requisitos)                                     |

# Pruebas En IDE

- **Caso 1:**
	![[{37715AF1-7FA1-4E6E-8336-F6826030E777}.png]]

- **Caso 2:**
	![[{03E487D8-DCEA-4D50-B7DB-3F843B7A21AD}.png]]

- **Caso 3:**
	![[{B2EDA422-AEB1-4B8B-A213-A86F73C4A1CE}.png]]

- **Caso 4**
	![[{33773063-8F70-463A-8401-809CE65FB38B}.png]]

---

# Ejercicio 2

![[{ADADA4DA-9337-4D00-8475-70EB8863409D}.png]]

![[Pasted image 20250511120312.png | 400]]
![[Pasted image 20250511120331.png | 600]]
## Datos para el calculo de complejidad

- **N.º de aristas:** 10
- **N.º de nodos:** 8
- **N.º de regiones:** 4

## Cálculo de complejidad ciclomática V(G) con las 3 fórmulas


- **V(G):** 4
- **V(G):** 10 - 8 + 2 = 4 
- **V(G):** 3 + 1 = 4

# Caminos independientes

- **Camino 1:** 1,2,3,7,8
- **Camino 2:** 1-2-4-7-8
- **Camino 3:** 1-2-5-7-8
- **Camino 4:** 1-2-6-7-8

# Tabla


| N.ª de Caso | Valores de entrada          | Resultado esperado                                                                                 |
| :---------: | --------------------------- | -------------------------------------------------------------------------------------------------- |
|      1      | - **TipoCliente:** PLATINO  | *Retorna un descuento de 50*<br>(Cumple con el caso "PLATINO")                                     |
|      2      | - **TipoCliente:** ORO      | *Retorna un descuento de 40*<br>(Cumple con el caso "ORO")                                         |
|      3      | - **TipoCliente:** BRONCE   | *Retorna un descuento de 10*<br>(Cumple con el caso "BRONCE")                                      |
|      4      | - **TipoCliente:** DIAMANTE | *Retorna un descuento de 0*<br>(No cumple con ningún caso, se le retorna el descuento por defecto) |
# Pruebas en IDE

- **Caso 1:**
  ![[{1AD5CF55-861C-4384-9C77-7C69DD15D206}.png]]
- **Caso 2:**
  ![[{6C3CF423-E3FD-4684-86BD-7B0578FE3D42}.png]]
- **Caso 3:**
  ![[{DD7E1AE1-788F-4477-B5CC-F21A1D7D383E}.png]]
- **Caso 4:**
  ![[{3BB7ABF0-9482-4202-AF3D-BA3FBA2DA3BB}.png]]

---

# Ejercicio 3

![[{11856937-8254-462B-9784-5CA374B5EDA0}.png]]

![[Pasted image 20250511121835.png | 550]]
![[Pasted image 20250511121943.png | 450]]
## Datos para el calculo de complejidad

- **N.º de aristas:** 9
- **N.º de nodos:** 8
- **N.º de regiones:** 3

## Cálculo de complejidad ciclomática V(G) con las 3 fórmulas


- **V(G):** 3
- **V(G):** 9 - 8 + 2 = 3 
- **V(G):** 3 + 1 = 4

# Caminos independientes

- **Camino 1:** 1,2,8
- **Camino 2:** 1,2,3,4,5,6,3,7,8
- **Camino 3:** 1,2,3,4,5,6,3,7,8

# Tabla

| N.ª de Caso | Valores de entrada                     | Resultado esperado                                        |
| ----------- | -------------------------------------- | --------------------------------------------------------- |
| 1           | **cadena:** ""<br>**letra:** "a"       | _Retorna_ numLetras = 0<br>(La cadena está vacía)         |
| 2           | **cadena:** "patata"<br>**letra:** "a" | _Retorna_ numLetras = 3<br>(La letra "a" aparece 3 veces) |
| 3           | **cadena:** "xyz"<br>**letra:** "a"    | _Retorna_ numLetras = 0<br>(No hay coincidencias)         |

# Pruebas En IDE

- **Caso 1:**
  ![[{FCD1A574-71AF-4BF8-8CB9-3A8658478371}.png]]
- **Caso 2:**
  ![[{8C319D67-40E0-401C-916B-5183EDF36A67}.png]]
- **Caso 3:**
  ![[{C914A33A-1BFA-4634-816E-4A173EE0E6C2}.png]]
  
---
