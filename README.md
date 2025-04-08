# Sistemas para una zapatería

## Modelo Entidad-Relacion

![modelo Entidad-Relacion](img/bd_zapateria.png "Modelo Entidad-Relación")

## Modelo físico de la BD

![modelo físico](img/modelo_fisico.png "Modelo físico de la BD")

## Tabla Fabricante

![Tabla Fabricante](img/tabla_fabricante.png "Tabla Fabricante")

## Tabla Articulo
![Tabla Articulo](img/tabla_articulo.png "Tabla Articulo")

## Consultas a la BD

1. Mostrar la lista de todos datos de los fabricantes

`SELECT * FROM Fabricante;`

2. Mostrar la lista de nombres de los Fabricantes, poniento un alias al nombre de la columna

`SELECT nombre_fabricante AS Fabricante FROM Fabricante;`

![Consulta 2](img/consulta_2.png "Consulta 2")

3. Mostrar los nombres de los productos.

`SELECT nombre_articulo FROM Articulo;`

![Consulta 3](img/consulta_3.png "Consulta 3")

4. Obtener los nombres y los precios de los productos de la tienda.

`SELECT nombre_articulo AS Nombre, precio_articulo AS Precio FROM Articulo;`

![Consulta 4](img/consulta_4.png "Consulta 4")

5. Obtener los nombres de los artículos cuyo precio sea superior a 50000.

`SELECT nombre_articulo FROM Articulo WHERE precio_articulo > 50000;`

![Consulta 5](img/consulta_5.png  "Consulta 5")

6. Obtener el nombre de los artículos cuyo precio esté entre 5000 y 40000 (ambos incluidos)

### Forma 1
`SELECT nombre_articulo FROM Articulo WHERE precio_articulo >= 5000 AND precio_articulo <= 40000;`

### Forma 2
`SELECT nombre_articulo FROM Articulo WHERE precio_articulo BETWEEN 5000 AND 40000;`

![Consulta 6](img/consulta_6.png  "Consulta 6")

7. Obtener el precio y el nombre de los articulos en dolares.

`SELECT nombre_articulo AS articulo, precio_articulo / 4300 AS Precio_USD FROM articulo;`

![Consulta 7](img/consulta_7.png  "Consulta 7") 
## intento 2

8. Mostrar el precio promedio de todos los productos.

`SELECT AVG(precio_articulo) AS precio_promedio FROM Articulo;`

![Consulta 8](img/consulta_8.png  "Consulta 8") 

9. Mostrar el precio promedio de los artículos cuyo código de fabricante sea fab02

`SELECT AVG(precio_articulo) AS promedio_fab02 FROM Articulo WHERE id_fabricante = 'fab02';`

![Consulta 9](img/consulta_9.png  "Consulta 9") 

10.  Obtener el número de artículos cuyo precio sea mayor o igual a $50000.

`SELECT nombre_articulo, precio_articulo FROM Articulo WHERE precio_articulo >= 50000
UNION ALL
SELECT 'Total de artículos' AS nombre_articulo, COUNT(*) AS precio_articulo FROM Articulo WHERE precio_articulo >= 50000;`

![Consulta 10](img/consulta_10.png  "Consulta 10") 

11.  Obtener el nombre y el precio de los artículos cuyo precio sea igual o mayor a $50000 y ordenarlos descendentemente por precio, y luego ascendentemente por nombre.

`SELECT nombre_articulo, precio_articulo FROM Articulo WHERE precio_articulo >= 50000 ORDER BY precio_articulo DESC, nombre_articulo ASC;`

![Consulta 11](img/consulta_11.png  "Consulta 11") 

12. Mostrar el listado completo de artículos, incluyendo por cada artículo los datos del artículo y de su fabricante.

`SELECT A.id_articulo, A.nombre_articulo, A.precio_articulo, F.nombre_fabricante FROM Articulo A JOIN Fabricante F ON A.id_fabricante = F.id_fabricante;`

![Consulta 12](img/consulta_12.png  "Consulta 12") 

13. Obtener un listado de artículos, incluyendo el nombre del artículo, su precio y el nombre de su fabricante.


`SELECT A.nombre_articulo, A.precio_articulo, F.nombre_fabricante FROM Articulo A JOIN Fabricante F ON A.id_fabricante = F.id_fabricante;`

![Consulta 13](img/consulta_13.png  "Consulta 13") 

14. Obtener el precio promedio de los productos de cada fabricante, mostrando solo los códigos de los fabricantes.

`SELECT id_fabricante, AVG(precio_articulo) AS promedio FROM Articulo GROUP BY id_fabricante;`

![Consulta 14](img/consulta_14.png  "Consulta 14")