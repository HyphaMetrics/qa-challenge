# Metalibrary QA Challenge
## SQL
Considere las siguientes tablas

### Households (Hogares)
| household\_id | region      | signup\_date |
| ------------- | ----------- | ------------ |
| HH001         | CDMX        | 2024-03-15   |
| HH002         | Guadalajara | 2024-05-01   |
| HH003         | Monterrey   | 2024-06-20   |
| HH004         | Puebla      | 2024-04-12   |
| HH005         | Mérida      | 2024-07-01   |
| HH006         | Tijuana     | 2024-06-05   |
| HH007         | León        | 2024-03-22   |
| HH008         | Querétaro   | 2024-05-18   |
| HH009         | Toluca      | 2024-07-10   |
| HH010         | Cancún      | 2024-02-25   |

### Devices (Dispositivos)
| device\_id | household\_id | device\_type | brand   | model       | active\_since |
| ---------- | ------------- | ------------ | ------- | ----------- | ------------- |
| D001       | HH001         | TV           | Samsung | QLED-Q60    | 2024-03-16    |
| D002       | HH001         | Tablet       | Apple   | iPad 9th    | 2024-03-20    |
| D003       | HH002         | TV           | LG      | OLED-C1     | 2024-05-02    |
| D004       | HH003         | TV           | Sony    | Bravia X80J | 2024-06-21    |
| D005       | HH004         | TV           | Hisense | U6H         | 2024-04-13    |
| D006       | HH004         | Phone        | Xiaomi  | Redmi 12    | 2024-04-20    |
| D007       | HH005         | TV           | TCL     | P735        | 2024-07-01    |
| D008       | HH006         | TV           | LG      | NanoCell    | 2024-06-06    |
| D009       | HH006         | TV           | LG      | OLED-C2     | 2024-06-10    |
| D010       | HH007         | TV           | Samsung | Crystal UHD | 2024-03-23    |
| D011       | HH008         | TV           | Sony    | X90K        | 2024-05-19    |
| D012       | HH009         | TV           | LG      | OLED-A1     | 2024-07-11    |
| D013       | HH010         | TV           | Hisense | U8H         | 2024-02-26    |
| D014       | HH010         | Tablet       | Lenovo  | Tab M10     | 2024-03-01    |


### Sessions (Sesiones)
| session\_id | device\_id | app\_name   | start\_time         | end\_time           |
| ----------- | ---------- | ----------- | ------------------- | ------------------- |
| S001        | D001       | Netflix     | 2024-07-30 19:00:00 | 2024-07-30 21:15:00 |
| S002        | D001       | YouTube     | 2024-07-30 08:30:00 | 2024-07-30 09:00:00 |
| S003        | D002       | Disney+     | 2024-07-30 14:00:00 | 2024-07-30 15:30:00 |
| S004        | D003       | Prime Video | 2024-07-29 20:00:00 | 2024-07-29 22:00:00 |
| S005        | D005       | Netflix     | 2024-07-30 18:00:00 | 2024-07-30 19:45:00 |
| S006        | D006       | YouTube     | 2024-07-30 10:00:00 | 2024-07-30 10:25:00 |
| S007        | D008       | Netflix     | 2024-07-29 21:00:00 | 2024-07-29 23:30:00 |
| S008        | D009       | Netflix     | 2024-07-30 22:00:00 | 2024-07-31 00:00:00 |
| S009        | D011       | HBO Max     | 2024-07-30 20:15:00 | 2024-07-30 21:00:00 |
| S010        | D013       | Netflix     | 2024-07-30 17:00:00 | 2024-07-30 19:00:00 |
| S011        | D014       | YouTube     | 2024-07-30 19:15:00 | 2024-07-30 20:00:00 |

#### Responda las siguientes preguntas en el archivo queries.txt

1. Obtener los nombres de todas las apps que se han usado desde televisores (device_type = 'TV').
2. Calcular el número total de sesiones y el tiempo total de visualización por aplicación.
Nota: duración = end_time - start_time
3. Mostrar los 5 hogares con más tiempo total de uso de apps, sumando la duración de todas las sesiones.
4. Para cada región, obtener el número de hogares y el promedio de dispositivos por hogar.
5. Obtener las sesiones iniciadas en el mes de junio de 2025, indicando la app, el dispositivo y la duración.
6. Crear una vista daily_usage_per_household que contenga:
household_id
usage_date (por día)
total_minutes_watched

Nota: calcula minutos desde las sesiones.

7. Identifica qué hogares tienen más de un dispositivo del mismo tipo (por ejemplo, dos TVs). Devuelve household_id, device_type y el conteo.
8. Escribe un query que detecte sesiones con duración anormal (mayor a 6 horas) y devuelva: household, device_type, app, duración.


##  Mongodb

- Base de datos: videoclub
- Colección: peliculas

Ejemplo de documentos en peliculas:

```
{
  "_id": ObjectId("..."),
  "titulo": "Volver al Futuro",
  "anio": 1985,
  "genero": "Ciencia Ficción",
  "calificacion": 8.5,
  "director": "Robert Zemeckis",
  "disponible": true
}
```

```
{
  "titulo": "Titanic",
  "anio": 1997,
  "genero": "Romance",
  "calificacion": 7.8,
  "director": "James Cameron",
  "disponible": false
}
```

### Llenar el archivo answers.txt con las siguientes queries:
- Mostrar todas las películas.
- Mostrar las películas del año 1997.
- Mostrar las películas con calificación mayor a 8.
- Mostrar solo el título y año de cada película.
- Mostrar películas que estén disponibles (disponible: true).
- Agrega una película nueva: "Inception", 2010, Ciencia Ficción, 8.8, Christopher Nolan, disponible.
- Actualizar la calificación de "Titanic" a 8.0.
- Consulta todas las películas dirigidas por Christopher Nolan.
- Muestra todas las películas ordenadas por año descendente.

### Explica brevemente en el archivo errors.txt ¿Cómo identificarías errores en la información que pudieran conllevar a estar repitiendo registros?

¿Cómo identificarías posibles errores o inconsistencias en los títulos que puedan estar causando registros duplicados?
Por ejemplo: "Lord of the rings", "Lrd of the rings", "Lord  of the rings", "Lord of the rings." 