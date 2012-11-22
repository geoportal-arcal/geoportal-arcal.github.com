---
layout: post
category : Google Earth
tags : [KML, Python]
---

**PRELIMINARY NOTE: This tutorial requires at least basic programming skills or at least a strong interest on programming.**


When dealing with an important amount of information and want to style it in a flexible, and efficient way, it is highly advised to script kml creationand manipulation. The **Python** scripting language offers very interesting possibilities.

### 1. Install Python

The Python version recommended here is the **2.7** one.

To download and install it, got to [http://www.python.org/download/](http://www.python.org/download/)


### 2. Basic Python tutorial

To have a quick overview of basic Python syntax (the one that might be sufficient to create KML files), [download this file](http://dl.dropbox.com/u/108352435/course/Python/PythonBasics.py), open it with **Idle** Python interpreter (installed with Python by default) and execute, modify the different sections of interest.


### 3. Creating and Parsing KML files with Python

KML Python modules are available but do not really offer more added value than a simple and very efficient xml parser as **ElementTree** (available by default after Python installation) considering that KML is XML based.

Here after some online resources on ElementTree:

* [http://www.bigfatalien.com/?p=223](http://www.bigfatalien.com/?p=223)

* [http://docs.python.org/2/library/xml.etree.elementtree.html](http://docs.python.org/2/library/xml.etree.elementtree.html)

* [http://effbot.org/zone/element-index.htm](http://effbot.org/zone/element-index.htm)

* [http://eli.thegreenplace.net/2012/03/15/processing-xml-in-python-with-elementtree/](http://eli.thegreenplace.net/2012/03/15/processing-xml-in-python-with-elementtree/)

The Xpath language allows to access any tags into an XML file very easily.	

* [http://effbot.org/zone/element-xpath.htm](http://effbot.org/zone/element-xpath.htm)

Here after you can download two examples of KML Creation and Parsing Python scripts. 

The first one shows how to access read and modify any specific KML tags. [Download Example 1 here.](http://dl.dropbox.com/u/108352435/course/Python/example1.zip)

The second one shows how to create and style a KML file based on a **.csv** input file.  [Download Example 2 here.](http://dl.dropbox.com/u/108352435/course/Python/example2.zip)




