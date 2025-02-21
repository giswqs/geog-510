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

# Ipyleaflet

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/giswqs/geog-510/blob/main/book/geospatial/ipyleaflet.ipynb)

## Introduction
**ipyleaflet** is a Python library that brings the power of **Leaflet.js** to **Jupyter Notebooks**. It allows interactive mapping, geospatial visualization, and dynamic map customization with widgets.

### Learning Objectives
By the end of this lecture, you will:
- Understand what ipyleaflet is and how it differs from Folium.
- Learn to create basic maps and add markers.
- Explore how to use geospatial layers and data.
- Customize maps with widgets and interactivity.

## 1. Installing and Importing ipyleaflet
To install ipyleaflet, run the following command:

```bash
pip install ipyleaflet
```

Then, import it in Python:

```{code-cell} ipython3
from ipyleaflet import Map, Marker
```

## 2. Creating a Basic Map
A simple ipyleaflet map can be created as follows:

```{code-cell} ipython3
m = Map(center=(37.7749, -122.4194), zoom=10)
m
```

### Map Parameters
- `center`: The latitude and longitude of the map center.
- `zoom`: The initial zoom level.

## 3. Adding Markers
Markers help highlight specific locations on the map.

```{code-cell} ipython3
marker = Marker(location=(37.7749, -122.4194))
m.add_layer(marker)
m
```

## 4. Adding Tile Layers
Different tile layers can be used to change the appearance of the map.

```{code-cell} ipython3
from ipyleaflet import TileLayer

m.add_layer(TileLayer(url="https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png"))
m
```

Common tile providers:
- `OpenStreetMap`
- `Stamen Terrain`
- `CartoDB DarkMatter`

## 5. Adding GeoJSON Layers
GeoJSON files allow visualization of geospatial boundaries.

```{code-cell} ipython3
from ipyleaflet import GeoJSON
import json

data = {
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "geometry": {"type": "Point", "coordinates": [-122.4194, 37.7749]},
            "properties": {"name": "San Francisco"},
        }
    ],
}

gj = GeoJSON(data=data)
m.add_layer(gj)
m
```

## 6. Adding a Choropleth Layer
Choropleth maps visualize geographic data distributions.

```{code-cell} ipython3
from ipyleaflet import Choropleth
import pandas as pd

# Example data
geojson_url = (
    "https://raw.githubusercontent.com/johan/world.geo.json/master/countries.geo.json"
)
data = {"USA": 100, "CAN": 50, "MEX": 75}

choro = Choropleth(geo_data=geojson_url, choro_data=data, key_on="id")
m.add_layer(choro)
m
```

## 7. Adding Layer Controls
To toggle layers dynamically:

```{code-cell} ipython3
from ipyleaflet import LayersControl

m.add_control(LayersControl())
m
```

## 8. Adding Interactive Widgets
Widgets enable real-time interaction with the map.

```{code-cell} ipython3
from ipywidgets import FloatSlider

zoom_slider = FloatSlider(description="Zoom Level", min=1, max=20, value=m.zoom)


def zoom_change(change):
    m.zoom = change["new"]


zoom_slider.observe(zoom_change, "value")
zoom_slider
```

## Summary
- **ipyleaflet** enables interactive mapping in Jupyter Notebooks.
- Supports **markers, tile layers, GeoJSON, and choropleth maps**.
- Interactive widgets enhance user experience.
- Suitable for real-time geospatial data visualization.

## Further Reading
- [ipyleaflet Documentation](https://ipyleaflet.readthedocs.io/en/latest/)
- [Leaflet.js Documentation](https://leafletjs.com/)
