---
layout: post
category : QGIS
tags : [desktop GIS, GRASS]
---

**Preliminary note: GRASS location, mapset must be defined in order to access GRASS toolbox in QGIS interface**

### 1. Interpolate with RST

1. Import QGIS vector into Grass with **v.in.ogr.qgis** module

2. Set raster region (through GRASS browser or QGIS toolbox): extent + resolution

3. Intepolate with  **v.surf.rst** module


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

* Export and colourized definitely your raster file with **r.out.tiff** (with compression: defflate and "Output TIFF world file" checked) 

