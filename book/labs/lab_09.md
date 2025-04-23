---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.16.7
---

# Lab 9

## Question 1: Creating an Interactive Map

1. Create an interactive map with search functionality that allows users to search for places and zoom to them. Disable the draw control on the map.

```{code-cell} ipython3

```

![image](https://github.com/user-attachments/assets/b930fb63-3bd1-4d7e-9bf8-87e6d398e5c3)

+++

## Question 2: Adding Map Legends

1. Add the [ESA World Cover](https://esa-worldcover.org/en) WMS tile layer to the map.
   - URL: `https://services.terrascope.be/wms/v2?`
   - Layer name: `WORLDCOVER_2021_MAP`
2. Add a legend to the map using the leafmap built-in `ESA_WorldCover` legend.

```{code-cell} ipython3

```

![image](https://github.com/user-attachments/assets/be5a9b07-4f6c-4245-9737-31db2df14f7f)

+++

## Question 3: Creating Marker Clusters

1. Create a marker cluster visualization from a GeoJSON file of building centroids:
   - URL: https://github.com/opengeos/datasets/releases/download/places/wa_building_centroids.geojson
   - Hint: Read the GeoJSON file using GeoPandas and add "latitude" and "longitude" columns to the GeoDataFrame.
2. Create circle markers for each building centroid using the `Map.add_circle_markers_from_xy()` method with the following styling:
   - Radius: 5
   - Outline color: "red"
   - Fill color: "yellow"
   - Fill opacity: 0.8

```{code-cell} ipython3

```

![image](https://github.com/user-attachments/assets/d60cbfc7-b8c9-4cab-8852-bc34e82fd665)

```{code-cell} ipython3

```

![image](https://github.com/user-attachments/assets/637e00ae-89af-495e-84b4-e668e16cce88)

+++

## Question 4: Visualizing Vector Data

1. Visualize the building polygons GeoJSON file and style it with:

   - Outline color: "red"
   - No fill color
   - URL: https://github.com/opengeos/datasets/releases/download/places/wa_overture_buildings.geojson

2. Visualize the road polylines GeoJSON file and style it with:

   - Line color: "red"
   - Line width: 2
   - URL: https://github.com/opengeos/datasets/releases/download/places/las_vegas_roads.geojson

3. Create a choropleth map of county areas in the US:
   - URL: https://github.com/opengeos/datasets/releases/download/us/us_counties.geojson
   - Column: `CENSUSAREA`

```{code-cell} ipython3

```

![image](https://github.com/user-attachments/assets/069eb704-c409-44ee-af9e-7582d1ab23a5)

```{code-cell} ipython3

```

![image](https://github.com/user-attachments/assets/f28d19a6-4f60-484c-b2f7-c1ecce7ecb26)

```{code-cell} ipython3

```

![image](https://github.com/user-attachments/assets/3aa9f54f-64d7-4788-89f1-f3ab88c1aa2e)

## Exercise 5: Creating a Split Map

1. Create a split map to compare imagery of Libya before and after the 2023 flood event:

   - Pre-event imagery: https://github.com/opengeos/datasets/releases/download/raster/Libya-2023-07-01.tif
   - Post-event imagery: https://github.com/opengeos/datasets/releases/download/raster/Libya-2023-09-13.tif

```{code-cell} ipython3

```

![image](https://github.com/user-attachments/assets/8cab4f1c-2dba-4652-a644-3ce6be4bbbd2)
