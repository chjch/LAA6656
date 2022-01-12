# Tutorial 2 - GIS analysis for Vector Data

- [Tutorial 2 - GIS analysis for Vector Data](#tutorial-2---gis-analysis-for-vector-data)
  - [1. Vector storage formats in ArcGIS Pro](#1-vector-storage-formats-in-arcgis-pro)
  - [2. Buffer](#2-buffer)
  - [3. Clip](#3-clip)
  - [4. Selection of Features](#4-selection-of-features)
    - [4.1. Select by Location](#41-select-by-location)
    - [4.2. Select by Attributes](#42-select-by-attributes)
    - [4.3. Interactive Selection](#43-interactive-selection)
    - [4.4. Creating new feature class from selected features (Export Data)](#44-creating-new-feature-class-from-selected-features-export-data)
  - [5. Spatial Join](#5-spatial-join)
  - [6. Field Calculation](#6-field-calculation)
    - [6.1. Reclassify a Field](#61-reclassify-a-field)
    - [6.2. Calculate Geometry](#62-calculate-geometry)
    - [6.3. Calculate a new field based on other fields](#63-calculate-a-new-field-based-on-other-fields)
  - [7. Feature Class Creation and Editing in ArcGIS Pro](#7-feature-class-creation-and-editing-in-arcgis-pro)

## 1. [Vector storage formats in ArcGIS Pro](https://www.esri.com/arcgis-blog/products/arcgis-pro/data-management/using-common-gis-data-types-in-arcgis-pro/)

- **Shapefile**
  - Pros: Commonly supported by virtually every GIS software and geospatial
    programming packages (e.g., geopandas of Python).
  - Cons: large storage size, computationally expensive and **limited in field
    name length: 10 characters (a dBASE table limit)**.
- **Feature class** in a _File GeoDatabase_
  - Pros: Fast geoprocessing operation, cost less storage for the same data,
    length and area are automatically computed and stored by ```Shape_Length```
    and ```Shape_Area``` respectively.
  - Cons: Only supported by ArcGIS platform.

## 2. [Buffer](https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/buffer.htm)

- Input data: [```BusStops.shp```](../datasets/transit.md).
- Parameters:
  1. Distance: ```500 meters```.
  2. Method: ```Planar```.
  3. Dissolve Type: ```No Dissolve```.

<img vspace="5px" src="img/buffer.png">

## 3. [Clip](https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/clip.htm)

- Input data: ```MSBFP.shp``` (input feature) and _output of the buffer tool_
  (clip feature).

<img src="img/clip.png" vspace="5px">

> :warning:**A Caveat**: Should I use the _Clip_ tool?<br>
> This tool physically cut through the geometry, which may result in
> **unintended sliver polygons** if the edges of the input and clip features
> are not perfectly aligned with each other.
> Let's take a look at the output of clipping.

## 4. Selection of Features

Although this is a basic operation, selecting features based on certain
criteria is a fundamental technique in GIS analysis, which helps you better
understand the area you are interested in.
Those criteria can be either the feature's own attributes
(characteristics/qualities) or its spatial relationship with other features in
the area.

### 4.1. [Select by Location](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-by-location.htm)

- Input data: ```MSBFP.shp``` (input feature) and _output of the buffer tool_
  (selecting feature).
- [Spatial relationships](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/select-by-location-graphical-examples.htm)
  - Intersecting
  - Within (what is the difference between within and completely within?)

### 4.2. [Select by Attributes](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-using-attributes.htm)

- Input data: [taxlot.shp](../tutorials/1-software_and_data.md#property).
- Selection type:
  1. **New selection**: The resulting selection replaces the current selection.
     This is the default.
  2. **Add to the current selection**: The resulting selection is added to the
     current selection if one exists.
     If no selection exists, this is the same as the new selection option.
  3. **Remove from the current selection**: The resulting selection is removed
     from the current selection.
     If no selection exists, this option has no effect.
  4. **Select subset from the current selection**: The resulting selection is
    combined with the current selection.
    Only records that are common to both remain selected.
  5. **Switch the current selection**: The selection is switched.
     All records that were selected are removed from the current selection, and
     all records that were not selected are added to the current selection.
     The Expression parameter (where_clause in Python) is ignored when this
     option is specified.
  6. **Clear the current selection**.
- [SQL selection query](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/sql-reference-for-elements-used-in-query-expressions.htm)
  1. JV > 200000
  2. JV < 100000 AND ACTYRBLT <= 2000
- Zoom to selection (lower right corner in map)

### 4.3. [Interactive Selection](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/selection-options.htm)

- Selection combination mode
  - Add to (```Shift + Click```)
  - Remove from (```Ctrl + Click```)
  - Select from (```Ctrl + Shift + Click```)
- [Selection shape](https://pro.arcgis.com/en/pro-app/latest/help/mapping/navigation/select-features-interactively.htm#ESRI_SECTION1_EDB7A6492B3D4521B934412A3A2CFDF1)
- Selectable layer (List by Selection in the ```Content Panel```)

### 4.4. Creating new feature class from selected features (Export Data)

> :notebook_with_decorative_cover:**Note**<br>
> Geoprocessing functions only operates on selected features.

## 5. [Spatial Join](https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/spatial-join.htm)

Joins the attributes from features in another dataset based on a specified
_spatial relationship_.
**Shapes of the target features** and **attributes of the join features** will
be written to the output feature class.

- Input data: ```MSBFP.shp``` (Target feature) [taxlot.shp](../tutorials/1-software_and_data.md#property)
- Parameters:
  1. Join Operation: ```Join one to one```
  2. Match Option:  ```Within```
  3. Field Map:
      - ```"JV" -> Mean```
      - ```"ACTYRBLT" -> Minimum```
      - Remove all other fields in the join feature from the output

## 6. Field Calculation

In this section, we will see how the [_Calculating Field_](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/calculate-field.htm) tool can be used in three practical scenarios.
**_Note_**: to follow the _best practice_, we will make a copy of the original
data before we perform these operations.

### 6.1. Reclassify a Field

- Input data: [FEMA flood zone](1-software_and_data.md#critical_zones)
- Field: "FLD_ZONE"
- _Add a New Field_
  - field name: "RISK_LEVEL"
  - field type: ```Text``` (length 50)
- Value Remapping:
  | old value | new value                  |
  |:---------:|----------------------------|
  | A         | HIGH RISK AREAS            |
  | AE        | HIGH RISK AREAS            |
  | X         | MODERATE TO LOW RISK AREAS |

### 6.2. Calculate Geometry

- Input data: [Census block](../datasets/census/census.md)
- _Add a New Field_
  - field name: "AREA_ACRE"
  - field type: ```Long``` (Integer)

### 6.3. Calculate a new field based on other fields

- Input data: ```CensusBlocks_2010_cp.shp```
- Field: "TOT_POP", "AREA_ACRE"
- _Add a New Field_
  - field name: "POPDEN"
  - field type: ```Double``` (Decimal)

## 7. Feature Class Creation and [Editing in ArcGIS Pro](https://pro.arcgis.com/en/pro-app/latest/help/editing/overview-of-desktop-editing.htm)

In this section, we will create a wildlife migration corridor based on the
wetland features.
To fully demonstrate the process, we will create both a line feature class and
a polygon feature class.

1. Create an empty feature class.
2. Go to the ```Edit``` tab.
3. Digitize new feature by clicking the ```Create``` button.
4. Select the created feature class in the ```Create Features``` panel on the
   right of the map.
5. Start to digitize features (double click to complete a feature).
6. Save the edits (often) after feature created.
