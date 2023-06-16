###3.1
```
SELECT p.Orden_no, p.Fechapedido, p.articulo, 
       COALESCE(a.NombreArticulo, 'INEXISTENTE') AS NombreArticulo,
       CASE WHEN a.Estado = 'INACTIVO' OR a.articulo IS NULL THEN 'FUERA DE STOCK' ELSE 'EN STOCK' END AS Estado,
       COALESCE(a.PrecioUntario, -1) AS PrecioUnitario,
       p.Vlrtotal
FROM PEDIDOS p
LEFT JOIN ARTICULO a ON p.articulo = a.articulo
WHERE p.Fechapedido BETWEEN '2021/01/01' AND '2022/05/31'

```
###3.2
```
SELECT p.cliente, p.fechapedido, p.artículo, p.vlrtotal
FROM pedidos p
LEFT JOIN articulo a ON p.artículo = a.art_codigo
WHERE p.fechapedido >= '2018-05-01'
AND a.estado <> 'INACTIVO'

```
###3.3
| Opcion  | Query | Justificación
| ------------- | ------------- |------------- |
| Incorrecta | ``` SELECT Department, AVG(Salary) FROM SALARIES GROUP BY DEPARTMENT ORDER BY AVG(Salary);  ```  | No se especifica la forma de ordenamiento (‘DESC’ o ‘ASC’), por defecto obtendremos ‘ASC’ |
|  Incorrecta | ``` SELECT Department, AVG(Salary) FROM SALARIES ORDER BY AVG(Salary) DESC LIMIT 1;  ```   |  No se hace ninguna agrupación, no podremos realizar la ninguna separación entre los departamentos   |
| Incorrecta | ``` SELECT Department, AVG(Salary) FROM SALARIES GROUP BY AVG(Salary) DESC LIMIT 1; ```   |  Esta agrupa de acuerdo con el valor del salario promedio, es decir, el resultado devolverá el salario promedio más alto de todos los departamentos, pero no el departamento cada departamento.  |
| Correcta | ``` SELECT Department, AVG(Salary) FROM SALARIES GROUP BY DEPARTMENT ORDER BY AVG(Salary) DESC LIMIT 1; ```   |  Respuesta correcta.  |

###3.4
```
SELECT Department, COUNT(*) AS Repetitions
FROM SALARIES
GROUP BY Department
HAVING COUNT(*) > 1
ORDER BY Repetitions DESC;
```

###3.5
```
SELECT DISTINCT Department
FROM SALARIES;
```
