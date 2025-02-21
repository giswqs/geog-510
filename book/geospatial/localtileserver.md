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

# Localtileserver

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/giswqs/geog-510/blob/main/book/geospatial/localtileserver.ipynb)

## Introduction
**localtileserver** is a Python package that enables efficient visualization of large raster datasets, such as GeoTIFFs, using tiled web maps. It can be used in Jupyter notebooks with **ipyleaflet** or **folium**, from the command line in a web browser, and with remote Cloud Optimized GeoTIFFs (COGs).

### Learning Objectives
By the end of this lecture, you will:
- Understand what **localtileserver** is and its use cases.
- Learn how to serve raster data as map tiles.
- Explore integration with **folium** and **ipyleaflet**.
- Customize and optimize raster visualization.

## 1. Installing and Importing localtileserver
To install **localtileserver**, run:

```bash
pip install localtileserver
```

Then, import the required modules:

```{code-cell} ipython3
from localtileserver import (
    TileClient,
    get_leaflet_tile_layer,
    get_folium_tile_layer,
    examples,
)
```

## 2. Serving a Local Raster File

To visualize a GeoTIFF, use the **TileClient**:

```{code-cell} ipython3
client = TileClient("path/to/geo.tif")
print(client.url)  # Prints the local tile service URL
```

Alternatively, you can use example data:

```{code-cell} ipython3
client = examples.get_san_francisco()
client
```

## 3. Retrieving Tiles and Thumbnails

To retrieve a single tile (z, x, y):

```{code-cell} ipython3
client.tile(10, 163, 395)
```

To generate a thumbnail preview:

```{code-cell} ipython3
client.thumbnail()
```

## 4. Integrating with ipyleaflet

To display raster data on an **ipyleaflet** map:

```{code-cell} ipython3
from ipyleaflet import Map

client = examples.get_elevation()
tile_layer = get_leaflet_tile_layer(
    client, indexes=1, vmin=-5000, vmax=5000, opacity=0.65
)

m = Map(zoom=3)
m.add(tile_layer)
m
```

## 5. Integrating with Folium

To display raster data on a **folium** map:

```{code-cell} ipython3
from folium import Map

client = examples.get_oam2()
tile_layer = get_folium_tile_layer(client)

m = Map(location=client.center(), zoom_start=16)
m.add_child(tile_layer)
m
```

## 6. Customizing Tile Rendering

You can apply colormaps and adjust transparency:

```{code-cell} ipython3
client = TileClient("/path/to/your/raster.tif", colormap="viridis")
```

Supported colormaps include any **matplotlib colormap**.

## 7. Serving Remote Raster Data

To serve **Cloud Optimized GeoTIFFs (COGs)**:

```{code-cell} ipython3
client = TileClient("https://example.com/path/to/cog.tif")
```

## 8. Stopping the Server

Once finished, stop the tile server to free up resources:

```{code-cell} ipython3
client.shutdown()
```

## Summary
- **localtileserver** serves raster data as interactive tile layers.
- It integrates seamlessly with **folium** and **ipyleaflet**.
- Supports local and remote raster files, including COGs.
- Allows customization with colormaps and resampling methods.

## Further Reading
- [localtileserver Documentation](https://github.com/banesullivan/localtileserver)
- [Folium Documentation](https://python-visualization.github.io/folium/)
- [ipyleaflet Documentation](https://ipyleaflet.readthedocs.io/)

---

### Assignment
1. Install **localtileserver** and serve a local raster file.
2. Visualize the raster data in both **folium** and **ipyleaflet**.
3. Apply a colormap to customize the visualization.
4. Submit your Jupyter Notebook with the implementation.

### Feedback
If you encounter issues or have feature requests, please open a discussion or issue on the [localtileserver GitHub page](https://github.com/banesullivan/localtileserver/discussions).

For debugging, generate a system report:

```{code-cell} ipython3
import localtileserver

print(localtileserver.Report())
```

Happy Mapping! 🌍
