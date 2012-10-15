---
layout: post
category : Tilemill
tags : [styling data]
---

TileMill is an open source software allowing to create map and to style your GIS layers in a very efficient and professional way.
By styling, I am refering to the visual techniques used to represent in an efficient way qualitative or quantitative data embedded in a map (such as population per cities, classification of landuse, ...). These techniques are well codified and have been theorized few decades ago as described in the tutorial related to **Semiology of graphics** (in GIS fundamentals).

So far these techniques have been implemented in many desktop GIS (both open source and proprietary) with various degrees of success. Furthermore, styling, creating maps that will be further disseminated through paper or digital media is one thing, creating, styling maps to be disseminated on the web and  making it interactive, "zoomable", fast to navigate is another story.

With **TileMill** and its online companion application named **MapBox** maps dissemination through the web is really straightforward. This software stack allows to style in a highly flexible way GIS layers, adding interactivy, to comply with the highest mapping standards using **TileMill** and to host it in **MapBox** that will make your maps and layers available in the cloud.  

The process can be summarize as follow:
1. Open your GIS layers of interest (for instance the ones you created with QGIS)
2. Apply styles (mss language)
3. Generate **.mbtiles** (see notes below)
4. Import **.mbtiles** in MapBox
5. Now your interactive layers are available in the cloud

**Notes:**

* The *mss* (Mapping Style Sheet) language allows to create in a text mode styles and apply it to your layers. It might look like an advanced techniques but it is finally far more simple and efficient than opening a dozen of windows and clicking on menus, ...). For those who are familiar with **CSS* the approach is extremly similar for the others it is very easy to learn it.

* **.mbtiles** is a file format allowing to embed in a single file your styled data at different zoom levels and to store it as tiles. At each zoom level your map will be divided in small tiles (squares of 125px*125px for instance). As a result when you want to visualize online your maps, your navigator only shows the part of the layer you are currently visualizing (according to the zoom level). This technique makes maps visualization on the web very fast. For further and more detailed information refer to this link [http://mapbox.com/developers/guide/](http://mapbox.com/developers/guide/). 

To take a look at online interactive maps produced with **TileMill** and **MapBox**, please refer to the following link [http://mapbox.com/tilemill/gallery/](http://mapbox.com/tilemill/gallery/). 

Both **TileMill** and **MapBox** propose a great documentation online, you can access it there:
* [TileMill Help](http://mapbox.com/tilemill/docs/)
* [MapBox Help](http://mapbox.com)

