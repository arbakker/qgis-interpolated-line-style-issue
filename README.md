# qgis-interpolated-line-style-issue

Repo for reproducing issue with the new (3.20.4) QGIS [Interpolated Line style](https://www.qgis.org/en/site/forusers/visualchangelog320/index.html#feature-interpolated-line-symbol-layer-type-for-vector-layers). 

> **TLDR:** Interpolated Line style does not handle data which has different projection than the current map projection. 


I also just ran into this issue and after some tests concluded that the Interpolated Line style cannot handle data that does not match the current map projection. 

I setup a git repository with an example QGIS project file and a GeoPackage containing the same dataset in three different projections EPSG:28992, EPSG:4326 and EPSG:3857. 

I added the three different layers to the project and tested for each map projection the result. Note that the correct location for this dataset is near Arnhem, in the Netherlands. 

**EPSG:28992**

[![EPSG:28992][1]][1]

**EPSG:3857**

[![EPSG:3857][2]][2]

**EPSG:4326**

[![EPSG:4326][3]][3]

As the images show, only the data matching the current map projection is portrayed correctly (although this was not entirely the case for the EPSG:4326 projection). Not sure if this is intended behaviour, but I would expect that styles should be portrayed correctly also when the geometries are reprojected.


  [1]: https://i.stack.imgur.com/sA10k.png
  [2]: https://i.stack.imgur.com/Glpkw.png
  [3]: https://i.stack.imgur.com/RWYBq.png
