---
layout: post
category : QGIS
tags : [desktop GIS, raster, interpolation, GRASS, GDAL]
---

**WORK IN PROGRESS ...**

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


### 5 Finetuning the raster file with GDAL




    gdalwarp -s_srs EPSG:4269 -t_srs EPSG:3785 -r bilinear dc.tif dc-3785.tif

    gdaldem hillshade -co compress=lzw dc-3785.tif dc-hillshade-3785.tif

    gdaldem color-relief input-dem.tif ramp.txt output-color-relief.tif

    gdaldem slope dc-3785.tif dc-slope-3785.tif

    gdalinfo -stats dem_slope.tif
