---
layout: post
category : Tilemill
tags : [styling data, qualitative data, point imposition]
---

[Download tutorial data](http://dl.dropbox.com/u/108352435/course/4-points_qualitative.zip), unzip it and copy it to:


    dss_course_dataset\tilemill\


1. Create a new project in TileMill

2. Load "points_qualitative.shp" with ID: **points_qualitative**

3. In MapBox/project/name_of_your_project, create a new folder named "icons"

4. Copy in this folder "square.svg" (currently under *dss_course_dataset/tilemill/4-points_qualitative/icons*)

5. Copy and paste the following **Carto** stylesheet into TileMill Stylesheet editor:

</br>

    @red: #900;
    @font: "Arial Regular";

    #points_qualitative {
      marker-width: [value_sqr]*5;
      marker-fill: @red;  
      marker-opacity: 0.4;
      marker-line-color: #111;
      marker-line-width: 1.5;
      marker-line-opacity: 0.8;
      marker-allow-overlap: true;
      ::shape {
        marker-file:url('icons/square.svg');
        marker-fill: #333;
        marker-line-color: #555;
        marker-allow-overlap: true;
        marker-transform:"scale(0.3) rotate(0)";
      }
      ::label {
        text-face-name: @font;
        text-name:[value];
        text-size: 11;
        text-fill:#222;
        text-dx: 0px;
        text-dy: -5px;
        text-transform:capitalize;
        text-halo-fill:#AAA;
        text-halo-radius:0.4;
        text-wrap-width:10;
        text-allow-overlap:true;
      }
    }


