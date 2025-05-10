```PLSQL
DECLARE
 n1 NUMBER(3) := 3;
 n2 NUMBER(3) := 5;
BEGIN
	DBMS_OUTPUT.PUT_LINE('La suma es :' || (n1 + n2));
END;
```