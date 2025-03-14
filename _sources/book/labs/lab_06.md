# **Lab 6**

## **Overview**

In this lab, you will extend your Python package by adding mapping functionalities. This package will be used throughout the rest of the semester, with new features added each week.

For this lab, you will:

1. Implement an interactive `Map` class using both `ipyleaflet` and `folium`.
2. Add essential methods for basemaps, layers, and controls.
3. Document the package with proper docstrings and a Jupyter Notebook tutorial.
4. Create a new release on GitHub Use GitHub Actions to publish your package on PyPI.

---

## **Task 1: Implement the Map Class (ipyleaflet)**

Enhance your package by adding a `Map` class that inherits from `ipyleaflet.Map` and provides the following functionalities:

- **Basemap Support:** Implement an `add_basemap` method that allows users to add a basemap by specifying its name as a string (e.g., `"OpenStreetMap"`, `"Esri.WorldImagery"`, `"OpenTopoMap"`).
- **Layer Control:** Implement an `add_layer_control` method that adds a layer control widget for managing map layers.
- **Vector Data Support:** Implement an `add_vector` method to add vector data in any format supported by `GeoPandas` (e.g., GeoJSON, Shapefile).

Ensure all methods include **docstrings** explaining their purpose, parameters, and return values.

---

## **Task 2: Implement the Map Class (folium)**

Repeat **Task 1** but using `folium.Map` instead of `ipyleaflet.Map`. Ensure that the `folium`-based map class includes similar methods (`add_basemap`, `add_layer_control`, and `add_vector`).

---

## **Task 3: Documentation and Notebook Example**

- Add a **Jupyter Notebook** to the package that demonstrates the functionalities of your `Map` class for both `ipyleaflet` and `folium`.
- Ensure the notebook is included in the package documentation and accessible via an **Open in Colab** badge.

---

## **Task 4: Package Deployment and Release**

- Bump your package version using bump-my-version.
- Automate the package deployment process to PyPI.
- Create a **new release on GitHub** with automatic deployment to PyPI.

---

## **Submission Requirements**

Submit the following:

1. **Link to the package's main module documentation** (e.g., https://geodev.gishub.org/geodev).
2. **Link to the package's folium module documentation** (e.g., https://geodev.gishub.org/foliumap`).
3. **Link to the Jupyter Notebook example** demonstrating the functionality (e.g.,https://geodev.gishub.org/examples/map/).
4. **Link to the PyPI release** of the package (e.g., https://github.com/giswqs/geodev/releases).
