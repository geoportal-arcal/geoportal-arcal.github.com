---
layout: post
category : QGIS
tags : [desktop GIS, raster, interpolation, GRASS, GDAL]
---

In this tutorial, we will see how to use QGIS GRASS plugin and GDAL command line utility programs to perform interpolation.

**[GRASS](http://grass.osgeo.org/intro/index.php)** (Geographic Resources Analysis Support System) is an extremely powerful and full-fledged GIS software. Originally developed by the U.S. Army Construction Engineering Research Laboratories (USA-CERL, 1982-1995), a branch of the US Army Corp of Engineers, as a tool for land management and environmental planning by the military, GRASS GIS has evolved into a powerful utility with a wide range of applications in many different areas of scientific research. GRASS is currently used in academic and commercial settings around the world, as well as many governmental agencies including NASA, NOAA, the U.S. Census Bureau, USGS, and many environmental consulting companies.

**GRASS** is a raster-oriented GIS software (contrary to QGIS which is vector-oriented) and was originally accessed through a set of command line commands ("restricted to specialist"). GRASS features cover:

* raster data management
* raster map algebra
* raster data transformation and interpolation
* spatial analysis with raster data (neighborhood analysis, landscape structure analysis, ...)
* landscape process modelling (erosion and deposition modelling, ...)
* vector data management
* digitizing
* vector geometry operations
* vector analysis network
* vector spatial interpolation and approximation
* satellite image processing 
* etc ...

Hopefully, all these interesting features have been integrated into QGIS through a more user-friendly graphical user interface.

**[GDAL](http://www.gdal.org/)** (Geospatial Data Abstraction Library) is a set of command line programs allowing to perform efficiently, repetitively some raster projection conversion, associate colour palette, format conversions, ...
GDAL use might seem impressive to users not familiar with "command line" interface but you will see that is quite simple and finally more efficient than graphical user interface.


### 1. Generating node points from digitized elevation contour lines
 
In that tutorial, we assume that we digitized elevation contour lines from a paper topographic map. We want to extract nodes composing the lines in order to use it during interpolation.

File to be used in that tutorial is:

    /dss_course_dataset/qgis/5-interpolation/contour_lines_900913.shp

**Check that fTools plugin has been installed**

See video tutorial either on your local copy or on YouTube [QGIS-Extract Nodes](http://www.youtube.com/watch?feature=player_detailpage&v=rNgU_D6o5Ps)


### 2. TIN interpolation with QGIS

In that tutorial, we will use the interpolation features provided by QGIS (with default TIN settings). Then we will see how to style a bit the raster layer created.

File to be used in that tutorial is:

    /dss_course_dataset/qgis/5-interpolation/dem_nodes.shp (file created in previous tutorial)

See video tutorial either on your local copy or on YouTube [QGIS-TIN Interpolation](http://www.youtube.com/watch?feature=player_detailpage&v=conNAabDA54)

Test IDW (Inverse Distance Weighting) interpolation (with different settings) and see how it differs.

Default QGIS raster format (when created from interpolation for instance), is ".asc" (ASCII). Open with **notepad++** **"the tin_dem_qgis.asc"** file just created and take a look at its content. If you close it and re-open it with QGIS, you will loose the style (colour palette) created in the video. To associate definitely a colour palette to a raster file, we will use GDAL tools (see above tutorial).

### 3. Introducing GRASS

When you installed QGIS (including GRASS plugin), a folder named **"\GIS DataBase"** might have been created (likely under user\MyDocuments).

Within this directory, the GRASS GIS data are organized by projects stored in subdirectories called **LOCATION**s.

Each **LOCATION** is defined by:
* its coordinate system,
* map projection and,
* geographical boundaries

When a new **LOCATION** is created (from QGIS interface), subdirectories and files defining a LOCATION are created automatically. Each LOCATION can have several **MAPSET**s (subdirectories of the **LOCATION**) that are used to subdivide the project into different topics, subregions, or as workspace for individual team members (in the context of a collaborative team accessing an unique GRASS instance). When creating a new **LOCATION**, GRASS automatically creates a special **MAPSET** called *PERMANENT* designed to store the core data for the project. In our case we will use this default **MAPSET**.

![GRASS folders](http://dl.dropbox.com/u/108352435/course_images/QGIS/grass_folders.jpg)

When you create or delete GIS layers, always go through the GRASS or QGIS interface as each individual layer includes various internal file associated.

Note however that you can delete a whole **LOCATION** at once through the Windows Explorer for instance.

Open the following file with QGIS:

    /dss_course_dataset/qgis/5-interpolation/dem_nodes.shp (file created in previous tutorial)

We will use it to define the GRASS **LOCATION** extent.

See video tutorial either on your local copy or on YouTube [GRASS-Setup](http://www.youtube.com/watch?feature=player_detailpage&v=KkEhWWIfbRU)

#### 3.1 Importing vector shapefile into GRASS 

File to be used in that tutorial is:

    /dss_course_dataset/qgis/5-interpolation/dem_nodes.shp (file created in previous tutorial)


See video tutorial either on your local copy or on YouTube [GRASS-Import Shapefile](http://www.youtube.com/watch?feature=player_detailpage&v=Rpw2RSxe98Y)

#### 3.2 Defining raster **Region**
 
With **GRASS**, each raster file has its own spatial extent and resolution. Thus, before performing an interpolation, you need to specify what is called the raster **REGION**. 

See video tutorial either on your local copy or on YouTube [GRASS-Raster REGION](http://www.youtube.com/watch?feature=player_detailpage&v=GJb2x9nNHxc)

### 4 Interpolation with GRASS

We will use the **RST (Regularized Spline with Tension)**, computing the values at grid points using a function wich simulates a thin flexible plate passing through or close to the data points. It is the most general and accurate method currently available in GRASS but it may require tuning of parameters to achieve optimal accuracy.

![RST plate](http://dl.dropbox.com/u/108352435/course_images/QGIS/rst_plate.jpg)

**GRASS** modules are prefixed by letters allowing to known their purpose. For instance modules dealing with vector data will start with **v.** and those dealing with raster data will be prefixed by **r.**. These modules are traditionnaly launched through a command line interface but are now available through the GRASS toolkit graphical user interface.

The module we will used in this tutorial is called **v.surf.rst**.

See video tutorial either on your local copy or on YouTube [GRASS-RST Interpolation](http://www.youtube.com/watch?feature=player_detailpage&v=18nfUenz3h8)

Now we will export the new interpolated raster file back to QGIS in order to associate definitely a palette color to it, re-project it with GDAL tools.

We will export the raster file created as **GeoTiff**. **GeoTiff** is a very common raster file embedding data (here elevation associated to each pixel) and information related to coordinate system and map projection.

See video tutorial either on your local copy or on YouTube [GRASS-Exporting Raster as GeoTiff](http://www.youtube.com/watch?feature=player_detailpage&v=QHNgLXnyy5s)


**IMPORTANT: THIS SECTION REQUIRED MINIMUM KNOWLEDGE OF COMMAND LINE INTERFACES DOS OR LINUX LIKE. OTHER OPTIONS ARE AVAILABLE THROUGH GRASS (see Workflows tutorial)**

### 5 Finetuning the raster file with GDAL

Our objective is to prepare the raster file in order to be published via TileMill and MapBox. To do so, it requires two main operations:

* associate a colour palette
* reproject to EPSG:3785

### 5.1 GDAL introduction

GDAL utilities is accessed through a command line interface (CLI). These utilities are accessible once you install **FWTools**.

**Command line interface reminder**

From *Windows start Menu*, in "Search programs and files", write **cmd.exe*** and click "Return/Enter". The command line interface should be launched now.

![Start Menu windows](http://dl.dropbox.com/u/108352435/course_images/QGIS/Windows7StartMenu.jpg).

* **dir**:To list files and folder of the current folder

* **cd *name_of_the_folder***: To go to a new folder

* **dl *name_of_file***: To delete a folder

See video tutorial either on your local copy or on YouTube [CLI-Introduction](http://www.youtube.com/watch?feature=player_detailpage&v=QWdJ57eUV28)

Once you accessd through CLI the /dss_course_dataset/qgis/5-interpolation/ folder, write 

    gdalinfo dem.tiff

This command will display a bunch of information on the specified raster file (projection, corner coordinates, max and min values, resolution, ...)


See video tutorial either on your local copy or on YouTube [GDAL-Launching utilities](http://www.youtube.com/watch?feature=player_detailpage&v=f9lSRvf3NBg)

### 5.2 Associate a colour palette

At the moment, each pixel is associated with a value of elevation, which is interesting if you want to use it for geospatial analysis. But what we want know is to associate to each pixel a color allow to order visually the series of elevation values (from min to max altitude). 

![visual variable color example6](http://dl.dropbox.com/u/108352435/course_images/semiology/vv_colour_example6.jpg)
 
In our case, we will simply associate a black and white colour palette to each pixel based on their value (black for min value and white for max value and different degrees of gray for intermediate values).

To do so, you simply need to write the following gdal command:

    gdaldem color-relief input_file palette.txt output_file

the structure and content of the palette.text file is:

    761	0	0	0
    761.6	50	50	50
    762.2	100	100	100
    762.8	150	150	150
    763.4	200	200	200
    764	250	250	250

with:

* first column: min limit of the class (761, 761.6, ... in meters)
* second column: red value
* third column: green value
* fourth column: blue value

In our case, we will use the following palette file:

    /dss_course_dataset/qgis/5-interpolation/palettes/bw_dem.txt

Our exact command is:

    gdaldem color-relief dem.tiff palettes\bw_dem.txt dem_coloured.tiff

Open the newly created **dem_coloured.tiff** file with QGIS, you will see that pixel elevation values are now replaced by a triplet of value (Band1, Band2, Band3).


See video either on your local copy or on YouTube [GDAL-Checking Coloured Pixel Values with QGIS](http://www.youtube.com/watch?feature=player_detailpage&v=lk7qM0PC-v0)
 
### 5.3 Reproject

To reproject an existing geotif raster file:

    gdalwarp -s_srs EPSG:4326 -t_srs EPSG:3785 -r bilinear input_file.tif output_file.tif

with:

* -s_srs EPSG:4326 *projection of input file (source spatial reference system)*

* -s_srs EPSG:4326 *projection of input file (target spatial reference system)*

* -r bilinear *resampling method*


**The geotiff file is now ready to be published via TileMill and MapBox**


**EXERCICE: **

Use the following file with QGIS:

    /dss_course_dataset/qgis/5-interpolation/cesium_900913.shp

Interpolate values of **soil_loss** using the RST GRASS module.

Style it using the:

    /dss_course_dataset/qgis/5-interpolation/palettes/soil_loss.txt

### 6. Other GDAL utilities

Example:

    gdaldem slope dem.tiff slope.tiff

Create a raster file showing slope of specified input digital elevation model.

[Look at GDAL utilities page for further information](http://www.gdal.org/gdal_utilities.html)


### 7. General remarks on Digital Elevation models

To create slope raster file or contour lines vector files, you can either use the GDAL tollkit (see above) or GRASS.

GRASS modules of interest are:

* **r.slope**: create a slope raster file from DEM raster fil. If value to be interpolated in GRASS 

* **r.contour**: create contour lines vector file from DEM raster file
