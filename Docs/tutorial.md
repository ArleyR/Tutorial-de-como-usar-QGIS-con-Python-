# Tutorial para usar QGIS

## Introducción 

Versión recomendada: QGIS 3.x (3.10+). Las instrucciones son aplicables a la mayoría de versiones 3.x; pequeñas diferencias de menú pueden existir.

Requisitos: QGIS instalado (Windows con OSGeo4W, macOS o Linux), datos vectoriales/raster (Shapefile, GeoPackage, GeoTIFF, GeoJSON), espacio de trabajo donde guardar salidas.

## Interfaz rápida (qué ver y para qué)

*	Panel Capas (Layers): lista de capas del proyecto.
* Panel Navegador (Browser): arrastra capas desde carpetas, GeoPackage, PostGIS.
* Proyectos: abrir/guardar proyecto, selección.
* Caja de herramientas de procesamiento (Processing Toolbox): aquí están todos los algoritmos (GDAL, GRASS, SAGA, QGIS nativos).
* Consola Python (Python Console): para scripts PyQGIS interactivos.
* Layout (Compositor de impresión): para producir mapas finales (PDF, PNG).

## Flujo de trabajo básico (pasos generales)
* Crear/abrir un proyecto: Proyecto > Nuevo o Archivo > Abrir proyecto.
* Definir CRS del proyecto: Proyecto > Propiedades del proyecto > CRS (importantísimo: trabaja en CRS apropiado para tu análisis).
* Cargar datos (vector/raster) desde Capa > Añadir capa > Añadir capa vectorial o arrastrando desde el Navegador.
* Inspeccionar atributos (abrir tabla de atributos) y geometrías.
* Diseñar mapa en Layout y exportar.

## Cómo cargar datos (GUI)
### Vector (Shapefile, GeoPackage, GeoJSON)
* Capa > Añadir capa > Añadir capa vectorial....
* Selecciona archivo (browse) o usa el Navegador y arrastra la capa.
* Revisa la tabla de atributos (clic derecho sobre la capa > Abrir tabla de atributos).
### Raster (GeoTIFF, JPEG, etc.)
* Capa > Añadir capa > Añadir capa raster....
* Selecciona el archivo TIFF/IMG.
* Si no se muestra correctamente, revisa CRS o georreferenciación.

## Reproyección y sistema de coordenadas 
* Para reproyectar una capa (guardar copia con otro CRS): clic derecho sobre la capa > Exportar > Guardar objetos como... > elegir CRS objetivo (por ejemplo, EPSG:4326 o un CRS proyectado local

## Simbología y etiquetado
•	Clic derecho sobre la capa > Propiedades > Simbología
•	Elige tipo: Simple, Graduado (para rangos), Categorized (por categorías), Rule-based (reglas complejas).
•	Para etiquetas: Etiquetado > Mostrar etiquetas > elegir campo.

## Herramientas de geoprocesamiento (GUI)
### Abre la Caja de herramientas de procesamiento (Processing Toolbox).

*	Buffer: Vector general > Buffer o native:buffer.
*	Clip (recorte): Vector overlay > Clip o native:clip.
*	Intersect / Union / Dissolve: disponibles bajo Vector > Geoprocesamiento.
*	Join attributes by location (unión espacial): native:joinattributesbylocation.

## Modeler (automatizar procesos sin programar)
*	Processing > Graphical Modeler
*	Arrastra herramientas (Buffer, Clip, Join) y conecta entradas/salidas.
*	Guarda el modelo; podrás ejecutarlo con parámetros y usarlo como herramienta.

## Guardar resultados y formatos recomendados
*	GeoPackage (.gpkg): recomendado para múltiples capas y atributos modernos.
*	GeoJSON: ideal para interoperabilidad web, pero cuidado con precisión y campos grandes.
*	Shapefile (.shp): compatibilidad, pero limitaciones: nombres de campo cortos, codificación DBF, tipos de datos limitados.
*	GeoTIFF: para ráster georreferenciado.
*	Cómo exportar (GUI): clic derecho > Exportar > Guardar objetos como... y elegir formato y CRS.

## Cartografía: crear un mapa para impresión
*	Proyecto > Nuevo diseño de impresión (o Proyecto > Layouts > Administrar diseños) > Nuevo.
*	En el diseñador: Añadir elemento > Añadir mapa y arrastra rectángulo para la vista.
*	Añade Leyenda, Escala, Norte, Título (desde Añadir elemento).
*	Ajusta etiquetado y simbología para que el mapa sea claro.
*	Layout > Exportar como PDF o Exportar como imagen.

# Tutorial para usar QGIS con PYTHON

