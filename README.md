# GmE 221 – Laboratory Exercise 3: 3D Computational Modeling: DEM–Vector Integration and GeoJSON Service Delivery 

# Overview
- This laboratory builds directly on Laboratory 2 by transitioning from traditional planar (2D) GIS analysis to true three-dimensional (3D) spatial modeling. Instead of visually “extruding” 2D features, this exercise constructs geometries that explicitly store elevation (Z) values within their coordinate structure.
- The core objective is to generate 3D LineString geometries (x, y, z) by integrating road vector data with elevation values sampled from a Digital Elevation Model (DEM) raster.

# Environment Setup
- Python, GeoPandas, Rasterio, Shapely, PyProj, Flask, GitHub (PostGIS for storage only)

# How to Run
1. Activate the virtual environment
2. Run the py to retrieved vector data from a relational spatial database and raster data is loaded from a grid-based file format (.tiff) that are now represented internally in Python 
3. Run the py to constructs LineString geometries whose coordinates include a Z value (x, y, z). Z is derived by sampling elevation values from a DEM raster.

# Output
- Exported shapefile 
- Exported 3D GeoJSON
- Visualizaton in QGIS

# Reflection : C. Hybrid IO Milestone
- A hybrid GIS workflow combines libraries like rasterio, psycopg2, and GeoPandas to mirror the way GIS is stored and processed. Most of the time, DEM loaded from a raster file while vector file like road are queried from a PostGIS database. Since rasters are often very large, so it does not benefit storing it in a database. While, vectors work better in database for efficient querying since they usually have many attributes and relational connections, which databases handle better than flat files. This hybrid workflow are architectured for performance, scalability, and data management. No spatial analysis is yet occuring at this stage as we only load spatial data using tow different storage model, Vector data (roads) stored in PostGIS and Raster data (DEM) stored as a GeoTIFF file.

# Reflection : D.  3D Geometry Construction Milestone 
- Densification is necessary before sampling elevation. The problem without densification, is that road geometries contain few vertices, so if the road only has two vertices, the DEM only gives two values, so the elevation in between the road are never sampled. Densification means adding extra vertices along a line before sampling elevation. DEM and road must use the same coordinate system, so CRS alignment must happen before sampling. When a sampling function tries to read the elevation data of the DEM but its corresponding location of the road falls outside the coordinates of DEM, no data will be given. If our road and DEM uses different coordinate systems and are not aligned, they may appear far apart, even if they represent the same location that makes the map confusing and can lead to wrong interpretations. Z values in geometry mean each road vertex now contains elevation that makes it a 3D geometry.








