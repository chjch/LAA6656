# Tutorial 5 - Introduction to ArcGIS Pro ModelBuilder

ArcGIS Pro [ModelBuilder](https://pro.arcgis.com/en/pro-app/latest/help/analysis/geoprocessing/modelbuilder/what-is-modelbuilder-.htm)
is a visual programming language for building _geoprocessing_ workflows.

- Build a model by [adding and connecting data and tools](https://pro.arcgis.com/en/pro-app/latest/help/analysis/geoprocessing/modelbuilder/add-connect-and-modify-data-and-tools-in-a-model.htm)
- [Iteratively](https://pro.arcgis.com/en/pro-app/latest/help/analysis/geoprocessing/modelbuilder/iterators-for-looping.htm) process every feature class, raster, file, or table in a workspace.
- Visualize your workflow sequence as an easy-to-understand diagram.
- [Run a model](https://pro.arcgis.com/en/pro-app/latest/help/analysis/geoprocessing/modelbuilder/run-a-model.htm) step-by-step, up to a selected step, or run the entire model.
- [Make your model into a geoprocessing tool](https://pro.arcgis.com/en/pro-app/latest/help/analysis/geoprocessing/modelbuilder/create-a-model-tool.htm) that can be shared or can be used in Python scripting and other models.

In this tutorial, we will go over how to use _ModelBuilder_ to create models that
(a) automates a series of _geoprocessing_ operations, and (b) document the
_geoprocessing_ workflow through two examples:
**Identifying the Region for High Residential Density Development**
and **Retention of Agriculture Land**.

## 1. Create a model in the project

- **Step 1**. Navigate to the _Toolboxes_ section in the _Catalog_ pane.
  <br><img src="images/create_model.png" vspace="5px">
- **Step 2**. Modify the model's _Name_ and _Label_ by go to the _Properties_ menu.
  <br><img src="images/mb_property.png" vspace="5px">
  - Name only supports alphanumeric characters.
  - Label is what you see in ArcGIS Pro support all characters.
- **Step 3**. Start to design the model's workflow by adding data and geoprocessing functions.

## 2. Model 1 - Identify the Region Suitable for High Residential Density

In this example, we will see how to create a ModelBuilder model that help
us identify areas that are suitable for high density residential development.
According to the fundamentals of _Location Theory_, high density tends to be associated with the central place of an urban area. Let's see how we can use
the existing data to create a process in ModelBuilder to identify what we may
call a _Central Business District_.

- Data: **taxlot.shp**
- Process: **Select Layer by Attribute** -> **Median Center** -> **Euclidean Distance** -> **Slice**

## 3. Organize and Run the Model

<img src="images/mb_tab.png" vspace="5px">

- Auto Layout and Fit To Window
- Validate
- Run individual tool vs. Run the whole model
- _Add to Display_
- Extra control in the _Diagram_ tab

## 4. New features in the ArcGIS Pro's ModelBuilder

1. Add a tool to the model by directly typing the tool's name
2. Use the **_Report_** to
    - Summarize all information about the model
    - Change a tool's or dataset's label
    - Configure individual tool's parameters <img src="images/mb_report.png" vspace="5px">

## 5. Model 2 - Retention of Agriculture Land

The _Program_ asks you to retain a minimum of 2,800 acres agriculture land in your
study area plans. According to the land use land cover raster layer, the existing total
amount of agriculture land (legend 42, 43, 44, 48, and 49) is 3,710 acres (597,325 pixels).
Thus, the task here is to find 2,800 out of the 3,710 acres of existing ag land that
are worth keeping as the status quo. Or conversely, we should find 910 acres that are
not so convincing to keep as ag land.

- Data: **soil_agcl** and **lulc2015.shp**
- Process: **Select** -> **Reclassify** -> **Zonal Statistics As Table** -> **Join Field**

## 6. Use an existing model as a tool within another model

- [Add a sub model to a model](https://pro.arcgis.com/en/pro-app/latest/help/analysis/geoprocessing/modelbuilder/add-a-submodel-to-a-model.htm)
- Use model 1 within model 2
- spatial join output of model 1 to the output of model 2
