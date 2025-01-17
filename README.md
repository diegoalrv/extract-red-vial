# Extracción de Redes Viales desde OpenStreetMap

Este proyecto permite descargar redes viales de un lugar determinado utilizando la librería [OSMnx](https://osmnx.readthedocs.io/). El script convierte las redes obtenidas a formato Shapefile, adecuado para su uso en herramientas GIS. Además, genera un archivo comprimido que contiene los nodos y aristas extraídos.

## Características

- Descarga redes viales para un tipo de transporte específico (peatonal, vehículos, etc.) desde OpenStreetMap.
- Convierte la red vial a GeoDataFrames y las exporta como archivos Shapefile.
- Comprime los archivos de salida para facilitar su distribución.

## Requisitos

Este proyecto requiere Python y las siguientes dependencias:

- `osmnx`
- `geopandas`
- `shapely`
- `pandas`

Puedes instalar las dependencias con:

```bash
pip install osmnx geopandas shapely pandas
```

## Estructura del Proyecto

- `extract_network.ipynb`: El script principal para extraer la red vial.
- `data/`: Carpeta donde se guardan los archivos generados.

## Uso

1. **Configura el nombre del lugar y tipo de red**

   En el notebook, modifica la variable `place_name` con el lugar que deseas analizar y la variable `network_type` con el tipo de red vial que necesitas (`walk`, `drive`, etc.).

   ```python
   place_name = "Talcahuano, Chile"
   network_type = "walk"
   ```

2. **Ejecuta el script**

   Abre el archivo `extract_network.ipynb` en Jupyter Notebook o JupyterLab y ejecuta las celdas en orden. Esto:
   
   - Descargará la red vial del lugar especificado.
   - Convertirá la red a formato Shapefile.
   - Comprimirá los resultados en un archivo `.zip`.

3. **Resultados**

   Los archivos generados se guardarán en una carpeta dentro de `data/` con el siguiente formato:

   ```
   data/
     talcahuano/
       walk/
         nodes.shp
         edges.shp
         talcahuano_walk.zip
   ```

   - `nodes.shp`: Contiene los nodos de la red.
   - `edges.shp`: Contiene las aristas de la red.
   - `talcahuano_walk.zip`: Archivo comprimido con todos los datos generados.

## Ejemplo

Para Talcahuano, Chile, y redes peatonales, el script descargará los datos de OpenStreetMap y guardará los resultados en `data/talcahuano/walk/`.
