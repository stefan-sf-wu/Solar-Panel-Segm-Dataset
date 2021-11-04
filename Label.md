# How to Create a Land-type Mapping Dataset for Instance/Semantic Segmentation

## Calling WMTS service  in QGIS
For land-type mapping, **Orthophoto** or **Unmanned Aerial Vehicle images** are common materials for building such dataset. Make sure the WMTS you called has such data.

See how to import WMT/WMTS into QGIS:
* [How can I add the OGC APIs (WMS, WMTS, WCS) to my QGIS?](https://land.copernicus.eu/global/faq/how-can-i-add-ogc-apis-wms-wmts-wcs-my-qgis)
* [Working with WMS Data](https://www.qgistutorials.com/en/docs/working_with_wms.html)

A list of WMTS for Taiwan: http://gis.rchss.sinica.edu.tw/qgis/?p=3640

Note that you should have ***consistent coordinate reference system throughout the project.*** 
Click the *system description* in the bottom-right corner of QGIS to change predefined system.

You may use any system as long as you or your IT guy know how to convert produced dataset to training format for your networks. However, a general reference system, such as "WGS 84 / EPSG:4326", can accelerate the development in many ways. 

## Set up Target Area Boundary 
1. Enter **coordinates** of target area in `template.kml`, 
2. **Import** `template.kml` into QGIS as a layer by 
    * direct dragging, *or*
    * "Layer > Add Layer > Add Vector Layer," and then select the file and open it.
3. Right click on the imported layer and select **"Zoom to Layer."** You shall have an overview of your target area.
4. Double click the layer and **set the symbol to *outline's*** so that you can view the area within the boundary.
_These steps will help you identify the area you are going to work on in QGIS._

## Create a Layer for Annotations
1. Select **Layer > Creat Layer > New Shaperfile Layer**.
2. Initialize layer information
    * Name your layer
    * Geometric type: **Polygon**
    * Select the reference system **you use for your background**.
    * In "Fields List," you can predefine metedata for your layer.
    Normally, we will create a **"id"** field in integer type to hold the unique id for each polygon

## Annotating
1. Click the new shapefile layer in "Layers."
2. Click "Toggle Editing" in toolbar, and then click "Add Polygon Feature" next to it.
3. For each polygon, 
    1. **Left click to draw** the outline of object
    2. **Right click to complete** the polygon
    3. Enter corresponding metadata on the pop-up

## Export feature
1. Right click the edited layer, and go to **"Export > Save Feature As..."**
2. For "Format", select "Geojson"
3. Choose the directory you want to place the file.
4. Click "OK" and all set!

The format of output file is also dependent on how you and your IT guy would like to communicate. It might not be Geojson.
