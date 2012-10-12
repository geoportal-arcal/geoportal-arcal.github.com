---
layout: post
category : QGIS
tags : [desktop GIS, georeferencing]
---

In that tutorial, we will see how to georeference images. By images we mean raster images as described in GIS Fundamentals tutorials (please, consult them for further details).

Raster (grid) images include: aerial pictures, scanned paper map, sattelite images, among others. A raster image being grid based, each pixel of an image as x (column), y (row) coordinates in pixels. At this stage, if we want incorporate such image in a GIS, we don't have any geographic reference and we are not able to overlay it with other already georeferenced GIS layers on our region of interest. They don't share the same coordinate system.  

In our case we will georeference an satellite image showing the ARCAL RLA 5/051 different sudy sites. Our task wil consist in associating to (column, row) coordinates, geographic coordinates as shown below:

![georeferencing](http://dl.dropbox.com/u/108352435/course_images/georeferencing/georeferencing.gif)

This process is called **georeferencing**. To collect reference geographic coordinates, you need to identify on the image you want to georeference, noticeable points easily identifiable in the field (intersection of roads, isolated tree, ...) and take accurate GPS measurements. Such points are called **Ground Control Points (GCP)**.

QGIS allows to georeference images very easily. To do so we will use in this tutorial the following files:

    /dss_course_dataset/img/el_dorado_argentina.jpeg

Accurate GPS coordinates of Ground Control Points are:

    GCP1 (lon/lat): -66.120186,-33.524861
    GCP2 (lon/lat): -66.053540,-33.524706
    GCP3 (lon/lat): -66.051052,-33.567278
    GCP4 (lon/lat): -66.136184,-33.56497

See video tutorial either on your local copy or on YouTube [QGIS-Georeferencing](http://www.youtube.com/watch?feature=player_detailpage&v=oRoAs0v93e8)


 

