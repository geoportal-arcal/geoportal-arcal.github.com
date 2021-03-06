---
layout: post
category : QGIS
tags : [desktop GIS, vector layer]
---

### 1. Creating a vector layer through selection
We want in that tutorial create a new vector layer from an existing layer by selecting a subset of features.
We will create here a "Latin America" vector layer from an existing vector layer showing world countries.

File to be used in that tutorial is:

    /dss_course_dataset/qgis/1-basics/ne_10m_admin_0_countries.shp (world countries)

See video tutorial either on your local copy or on YouTube [QGIS-Vector Layer Creation Through Selection](http://www.youtube.com/watch?v=NhSmy5IcxOw&feature=player_detailpage) 

### 2. Creating a vector layer from a ".csv" file embedding geographic coordinates
".csv" file stands for "Comma Separated Value". This is a very simple way to store tabular data.
For instance, let's say we want to store measurements of cesium 137 and their relative geographic coordinates. Such ".csv' file could look like:

    latitude,longitude,cesium_137
    -33.56367896,-66.09190450,1020.32085461
    -33.56322856,-66.09191961,1007.48943394
    -33.56277816,-66.09193472,797.48331174
    -33.56232777,-66.09194983,708.29986021
    -33.56187737,-66.09196494,667.05923843
    -33.56366630,-66.09136651,1165.35554756
    -33.56321591,-66.09138162,895.07829585
    -33.56276551,-66.09139673,772.21839713
    
where different columns are separated by commas, first row defining fields name and followinf rows different measurements.

**Note**: *The software Notepad++ (installation is detailed in website at /Tutorials/GoogleEarth/GoogleEarth installations) is perfectly suited for management of such files.*

In this tutorial, we will import a ".csv" file embedding geographic coordinates into QGIS.

File to be used is:

    /dss_course_dataset/qgis/3-creating_vector_layers/grid_Cs.csv (measurements of Cesium137, its error, estimated soil_loss)

**IMPORTANT**
When importing a ".csv" file, a 'companion' file needs to be systematically created in order to specify the data type of each individual field. In our case, we have a ".csv" file we want to import whose name is "grid_Cs.csv" with the following content:

    utm_east,utm_north,latitude,longitude,ada_cs,delta_ada_cs,soil_loss
    769969.00000000,6282433.00000000,-33.56367896,-66.09190450,1020.32085461,102.03208546,-139.03743393
    769969.00000000,6282435.00000000,-33.56322856,-66.09191961,1007.48943394,100.74894339,-148.96650945
    etc ...

Then we need to create another file with similar name but different extention "grid_Cs.csvt", the final "t" of the file extension standing for type. Refer to the website tutorial in /Tutorials/Basics/Data Types for further information on data types.

Types available are:
* **"Integer"**
* **"Real"**
* **"String"**

We can even further detail type declaration by specifying sizes:
* **"Integer(5)"**
* **"Real(2)"**
* **"String(254)"**

In our case, we have seven fields whose type is "real" so the content of "grid_Cs.csvt" file wil be:

    "Real","Real","Real","Real","Real","Real","Real"

Note that "grid_Cs.csvt" must be placed in the same folder as "grid_Cs.csv" file.

**So, now let's import it in QGIS!**
See video tutorial either on your local copy or on YouTube [QGIS-Import CSV file](http://www.youtube.com/watch?feature=player_detailpage&v=nKXQS0Z7-B0)

### 3. Creating a new calculated field in an exisiting vector layer
In that tutorial, based on the layer we have just created (by importing csv file), we would like to add a new field showing the relative error of cesium measurement. Indeed, in the csv file imported, we had a column showing Cesium 137 measurements, and absolute measurements errors. Here, we would like to add (calculate a new field) showing the relativer error measurement of Cesium 137.

File to be used in that tutorial is:

    /dss_course_dataset/qgis/3-creating_vector_layers/grid_Cesium.shp (the one you have just created by importing the CSV file)

See video tutorial either on your local copy or on YouTube [QGIS-Adding Calculated Field](http://www.youtube.com/watch?feature=player_detailpage&v=2eREApVNAx0)

    
### 4. Creating a new vector layer through digitizing

Digitizing is the manual or semi-automatic process allowing to create vector layers from a raster layer. In our case, we will use the satellite image georeferenced in next tutorial (see image georeferencing) and create a new vector layer showing landuse.

The process involves visually interpreting the limit of each piece of land and to draw (digitize) it through QGIS digitizing toolbox.

File to be used in that tutorial is:

    /dss_course_dataset/qgis/3-creating_vector_layers/el_dorado_argentina.tif


See video tutorial either on your local copy or on YouTube [QGIS-Digitizing](http://www.youtube.com/watch?feature=player_detailpage&v=vinGD2Jlka8)


### 5. Editing attributes name and type

Be sure to have the "Table manager" plugin installed and DBF manager downloaded on your computer.

File to be used in that tutorial is:

    /dss_course_dataset/qgis/3-creating_vector_layers/measurements.shp


### 5.1 Through the "Layer Properties/Fields tab"

See video tutorial either on your local copy or on YouTube [QGIS-Edit Attributes through Layer Properties](http://www.youtube.com/watch?feature=player_detailpage&v=YyzBt97Sibo)

### 5.2 Rename, change order, clone through Table Manager plugin

Open "Table Manager plugin" in "Plugins" menu. You can move up, down, delete, rename, add, clone fields.

### 5.3 Through DBFExplorer

".dbf" file format was used by **dBase** ([one of the first Database Management System for microComputers](http://en.wikipedia.org/wiki/DBase)). This file format is still used by many programs including by ESRI **shapefile** GIS format to store attribute data.

**DBFExplorer** is a usefull program allowing to rapidly edit your .dbf files (please refer to **shapefile** tutorial).

**Note that the shapefile to be edited needs to be closed from QGIS before being edited with DBFExlplorer.**

See video tutorial either on your local copy or on YouTube [QGIS-Edit Attributes through DBFExplorer](http://www.youtube.com/watch?feature=player_detailpage&v=SuIrbh3iwmY)





 

Double click on "DBFExplorer.exe", 


