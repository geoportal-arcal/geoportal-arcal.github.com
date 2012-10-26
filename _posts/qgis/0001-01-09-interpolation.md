---
layout: post
category : QGIS
tags : [desktop GIS, interpolation]
---

### TIN interpolation

1. From digitized countour lines
2. Convert to nodes
3. Interpolate with IDW (different parameters)
4. Interpolate with TIN
5. Generate contour lines


Interpolation is a method used to create new elevation points using information from a discrete set of known elevation points. The new elevation points are combined with known elevation points to create a continuous plane representing the Earth's surface. Before creating the interpolation, digitized contour lines must be converted to points. The known elevation points are concentrated along the trace of the contour lines, leaving large gaps of unknown elevation points between contour lines. If the elevation points were spaced in a regular gridded fashion, the elevation values could automatically be converted into a raster DEM. Typically the TIN interpolation method works best for creating digital topography from irregularly spaced known elevation points, like points extracted from contour lines. The TIN interpolation produces a triangulated network that builds connections between each known elevation points (Figure 3). The elevation can be calculated at any location on the TIN using the geometry of the triangle faces. However, the TIN interpolation sometimes creates irregular flat terraces on ridge lines and in valleys resulting from the connection of the different triangle faces [Ware, 1998; Barbalic and Omerbegovic, 1999]. The slope map in figure 4d illuminates these unrealistic irregular flat terraces not seen in the actual topography of Macchapucchare.
