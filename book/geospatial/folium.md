---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.16.7
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# folium

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/giswqs/geog-510/blob/main/book/geospatial/folium.ipynb)

## Introduction
**Folium** is a powerful Python library that enables the creation of interactive maps using **Leaflet.js**. It provides a simple interface to visualize geospatial data and integrates well with **Pandas**, **GeoPandas**, and other geospatial libraries.

### Learning Objectives
By the end of this lecture, you will:
- Understand what Folium is and how it works.
- Learn to create basic maps and add markers.
- Explore how to visualize geospatial data.
- Customize maps with different layers and styles.

## 1. Installing and Importing Folium
To install Folium, run the following command:

```bash
pip install folium
```

Then, import Folium in Python:

```{code-cell} ipython3
import folium
```

## 2. Creating a Basic Map
A Folium map is centered on a specific latitude and longitude.

```{code-cell} ipython3
m = folium.Map(location=[37.7749, -122.4194], zoom_start=10)
m.save("map.html")  # Save map as an HTML file
m  # Display the map in Jupyter Notebook
```

### Map Parameters
- `location`: Center of the map (latitude, longitude).
- `zoom_start`: Initial zoom level.
- `tiles`: The map style (default: `"OpenStreetMap"`).

## 3. Adding Markers and Popups
Folium allows adding markers to highlight specific locations.

```{code-cell} ipython3
m = folium.Map(location=[37.7749, -122.4194], zoom_start=10)
folium.Marker(
    [37.7749, -122.4194],
    popup="San Francisco",
    tooltip="Click for info",
    icon=folium.Icon(color="blue", icon="info-sign")
).add_to(m)

m.save("map_with_marker.html")
m
```

## 4. Adding GeoJSON and Choropleth Layers
Folium supports **GeoJSON** and **Choropleth** layers for visualizing geographic data.

### Adding a GeoJSON Layer

```{code-cell} ipython3
import json

geojson_data = {
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "geometry": {"type": "Point", "coordinates": [-122.4194, 37.7749]},
            "properties": {"name": "San Francisco"},
        }
    ]
}

m = folium.Map(location=[37.7749, -122.4194], zoom_start=10)
folium.GeoJson(geojson_data, name="GeoJSON Layer").add_to(m)
m
```

### Creating a Choropleth Map

```{code-cell} ipython3
import pandas as pd

# Sample data: FIPS codes and values
data = pd.DataFrame({
    "FIPS": ["06075"],  # San Francisco county FIPS code
    "Value": [100]
})

m = folium.Map(location=[37.7749, -122.4194], zoom_start=6)
folium.Choropleth(
    geo_data="https://raw.githubusercontent.com/PublicaMundi/MappingAPI/master/data/geojson/us-states.json",
    data=data,
    columns=["FIPS", "Value"],
    key_on="feature.id",
    fill_color="YlGn",
    fill_opacity=0.7,
    line_opacity=0.2,
    legend_name="Sample Data"
).add_to(m)

m
```

## 5. Customizing Map Tiles
Folium allows switching between different map tiles:

```{code-cell} ipython3
m = folium.Map(location=[37.7749, -122.4194], zoom_start=10)
m
```

Other tile options:
- `CartoDB positron`
- `CartoDB dark_matter`

## 6. Adding Layer Controls
To allow toggling between layers:

```{code-cell} ipython3
m = folium.Map(location=[37.7749, -122.4194], zoom_start=10)
folium.TileLayer("CartoDB positron").add_to(m)
folium.TileLayer("CartoDB darkmatter").add_to(m)
folium.LayerControl().add_to(m)
m
```

## 7. Saving and Sharing Maps
Folium maps can be saved as HTML files:

```{code-cell} ipython3
m.save("interactive_map.html")
```

## Summary
- **Folium** is a Python library for creating interactive maps.
- Basic maps can be customized with **markers, popups, and tooltips**.
- Advanced features include **GeoJSON, choropleth maps, and tile layers**.
- Maps can be saved as **HTML files** and shared easily.

## Further Reading
- [Folium Documentation](https://python-visualization.github.io/folium/)
- [Leaflet.js Documentation](https://leafletjs.com/)
