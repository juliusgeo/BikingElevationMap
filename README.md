## About
Python notebook (and auto-exported script) to create custom maps in the style of those featured on [systemed.net](http://blog.systemed.net/post/10). Uses OSM and GeoPandas and exports to shapefiles.

## What it does
For each of the roads in the box defined by the lat and long bounds, it separates the road into segments defined as sections of road between intersection, and then reprojects those segments. The segments are reprojected first by taking all of the points between the first and last point in the segment, non-inclusive, and projecting them onto the line formed by the first and last points. Then those points are sorted by distance from the starting point, to prevent overlaps. From there, they are reprojected upwards with a distance equal to the elevation distance between the point and and the lower of either the start or end point. 

The end result is a file of the polygons outlining the elevation profile, each of the reprojected points along with their elevation, and the new outline of the street geometry after it has been transformed. 

To create the sample maps, I loaded each of those files into one QGIS project and then exported it with the OpenStreetMap baselayer.

## Example
![Map of area in Southeastern PA](Elevation_Map.png?raw=true "Elevation Map")
