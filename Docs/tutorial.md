# Tutorial para usar QGIS

## Introducción 

QGIS (Quantum GIS) es un software libre y de código abierto diseñado para trabajar con información geográfica. Con él es posible visualizar, analizar y editar datos espaciales en diferentes formatos, así como crear mapas personalizados. Su uso abarca múltiples áreas como la planificación urbana, el medio ambiente, la ingeniería, la agricultura y la gestión territorial.

Una de las grandes ventajas de QGIS es que incorpora Python como lenguaje de programación a través de su API llamada PyQGIS. Esto permite automatizar procesos, manipular datos de manera más eficiente y crear scripts que simplifican tareas repetitivas dentro del entorno de QGIS.

Además, gracias a Python es posible desarrollar plugins personalizados que amplían las capacidades del software y lo adaptan a necesidades específicas. En conjunto, QGIS y Python ofrecen una herramienta potente y flexible para el trabajo con datos espaciales, tanto para principiantes como para usuarios avanzados.

#### Requisitos:
Versión recomendada: QGIS 3.x (3.10+). Las instrucciones son aplicables a la mayoría de versiones 3.x; pequeñas diferencias de menú pueden existir.
QGIS instalado (Windows con OSGeo4W, macOS o Linux), datos vectoriales/raster (Shapefile, GeoPackage, GeoTIFF, GeoJSON), espacio de trabajo donde guardar salidas.

## Paso a paso para la creación de un proyecto Proyecto
### Paso 1 Configurar QGIS para Colombia Bogotá
1.	Abrir la aplicación QGIS
2.	Ir a Proyecto, → Propiedades → SRC 
3.	En la opción Filtrar, escribe EPSG:3116 – MAGNA-SIRGAS / Colombia Bogotá zone. Selecciónalo, luego haz clic en Aplicar y después en Aceptar.

<img width="678" height="495" alt="image" src="https://github.com/user-attachments/assets/f01b27c4-6141-4b3b-ad00-964af70d78f6" />

4.	Luego Vuelve al menú Proyecto y selecciona Guardar como…. Escribe un nombre para tu proyecto (ejemplo: Mapa_Bogotá) y asegúrate de guardarlo en formato .qgz (formato de QGIS).

###  PASO 2 Descarga los mapas vectoriales 
Opción A: Descargar los datos desde Mapas Bogotá
1.	Ir al navegador web
2.	Ir a la página: [Mapas Bogotá](https://mapas.bogota.gov.co/#)  
3.	En el portal de Mapas Bogotá, selecciona la opción Ver datos (puedes elegir por Temática o por Sector).
4.	Haz clic en Más información en el conjunto de datos que quieras descargar; esto te llevará al portal de Datos Abiertos de Bogotá.

.<img width="578" height="395" alt="image" src="https://github.com/user-attachments/assets/2b802948-c731-4f85-b34d-8a4d7b449262" />

5.	En el listado de formatos disponibles, busca el archivo Shapefile (.shp), selecciona Exportar y luego haz clic en Descargar.
6.	Y Repite este mismo procedimiento con las demás bases que necesites de Mapas Bogotá.
7.	En caso de que prefieras descargar directamente desde el portal de Datos Abiertos de Bogotá, busca la temática que te interese, selecciona la base correspondiente y asegúrate de que tenga el formato Shapefile (.shp). Luego sigue el mismo proceso explicado en los pasos anteriores para exportar y descargar.

### Opción B: Descargar las bases de Localidades y UPZ desde el Laboratorio Urbano de Bogotá
1.	Ir al navegador web
2.	Para descargar las Localidades, ingresa a: [Localidades](https://bogota-laburbano.opendatasoft.com/explore/dataset/poligonos-localidades/table/)
3.	Para descargar las UPZ, ingresa a: [UPZ](https://bogota-laburbano.opendatasoft.com/explore/dataset/upz-bogota/table/)
4.	En cada página, selecciona la opción Exportar.
5.	Descarga los archivos en formato Shapefile (.shp).



## PASO 3 Verificación de la carga de los datos
1.	 Arrastra los archivos descargados al panel de capas de QGIS; allí podrás verlos cargados en el proyecto.

<img width="780" height="408" alt="image" src="https://github.com/user-attachments/assets/db35f3e3-0081-4a30-8055-bc4c80a73b93" />

2.	Haz clic derecho sobre una capa para acceder a sus opciones: abrir la tabla de atributos, duplicar la capa, cambiar el nombre, o ver y modificar el SRC de la capa, entre otras.

<img width="303" height="352" alt="image" src="https://github.com/user-attachments/assets/929a2e94-8db5-477e-9061-03b75baae1cd" />


3.	Verifica que las capas tengan asignado el sistema de coordenadas EPSG:3116 – MAGNA-SIRGAS / Colombia Bogotá zone. Si no lo tienen, corrígelo: ve a Exportar → Guardar como…, asigna un nombre al archivo (preferiblemente el mismo nombre original) y selecciona el SRC correcto (EPSG:3116).

<img width="347" height="389" alt="image" src="https://github.com/user-attachments/assets/35eee38f-9440-49d1-a8bd-30bc1582fcf7" />

4.	Una vez hecho esto, deberías visualizar correctamente el mapa de Bogotá en la pantalla de QGIS.

<img width="398" height="353" alt="image" src="https://github.com/user-attachments/assets/a8aee186-34e5-431e-b8d5-b7a37a816210" />


### Otra forma de cargar los datos:
1.	En QGIS, ve al menú Capa → Añadir capa → Añadir capa vectorial.

<img width="873" height="444" alt="image" src="https://github.com/user-attachments/assets/5bb1fda6-1281-4973-98f5-64b9297242de" />

2.	En la sección Fuente, haz clic en los tres puntos (…) y navega hasta la carpeta donde guardaste tus capas

<img width="870" height="550" alt="image" src="https://github.com/user-attachments/assets/0c024a73-a3f6-4bd6-b88a-a0f7d77b45a2" />

3.	Selecciona los archivos y haz clic en Añadir; las capas deberían aparecer en el panel de capas de QGIS


## PASO 4 CONFIGURACIÓN DE COLORES 
1.	 Haz clic derecho sobre la capa y selecciona Propiedades.

<img width="450" height="460" alt="image" src="https://github.com/user-attachments/assets/b40b4853-4c78-48dc-a599-2e28b772b7fd" />

2.	En la ventana que se abre, ubícate en la pestaña Simbología.

<img width="535" height="415" alt="image" src="https://github.com/user-attachments/assets/cf1b566b-4182-4855-953e-048a119aa2ed" />

3.	Selecciona el Marcador simple y allí podrás cambiar el tamaño, el color de relleno, el estilo de la marca y otros parámetros de visualización.
4.	En la parte superior de la ventana de Simbología, aparece un cuadro con el nombre Símbolo único. Desde allí puedes cambiar el tipo de simbología (por ejemplo: categorías, graduado, etc.), lo que permite representar la información de manera más detallada.

<img width="836" height="232" alt="image" src="https://github.com/user-attachments/assets/18017830-a364-4c7d-a0d9-6628422f658e" />

5.	Finalmente, haz clic en Aplicar y luego en Aceptar para guardar los cambios.
6.	Repite este proceso con las demás capas para que todas tengan una visualización clara y coherente.

## PASO 5: Uso de Herramientas Vectoriales
1.	En el menú superior de QGIS, haz clic en Vectorial. Allí encontrarás varias carpetas de herramientas que te permiten analizar y transformar tus datos

<img width="347" height="258" alt="image" src="https://github.com/user-attachments/assets/02f2d7bb-4758-4050-87e2-3a2deb02b799" />

A continuación, una breve explicación de cada grupo:
   * Analysis Tools: Son herramientas de análisis de datos espaciales, como las que ya vimos (estadísticas básicas, contar puntos en           polígonos, matriz de distancias, etc.

     <img width="609" height="266" alt="image" src="https://github.com/user-attachments/assets/f02f7eff-f8fc-4005-89cc-77cac47860b1" />

   * Geoprocessing Tools: Son operaciones geométricas que se hacen sobre polígonos, líneas o puntos.
     Incluyen: Buffer, Intersección, Unión, Diferencia, Cortar, etc.

     <img width="592" height="296" alt="image" src="https://github.com/user-attachments/assets/c3764c45-295d-4cb7-ab88-50f0552f8f61" />

   * Geometry Tools: Permite hacer análisis y ediciones geométricas más específicas: calcular centroides, extraer vértices, convertir          geometrías, calcular áreas o longitudes.

     <img width="447" height="332" alt="image" src="https://github.com/user-attachments/assets/1389ace1-e048-4b71-8a9e-e89a35fd6186" />

   * Research Tools: Son herramientas de exploración: seleccionar por ubicación, localizar por atributo, buscar vecinos más cercanos,etc.
     
     <img width="513" height="370" alt="image" src="https://github.com/user-attachments/assets/00eef671-4798-4f8e-a7b3-88454fe2c293" />

   * Data Management Tools: Se enfocan en la gestión de capas: unir tablas, dividir una capa por atributos, exportar campos, convertir         formatos, etc.
     
     <img width="586" height="286" alt="image" src="https://github.com/user-attachments/assets/f0c780f4-5282-4561-9cf1-6beeb8002896" />

2.	Estas herramientas te permiten analizar y transformar tus datos vectoriales de manera sencilla.
3.	Cuando realices una operación con estas herramientas (como unir capas, contar puntos en un polígono, calcular distancias, etc.), QGIS genera automáticamente una nueva capa de resultados.
4.	Es recomendable renombrar estas capas para identificarlas fácilmente y evitar confusiones con las capas originales. De lo contrario, podrías perder el rastro de qué operación realizaste en cada capa.
5.	Es recomendable guardar las capas de resultados para no perder la información. Para hacerlo, puedes guiarte con el procedimiento explicado en el Paso 3, parte 3 (Exportar → Guardar como objeto). 

<img width="1082" height="559" alt="image" src="https://github.com/user-attachments/assets/32e9f3af-3faa-437a-8afe-300e57a6640d" />

    #Como puedes ver, al lado de la capa combinada aparece un cuadro pequeño. Esto significa que los resultados están cargados, pero solo de forma temporal. Si cierras la aplicación, esa información se perderá. Por eso es recomendable guardar la capa siguiendo lo explicado en el Paso 5, parte 5.

## Paso 6: visualización de graficas 
1.	Ve al menú Complementos y selecciona Administrar e instalar complementos.

<img width="921" height="108" alt="image" src="https://github.com/user-attachments/assets/12bac589-31b1-42e1-9610-a31926096c11" />

2.	En el buscador escribe DataPlotly, instálalo y, cuando termine, haz clic en Cerrar.

<img width="921" height="718" alt="image" src="https://github.com/user-attachments/assets/5f14e6e2-1fff-405c-ac61-8af59e47a93a" />

3.	En la barra de herramientas, ubica el ícono de DataPlotly (al lado de la consola de Python) y haz clic en él.

<img width="921" height="101" alt="image" src="https://github.com/user-attachments/assets/450f41f1-602e-4d7a-bd85-f070be35a8e8" />

4.	Se abrirá la ventana del complemento

 <img width="677" height="667" alt="image" src="https://github.com/user-attachments/assets/c3d79fa8-f4cd-4329-b2d9-9487c3130617" />

5.	En el ícono con forma de escoba, selecciona la capa vectorial que quieras graficar. Después elige el campo para el eje X (por ejemplo, “Localidad”) y el campo para el eje Y (por ejemplo, “Población”).

<img width="583" height="536" alt="image" src="https://github.com/user-attachments/assets/54b11135-7303-46aa-a56c-a2637e39a49e" />

6.	Escoge el tipo de gráfico: barras, dispersión, histograma, pastel, entre otros. También puedes personalizar colores, títulos y etiquetas.
7.	Haz clic en Crear diagrama y verás el gráfico en pantalla

<img width="814" height="756" alt="image" src="https://github.com/user-attachments/assets/0f2add2e-9d3f-45de-bb35-6e7864dd8425" />

8.	Si necesitas usarlo en informes o presentaciones, guárdalo con el ícono de Exportar, eligiendo el formato de imagen (.png o .jpg).


## Paso 7   instalar el complemento QuickMapServices

1.	Ve al menú Complementos y selecciona Administrar e instalar complementos
2.	En la pestaña Todos, escribe en el buscador QuickMapServices.
3.	Selecciona el complemento y haz clic en Instalar complemento.
4.	Una vez finalizada la instalación, haz clic en Cerrar para salir de la ventana.

  Ahora agregar mapa:
  1.	En el menú superior, ve a Web → QuickMapServices → Settings.

  <img width="733" height="913" alt="image" src="https://github.com/user-attachments/assets/cd3ba0b6-0c32-4908-b0f1-5c800a99173b" />

  2.	En la pestaña More services, haz clic en Get contributed pack para activar más proveedores de mapas.
  
  <img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/5606ba75-14ca-46eb-a78d-c37087eb3da3" />

  3.	Cierra la ventana de configuración.
  4.	Ahora dirígete a Web → QuickMapServices → Google → Google Satellite Hybrid para cargar el mapa satelital.

  <p align="center">
  <img src="https://github.com/user-attachments/assets/068b94ef-1c2a-4791-8845-89998a9236bd" alt="Imagen 1" style="width:600px; height:400px; object-fit:cover; margin-right:15px;" />
  <img src="https://github.com/user-attachments/assets/1aad1605-b09e-4321-b853-e3991564865f" alt="Imagen 2" style="width:600px; height:400px; object-fit:cover;" />
  </p>


  5.	Si necesitas ajustar la transparencia, haz clic derecho sobre la capa, selecciona Propiedades, entra a la opción Transparencia y          configúrala entre 70–80% para visualizar        mejor tus capas vectoriales.

  Añadir Límites:
  1.	Web → QuickMapServices → OSM → OSM Standard
     <img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/0dd8f712-75c5-42ae-b9aa-f65916225969" />

Paso 8 Crear un mapa para impresión
1.	En el menú, haz clic en Propiedades y selecciona Nueva composición de impresión.
2.	Asigna un nombre a tu mapa para identificarlo fácilmente

<img width="577" height="278" alt="image" src="https://github.com/user-attachments/assets/034d4f94-b816-49e9-9ff9-f8d3b8ed595e" />

3.	En el menú de la composición, dirígete a Añadir elementos.
4.	Allí encontrarás opciones como añadir mapa, imágenes, etiquetas, flecha del norte, escala, entre otros. También puedes ver estas herramientas en la parte izquierda de la pantalla.

<img width="847" height="476" alt="image" src="https://github.com/user-attachments/assets/d85cbf1f-7ccb-4762-af74-772710942a64" />

5.	Para agregar un título, selecciona Añadir etiqueta. Desde ahí puedes escribir el nombre del mapa, además de cambiar el color, tipo de letra y tamaño del texto.

<img width="506" height="630" alt="image" src="https://github.com/user-attachments/assets/6e8a3dbe-74cc-4c95-beaf-e7da169586f0" />

6.	Una vez añadidos todos los elementos, tu mapa quedará listo para impresión

<img width="921" height="471" alt="image" src="https://github.com/user-attachments/assets/4c367a21-45f9-4c1b-98b7-99c62e463cc5" />

7.	Finalmente, en el menú selecciona Exportar a PDF, haz clic y guarda tu mapa en tu computador. 


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






