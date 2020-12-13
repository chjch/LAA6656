# Tutorial 1 - Software setup and introduction to datasets

## 1. Install ArcGIS Pro

- **Step 1 - Download**: Follow the instruction on https://www.geoplan.ufl.edu/software/arcgis-pro/ to obtain a copy of the software. Make sure you download the latest version i.e., ArcGIS Pro 2.6. The file is located inside `AGP2.6` with a name of `ArcGISPro_26_175036.exe`.
- **Step 2 - Install**: Double-click the installation file you just downloaded from last step, follow the instructions to install the application on your computer.
- **Step 3 - Open the software**: Find the software in your start menu just as any other existing program on your computer. You can either locate it in the App list under `ArcGIS` or search for `ArcGIS Pro` using the Search button on your taskbar.
- **Step 4 - Log in**:  Follow the instruction on https://www.geoplan.ufl.edu/software/esri-login-instructions/ to login to ArcGIS Pro.

## 2. Introduction to the GIS datasets

- **Download** from this [Dropbox link](https://www.dropbox.com/s/wzigykb4zmsmmca/LAA6656DataFiles.zip?dl=0).
- Critical to be aware and acquainted with what's available.
- Identifying and acquiring useful datasets is an essential skill.
- Understanding the concepts behind different types of GIS data.
  - vector: object view (discrete)
  - raster: field view (continuous)
  - "People manipulate object but cultivate field" (Couclelis, 1992).

| Theme | ID | File Name            | Data Format | Type | Description                                               |
| - |----|----------------------|-----------|-------------|-----------------------------------------------------------|
| [Demography](../datasets/census/census.md) | 1 <br> 2 | CensusBlocks_2010_cp <br> CensusTracts_2010_cp | vector <br> vector  | polygon <br> polygon   | 2010 [Census](https://www2.census.gov/geo/pdfs/reference/geodiagram.pdf) blocks <br> 2010 Census tracts |
| [Zoning & FLU](../datasets/zoning_flu.md) | 3 <br> 4 <br> 5 | ApopkaZoning <br> Zoning_OBoundary <br> FutureLandUse | vector <br> vector <br> vector | polygon <br> polygon <br> polygon | [City of Apopka zoning ordinance](https://library.municode.com/fl/apopka/codes/code_of_ordinances?nodeId=PTIIILADECO_ART3ZODI_S3.1GEPR) <br> [Orange County zoning ordinance](https://library.municode.com/fl/orange_county/codes/code_of_ordinances?nodeId=PTIIORCOCO_CH38ZO_ARTIVZODIESZOMA) <br> [Orange County Future Land Use](https://www.orangecountyfl.net/PlanningDevelopment/ComprehensivePlanning.aspx#.X87_PGhKj-g)                                      |
| Boundaries | 6 <br> 7 <br> 8 <br> 9 | Jurisdiction <br> Oboundary_EB <br> PublicFacilities <br> PublicLand | vector <br> vector <br> vector <br> vector | polygon <br> polygon <br> polygon <br> polygon | Apopka jurisdiction map <br> Study area boundary (partitioned into three sections) <br> Orange county roads, drainage, water/waste reclaimation <br> Public land (federal, state, county, municipal, etc.) |
| Critical Zones  | 10 <br> 11 <br> 12 <br> 13 | Conservation <br> Fema Flood Zones_clp <br> histUndBus <br> wetlands | vector <br> vector <br> vector <br> vector | polygon <br> polygon <br> polygon <br> polygon | Conservation lands <br> FEMA flood zones <br> Historically underutilized business zones <br> National wetland inventory                                      |
| [Transit](../datasets/transit.md) | 14 <br> 15 | BusRoutes <br> BusStops           | vector <br> vector   | line <br> point       | Bus routes ([LYNX](https://www.golynx.com/corporate-info/facts-glance.stml) data) <br> Bus stops (LYNX data) |
| Transport | 16 <br> 17 | rail <br> Roads | vector <br> vector | line <br> line | Railway <br> State and county roads |
| [Property Parcels]((https://colab.research.google.com/drive/1uxxKyKYX3QXKmEhCsXfnbMc2WVoO98kc)) | 18 | [taxlot] | vector | polygon | [FGDL](https://www.fgdl.org/metadataexplorer/full_metadata.jsp?docId=%7B147B34F0-9E64-49AE-8B7F-5C4999BEC541%7D&loggedIn=false) Property parcel |
| [LULC] | 19 <br> 20 | LULC_2015 <br> CLC_LULC | raster <br> vector    | grid <br> polygon | Land Use Land Cover ca. 2015 <br> Conservation Land Commission Land Use Land Cover |
| [Soils](../datasets/soils.md) | 21 <br> 22 <br> 23 <br> 24 | Soils <br> soil_agcl <br> soil_hgrp <br> soil_wt | vector <br> raster <br> raster <br> raster | polygon <br> grid <br> grid <br> grid | [SSURGO](https://www.nrcs.usda.gov/wps/portal/nrcs/detail/soils/survey/?cid=nrcs142p2_053627) soil polygons <br> Non-irrigated land capability class <br> Depth to bedrock (inches, classed) <br> Depth to water table (feet, classed)     |
| [DEM] | 25 <br> 26 <br> 27 <br> 28 <br> 29 | grdn29w_clip <br> elevation_ft <br> aspect <br> hillshade <br> slope_ps | raster <br> raster <br> raster <br> raster <br> raster | grid <br> grid <br> tiff <br> grid <br> grid | Elevation 10m DEM <br> Elevation 10m DEM (in feet) <br> Aspect in degrees <br> Hillshade (azimuth 315, altitude 45) <br> Slope (percent rise)  |
| Aerial Photo | 30 | orthoNAIP      | raster    | .tif        | 2015 NAIP aerial photo             |

## 3. Create an ArcGIS Pro project

- 