---
layout: post
category : Tilemill
tags : [styling data, Carto mss]
---

### 1. Introduction

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

### 2. Principles

The principle is very simple: based on the type of features (point, line, polygon) you want to style, you choose a symbolizer to use. Let's say we want to style 'point' data using colored circles of specific sizes, we will use **markers** symbolizers. Once you 've chosen a symbolizer, you apply a list of symbolizer properties associated with it. Let's see a commented example:

**Step 1: define the ID of the layer**

*The ID of the layer is defined when you import/load the shapefile for instance (refer to next tutorial).*

    #grid_be {

    }

**Notes**:
* the # symbol allows to specify that grid_be is the ID of the layer we want to style
* symbolizer properties will be put between the curly brackets

**Step 2: add marker symbolizer properties**

    #grid_be {
      marker-width: 20;
      marker-opacity: 0.9;
      marker-line-color: #AAA;
      marker-line-width: 1;
      marker-line-opacity: 0.7;
      marker-allow-overlap: true;
      //marker-allow-overlap: false;
      /*marker-line-width: 1;
      marker-line-opacity: 0.7;*/
    }

**Notes**:

* each property ends with a semi-column (in order to indicate the beginning and end of a property declaration)

* **marker-width** defines the size of the circle (marker) in pixels
* **marker-opacity** defines the level of transparency (between 0 -transparent- and 1-opaque)
* **marker-line-color** defines the color of the outline of the circle
* **marker-line-width** defines the width of the outline of the circle
* **marker-allow-overlap** defines the behaviour of circles who are partially covering each other (do we hide one of them or not). When set to 'true', markers can be juxtaposed.
* the double slash symbol // specify that the following property is unactivated (commented)
* the properties surrounded by /\* blabalbalb \*/ are unactivated as well (commented). The difference is that this style of comment allows to comment several lines at once.

### 3.Other resources
As indicated in the TileMill tutorial describing the user interface, you can access help on Carto style sheet language within the editor window at any time. There is a full description of all symbolizer properties.

![carto help editor](http://dl.dropbox.com/u/108352435/course_images/Carto/carto_help_editor.gif)

We will cover most of the Carto symbolizer and their respective properties in the next tutorials.


