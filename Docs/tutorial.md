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
