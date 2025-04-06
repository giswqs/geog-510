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
import os
import json
import random
import requests

from ipyleaflet import Map, GeoJSON

if not os.path.exists("europe_110.geo.json"):
    url = "https://github.com/jupyter-widgets/ipyleaflet/raw/master/examples/europe_110.geo.json"
    r = requests.get(url)
    with open("europe_110.geo.json", "w") as f:
        f.write(r.content.decode("utf-8"))

with open("europe_110.geo.json", "r") as f:
    data = json.load(f)


def random_color(feature):
    return {
        "color": "black",
        "fillColor": random.choice(["red", "yellow", "green", "orange"]),
    }


m = Map(center=(50.6252978589571, 0.34580993652344), zoom=3)

geo_json = GeoJSON(
    data=data,
    style={"opacity": 1, "dashArray": "9", "fillOpacity": 0.1, "weight": 1},
    hover_style={"color": "white", "dashArray": "0", "fillOpacity": 0.5},
    style_callback=random_color,
)
m.add(geo_json)

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

## 9. Adding an image overlay

```{code-cell} ipython3
from ipyleaflet import Map, ImageOverlay
```

```{code-cell} ipython3
m = Map(center=(25, -115), zoom=4)

image = ImageOverlay(
    url="https://i.imgur.com/06Q1fSz.png",
    # url='../06Q1fSz.png',
    bounds=((13, -130), (32, -100)),
)

m.add(image)
m
```

```{code-cell} ipython3
m = Map(center=(24, 115), zoom=4)

image = ImageOverlay(url="https://i.gifer.com/4j.gif", bounds=((13, 100), (45, 130)))

m.add(image)
m
```

## 10. Adding a video overlay

```{code-cell} ipython3
from ipyleaflet import Map, VideoOverlay
```

```{code-cell} ipython3
m = Map(center=(25, -115), zoom=4)

video = VideoOverlay(
    url="https://www.mapbox.com/bites/00188/patricia_nasa.webm",
    bounds=((13, -130), (32, -100)),
)

m.add(video)
m
```

```{code-cell} ipython3
m = Map(center=(37.562984, -122.514426), zoom=17)

video = VideoOverlay(
    url="https://static-assets.mapbox.com/mapbox-gl-js/drone.mp4",
    bounds=((37.56238816, -122.515963), (37.563391708, -122.5130939)),
)
m.add(video)
m
```

## 11. Adding WMS layers

```{code-cell} ipython3
from ipyleaflet import Map, WMSLayer, basemaps
```

```{code-cell} ipython3
wms = WMSLayer(
    url="http://mesonet.agron.iastate.edu/cgi-bin/wms/nexrad/n0r.cgi",
    layers="nexrad-n0r-900913",
    format="image/png",
    transparent=True,
    attribution="Weather data © 2012 IEM Nexrad",
)

m = Map(basemap=basemaps.CartoDB.Positron, center=(38.491, -95.712), zoom=4)
m.add(wms)
m
```

https://apps.nationalmap.gov/services/

```{code-cell} ipython3
wms = WMSLayer(
    url="https://imagery.nationalmap.gov/arcgis/services/USGSNAIPPlus/ImageServer/WMSServer?",
    layers="USGSNAIPPlus:NaturalColor",
    format="image/png",
    transparent=True,
    attribution="USGS",
)

m = Map(basemap=basemaps.CartoDB.Positron, center=(38.491, -95.712), zoom=4)
m.add(wms)
m
```

## Summary
- **ipyleaflet** enables interactive mapping in Jupyter Notebooks.
- Supports **markers, tile layers, GeoJSON, and choropleth maps**.
- Interactive widgets enhance user experience.
- Suitable for real-time geospatial data visualization.

## Further Reading
- [ipyleaflet Documentation](https://ipyleaflet.readthedocs.io/en/latest/)
- [Leaflet.js Documentation](https://leafletjs.com/)
