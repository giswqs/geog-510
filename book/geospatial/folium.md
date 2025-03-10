---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.16.7
kernelspec:
  display_name: geo
  language: python
  name: python3
---

# Folium

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
m = folium.Map(
    location=[37.7749, -122.4194], zoom_start=10, tiles="CartoDB dark matter"
)
m.save("map.html")  # Save map as an HTML file
m  # Display the map in Jupyter Notebook
```

### Map Parameters
- `location`: Center of the map (latitude, longitude).
- `zoom_start`: Initial zoom level.
- `tiles`: The map style (default: `"OpenStreetMap"`). Try other styles like `Esri.WorldImagery`, `CartoDB positron`, or `CartoDB dark_matter`.

## 3. Adding Markers and Popups
Folium allows adding markers to highlight specific locations.

```{code-cell} ipython3
m = folium.Map(location=[37.7749, -122.4194], zoom_start=10)
folium.Marker(
    [37.7749, -122.4194],
    popup="San Francisco",
    tooltip="Click for info",
    icon=folium.Icon(color="blue", icon="info-sign"),
).add_to(m)

m.save("map_with_marker.html")
m
```

## 4. Adding GeoJSON and Choropleth Layers

Folium supports **GeoJSON** and **Choropleth** layers for visualizing geographic data. You can create GeoJSON data using the [geojson.io](https://geojson.io/) website or any other tool.

### Adding a GeoJSON Layer

```{code-cell} ipython3
geojson_data = {
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "geometry": {"type": "Point", "coordinates": [-122.4194, 37.7749]},
            "properties": {"name": "San Francisco"},
        }
    ],
}

m = folium.Map(location=[37.7749, -122.4194], zoom_start=10)
folium.GeoJson(geojson_data, name="GeoJSON Layer").add_to(m)
m
```

```{code-cell} ipython3
geojson_data = {
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "properties": {},
            "geometry": {
                "coordinates": [
                    [
                        [-122.44429382986985, 37.81964485838134],
                        [-122.53122643397364, 37.788427732684966],
                        [-122.50990691298375, 37.68952854933407],
                        [-122.49092010922561, 37.64775768422055],
                        [-122.35255325612343, 37.648179496058006],
                        [-122.33880916574914, 37.720239370115394],
                        [-122.36423573112428, 37.786798465627456],
                        [-122.39984452556665, 37.8209585063379],
                        [-122.44429382986985, 37.81964485838134],
                    ]
                ],
                "type": "Polygon",
            },
        }
    ],
}

m = folium.Map(location=[37.7749, -122.4194], zoom_start=10)
folium.GeoJson(geojson_data, name="GeoJSON Layer").add_to(m)
m
```

### Creating a Choropleth Map

```{code-cell} ipython3
import requests

m = folium.Map([43, -100], zoom_start=4)

us_states = requests.get(
    "https://raw.githubusercontent.com/python-visualization/folium-example-data/main/us_states.json"
).json()

folium.Choropleth(
    geo_data=us_states,
    fill_opacity=0.3,
    line_weight=2,
).add_to(m)

m
```

```{code-cell} ipython3
import pandas

state_data = pandas.read_csv(
    "https://raw.githubusercontent.com/python-visualization/folium-example-data/main/us_unemployment_oct_2012.csv"
)

m = folium.Map([43, -100], zoom_start=4)

folium.Choropleth(
    geo_data=us_states,
    data=state_data,
    columns=["State", "Unemployment"],
    key_on="feature.id",
).add_to(m)

m
```

## 5. Customizing Map Tiles
Folium allows switching between different map tiles:

```{code-cell} ipython3
m = folium.Map(location=[37.7749, -122.4194], zoom_start=10, tiles="Esri.WorldImagery")
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
