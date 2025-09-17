# Tutorial-de-como-usar-QGIS-con-Python-

## Introducción
Este repositorio presenta un informe y analiza el contenido del tutorial de QGIS, un software libre de sistemas de información geográfica (SIG). QGIS permite visualizar, editar y analizar datos espaciales, siendo una herramienta clave en proyectos de cartografía, análisis territorial y gestión de información geográfica.

El tutorial se centra en un caso práctico para la ciudad de  Bogotá, utilizando datos oficiales disponibles en plataformas abiertas de la ciudad.

## 1. Requisitos previos
* Instalar y configurar QGIS.  [QGIS](https://qgis.org/download/) (versión recomendada: 3.x)
* Configurar Python.Python 3.x (viene incluido con QGIS)
* Librerías adicionales (si se usan scripts externos): "pip install geopandas rasterio pyproj"


## 2. Objetivos del Tutorial
* Introducir a los usuarios en el manejo básico de QGIS.
* Enseñar la carga y configuración de archivos vectoriales en formato Shapefile (.shp).
* Configurar el sistema de referencia de coordenadas de Colombia (EPSG:3116 – MAGNA-SIRGAS / Bogotá zone).
* Aplicar simbología personalizada para mejorar la visualización.
* Utilizar herramientas vectoriales básicas para análisis.
* Incorporar complementos como DataPlotly y QuickMapServices.
* Diseñar un mapa final y exportarlo en formato PDF.

## 3. Contenido del Tutorial  

Vectorial :
   0.1 Preparación del Proyecto

   0.2 Descarga de Mapas Vectoriales

   0.3 Carga y Verificación de Datos

   0.4 Configuración de Simbología

   0.5 Herramientas Vectoriales

   0.6 Visualización de Gráficas

   0.7 Complemento QuickMapServices

   0.8 Diseño de Mapas para Impresión
Ráster:
   0.1 Carga de un mapa de coberturas de MapBiomas Colombia (formato .tif).

   0.2 Configuración de simbología y asignación de colores por tipo de cobertura usando códigos HTML.

   0.3 Análisis básico mediante histogramas y estadísticas generales.

   0.4 Cálculo de área por clase de cobertura con la herramienta Raster layer unique values report.

   0.5 Complemento QuickMapServices para añadir mapas de fondo y límites administrativos.

   0.6 Preparación del mapa final para impresión con leyenda, título, escala y elementos cartográficos.


## 4. Resultados 

El tutorial permitió construir mapas temáticos de Bogotá tanto con información vectorial como con datos ráster. Se lograron representaciones claras con colores personalizados para diferentes coberturas, análisis de atributos con tablas y gráficos, y cálculos de áreas a partir de datos ráster. Finalmente, se generaron mapas listos para impresión y presentación, evidenciando la aplicabilidad de QGIS en proyectos de análisis territorial y planificación urbana..

## 5. Conclusiones
Este tutorial mostró cómo usar QGIS para trabajar con datos vectoriales y ráster, desde la carga y personalización de capas hasta el análisis espacial y la creación de mapas listos para impresión. La experiencia evidencia que QGIS es una herramienta práctica y versátil para visualizar, analizar y comunicar información geográfica de manera clara y profesional.

## Paso 1. Instalar los programas (Links ya mostrados)

1. **Instalar QGIS**  
   [https://qgis.org/es/site/](https://qgis.org/es/site/)  

2. **Instalar Python y librerías necesarias**
   [https://www.python.org/downloads/](https://www.python.org/downloads/)  

## Paso 2. Utilización de QGIS

Con los pasos mostrados en la primera fase, tendrás los conosimientos necesarios para pasar los datos de **QGIS* a **Python*

## Paso 3 Lectura de los datos en Python

Una vez exportados los datos desde QGIS, se pueden cargar en Python.

## Paso 4 Trabajar con los datos a tu gusto

Con los datos ya en Python puedes utilizarlos para el análisis de tu interés!

---

La información completa del tutorial se encuentra en la carpeta DOC, bajo el archivo denominado *tutorial.md*, junto con las carpetas que contienen los datos utilizados para la elaboración del mapa.
