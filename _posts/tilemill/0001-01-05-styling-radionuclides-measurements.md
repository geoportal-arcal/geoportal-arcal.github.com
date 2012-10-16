---
layout: post
category : Tilemill
tags : [styling data, quantitative data, point imposition]
---

In this tutorial we will see:

1. How to style **quantitative data** (refer to semiology of graphics tutorial) associated with **point features** (concentration of Cesium or Beryllium in specific location);

2. How to visualize in parallel the **relative error of measurements**;

3. How to add **interactivity** in order to visualize Beryllium **concentration profiles** (concentration at different depth) while hover on features;

4. Add legend to your map.

### Step 1: Opening a shapefile in TileMill

File to be used in that tutorial is:

    /dss_course_dataset/tilemill/shp/grid_Be.shp

See video tutorial either on your local copy or on YouTube [TileMill-Opening Shapefile](http://www.youtube.com/watch?feature=player_detailpage&v=hjQ-FfEcj_Y)

**IMPORTANT**: the GIS layer to be imported must be projected (refer to projections related tutorials) either WGS84 (EPSG:4326) or Google Mercator (EPSG:900913). That is the case of the grid_Be.shp file whose geographical projection is WGS84.

At this stage, the Shapefile is loaded into TileMill but not styled. To be styled, your layer (identified by an ID -identifier- as shown in the previous video) need to be associated with a style sheet.

### Step 2: Editing the style sheet




