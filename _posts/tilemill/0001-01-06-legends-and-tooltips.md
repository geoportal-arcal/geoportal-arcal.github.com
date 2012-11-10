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

The output of legend and tooltips as those shown in the video is still very basic, however this editing tool becomes very powerfull when we incorporate HTML, CSS and Google Image charts.

### 2. Legend with HTML and CSS

The process is documented here as well: [http://mapbox.com/tilemill/docs/guides/advanced-legends/](http://mapbox.com/tilemill/docs/guides/advanced-legends/)

To understand the following code you need to be familiar with HTML and CSS.
Very interesting resources to study HTML and CSS are:

* [http://es.html.net/tutorials/](http://es.html.net/tutorials/)

* [http://www.w3schools.com](http://www.w3schools.com/)

* [http://www.codecademy.com/tracks/htmlcss](http://www.codecademy.com/tracks/htmlcss)


Copy and paste the following HTML and CSS code into the legend editing area in TileMill:

    <!-- HTML section -->
    <div class='legend-beryllium'>
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

    <!-- CSS stylesheet -->
    <style type='text/css'>
    .wax-legend{
      background: rgba(0,0,0,0.9);
      color: #EEE;  
    }
    .legend-beryllium .legend-title {
      clear: both;
      text-align: left;
      margin-bottom: 8px;
      font-weight: bold;
      font-size: 100%;
      border-bottom: 1px solid #888;
    }
    .legend-beryllium .legend-subtitle {
      text-align: left;
      font-size: 100%;
      clear: both;
    }
    .legend-beryllium .legend-scale ul {
      margin: 0;
      padding: 0;
      float: left;
      list-style: none;
    }
    .legend-beryllium .legend-scale ul li {
      display: block;
      float: left;
      width: 70px;
      margin-bottom: 6px;
      text-align: center;
      font-size: 80%;
      list-style: none;
    }
    .legend-beryllium ul.legend-labels li span {
      display: block;
      float: left;
      height: 15px;
      width: 70px;
    }
    .legend-beryllium .legend-source {
      font-size: 70%;
      color: #666;
      clear: both;
    }
    .legend-beryllium a {
      color: #666;
    }
    .legend-beryllium .explain {
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

Copy and paste the HTML & CSS code provided in:

    /dss_course_dataset/tilemill/2-legends_tooltips/code_tooltip.txt

into the Teaser editing area into TileMill. 

How you can see the syntax to use to insert shapefile field values is the name of the field surrounded by three curly brackets.

The HTML and CSS codes shown above, simply defines font styles (bold, italic, normal), sizes, margins, color, background color, ... Study it and customize it as you want.

### 4. Embedding Google Chart images

Google provides a very interesting online services allowing to embed interactive charts into your HTML code and in our case into TileMill tooltips.

The principle is the following:

**Step 1**: Design on line the type of chart you are interested in, style it as shown here: [https://developers.google.com/chart/image/docs/chart_wizard](https://developers.google.com/chart/image/docs/chart_wizard)

**Step2**: Copy the automatically generated html code that you will incorporate in your tooltips html code, in our case:


    <img src="http://chart.googleapis.com/chart?
    chf=bg,s,00000000&
    chxl=0:|0|50|100|150|200|250|1:|6-8|4-6|2-4|0-2&
    chxr=0,0,250&
    chxs=0,FFFFFF,11.5,0,t,FF0000|1,FFFFFF,11.5,0,l,FFFFFF&
    chxt=t,y&
    chbh=a&
    chs=230x125&
    cht=bhg&
    chco=444444&
    chds=0,250&
    chd=t:FIELD1,FIELD2,FIELD3,FIELD4&
    chm=D,FF9900,0,-1,1.5" width="240" height="125" alt="" />


 Replace:
* **FIELD 1** by \{\{\{be_1\}\}\}
* **FIELD 2** by \{\{\{be_2\}\}\}
* **FIELD 3** by \{\{\{be_3\}\}\}
* **FIELD 4** by \{\{\{be_4\}\}\}


It's worth studying the meaning of each individual google chart images parameters (chf, chd, ...) as it offers a wide range of interesting and flexible configuration. It will allow you to show interactively in an efficient way a wide range of information.

Google chart parameters description is available here [https://developers.google.com/chart/image/docs/chart_params](https://developers.google.com/chart/image/docs/chart_params). Test different parameter values and see how it changes the graph. 



