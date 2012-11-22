---
layout: post
category : geoportal-DSS
tags : [DSS, Posting MapBox layer]
---

In order to post MapBox layers, you just need to create a new file indicating the title, location of interest, MapBox ID, ... 

To do so you need to access the system hosting the DSS with a system online name **prose.io** (See Video above for all details).

The information to be filled are the following: 

    title: your title
    categories: 
        - data
    geography: your geo-tag
    status: normal
    default-position: 0
    layer: Map ID (MapBox layer)
    source: <a href="http://www.unsl.edu.ar">GEA-UNSL</a>
    license: Public Domain
    updated: 2012/10/19
    description: Beryllium 7 concentration 
    downloads:
      - type: kml
        link: link to your kml file if any


**status** possible values are: *default* or *normal*

* If *default*, then your layer will be active by default. In that case the **default-position** value will specify the relative position of the layer (with respect to the stack of active layers)

* If *normal*, then the new layer will be unactive.

For more detailed information, see video above.

See video tutorial on YouTube [DSS-Posting New MapBox Layers](http://www.youtube.com/watch?feature=player_detailpage&v=2GOu-WryZZE)


