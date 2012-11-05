---
layout: post
category : Tilemill
tags : [styling data, qualitative data, polygon implantation]
---

In that tutorial, we will style a layer showing landuse on El Dorado study site in Argentina. This layer includes farming techniques, cultivation type in 2010, 2011 and 2012 in each parcel with their relative extent.

File to be used in that tutorial is:

    /dss_course_dataset/tilemill/3-poly_qualitative/land_use_eldorado.shp

**Preliminary analysis**: 

* What is the implantation of the geographic feature? **Polygon**
* Is data to be shown qualitative or quantitative? **Qualitative**

In that case we will use the visual variable colour or/and texture to represent the type of farming techniques used over El Dorado. The associativity and selectivity of these visual variables will allow to identify at a glance the landuse of a specific parcel or to group visually parcels with the same landuse. 

The **Carto** symboliser we will use is **polygon**.

### 1. Open/load the shapefile into TileMill

Refer to previous tutorials to learn how to open a shapefile into TileMill, and define default layer extent and zoom level.

Associate the ID **landuse** with your new layer.

### 2. Styling polygons with the visual variable "colour"

    #landuse { 
      polygon-fill: #FFF;  // defines polygon colour
      polygon-opacity: 0.9;  // defines opacity (between 0 and 1)
      line-color: #777;  // colour of polygon sides
      line-width: 1;  // width of polygon sides
      line-opacity: 0.2; // opacity of sides
    }

Copy and paste the definition in your TileMill stylesheet editor.

**Output**: You should see all polygons with the same colour.

What we want to do is to associate a specific colour to each farming technique category. To do so, you simply need to conditionnaly define color based on land_use attribute values, as shown below:

    #landuse { 
      polygon-fill: #666;
      polygon-opacity: 0.9;
      line-color: #777;
      line-width: 1;
      line-opacity: 0.2;
      [land_use = 'plough'] {
        polygon-fill: #d2c4a3;
      }
      [land_use = 'forage'] {  // when land_use = 'forage' then colour is #c5d7b2
        polygon-fill: #c5d7b2;
      }
      [land_use = 'house'] {
        polygon-fill: #000000;
      }
      [land_use = 'livestock'] {
        polygon-fill: #e2d2ca;
      }
      [land_use = 'no-till farming'] {
        polygon-fill: #9e9e73;
      }
      [land_use = 'non cultivated'] {
        polygon-fill: #b1b7c1;
      }
    }

Copy and paste the definition in your TileMill stylesheet editor.

**Output**: Each type of landuse is shown with a specific colour.

### 3. Adding interactive tooltip to show cultivation type

Copy and paste the content of the following text file into the tooltip editing area:

    /dss_course_dataset/tilemill/3-poly_qualitative/tooltip_landuse.txt


### 4. Adding visual variable texture

The visual variable texture has good selectivity and associativity properties and even more efficient when combined with the visual variable colour. 

In your Mapbox/Project/name_of_your_project folder, create a new folder named 'textures', and copy the content of the following folder into it:

    /dss_course_dataset/tilemill/3-poly_qualitative/textures/


The **Carto** symboliser we will use is **polygon-pattern**. Tbus symboliser allows to repeat an image (here patterns) over the extent of polygons. It is very easy to create patterns with inkscape, gimp and then use it in TileMill as patterns.

Normally, when you set a style rule, it ovverrides any previous style rules. Here we want to add a polygon-pattern symboliser but a polygon symbolizer already exist. We will used what is called **attachment** as defined above.

***Note on Attachments from TileMill Carto help***

*By default, if you set a style rule, it overrides any previous style rules. However, sometimes you want to add multiple instances of a style, like in the case of a road border, country outline or for glow effects.*

    #world {
      ::outline {
        line-color: #000;
        line-width: 6;
      }
      line-color: #fff;
      line-width: 3;
    }

*This style first renders a black line with width 6, and on top of that, an additional white line with width 3. You can use an arbitrary amount of attachments to draw the same feature multiple times. The order in which you define attachments matters, the earlier it is defined, the lower it is drawn. This means that you should define shadows first before defining the actual feature symbolizer.*

Following this technique, the finel Carto MSS file will be:

    #landuse { 
      polygon-fill: #666;
      polygon-opacity: 0.9;
      line-color: #777;
      line-width: 1;
      line-opacity: 0.2;
      [land_use = 'plough'] {
        polygon-fill: #d2c4a3;
      }
      [land_use = 'forage'] {
        polygon-fill: #c5d7b2;
      }
      [land_use = 'house'] {
        polygon-fill: #000000;
      }
      [land_use = 'livestock'] {
        polygon-fill: #e2d2ca;
      }
      [land_use = 'no-till farming'] {
        polygon-fill: #9e9e73;
      }
      [land_use = 'non cultivated'] {
        polygon-fill: #b1b7c1;
      }
      ::textures {
      [land_use = 'plough'] {
        polygon-pattern-file: url(textures/text-diag-right.png);
        polygon-pattern-opacity: 0.8;
      }
      [land_use = 'forage'] {
        polygon-pattern-file: url(textures/text-diag-left.png);
        polygon-pattern-opacity: 0.8; 
      }
      [land_use = 'livestock'] {
        polygon-pattern-file: url(textures/text-hbar.png);
        polygon-pattern-opacity: 0.5;
      }
      [land_use = 'no-till farming'] {
        polygon-pattern-file: url(textures/text-circle.png);
        polygon-pattern-opacity: 0.3; 
      }
      [land_use = 'non cultivated'] {
        polygon-pattern-file: url(textures/text-circle.png);  
        polygon-pattern-opacity: 0.3; 
      }
      }
    }
