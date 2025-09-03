# Tutorial-de-como-usar-QGIS-con-Python-

## Introducción
Este repositorio contiene un tutorial paso a paso sobre cómo usar QGIS junto con Python para automatizar procesos, manipular capas geográficas y crear scripts personalizados dentro del entorno de QGIS.

Aprenderás a:
* Breve explicación de qué es QGIS y qué es PyQGIS.
* Qué aprenderá el usuario siguiendo el tutorial.
Desarrollar un plugin sencillo en QGIS con PyQGIS.

Requisitos previos
* Instalar y configurar QGIS.  [QGIS](https://qgis.org/download/) (versión recomendada: 3.x)
* Configurar Python.Python 3.x (viene incluido con QGIS)
* Librerías adicionales (si se usan scripts externos): "pip install geopandas rasterio pyproj"

### contenido para QGIS
1.  Introducción
2.  Interfaz rápida (qué ver y para qué)
3.  Flujo de trabajo básico (pasos generales)
4.  Cómo cargar datos (GUI)
5.  Reproyección y sistema de coordenadas
6.  Simbología y etiquetado
7.  Herramientas de geoprocesamiento (GUI)
8.  Modeler (automatizar procesos sin programar)
9.  Guardar resultados y formatos recomendados
10.  Cartografía: crear un mapa para impresión

### contenido para QGIS con Python

# Tutorial Básico: Usar archivos SHP en Python con ayuda de QGIS

Este tutorial está pensado para **principiantes totales**, que nunca han usado QGIS ni Python con datos espaciales.  
El objetivo es aprender a **abrir un archivo SHP, exportarlo y trabajarlo en Python**.

---

## Paso 1. Instalar los programas

1. **Instalar QGIS**  
   - Descarga desde: [https://qgis.org/es/site/](https://qgis.org/es/site/)  
   - Elige la versión **LTS (Long Term Support)**, más estable.  
   - Instálala como cualquier programa.

2. **Instalar Python y librerías necesarias**  
   - Descarga Python desde: [https://www.python.org/downloads/](https://www.python.org/downloads/)  
   - Una vez instalado, abre la terminal (o símbolo del sistema) y ejecuta:  

   ```bash
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
```python
import pandas as pd

# Ruta del archivo exportado
df = pd.read_csv("C:/ruta/archivo.csv")

# Visualizar las primeras filas
print(df.head())
```
