# QGIS

[QGIS](https://qgis.org/) is a powerful, free, and open-source Geographic Information System (GIS) platform used for spatial data visualization, analysis, and cartographic mapping. It supports a variety of spatial formats and integrates seamlessly with Python for advanced customization and automation.

## Installation

Follow these steps to install QGIS on your system:

1. **Download QGIS:**

   - Visit the [QGIS download page](https://qgis.org/en/site/forusers/download.html).
   - Choose the appropriate version for your operating system (Windows, macOS, or Linux).

2. **Install QGIS:**

   - Run the installer and follow the setup instructions.
   - For Windows users, it is recommended to install the Long Term Release (LTR) version for stability.

3. **Verify Installation:**
   - Open QGIS after installation.
   - Ensure that the interface loads successfully with components such as the Browser Panel, Layers Panel, and Map Canvas visible.

---

## Adding Basemaps to QGIS

Basemaps are essential for providing geographic context to spatial data. QGIS does not come with a lot of built-in basemaps, but you can add them using the following steps:

### Steps to Add Basemaps

1. **Download the Python Script:**

   - Download the script [qgis_basemaps.py](https://github.com/opengeos/qgis-basemaps/blob/main/qgis_basemaps.py) from the [qgis-basemaps](https://github.com/opengeos/qgis-basemaps) repository to your local machine.

2. **Open the Python Console in QGIS:**

   - In QGIS, go to **Plugins > Python Console** to open the Python Console.

3. **Load the Script into the Python Editor:**

   - In the Python Console, click on the **Show Editor** button (a small pencil icon).
   - Load the downloaded `qgis_basemaps.py` script into the Python Editor.

4. **Run the Script:**

   - Click the **Run script** button (a green play icon) in the Python Editor.
   - This will add a variety of basemaps (e.g., OpenStreetMap, Google Maps) as XYZ Tiles to QGIS.

5. **Restart QGIS:**
   - Close and reopen QGIS to see the new basemaps in the **XYZ Tiles** section of the Browser Panel.

### Example of Added Basemaps

Once added, you can drag and drop basemaps from the **XYZ Tiles** section into the Map Canvas.

![Added basemaps](https://github.com/user-attachments/assets/90062fa8-ab18-4e9e-9724-8c7bbdbb1f4b)

---

## Using QGIS for Spatial Data Visualization

### Loading Spatial Data

1. Open the **Browser Panel** in QGIS.
2. Navigate to your data source (e.g., Shapefile, GeoJSON, GeoPackage, or CSV).
3. Drag and drop the dataset into the **Map Canvas** or right-click and select **Add Layer to Canvas**.

### Styling Spatial Data

1. Right-click on the layer in the **Layers Panel** and select **Properties**.
2. Go to the **Symbology** tab to customize the layer style (e.g., color, line thickness, fill pattern).
3. Experiment with **Graduated** or **Categorized** styles for thematic mapping.

### Basic Analysis

1. Open the **Processing Toolbox** (Ctrl+Alt+T or from the main menu under **Processing**).
2. Use tools like:
   - **Buffer**: Create buffer zones around features.
   - **Clip**: Extract features within a specific boundary.
   - **Intersect**: Find overlapping features between layers.

---

## Additional Resources

1. **Official QGIS Documentation:**

   - [https://qgis.org/en/docs/](https://qgis.org/en/docs/)

2. **QGIS Tutorials and Tips:**

   - [https://docs.qgis.org/latest/en/docs/training_manual/](https://docs.qgis.org/latest/en/docs/training_manual/)

3. **PyQGIS Developer Resources:**
   - [https://docs.qgis.org/latest/en/docs/pyqgis_developer_cookbook/](https://docs.qgis.org/latest/en/docs/pyqgis_developer_cookbook/)
