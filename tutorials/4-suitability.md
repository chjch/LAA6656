# Tutorial 4 - Suitability Analysis using ArcGIS Pro

In this tutorial, we will learn how to perform suitability analysis using the _Suitability Modeler_ in ArcGIS Pro. You will be shown an example of suitability analysis for a specific type of land use—industrial area. In general, the process introduced in this example is applicable to all types of land uses. First, let's take a look at the program's description/requirement:
> Industrial areas: 75 acres (12,075 grid cells) of new industrial land should be appropriately sited. New industrial sites are in greatest demand if they are in contiguous territories of at least 20 acres (3220 grid cells). Appropriate legend classes = 36.

## 2. The General Process of Suitability Analysis

### Step 1: Identify the criteria for the specific land use

The question you want to ask is what qualities make a given piece of land suitable for the specific type of land use you are analyzing.

1. Soil - Certain characteristics, such as high acidity, of soil are not suitable for sustaining structures.
   - Data: `Soils.shp`
   - Field: `corsteel` (susceptibility of uncoated steel to corrosion when in contact with the soil).
   - Geoprocessing: `Polygon to Raster`.
2. Flood risk - High flood risk raises serious safety concerns to industrial production.
   - Data: `Fema Flood Zones.shp` (an output from [Tutorial 2](2-vector_gis.md))
   - Field: `RISK_LEVEL`
   - Geoprocessing: `Polygon to Raster`
3. Accessibility - Proximity to major roads provides good accessibility which benefits the transportation of raw materials and manufactured products.
   - Data: `Roads.shp`
   - Field: n/a
   - Geoprocessing: `Euclidean Distance`
4. Impact to residential areas - Heavy industrial production, such as papermaking, may become a nuisance to the detriment of nearby residential areas as it degrades the air and water quality.
   - Data: `taxlot.shp` or `lulc.tif`
   - Field: `DORUC`
   - Geoprocessing: `Euclidean Distance`

### Step 2: Rescale to a common suitability scale

In this example, we will adopt a common suitability scale used in land use analysis, which is a range from 1 (lowest suitability) to 9 (highest suitability).

Rescale (transformation) Methods:

1. **Unique Categories**

    _Soil_:

    | corsteel | old value | new value |
    |----------|-----------|-----------|
    | Low      | 1         | 9         |
    | (empty)  | 2         | 1         |
    | Moderate | 3         | 7         |
    | High     | 4         | 4         |

    _Flood risk_:

    | RISK_LEVEL                 | old value | new value |
    |----------------------------|-----------|-----------|
    | HIGH RISK AREAS            | 1         | 1         |
    | MODERATE TO LOW RISK AREAS | 2         | 9         |

2. **Range of Classes** -> Impact to residential areas
    | old value  | new value |
    |------------|-----------|
    | below 500  | 1         |
    | 500-1000   | 3         |
    | 1000-1500  | 5         |
    | above 2000 | 9         |
3. **Continuous Functions** -> Accessibility

![transform_pane](images/transform_pane.png)

### Step 3: Weight criteria relative to one another

Methods to weight individual criterion:

- **Multiplier**: This method is best when you can directly weight the criteria relative to one another.
- **Percent**: This method is best when you want to indicate how much each criterion influences the resulting suitability map. Total weights for all criteria must sum to 100 percent.

### Step 4: Locate suitable areas

1. Total area: 75
2. Area units: Acres
3. Number of regions: 6
4. Region minimum area: 4
5. Region maximum area: 25
