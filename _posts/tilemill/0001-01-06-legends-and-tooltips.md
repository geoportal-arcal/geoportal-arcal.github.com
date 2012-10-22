---
layout: post
category : Tilemill
tags : [styling data, legends, tooltips, interactivity]
---

In TileMill, open the project we have created in the previous tutorial 'Berryllium 7 spatial distribution' and replace the shapefile used previously with the one located in:

    /dss_course_dataset/tilemill/2-legends_tooltips/grid_Be.shp

**NOTE**: Don't delete it, just edit it and change the path.

This version of 'grid_be.shp' includes additionnal fields to be visualized in tooltips (interactivity boxes showing contextual information when hover on features with the mouse).

### 1.Principle

The TileMill user interface offers an interactive editor tool allowing to design legend and tooltips very easily as shown in the video tutorial below:

See video tutorial either on your local copy or on YouTube [TileMill-Legends_And_Tooltips](http://www.youtube.com/watch?feature=player_detailpage&v=ikZT52OLL3s)

The output of legend and tooltips as those shown in the video is still very basic, however this edition tool becomes very powerfull when we incorporate HTML, CSS and Google Image charts.

### 2. Legend with HTML and CSS

The process is documented here as well: [http://mapbox.com/tilemill/docs/guides/advanced-legends/](http://mapbox.com/tilemill/docs/guides/advanced-legends/)

To understand the following code you need to be familiar with HTML and CSS.
Very interesting resources to study HTML and CSS are:

* [http://www.w3schools.com](http://www.w3schools.com/)

* [http://www.codecademy.com/tracks/htmlcss](http://www.codecademy.com/tracks/htmlcss)


Copy and paste the following HTML and CSS code into the legend edition area in TileMill:

    <div class='my-legend'>
    <div class='legend-title'>BERYLLIUM 7 CONCENTRATION</div>
    <div class='legend-subtitle'>Be7 measurement error</div>
    <div class='legend-scale'>
      <ul class='legend-labels'>
        <li><span style='background:#EFF3FF;'></span>4 - 9.5%</li>
        <li><span style='background:#BDD7E7;'></span>9.5 - 14.5%</li>
        <li><span style='background:#6BAED6;'></span>14.5 - 17%</li>
        <li><span style='background:#2171B5;'></span>17 - 20 %</li>
      </ul>
    </div>
    <div class='legend-subtitle'>Be7 total concentration</div>
    <div class='explain'>Area of circles is proportional to the square of Beryllium 7 contentration values.</div>
    <div class='legend-source'>Source: <a href="#link to source">National University of San Luis, Argentina (GEA-UNSL)</a></div>
    </div>

    <style type='text/css'>
      .wax-legend .legend-title {
      max-width: 200px !important;
      text-align: left;
      margin-bottom: 8px;
      font-weight: bold;
      font-size: 100%;
      color: #333;
      border-bottom: 1px solid #888;
      }
      .wax-legend .legend-subtitle {
        text-align: left;
        font-weight: bold;
        font-size: 100%;
        clear: both;
      }
      .wax-legend .legend-scale ul {
        margin: 0;
        padding: 0;
        float: left;
        list-style: none;
      }
      .wax-legend .legend-scale ul li {
        display: block;
        float: left;
        width: 70px;
        margin-bottom: 6px;
        text-align: center;
        font-size: 80%;
        list-style: none;
      }
      .wax-legend ul.legend-labels li span {
        display: block;
        float: left;
        height: 15px;
        width: 70px;
      }
      .wax-legend .legend-source {
        font-size: 70%;
        color: #999;
        clear: both;
      }
      .wax-legend a {
        color: #777;
      }
      .wax-legend .explain {
        text-align: left;
        font-weight: normal;
        font-style: italic;
        font-size: 85%;
      }
    </style>	

**Comments**:

1. There are two parts:
  * the HTML part made of a series of 'div' elements containing title, subtitle, color palette, ...
  * the CSS part providing the necessary styling to the HTML elements.
2. You won't need to create such code from scratch every time you want to create a legend. Simply copy, paste it and customize it as you like. 
3. However, I strongly recommend to go through the HTML and CSS tutorials mentionned above



### 3. Tooltips with HTML and CSS

The principle is the same, to style the tooltips, you need to create an HTML part, embedding your title, name of fields, fields, ... and then style it with CSS. 

Copy and paste the following HTML & CSS code into the Teaser edition area into TileMill. 

    <!-- TOOLTIP TITLE -->
    <div>
      <span class='tooltip-title'>BERYLLIUM 7 CONCENTRATION</span>
    </div>

    <div class='separator'></div>

    <!-- TOOLTIP SECTION -->
    <div>
      <span class='tooltip-section'>TOTAL (Bq/m2)</span>
    </div>
    <div class='field-value'>
      <span> Max: FIELD 1</span>
    </div>
    <div class='field-value-important'>
      <span> Mean: FIELD 2</span>
    </div>
    <div class='field-value'>
      <span> Min: FIELD 3</span>
    </div>
    <div class='field-value'>
      <span> Error: FIELD 4</span>
    </div>
    <div class='separator'></div>

    <!-- TOOLTIP SECTION -->
    <div>
      <span class='tooltip-section'>VERTICAL PROFILE (depth in mm)</span>
    </div>


    <!-- CSS stylesheet -->
    <style type="text/css">
      .wax-tooltip {
        max-width: 280px !important;
        color: #DDD;
        background: rgba(0,0,0,0.9);
      }
      .wax-tooltip .tooltip-title {
        font-weight: bold;
        font-size:110%;  
      }
      .wax-tooltip .tooltip-section {
        font-weight: bold;
      }
      .wax-tooltip .field-value {
        margin: 5px 0 0 20px;
        font-size:120%;  
        font-weight: bold;
      }
      .wax-tooltip .field-value-important {
        margin: 5px 0 0 20px;
        font-size:150%;  
        font-weight: bold;
      }
      .wax-tooltip .separator {
        margin: 10px 0px 10px 0px;
        border-bottom:1px solid rgba(255,255,255,0.3);
      }
    </style>

Replace **FIELD 1** by \{\{\{be_max\}\}\}

Replace **FIELD 2** by \{\{\{be\}\}\}

Replace **FIELD 3** by \{\{\{be_min\}\}\}

Replace **FIELD 4** by \{\{\{rel_error\}\}\}

