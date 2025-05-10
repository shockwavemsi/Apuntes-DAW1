```PLSQL
DECLARE
    CURSOR cur_empleados IS 
        SELECT id_empleado, salario 
        FROM empleados 
        WHERE departamento = 'Ventas'
        FOR UPDATE OF salario;
BEGIN
    FOR registro IN cur_empleados LOOP
        UPDATE empleados
        SET salario = registro.salario * 1.1
        WHERE CURRENT OF cur_empleados;
    END LOOP;
    
    COMMIT;
END;
```

- **Declaramos un cursor** (`cur_empleados`) que selecciona empleados del departamento de ventas y bloquea la columna `salario` para actualización.
    
- **Iteramos sobre el cursor** con un `FOR LOOP`.
    
- **Usamos** `WHERE CURRENT OF` para actualizar directamente la fila actual del cursor sin necesidad de especificar `WHERE id_empleado = ...`.
    
- **Aplicamos** `COMMIT` al final para guardar los cambios.