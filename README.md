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








