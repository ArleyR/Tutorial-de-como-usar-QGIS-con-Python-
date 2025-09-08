# Tutorial para usar QGIS

## 1. Introducción 

QGIS (Quantum GIS) es un software libre y de código abierto diseñado para trabajar con información geográfica. Con él es posible visualizar, analizar y editar datos espaciales en diferentes formatos, así como crear mapas personalizados. Su uso abarca múltiples áreas como la planificación urbana, el medio ambiente, la ingeniería, la agricultura y la gestión territorial.

Una de las grandes ventajas de QGIS es que incorpora Python como lenguaje de programación a través de su API llamada PyQGIS. Esto permite automatizar procesos, manipular datos de manera más eficiente y crear scripts que simplifican tareas repetitivas dentro del entorno de QGIS.

Además, gracias a Python es posible desarrollar plugins personalizados que amplían las capacidades del software y lo adaptan a necesidades específicas. En conjunto, QGIS y Python ofrecen una herramienta potente y flexible para el trabajo con datos espaciales, tanto para principiantes como para usuarios avanzados.

#### Requisitos:
Versión recomendada: QGIS 3.x (3.10+). Las instrucciones son aplicables a la mayoría de versiones 3.x; pequeñas diferencias de menú pueden existir.
QGIS instalado (Windows con OSGeo4W, macOS o Linux), datos vectoriales/raster (Shapefile, GeoPackage, GeoTIFF, GeoJSON), espacio de trabajo donde guardar salidas.

## 2. Interfaz rápida (qué ver y para qué)

*	Panel Capas (Layers): lista de capas del proyecto.
* Panel Navegador (Browser): arrastra capas desde carpetas, GeoPackage, PostGIS.
* Proyectos: abrir/guardar proyecto, selección.
* Caja de herramientas de procesamiento (Processing Toolbox): aquí están todos los algoritmos (GDAL, GRASS, SAGA, QGIS nativos).
* Consola Python (Python Console): para scripts PyQGIS interactivos.
* Layout (Compositor de impresión): para producir mapas finales (PDF, PNG).

## 3. Flujo de trabajo básico (pasos generales)
* Crear/abrir un proyecto: Proyecto > Nuevo o Archivo > Abrir proyecto.
* Definir CRS del proyecto: Proyecto > Propiedades del proyecto > CRS (importantísimo: trabaja en CRS apropiado para tu análisis).
* Cargar datos (vector/raster) desde Capa > Añadir capa > Añadir capa vectorial o arrastrando desde el Navegador.
* Inspeccionar atributos (abrir tabla de atributos) y geometrías.
* Diseñar mapa en Layout y exportar.

## 4. Cómo cargar datos (GUI)
### Vector (Shapefile, GeoPackage, GeoJSON)
* Capa > Añadir capa > Añadir capa vectorial....
* Selecciona archivo (browse) o usa el Navegador y arrastra la capa.
* Revisa la tabla de atributos (clic derecho sobre la capa > Abrir tabla de atributos).
### Raster (GeoTIFF, JPEG, etc.)
* Capa > Añadir capa > Añadir capa raster....
* Selecciona el archivo TIFF/IMG.
* Si no se muestra correctamente, revisa CRS o georreferenciación.

## 5. Reproyección y sistema de coordenadas 
* Para reproyectar una capa (guardar copia con otro CRS): clic derecho sobre la capa > Exportar > Guardar objetos como... > elegir CRS objetivo (por ejemplo, EPSG:4326 o un CRS proyectado local

## 6. Simbología y etiquetado
•	Clic derecho sobre la capa > Propiedades > Simbología
•	Elige tipo: Simple, Graduado (para rangos), Categorized (por categorías), Rule-based (reglas complejas).
•	Para etiquetas: Etiquetado > Mostrar etiquetas > elegir campo.

## 7. Herramientas de geoprocesamiento (GUI)
### Abre la Caja de herramientas de procesamiento (Processing Toolbox).

*	Buffer: Vector general > Buffer o native:buffer.
*	Clip (recorte): Vector overlay > Clip o native:clip.
*	Intersect / Union / Dissolve: disponibles bajo Vector > Geoprocesamiento.
*	Join attributes by location (unión espacial): native:joinattributesbylocation.

## 8. Modeler (automatizar procesos sin programar)
*	Processing > Graphical Modeler
*	Arrastra herramientas (Buffer, Clip, Join) y conecta entradas/salidas.
*	Guarda el modelo; podrás ejecutarlo con parámetros y usarlo como herramienta.

## 9. Guardar resultados y formatos recomendados
*	GeoPackage (.gpkg): recomendado para múltiples capas y atributos modernos.
*	GeoJSON: ideal para interoperabilidad web, pero cuidado con precisión y campos grandes.
*	Shapefile (.shp): compatibilidad, pero limitaciones: nombres de campo cortos, codificación DBF, tipos de datos limitados.
*	GeoTIFF: para ráster georreferenciado.
*	Cómo exportar (GUI): clic derecho > Exportar > Guardar objetos como... y elegir formato y CRS.

## 10. Cartografía: crear un mapa para impresión
*	Proyecto > Nuevo diseño de impresión (o Proyecto > Layouts > Administrar diseños) > Nuevo.
*	En el diseñador: Añadir elemento > Añadir mapa y arrastra rectángulo para la vista.
*	Añade Leyenda, Escala, Norte, Título (desde Añadir elemento).
*	Ajusta etiquetado y simbología para que el mapa sea claro.
*	Layout > Exportar como PDF o Exportar como imagen.

# Tutorial para usar QGIS con PYTHON

## 1. Introducción

QGIS es un Sistema de Información Geográfica (SIG) que permite trabajar con mapas, datos espaciales y análisis geográficos.
Tiene dos formas principales de uso:

* Interfaz gráfica (GUI): todo con menús y botones, sin necesidad de programar.

* PyQGIS (Python): escribir código para automatizar y repetir procesos fácilmente.

En este tutorial haremos lo mismo en ambos métodos:

* Cargar capas.
* Reproyectar.
* Crear un buffer.
* Recortar (clip).
* Exportar resultados.

## 2. Paso a paso en la GUI (Interfaz Gráfica)
### 2.1 Cargar capas
* Menú Capa > Añadir capa > Añadir capa vectorial.
* Selecciona tu archivo (ejemplo: limite.gpkg).
* Repite para otra capa (ejemplo: rios.shp).

### 2.2 Reproyectar capas

* Clic derecho sobre la capa > Exportar > Guardar objetos como....
* Elige un CRS objetivo (ejemplo: EPSG:4326).
* Guarda con nuevo nombre (ej. rios_4326.gpkg).

### 2.3 Crear un buffer

* Abre la Caja de Herramientas de Procesamiento (Ctrl+Alt+T).
* Busca "Buffer".
* Selecciona rios_4326, define una distancia (ej. 500 metros) y ejecuta.

### 2.4 Recortar (Clip)

* Busca "Clip" en la Toolbox.
* Usa como entrada el buffer y como capa de recorte el limite.gpkg.
* Guarda salida como rios_buffer_clip.gpkg.

### 2.5 Exportar resultados

* Clic derecho sobre la capa final > Exportar > Guardar objetos como....
* Elige formato (GeoPackage, Shapefile, GeoJSON).
  
## 3. Paso a paso en PyQGIS (Python)

* Abrir la Consola Python (Complementos > Consola Python) y ejecutar los scripts.
### 3.1 Cargar capas
### 3.2 Reproyectar
### 3.3 Crear buffer
### 3.4 Recortar (Clip)
### 3.5 Exportar resultados

## 4. Comparación GUI vs PyQGIS
* GUI: más fácil, intuitivo y visual. Perfecto para empezar.
* PyQGIS: ideal para automatizar, documentar y repetir procesos.
ojo (con PyQGIS puedes hacer buffers de 100 capas con un bucle, algo muy lento en la GUI.)

## 5 Buenas prácticas para principiantes
* Usa GeoPackage en lugar de Shapefile.
* Mantén siempre el mismo CRS en tu proyecto.
* Revisa geometrías con Vector > Herramientas de geometría > Verificar validez.
* Guarda tus scripts y proyectos en carpetas ordenadas.

## 6. Conclusión

* La GUI de QGIS es el primer paso: te permite aprender el flujo básico de análisis.
* PyQGIS da un segundo nivel: automatización y escalabilidad.
* Lo mejor es combinar ambos enfoques: probar en GUI y luego convertir en script.

---

# Tutorial para usar datos de QGIS en Python

## Paso 1. Instalar los programas

1. *Instalar QGIS*  
   - Descarga desde: [https://qgis.org/es/site/](https://qgis.org/es/site/)  
   - Elige la versión *LTS (Long Term Support)*, más estable.  
   - Instálala como cualquier programa.

2. *Instalar Python y librerías necesarias*  
   - Descarga Python desde: [https://www.python.org/downloads/](https://www.python.org/downloads/)  
   - Una vez instalado, abre la terminal (o símbolo del sistema) y ejecuta:  

   bash
   pip install geopandas pandas matplotlib

## Paso 2. Abrir un SHP en QGIS

Abre QGIS.

Menú superior → Capa → Añadir capa → Añadir capa vectorial.

Selecciona tu archivo nombre.shp.

Haz clic en Añadir.

**El mapa aparecerá en pantalla**

Para ver la tabla de atributos:

Clic derecho sobre la capa (panel izquierdo).

Selecciona Abrir tabla de atributos.

Verás columnas (atributos) y filas (cada elemento del mapa).

## Paso 3: Exportación de datos desde QGIS

Una vez cargada la capa en QGIS, es posible exportar la información en diferentes formatos según los objetivos del análisis. Este procedimiento se realiza desde el panel de capas con un clic derecho sobre la capa deseada y seleccionando la opción *Exportar → Guardar entidades como…*.

### 🔹 Exportar únicamente la tabla de atributos
1. Seleccionar la capa y hacer clic derecho → *Exportar → Guardar entidades como…*.  
2. En el campo *Formato, escoger **CSV*.  
3. Definir la ruta y el nombre del archivo en *Archivo de salida*.  
4. Confirmar con *Aceptar*.  

De este modo se genera un archivo *.csv, que contiene únicamente la información tabular (sin geometría) y que puede ser abierto en programas como **Excel* o en *Python* mediante la librería *pandas*.

---

## Paso 4: Lectura de los datos en Python

Una vez exportados los datos desde QGIS, se pueden cargar en Python de acuerdo con el formato elegido:

### 🔹 Lectura de archivos CSV (solo tabla)
python
```
import pandas as pd
```

# Ruta del archivo exportado
```
df = pd.read_csv("C:/ruta/archivo.csv")
```

# Visualizar las primeras filas
```
print(df.head())
```

# Análisis de los datos

Luego de tener la base cargada y haber visualizado que este de forma correcta, solo queda hacer el análisis que requieras para tus datos. Aquí te dejamos algunos ejemplos para que empieces a utilizar los datos espaciales en Python.

# Ejemplos de Análisis Espacial en Python con datos de QGIS

Este apartado muestra **ejemplos prácticos** de lo que puedes hacer una vez exportes tus datos desde QGIS a Python, ya sea en **CSV** (solo tabla) o en **SHP/GPKG** (tabla + geometría).

---

## 1. Análisis básico de tabla (con `pandas`)

Si exportaste solo la **tabla en CSV**, puedes trabajar con `pandas`:

```
import pandas as pd

df = pd.read_csv("datos.csv")

# Ver primeras filas
print(df.head())

# Conteo de registros por categoría (ejemplo: barrios)
print(df["BARRIO"].value_counts())

# Promedio de una variable (ejemplo: población)
print(df["POBLACION"].mean())
```

## 2. Visualizar mapas simples (con geopandas)
Si tienes geometría (SHP o GPKG):

```
import geopandas as gpd

gdf = gpd.read_file("mapa.gpkg")

# Dibujar todo el mapa
gdf.plot()

# Colorear por una variable (ejemplo: población)
gdf.plot(column="POBLACION", legend=True, cmap="Blues")
```

## 3. Cálculo de áreas y perímetros
Si tus datos son polígonos (ej: barrios, municipios):

```
# Cambiar proyección a metros (ej: EPSG:3116 para Colombia)
gdf = gdf.to_crs(epsg=3116)

# Calcular área y perímetro
gdf["area_m2"] = gdf.geometry.area
gdf["perimetro_m"] = gdf.geometry.length

print(gdf[["NOMBRE", "area_m2", "perimetro_m"]].head())
```

## 4. Uniones espaciales (Spatial Join)
Ejemplo: ¿cuántos puntos de colegios hay en cada barrio?

```
# Cargar barrios y colegios
barrios = gpd.read_file("barrios.gpkg")
colegios = gpd.read_file("colegios.gpkg")

# Unir puntos a polígonos
join = gpd.sjoin(colegios, barrios, how="left", predicate="within")

# Contar colegios por barrio
conteo = join.groupby("NOMBRE_BARRIO").size()
print(conteo)
```

## 5. Cálculo de distancias
Ejemplo: distancia de cada colegio al centro de un barrio.

```
from shapely.geometry import Point

# Centroide de Chapinero
centro = barrios[barrios["NOMBRE"]=="Chapinero"].geometry.centroid.values[0]

# Calcular distancia de cada colegio al centroide
colegios["distancia_m"] = colegios.geometry.distance(centro)

print(colegios[["NOMBRE", "distancia_m"]].head())
```

## 6. Mapas personalizados con Matplotlib
```
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(8,6))
barrios.plot(ax=ax, color="lightgrey", edgecolor="black")
colegios.plot(ax=ax, color="red", markersize=10)
plt.title("Colegios dentro de barrios")
plt.show()
```






