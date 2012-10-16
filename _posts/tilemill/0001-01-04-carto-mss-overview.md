---
layout: post
category : Tilemill
tags : [styling data, Carto mss]
---

**WORK IN PROGRESS**

Carto styling language (extension of such styling file is ".mss" as you can see in the style sheet editor), is a very flexible and efficient way to style your map and produce maps complying with the highest mapping standards.

To style your data, you need to associate with a data layer loaded in TileMill identified by an ID (see next tutorial), a series of text based style definition. The definition of your style need to be inserted into the Style sheet editing panel (as shown below).

![Style sheet editor](http://dl.dropbox.com/u/108352435/course_images/tilemill_user_interface/style_sheet_editor.gif)

Such technique might impress people not familiar with programming but it is in reality **very simple**.

The Carto language proposes ten different symbolizers, each of which can be applied to a certain type or types of geometry:

1. **Line (for lines & polygons)**: *For instance to define the color, width of lines representing roads features, or landuse polygons sides, ...*

2. **Polygon (for polygons)**: *To define the color of polygons, transparency level, ...*

3. **Point (for points)**: *To associate images (different symbols) to point according to the category of the data (Cesium measurement site, Beryllium measurement site, ...)*

4. **Text (for points, lines, and polygons)**: *To define the font, size, color of text to be displayed*

5. **Shield (for points & lines)**: *To ensure that text is displayed into defined images (see example below)*

6. **Line Pattern (for lines & polygons)**: *To repeat a specific pattern image while representing the line*

7. **Polygon Pattern (for polygons)**: *To repeat a specific pattern image (image representing a tree for example) while representing the polygon (in our case to show that the polygon represents a forest)*

8. **Raster (for rasters)**: *To show raster images (digital elevation model, satellite images, ...)*

9. **Markers (for points, lines, & polygons)**: *To create points of specific colors and sizes according to the value of a specific attribute (for instance concenration of Cesium 137)*

10. **Buildings**: *pseudo 3D styles allowing for instance to associate a polygon height to the value of a specific attribute*

![Carto examples](http://dl.dropbox.com/u/108352435/course_images/Carto/carto_examples.gif)


