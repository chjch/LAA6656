# Tutorial 1 - Software setup and introduction to datasets

## 1. Install ArcGIS Pro

- **Step 1 - Download**: Follow the instruction on https://www.geoplan.ufl.edu/software/arcgis-pro/ to obtain a copy of the software. Make sure you download the latest version i.e., ArcGIS Pro 2.6. The file is located inside `AGP2.6` with a name of `ArcGISPro_26_175036.exe`.
- **Step 2 - Install**: Double-click the installation file you just downloaded from last step, follow the instructions to install the application on your computer.
- **Step 3 - Open the software**: Find the software in your start menu just as any other existing program on your computer. You can either locate it in the App list under `ArcGIS` or search for `ArcGIS Pro` using the Search button on your taskbar.
- **Step 4 - Log in**:  Follow the instruction on https://www.geoplan.ufl.edu/software/esri-login-instructions/ to login to ArcGIS Pro.

## 2. Introduction to the GIS datasets

- Critical to be aware and acquainted with what's available.
- Identifying and acquiring useful datasets is an essential skill.
- Understanding the concepts behind different types of GIS data.
  - vector: object view (discrete)
  - raster: field view (continuous)
  - "People manipulate object but cultivate field" (Couclelis, 1992).

| ID | File Name            | Data Type | Data Format | Description                                               |
|----|----------------------|-----------|-------------|-----------------------------------------------------------|
| 1  | ApopkaZoning         | vector    | polygon     | Apopka city zoning                                        |
| 2  | BusRoutes            | vector    | line        | Bus routes (LYNX data)                                    |
| 3  | BusStops             | vector    | point       | Bus stops (LYNX data)                                     |
| 4  | CensusBlocks_2010_cp | vector    | polygon     | 2010 Census block groups                                  |
| 5  | CensusTracts_2010_cp | vector    | polygon     | 2010 Census tracts                                        |
| 6  | CLC_LULC             | vector    | polygon     | Conservation Land Commission Land Use Land Cover          |
| 7  | Conservation         | vector    | polygon     | Conservation lands                                        |
| 8  | Fema Flood Zones_clp | vector    | polygon     | FEMA flood zones                                          |
| 9  | FutureLandUse        | vector    | polygon     | Future land use                                           |
| 10 | histUndBus           | vector    | polygon     | Historically underutilized business zones                 |
| 11 | Jurisdiction         | vector    | polygon     | Apopka jurisdiction map                                   |
| 12 | Oboundary_EB         | vector    | polygon     | Study area boundary                                       |
| 13 | PublicFacilities     | vector    | polygon     | Orange county roads , drainage, water/waste reclaimation  |
| 14 | PublicLand           | vector    | polygon     | Public land (federal, state, county, municipal, etc.)     |
| 15 | rail                 | vector    | line        | Railway                                                   |
| 16 | Roads                | vector    | line        | State and county roads                                    |
| 17 | Soils                | vector    | polygon     | SSURGO soil polygons                                      |
| 18 | taxlot               | vector    | polygon     | State tax parcel                                          |
| 19 | wetlands             | vector    | polygon     | National wetland inventory                                |
| 20 | Zoning_Oboundary     | vector    | polygon     | Orange county zoning                                      |
| 21 | aspect               | raster    | .tif        | Aspect in degrees                                         |
| 22 | elevation_ft         | raster    | grid        | Elevation 10m DEM in feet                                 |
| 23 | grdn29w_clip         | raster    | grid        | Elevation 10m DEM                                         |
| 24 | hillshade            | raster    | grid        | Hillshade derived from 10m DEM (azimuth 315, altitude 45) |
| 25 | LULC_2015            | raster    | grid        | Land Use Land Cover ca. 2015                              |
| 26 | orthoNAIP            | raster    | .tif        | 2015 NAIP aerial photo                                    |
| 27 | slope_ps             | raster    | grid        | Slope (percent rise)                                      |
| 28 | soil_agcl            | raster    | grid        | Non-irrigated land capability class                       |
| 29 | soil_hgrp            | raster    | grid        | Depth to bedrock (inches, classed)                        |
| 30 | soil_wt              | raster    | grid        | Depth to water table (feet, classed)                      |

## 3. Create an ArcGIS Pro project

- 