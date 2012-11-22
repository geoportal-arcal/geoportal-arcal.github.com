---
layout: post
category : QGIS
tags : [desktop GIS, WORKFLOWS]
---


### 1. Importing CSV file into QGIS

* Create a **.csvt** file with type of attribute data ("Real", "Integer", "String")

* Import it into QGIS with "Add Delimited Text Layer" tool 

* Save it as shapefile. 


### 1. Interpolate with RST

1. Create a vector layer delimiting your area of interest (named here *limit*) if required with QGIS)

2. Open or create a new GRASS region/mapset

2. Import QGIS vectors (mask and vector file to be interpolated) into Grass with **v.in.ogr.qgis** module

3. Convert the newly imported *limit* layer to raster with **v.to.rast** module

4. Intepolate with  **v.surf.rst** module

5. Apply your own or predetermined colour palette (see below on how to create customized colour palette) with **r.colors.rules** or **r.colors.table** to your new inteporlated raster file

6. Export and colourized definitely your raster file with **r.out.tiff** (with compression: defflate and "Output TIFF world file" checked) 

7. Now on QGIS, clip (cut the newly created tiff file with the boundary of your **limit** layer) with Raster/Extraction/Clipper

**IMPORTANT NOTES:**

* When you export in **tiff** and colourize your GRASS raster file, values will be transformed into integers, so if the range of value to be interpolated is too small (for instance between 0.1 and 0.9) then your output **tiff** will contain only one colour (as values will be converted to integer -here 0-). The solution is to scale your raster value with **r.map.calculator** module (multiplying your values by 100 or 1000 for instance).

* You might face a problem in clipping the raster file with QGIS Clipper tool (message 'Cannot compute bounding box of cutline' appearing). A work around is to edit the gdal code (press the yellow pencil) and to replace the *-crop_to_line* command argument by *-r cubic* one.


### 2. Design colour palette (difference oriented)

* Create a new text file with the following content:

</br>

    -457	0	133	172
    -320	0	167	204
    -240	94	193	208
    -160	145	214	223
    -80	180	222	217
    0	201	224	198
    120	222	217	179
    240	223	207	145
    360	208	183	93
    480	199	151	5
    644	167	122	4
  
* Use this text file to colourized your interpolation raster with **r.colors.rules** module


