# TO_CHAR

**Función:** Convertir valores a otros valores o formatos.
**Ejemplo:** La usamos para convertir valores de tipo Fecha `(DATE O TIMESTAMP)` a formato de texto específico.

```PLSQL
SELECT TO_CHAR(SYSDATE, 'DD-MM-YYYY HH24:MI:SS' ) FROM dual;
```

Esto devuelve la fecha actual en el formato `día-mes-año hora:minuto:segundo`.

---

1. Entrada

```PLSQL
SELECT TO_CHAR(TO_DATE('2025-05-07', 'YYYY-MM-DD'), 'DD "de" Month YYYY')
AS fecha_formateada
FROM dual;
```

2. Salida

```MD
07 de May 2025
```

>[!INFO] DATO
>Cuando pidamos que nos devuelva el mes con `TO_CHART` nos devolverá en inglés, por esto tenemos que traducirla al español.

