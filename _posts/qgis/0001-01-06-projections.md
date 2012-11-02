---
layout: post
category : QGIS
tags : [desktop GIS, projections]
---

We saw in GIS Fundamentals tutorials, how critical the choice of a reference ellipsoid and cartographic projection is.
We will illustrate these points using QGIS and a vector layer representing Latin America.

### 1. Change vector layer projection and QGIS projection setup

Each individual vector or raster layer in QGIS (and in GIS generally speaking) needs to be associated with a reference ellipsoid and optionnaly a cartorgraphic/map projection. These choices can be changed at any time by simply saving the layer with the desired spatial reference system. Additionnaly, a default Spatial Reference System (SRS) can be choosen by default in QGIS and vector or raster layers to be further opened will be reprojected according to this default SRS 'On the fly'.

File to be used in that tutorial is:

    /dss_course_dataset/qgis/2-projections/ne_10m_admin_0_latin_america.shp

See video tutorial either on your local copy or on YouTube [QGIS-Projection Setup](http://www.youtube.com/watch?feature=player_detailpage&v=kcnQ37NC9eM)

**IMPORTANT**: You need to know that when no map projection is selected (only the ellipsoid, for instance WGS84), though we call it unprojected layers, it is projected (we have indeed flat computer screen and not spherical one). As a consequence, when we select a non projected SRS (as WGS84) the layer is by default projected into "Platte carrée"/"Equidistant cylindrical" (refere GIS fundamentals tutorials). 

### 2. Projecting "Latin America" into different Geographic projections

Based on what we seen above, play with different non projected SRS such as: NAD27 (using the clarke 1866 ellipsoid) or AGD66(local ellipsoid). Overlay the WGS84 and these two last version and see differences.

**NOTE**: Don't forget to uncheck the 'On the fly' reprojection if you want to compare different projections.

### 3. Projection "Latin America" into different Cartographic projections.

Reproject the WGS84 of the Latin America layer into Google Mercator (EPSG:900913), Equal Area Cylindrical (EPSG:3410), several UTM and see differences.
