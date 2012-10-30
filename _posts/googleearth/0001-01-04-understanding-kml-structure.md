---
layout: post
category : Google Earth
tags : [KML]
---

**WORK IN PROGRESS...***

KML stands for Keyhole Markup Language (Keyhole is the name of a company that Google acquired in 2004 and which developped the first version of GoogleEarth-named Keyhole Earth Viewer at that time). [Look at the Wikipedia article for general context](http://en.wikipedia.org/wiki/Keyhole_Markup_Language).

Understanding in detail the structure and logic of KML is very rewarding and demistify it as well. Then, you will be in a postion to tap into the potential of the language and GoogleEarth and seeing the limit of it as well.

KML is a XML-like language (see this XML w3school tutorial for further information on XML [http://www.w3schools.com/xml/](http://www.w3schools.com/xml/)). 

### 1. Minimal KML

The line below shows a minimal KML file: 

    <kml>
      <Document>
        <name>my first point</name>
        <Placemark>
          <name>my first placemark</name>
          <Point>
            <coordinates>-66.09993326298255,-33.56312777383666,0</coordinates> 
          </Point>
        </Placemark>
      </Document>
    </kml>

**Instruction:** Copy the lines above, paste it into notepad++, save it with the an kml file extension and open it with Google Earth. You will see a single point.

See video tutorial either on your local copy or on YouTube [GoogleEarth-Create Minimal KML file](http://www.youtube.com/watch?feature=player_detailpage&v=UnI2d9TVRxo)

Let's dissect the lines shown above:

1. text surrounded by <> are named tag or element
2. For instance <name> is an opening tag and </name> the closing tag. It is mandatory to close a tag once open
3. Between an opening and closing tag you can find values (for instance 'my first point') or other tags
4. the kml tag is named the root element (or tag)

The name "root" comes from that KML file or generally speaking any XML-like file can be visualized as tree as shown below:

![kml tree image](http://dl.dropbox.com/u/108352435/course_images/google_earth/kml_tree.jpg)

Let's read it from bottom to top:

* we have the latitude, longitude, elevation between "coordinates" tag
* we specify it is a point "Point" tag
* any geographical feature (point, polygons, ...) should be stored in what is call a "Placemark"
* the placemark can have a name, here "my first placemark"
* all placemarks are stored in a "Document" (a container)
* a "Document" can have a name, here "my first point"
* a "Document" is under the root tag named "kml"

Tags have parent-children relationships.

### 2. Add several features

Any new geographical feature needs to be placed under a new placemark, so it we want to add a new point at the following location (lon:-66.1 lat:-33.562), the kml file will become:

    <kml>
      <Document>
        <name>my kml document</name>
        <Placemark>
          <name>my first placemark</name>
          <Point>
            <coordinates>-66.09993326298255,-33.56312777383666,0</coordinates> 
          </Point>
        </Placemark>
        <Placemark>
          <name>my second placemark</name>
          <Point>
            <coordinates>-66.1,-33.562,0</coordinates> 
          </Point>
        </Placemark>
      </Document>
    </kml>

Copy this code into notepad++, save it as KML and open it in Google Earth.

### 3. Polygon features

"Point" features were stored into "Point" tag as seen before. "Polygon" features are stored within "Polygon" tag as shown below:

    <kml>
      <Document>
        <name>my first polygon</name>
        <Placemark>
          <Polygon>
            <outerBoundaryIs>
              <LinearRing>
                <coordinates>
                  -122.366278,37.818844,30
                  -122.365248,37.819267,30
                  -122.365640,37.819861,30
                  -122.366669,37.819429,30
                  -122.366278,37.818844,30
                </coordinates>
              </LinearRing>
            </outerBoundaryIs>
         </Polygon>
        </Placemark>
      </Document>
    </kml>

**Comments**:

* we have a set of coordinates (edges of polygon), within "coordinates" tag
* coordinates are stored in a tag named "LinearRing"
* Then within "outerBoundaryIs" tag

Actually, as a polygon can contain cut-outs (holes) than by defining polygons as shown below (both "outerBoundaryIs" and "innerBoundaryIs" tags), you can draw polygons with "holes":

    <kml>
      <Document>
        <name>my first polygon with an hole</name>
        <Placemark>
          <Polygon>
            <outerBoundaryIs>
              <LinearRing>
                <coordinates>
                  -122.366278,37.818844,30
                  -122.365248,37.819267,30
                  -122.365640,37.819861,30
                  -122.366669,37.819429,30
                  -122.366278,37.818844,30
                </coordinates>
              </LinearRing>
            </outerBoundaryIs>
            <innerBoundaryIs>
              <LinearRing>
                <coordinates>
                  -122.366212,37.818977,30
                  -122.365424,37.819294,30
                  -122.365704,37.819731,30
                  -122.366488,37.819402,30
                  -122.366212,37.818977,30
                </coordinates>
              </LinearRing>
            </innerBoundaryIs>
          </Polygon>
        </Placemark>
      </Document>
    </kml>

Copy this code into notepad++, save it as KML and open it in Google Earth.


### 4. Styles

Of course, to make your KML more appealing, you might want to add styles (color, change size, type of icon, ...).

    <kml>
      <Document>
        <Placemark>
          <name>my first point</name>
          <Style id="myFirstStyle">
            <IconStyle>
              <color>a1ff00ff</color>
              <scale>1.5</scale>
              <Icon>
                <href>http://maps.google.com/mapfiles/kml/shapes/shaded_dot.png</href>
              </Icon>
            </IconStyle>
            <LabelStyle>
              <color>7fffaaff</color>
              <scale>1.5</scale>
            </LabelStyle>
          </Style>        
          <Point>
            <coordinates>-66.09993326298255,-33.56312777383666,0</coordinates> 
          </Point>
        </Placemark>
      </Document>
    </kml>

**Comments**:

* Style is defined within "Style" tag
* As you can see we can embed additionnal information into a tag called attributes. Within the "Style" tag for instance, we have an attribute whose name is "id" and whose value is "myFirstStyle". We will use of it later on.
* there are different types of styles: for Icons, for lables, ... 
* for each of them we can define the color, the size (scale), the reference to the icon image we want to use, ...
* **IMPORTANT:** the information shown as "label" is the "name" of the placemark
* If you want to hide the labels, simply select a "scale" lower than 0.4

### 5. Shared styles

When we have hundreds of placemarks, we don't want to embed styles definiton directly into placemarks. Instead, we use what is called 'shared style'.

    <kml>
      <Document>
        <Style id="mySharedStyle">
          <IconStyle>
            <color>a1ff00ff</color>
            <scale>1.5</scale>
            <Icon>
              <href>http://maps.google.com/mapfiles/kml/shapes/shaded_dot.png</href>
            </Icon>
          </IconStyle>
          <LabelStyle>
            <color>7fffaaff</color>
            <scale>1.5</scale>
          </LabelStyle>
        </Style>        
        <Placemark>
          <name>my first point</name>
          <styleUrl>#mySharedStyle</styleUrl>
          <Point>
            <coordinates>-66.09993326298255,-33.56312777383666,0</coordinates> 
          </Point>
        </Placemark>
        <Placemark>
          <name>my second point</name>
          <styleUrl>#mySharedStyle</styleUrl>
          <Point>
            <coordinates>-66.11,-33.58,0</coordinates> 
          </Point>
        </Placemark>
      </Document>
    </kml>

**Comments**:

* By referencing within the "Placemark" the shared style defined at "Document" tag level (using the id), we can apply the style to any placemarks referencing it.
* If an additionnal style is defined within a "Placemark", this one overwrite the shared style, thus applying the specific one for this placemark. 

### 6. Balloons

Balloons are small contextual boxes appearing when clicking to a feature. As soon as you define a "description" tag within the "Placemark' one, the text inside "description" tag is embedded and visible into balloons.

    <kml>
      <Document>
        <name>my first balloon</name>
        <Placemark>
          <name>my first placemark</name>
          <description>This is the information displayed in my balloons</description>
          <Point>
            <coordinates>-66.09993326298255,-33.56312777383666,0</coordinates> 
          </Point>
        </Placemark>
        <Placemark>
          <name>my second placemark</name>
          <Point>
            <coordinates>-66.1,-33.562,0</coordinates> 
          </Point>
        </Placemark>
      </Document>
    </kml>

If you copy this code into notepad++, save it as KML and open it in Google Earth, you will see when clicking on the icon a balloon appearing with the information provided by the "description" tag.

#### 6.1 Balloons formatted with HTML

Hopefully, it is possible to embed richer content than a simple text line. Actually, you can embed any HTML content styled with CSS.

The following example shows how to embed HTML/CSS, images and video into a KML balloon.

You can see an example of such HTML/CSS content in:

    dss_course_dataset/google_earth/2-kml_structure/my_first_html_balloon_video.html

and embedded in an KML file:

    dss_course_dataset/google_earth/2-kml_structure/kml_balloon_html_rich_content.kml

**Few comments:**

1. you will see that the Html/CSS code is surrounded by CDATA tags. It specifies that following code must not be interpreted as XML (for instance < and > symbols we might use in html and css). 

2. the snippet tag allows to specify the text we want to appear under the feature in the "Places" left panel.


##### 6.1.1 How to embed youtube video into KML balloons?

See video tutorial either on your local copy or on YouTube [GoogleEarth-Embedding YouTube Video](http://www.youtube.com/watch?feature=player_detailpage&v=dwlY7ZlDDA4)


##### 6.1.2 Using shared balloon styles

You might have noticed than html code to be embedded into balloons needs to be replicated in any single placemark. This approach is quite unefficient.
Hopefully, as in the case of features styling, it is possible to define a balloon template at "document tag level"" and to reference it within placemarks.

You will find an example of such shared balloon style in the following KML file:

    dss_course_dataset/google_earth/2-kml_structure/kml_shared_balloon_style.kml

**Some remarks:**

1. shared balloon style definition allows to define backround and text color for all balloons at once;
2. the html and css code must be but with the "text" tag. 

### 7. Embedding additional attibute data

By default, attribute information associated to each placemark is limited to information embedded in the "name" tag and the "description" tag within the "Placemark" tag.

        <Placemark>
          <name>my first placemark</name>
          <description>This is the information displayed in my balloons</description>
          <Point>
            <coordinates>-66.09993326298255,-33.56312777383666,0</coordinates> 
          </Point>
        </Placemark>
 
We will see in this chapter how to add new attribute information and embed it into balloons to enhance interactivity.
