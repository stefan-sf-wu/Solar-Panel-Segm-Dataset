# Solar Panel Detection Dataset
## Reference
Dataset modified based on [*Full Collection: Distributed Solar Photovoltaic Array Location and Extent Data Set for Remote Sensing Object Identification*](https://figshare.com/collections/Full_Collection_Distributed_Solar_Photovoltaic_Array_Location_and_Extent_Data_Set_for_Remote_Sensing_Object_Identification/3255643/1).
> Earth-observing remote sensing data, including aerial photography and satellite imagery, offer a snapshot of the world from which we can learn about the state of our environment, anthropogenic systems, and natural resources. The components of energy systems that are visible from above may be assessed with these remote sensing data when combined with machine learning methods. Here we focus on the information gap in distributed solar photovoltaic (PV) arrays, of which there is limited data on solar PV deployments at small geographic scales. We created a machine learning dataset to develop the process of automatically identifying solar PV locations through the use of remote sensing imagery.\
> \
> This dataset contains the geospatial coordinates and border vertices for over 19,000 solar panels across 601 high resolution images from four cities in California. Dataset applications include training object detection and other machine learning algorithms that use remote sensing imagery, developing specific algorithms for predictive detection of distributed PV systems, and analysis of the socioeconomic correlates of PV deployment.

## Format
- Each 5000 * 5000 high-res images is tiled into 400 pieces of 250 * 250 images for training at a proper zoom level
- Zero-instance image tiles are removed from the dataset
- Annotation
  - Binary Single-channel bitmap:
    - 0: nan
    - 1: solar panel

## Dataset Link
- [Google Drive](https://drive.google.com/file/d/19xVO0yPyXLggJN8LEg31bd9ZKeNCQiBp/view?usp=share_link)
