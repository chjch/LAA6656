# GIS analysis for Vector Data

## 1. [Vector storage formats in ArcGIS Pro](https://www.esri.com/arcgis-blog/products/arcgis-pro/data-management/using-common-gis-data-types-in-arcgis-pro/)

- Shapefile
  - Pros: Commonly supported by virtually every GIS software and geospatial programming packages (e.g., geopandas of Python)
  - Cons: large storage size, computationally expensive and **limited in field name length: 10 characters (a dBASE table limit)**
- Feature class in file GeoDatabase
  - Pros: Fast geoprocessing operation, cost less storage for the same data, length and area are automatically computed and stored by ```Shape_Length``` and ```Shape_Area``` respectively.
  - Cons: Only supported by ArcGIS platform

## 1. Selection of Features

Selecting features based on certain criteria helps you better understand the area you are interested in. Those criteria can be either the feature's own attributes (characteristics/qualities) or its spatial relationship with other features in the area.

- [Select by Attributes](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-using-attributes.htm)
  - Zoom to selection
- [Select by Location](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-by-location.htm)
- [Interactive Selection](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/selection-options.htm):
  - Selection combination mode
    - Add to (```Shift + Click```)
    - Remove from (```Ctrl + Click```)
    - Select from (```Ctrl + Shift + Click```)
  - [Selection shape](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-interactively.htm#ESRI_SECTION1_EDB7A6492B3D4521B934412A3A2CFDF1)
  - Selectable layer
- Creating new feature class from selected features
  - **Note**: Geoprocessing functions only operates on selected features.

## 2. Field Calculation

Example 1 - Reclassify a value:

- Dataset: [FEMA flood zone](1-software_and_data.md#critical_zones)
- Field: FLD_ZONE

Example 2 - Calculate a new field based on other fields

- Dataset: [Census block]()

## 3. Spatial Join and Intersection

Not only selecting but joins the attributes from features in the other dataset that meet the criterion.

## 3. Buffer

- Bus stops parcels

## 4. Clip

**Caveat**: Physically cut the geometry.



## 6. Feature Class Creation and Editing

- Wildlife migration corridor (conservation) 
- 