---
layout: post
category : Tilemill
tags : [styling data, raster]
---


File to be used in that tutorial is:

    /dss_course_dataset/tilemill/5-raster/soil_loss_coloured.tiff

Once created with QGIS, it is very easy to import a raster file into TileMill using the **Carto** raster symbolizer, as shown below:

    #soil_loss {
      raster-opacity: 1;
      raster-scaling: bilinear;
    }

The html/CSS associated file is available into:

    /dss_course_dataset/tilemill/5-raster/legend_raster.text

Simply copy and paste it into the Legend editing area in TileMill.

**NOTE THAT YOU RASTER FILE NEED TO PROJECTED IN EPSG: 900913**

See video tutorial either on your local copy or on YouTube [TileMill-Styling Raster](http://www.youtube.com/watch?feature=player_detailpage&v=TjPPB-BsdAQ)




