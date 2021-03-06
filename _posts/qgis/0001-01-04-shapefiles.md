---
layout: post
category : QGIS
tags : [desktop GIS, shapefiles, vector layer]
---

The Esri (software development and services company providing GIS applications) shapefile or simply a shapefile is a popular geospatial vector data format for geographic information systems software. It is developed and regulated by Esri as a (mostly) open specification for data interoperability among Esri and other software products (QGIS and TileMille for instance). This GIS vector data format has become a de facto standard format that any GIS software should be able to open, create and process.

We saw earlier that a GIS file is the marriage of a drawing software and database software and that any GIS layer open in QGIS for instance show both a map view and a data attribute view. This fact is reflected in the composition of a **"shapefile"**: 
1. **".shp"** file: contains the geometry of features, the "shapes" (for instance points, lines or polygons with their associated coordinates)
2. **".dbf"** file: contains the attribute information of features (for instance population, name, country name of world capital cities) 
3. **".shx"** file: a companion file to the .shp, contains shapes index, a positional index of the feature geometry to allow seeking forwards and backwards quickly.

Note that in each of the ".shp", ".shx", and ".dbf" files, the shapes in each file correspond to each other in sequence. That is, the first record in the ".shp" file corresponds to the first record in the ".shx" and ".dbf" files, and so on.

When you open a **"shapefile"** with QGIS, only ".shp" files are presented but behind the scene, all files are open and used.

Note that ".dbf" files can be open with any spreadsheet application (Microsoft Excel, Open Office Calc spreadsheet, ...)

Optional files might be associated with the three mandatory ones:
1. ".prj": text files including information on layer geographic/cartographic projection
2. ".shp.xml": metadata
3. etc ...


