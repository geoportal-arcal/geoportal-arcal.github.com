---
layout: post
category : Tilemill
tags : [styling data, quantitative data, point implantation]
---


In this tutorial we will see:

1. How to style **quantitative data** (refer to semiology of graphics tutorial) associated with **point features** (concentration of Cesium or Beryllium in specific location);

2. How to visualize in parallel the **relative error of measurements**;

### 1.  Opening a shapefile in TileMill

File to be used in that tutorial is:

    /dss_course_dataset/tilemill/1-points_quantitative/grid_Be.shp

See video tutorial either on your local copy or on YouTube [TileMill-Opening Shapefile](http://www.youtube.com/watch?feature=player_detailpage&v=hjQ-FfEcj_Y)

**IMPORTANT**: the GIS layer to be imported must be projected (refer to projections related tutorials) either WGS84 (EPSG:4326) or Google Mercator (EPSG:900913). That is the case of the grid_Be.shp file whose geographical projection is WGS84.

At this stage, the Shapefile is loaded into TileMill but not styled. To be styled, your layer (identified by an ID -identifier- as shown in the previous video) need to be associated with a style sheet.

### 2. Editing the style sheet

We want to visualize the concentration of Beryllium in each measured point. Based on the theoretical framework provided by the **Semiology of Graphics**, before embarking on styling, we must answer some questions. 

**Preliminary analysis**: 

* What is the implantation of the geographic feature? **Point**
* Is data to be shown qualitative or quantitative? **Quantitative**
* Is data to be shown relative (percentage) or absolute? **Absolute**

As a result we will represent Beryllium concentration by size variation (in our case using circles).

The **Carto** symboliser we will use is **Marker** (as presented in the previous tutorial).

Let's try a first style definition:

    #grid_be {
      marker-width: 20;  // defines size of marker in pixels
      marker-opacity: 0.8;  // defines opacity level here 80%
      marker-line-color: #888;  // defines marker outline color
      marker-line-width: 1;  // defines marker outline width
      marker-line-opacity: 0.7;  // defines marker outline opacity
      marker-allow-overlap: true;  // defines markers overlap behaviour
    }

Copy and paste the definition in your TileMill stylesheet editor.

**Output**:You will see a single blue point. We need to zoom to the layer extent and to save this default setting.

####  2.1 Zoom to and save the default layer extent

See video tutorial either on your local copy or on YouTube [TileMill-Defining default zoom level and geographical extent](http://www.youtube.com/watch?feature=player_detailpage&v=dYhGhkIinig)

#### 2.2 Varying circles size based on attribute values

What we have now is a grid of blue points. It does not give any information of Beryllium concentration.

Let's explore additionnal **marker** properties:

    #grid_be {
      marker-width: 100;  // defines size of marker in pixels
      marker-fill: #F00; // defines marker color (here Red)
      marker-opacity: 0.8;  // defines opacity level here 80%
      marker-line-color: #888;  // defines marker outline color
      marker-line-width: 1;  // defines marker outline width
      marker-line-opacity: 0.7;  // defines marker outline opacity
      marker-allow-overlap: false;  // defines markers overlap behaviour
    }

**Output**: Big red circles but some of them are hidden because of the *marker-allow-overlap* property set to *false*.

**Action**: Set *marker-allow-overlap* to true and see what happens (all circles are now visible).

What we want know is circles whose size vary based on a field value (here **be**)

     #grid_be {
       marker-width: [be]; // defines the marker-width based on an attribute value
       marker-fill: #F00; // defines marker color (here Red)
       marker-opacity: 0.8;  // defines opacity level here 80%
       marker-line-color: #888;  // defines marker outline color
       marker-line-width: 1;  // defines marker outline width
       marker-line-opacity: 0.7;  // defines marker outline opacity
       marker-allow-overlap: true;  // defines markers overlap behaviour
     }

**Output**: Big mess with big circles of varying sizes.
 
**Action**: We need to scale the size of the circle as *marker-width* unit is pixels, to use directly the value of Beryllium concentration values (ranging here from 256 to 875) is not relevant. We need to scale it. Let's divide [be] by 12.

     #grid_be {
       marker-width: [be]/12; // defines the marker-width based on an attribute value
       marker-fill: #F00; // defines marker color (here Red)
       marker-opacity: 0.8;  // defines opacity level here 80%
       marker-line-color: #888;  // defines marker outline color
       marker-line-width: 1;  // defines marker outline width
       marker-line-opacity: 0.7;  // defines marker outline opacity
       marker-allow-overlap: true;  // defines markers overlap behaviour
     }

**Output**: We efficiently visualize the different concentration of Beryllium throughout the site. 

#### 2.3 Correcting a very frequent error while styling data with proportional circles

Based on what we saw during the "Semiology of Graphics" course, a visualization is effecient when the system of symbols and retinal variables used (color, size, shape, orientation, ...) is closely related to the data to be visualized. In our case we want to draw circles whose surfaces are proportional to Beryllium concentration in each measurement point. Indeed, the eyes see circles surfaces first of all. As a result, when we simply draw circles whose diameters are proportional to Beryllium concentration, what we see is circles whose areas are proportional to the square of Beryllium value (Circle Surface=PIxRxR). 

![Proportional circles](http://dl.dropbox.com/u/108352435/course_images/Carto/proportional_circles.png)

As a result, the representation of quantities we want to represent is simply false and misleading unless you mention clearly in a legend that circles areas are proportional to the square of the values you want to represent and not directly to the values 

To correct circles whose surface is proportional to the values, you simply need to use the square root of the value instead of the value directly.

In our case we will create a new calculated field into the original shapefile then to use it as *marker-width*
 
As a reminder, the original shapefile we want to edit and currently loaded into TileMill is in:

    /dss_course_dataset/tilemill/1-points_quantitative/grid_be.shp


See video tutorial either on your local copy or on YouTube [TileMill-Adjusting Circle Proportionality](http://www.youtube.com/watch?feature=player_detailpage&v=o7CVh7gM1RY)

#### 2.4 Styling relative error of Beryllium measurements.

It's particularly relevant to visualize simultaneously the concentration of radionuclides and the relative error or measurements. We will see how to achieve this very easily.

**Preliminary analysis**: 

* What is the implantation of the geographic feature? **Point**
* Is data to be shown qualitative or quantitative? **Quantitative**
* Is data to be shown relative (percentage) or absolute? **Relative**

As a result we will represent Beryllium concentration measurement error by value variation (refer to 'Semiology of Graphics' tutorial).

We will discretize relative error in 4 classes (*refer basics for further information on discretization and QGIS others for further information on how to find classes limits with QGIS*):

    Class 1: From 4% to 9.5% 
    Class 2: From 9.5% to 14.5%
    Class 3: From 14.5% to 17%
    Class 4: From 17% to 20%

Choose a color scheme with [Color Brewer](http://colorbrewer2.org/) (refer to "Semiology of Graphics" for further information):

    Class 1: EFF3FF
    Class 2: BDD7E7
    Class 3: 6BAED6
    Class 4: 2171B5

Now we will defines the *marker-fill* color depending on measurements error values:

    #grid_be {
      marker-width: [be_sqrt]*2; // defines the marker-width based on an attribute value
      marker-opacity: 0.8;  // defines opacity level here 80%
      marker-line-color: #888;  // defines marker outline color
      marker-line-width: 1;  // defines marker outline width
      marker-line-opacity: 0.7;  // defines marker outline opacity
      marker-allow-overlap: true;  // defines markers overlap behaviour
      [rel_error>=4][rel_error<9.5]  {  // when 4<=rel_error<9.5
        marker-fill: #EFF3FF;  // defines marker-fill (color)
      }  
      [rel_error>=9.5][rel_error<14.5]  {  // when 9.5<=rel_error<15.5
        marker-fill: #BDD7E7;
      }
      [rel_error>=14.5][rel_error<17]  {  // etc
        marker-fill: #6BAED6;
      }
      [rel_error>=17][rel_error<=20]  { // note that for each selected case are surrounded by curly brackets.
        marker-fill: #2171B5;
      }
    }

Copy and paste these declarations in your TileMill style sheet editor and you should see proportional circles with colors related to the relative level of measurements errors.   

We will see in a next tutorial how to add interactivity (tooltips) and legends.


#### 2.5 Adapting styling based on zoom levels

We worked so far at zoom level 17 (zoom level best fitting the layer extent). However, it might be interesting to visualize this layer at other zoom level. In our example if you unzoom (switching to zoom level 16), the scale of proportional circle will not be adapted anymore (too big).	

Hopefully, the Carto language allows to define define style selectively based on zoom level as shown below:

    #grid_be {
      [zoom > 15] {
        marker-width: [be]/22;
      }
      [zoom > 16] {
        marker-width: [be]/12;
      }
      marker-opacity: 0.95;  // defines opacity level here 80%
      marker-line-color: #222;  // defines marker outline color
      marker-line-width: 1;  // defines marker outline width
      marker-line-opacity: 0.4;  // defines marker outline opacity
      marker-allow-overlap: true;  // defines markers overlap behaviour
      marker-fill: #111;
    }
