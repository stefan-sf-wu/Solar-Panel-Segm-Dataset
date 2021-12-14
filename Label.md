# Create a Land-type Mapping Dataset for Instance/Semantic Segmentation using QGIS

## Calling WMTS service  in QGIS
For land-type mapping, **Orthophoto** or **Unmanned Aerial Vehicle images** are common materials for building such dataset. Make sure the WMTS you called has such data.

See how to import WMTS into QGIS:
* [How can I add the OGC APIs (WMS, WMTS, WCS) to my QGIS?](https://land.copernicus.eu/global/faq/how-can-i-add-ogc-apis-wms-wmts-wcs-my-qgis)
* [Working with WMS Data](https://www.qgistutorials.com/en/docs/working_with_wms.html)


Currently, Center for GIS uses "正射影像圖(通用)" from Nation Land Survey Center's WMTS for most on-going projects. A list of WMT channels of Taiwan can be found [here](http://gis.rchss.sinica.edu.tw/qgis/?p=3640).

**Note that you should have consistent coordinate reference system throughout the project.** Click the *system description* in the bottom-right corner of QGIS to change predefined system.

> You may use any system as long as you or your IT guy know how to convert produced dataset to training format for your networks. However, a general reference system, such as "WGS 84 / EPSG:4326", can accelerate the development in many ways. 

## Set up Target Area Boundary 
1. Enter **coordinates** of target area in `template.kml`. Note that: 
    * Coordinates should be listed **in clockwise order**.
    * Coordinates should form **a close graph**.\
    That is, the *first* set of coordinates and the *last* set of coordinates should point to the same spot. In other words, you will need 5 set of coordinates to describe a rectangular area.
    
2. Import `template.kml` into QGIS as a layer by 
    * direct dragging, *or*
    * "Layer > Add Layer > Add Vector Layer," and then select the file and open it.
3. Right click on the imported layer and select "Zoom to Layer." You shall have an overview of your target area.
4. Double click the layer and **set the symbol to *outline's*** so that you can view the area within the boundary.
> These steps are not necessary, but it will help you identify the area you are going to work on in QGIS.

## Create a Layer for Annotations
1. Select Layer > Creat Layer > **New Shaperfile Layer**.
2. Initialize layer information
    * Name your layer
    * Geometric type: *Polygon*
    * Select the reference system you use for WMT.
    * In "Fields List," you can predefine metedata for your layer.
    Normally, we will create a field *"id"*  in integer type to hold the unique id for each polygon

## Annotating
1. Click the new shapefile layer in "Layers."
2. Click "Toggle Editing" in toolbar, and then click "Add Polygon Feature" next to it.
3. For each polygon, 
    1. **Left click to draw** the outline of object
    2. **Right click to complete** the polygon
    3. Enter corresponding metadata on the pop-up
4. Remember to click **"Save Layer Edits"** to write polygons to the layer.

## Export feature
1. Right click the edited layer, and go to "Export > Save Feature As..."
2. For "Format", select "GeoJSON"
3. Choose the directory you want to store the file.
4. Click "OK." All set!

    > Again, the format of output file is also dependent on how you and your IT guy would like to communicate. It does not necessarily be a GeoJSON file.
