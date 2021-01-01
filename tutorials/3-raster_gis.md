# GIS Analysis for Raster Data

## 1. What is Raster Data <img style="float: right;" src="images\rasterbands.png">

In its simplest form, a raster consists of ***a matrix of cells*** (or pixels) organized into rows and columns (or a grid) where ***each cell contains a value*** representing information, such as temperature. Raster grids can be outputs from raster analysis, digital aerial photographs, imagery from satellites, digital pictures, or even scanned maps.

### 1.1 Single band

- temperature, elevation, soil pH value, etc.

<img src="images\raster_colormap.gif">

### 1.2 Multiple bands and [RGB composite](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/renderers-used-to-display-raster-data.htm#ESRI_SECTION2_6DA80CD25C02461BBD61A752F92D2E6D)

- different wavelengths from the ultraviolet through the visible and infrared portions of the electromagnetic spectrum

<img src="images\rgb_composite.gif">

### 1.3 Comparison

|    single-band satellite image     |    3-band RGB composite satellite image    |
|------------------------------------|--------------------------------------------|
| ![grayscale](images/grayscale.png) | ![rgb_composite](images/rgb_composite.png) |

### 1.4 Fundamental [Properties of a Raster Dataset](https://pro.arcgis.com/en/pro-app/latest/help/data/imagery/raster-dataset-properties.htm)

- Spatial Reference (projection): [GCS vs. PCS](https://www.esri.com/arcgis-blog/products/arcgis-pro/mapping/coordinate-systems-difference/)
- Extent: The top, bottom, left, and right coordinates of the rectangle (boundary) containing the raster dataset.
- Cell Size: determines how detailed or coarse of the information presented by the raster dataset.

![cell_size](images/cellSize.gif)
