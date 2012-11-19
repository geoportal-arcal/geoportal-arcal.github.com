---
layout: post
category : Google Earth
tags : [Ground Overlay]
---

[Download tutorial data](http://dl.dropbox.com/u/108352435/course/3-ground_overlay.zip), unzip and copy it into:


    dss_course_dataset\google_earth\

### 1. Adding Ground Overlay

1. Open the "geotiff" (*soil_loss.tif*) to be overlayed with **gimp** and save it as "jpeg"

2. If the "geotiff" not projected in **WGS84**, convert it with **QGIS** (*Raster/Projection/Warp*) in WGS84 in order to access coordinates of the boundaries of the raster file in WGS84 (required to position it in GoogleEarth)

3. Add "Image Overlay" with GoogleEarth(*Add/Image Overlay*) and use boundaries identified with QGIS (*Layer Properties/Metadata*) using *Placemark Properties/Location* tab 

4. Create a new Folder with name "Erosion" in **GoogleEarth** and move the **Image Overlay** created into it.

5. Save it as **kml** (erosion.kml)

### 2. Adding Legend


1. Open *legend_soil_loss.svg* with **Inkscape** and modify it if required 

2. Export it in **png** (*File/Export Bitmap*) as "legend.png"

3. Open "erosion.kml" with notepad++

4. Paste between *Folder* tags the following tags:

</br>

    <ScreenOverlay>
      <visibility>1</visibility>
      <name><font color="#999">Legend</font></name>
      <description>
      </description>
      <Icon>
        <href>legend.png</href>
      </Icon>
      <overlayXY x="0.01" y="0.99" xunits="fraction" yunits="fraction"/>
      <screenXY x="0.01" y="0.99" xunits="fraction" yunits="fraction"/>
    </ScreenOverlay>


### 3. Using time series animation

1. Create a new "Image Overlay" with "soil_loss-1.jpeg" with the same "Location parameters"

2. Add time stamp in both "GroundOverlay" tags (with notepad++):

</br>

    <TimeSpan>
      <begin>2012-01-01</begin>     <!-- kml:dateTime -->
      <end>2012-12-31</end>         <!-- kml:dateTime -->
    </TimeSpan>
 
