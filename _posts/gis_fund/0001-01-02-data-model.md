---
layout: post
category : GIS fundamentals
tags : [data model, raster, vector, topology]
---

In Geographical Information System, geographical features we want to show (roads, administrative boundaries, lakes, landuse, cities, points of interest, ...) are symbolized by points, lines and polygons.

To draw such features two fundamental approaches can be considered:

* **the raster (grid) based**: space is regularly subdivided into cells (usually square in shape), as shown in the figure below. The location of geographic objects or conditions is defined by the row and column positions of the cells they occupy. The area that each cell represents defines the spatial resolution available. The value stored for each cell indicates the type of object or condition that is found at that location in the raster model, and the homogeneous units are the cells.

* **the vector based**: objects or conditions in the real world are represented by points and lines and polygons that define their boundaries, much as if they were being drawn on a map. The position of each object is defined by its placement in a map space that is organized by a coordinate reference system, as shown below.

![Raster vs vector](http://dl.dropbox.com/u/108352435/course_images/data_model/raster_vs_vector.gif)  

Comparison of the Raster and Vector Models. The landscape in 1 is shown in a raster representation (2) and in a vector representation (3). The pine forest stand (P) and spruce(picea) forest stand (S) are features. The river is a line feature, and the house (H) is a point feature.

Some basic properties of raster and vector data are as follows:

* Each entity in a vector file appears as an individual data object. It is easy to record information about an object or to compute characteristics such as its exact length or surface area. It is difficult to derive this kind of information from a raster file because raster files contain little (and sometimes no) geometric information.
* Some applications can be handled much more easily with raster techniques than with vector techniques. Raster works best for applications where individual features are not important.

<table border='1' bordercolor='#999'>
  <tr>
    <td width='200px'></td>
    <td width='200px'> <b>Raster</b> </td>
    <td width='200px'> <b>Vector</b> </td>
  </tr>
  <tr>
    <td> <b>Advantages</b></td>
    <td>
      <ul>
        <li>Good for complex analysis</li>
        <li>Efficient for overlays</li>
        <li>Data structure common for imagery</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Compact data structure</li>
        <li>Efficient for encoding topology</li>
        <li>True representation of shape</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td> <b>Disadvantages</b></td>
    <td>
      <ul>
        <li>Large datasets</li>
        <li>Topology hard to represent</li>
        <li>Maps less 'realistic'</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Complex structure</li>
        <li>Overlay operations difficult</li>
        <li>Might imply false sense of accuracy</li>
      </ul>
    </td>
  </tr>
</table>

</br>

**NOTE**: Geospatial **topology** studies the rules concerning the relationships between the points, lines, and polygons that represent the features of a geographic region. For example, where two polygons represent adjacent counties, typical topological rules would require that the counties share a common boundary with no gaps and no overlaps. Similarly, it would be nonsense to allow two polygons representing lakes to overlap. 


