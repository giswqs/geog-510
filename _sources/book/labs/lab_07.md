# Lab 7

## **Overview**

In this lab, you'll extend the functionality of your interactive mapping package by implementing support for raster data, static image overlays, and Web Map Service (WMS) layers. These enhancements will make your package more versatile for real-world geospatial visualization tasks.

---

## Task 1: Add `add_raster()` Method

Implement an `add_raster()` method in your `Map` class to visualize **Cloud Optimized GeoTIFFs (COGs)**.

- Method parameters should include:
  - `url`: path to the COG
  - `name`: optional display name
  - `colormap` (optional): a dictionary or string identifier
  - `opacity`: transparency level

---

## Task 2: Add `add_image()` Method

Implement an `add_image()` method to overlay **static images** or **animated GIFs** on the map.

- Use `ipyleaflet.ImageOverlay`
- Required parameters:
  - `url`: image or GIF URL
  - `bounds`: a tuple of ((south, west), (north, east)) geographic coordinates
  - `opacity`: transparency level

## Task 3: Add `add_video()` Method

Implement an `add_video()` method to overlay **videos** on the map.

- Use `ipyleaflet.VideoOverlay`
- Required parameters:
  - `url`: image or GIF URL
  - `bounds`: a tuple of ((south, west), (north, east)) geographic coordinates
  - `opacity`: transparency level

## Task 4: Add `add_wms_layer()` Method

Add a method to support **WMS (Web Map Service) layers**, commonly used for serving satellite imagery, weather maps, and environmental data.

- Use `ipyleaflet.WMSLayer`
- Parameters to support:
  - `url`: base WMS endpoint
  - `layers`: comma-separated layer names
  - `name`: display name for the layer
  - `format`: (e.g., 'image/png')
  - `transparent`: boolean for layer transparency
- Optionally support additional query string parameters.

---

## 🗂 Submission Checklist

Your submission should include links to the following:

- Updated `Map` class with all four methods:
  - `add_raster()`
  - `add_image()`
  - `add_video()`
  - `add_wms_layer()`
- A Jupyter Notebook demonstrating the new functionalities.
