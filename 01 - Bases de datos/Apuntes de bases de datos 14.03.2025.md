

**Esto es un procedimiento almacenado**

```PLSQL
create or replace procedure "CAMBIODEDIVISAS" (Cantidad_Euros in Number,
	Cambio_Actual in Number,
	Tipo_Interes_Comision in out Number,
	Comision out Number,
	Cantidad_Cambiada out Number)
	is
begin
	--Asignamos un valor 0.02, si el Tipo_Interes_Comision es null
	If Tipo_Interes_Comision is null
		Then Tipo_Interes_Comsion :=0.02;
	End if;

	--Si el resultado de aplicar la comisión da menors de 3, asignamos la comision a 3, en caso de que no , calculamos la comisión.
	If (Cantidad_Euros * Tipo_Interes_Comision) /100 < 3
		Then comision:= 3;
	Else comision:= (Cantidad_Euros * Tipo_Interes_Comision) /100;
	End If;
	
	--Calculamos la Cantidad_Cambiada
	Cantidad_Cambiada := (Cantidad_Euros * Cambio_Actual) - comision;
End;
```

```PLSQL
Declare
	--Aqui declaramos las varibles para los parametros de salida
	V_interes Number; -- V_interes para Tipo_Interes_Comision 
	V_comision Number; -- V_comision para Comision
	V_cantidad Number; -- V_cantidad para Cantidad_Cambiada
Begin
	--Aqui llamamos al procedimiento almacenado , pasamos los parametros y varibles para
	CAMBIODEDIVISAS(100,1.09,V_interes,V_comision,V_cantidad)
End
```