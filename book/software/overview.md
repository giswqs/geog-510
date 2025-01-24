---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.16.2
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Overview

## Software Tools

In this course, we will use essential software tools that streamline development, version control, and geospatial analysis. Make sure you have these installed and configured:

- **[Visual Studio Code](https://code.visualstudio.com/)**: A lightweight, highly customizable code editor with robust extensions for Python development.
- **[Git](https://git-scm.com/downloads)**: A version control system for tracking code changes and collaborating on projects.
- **[Miniconda](https://docs.conda.io/en/latest/miniconda.html)** or **[Anaconda](https://www.anaconda.com/)**: Python distribution platforms that simplify environment management and package installation.
- **[QGIS](https://qgis.org)**: An open-source GIS software that complements Python tools for geospatial data visualization and analysis.

_Tip:_ If you're new to any of these tools, refer to their official documentation for setup guides or seek tutorials in the course **Software Tools** section.

## Cloud Computing Platforms

Geospatial analysis often involves large datasets and computationally intensive tasks. Cloud platforms provide scalable solutions to handle these efficiently. Here are some popular options:

- **[Google Colab](https://research.google.com/colaboratory)**: A free Jupyter notebook environment with pre-installed Python packages, ideal for coding on the go. _We will primarily use this platform in the course._
- **[Google Earth Engine](https://earthengine.google.com/)**: A cloud-based platform for processing geospatial data, especially remote sensing imagery.
- **[Amazon SageMaker Studio Lab](https://studiolab.sagemaker.aws)**: Offers free cloud computing resources for Python-based machine learning and data analysis.
- **[Microsoft Planetary Computer](https://planetarycomputer.microsoft.com/)**: Provides geospatial datasets and APIs for large-scale environmental analysis.

### Why Use Google Colab?

- **Accessibility:** Works entirely in the browser, so no setup is required.
- **Free Resources:** Includes free access to GPUs/TPUs for advanced computations.
- **Integration:** Supports popular geospatial libraries like GeoPandas, Shapely, and Leafmap out of the box.

To get started, visit [colab.research.google.com](https://colab.research.google.com) and sign in with your Google account.

## Install Python Packages

There are different ways to install Python packages. The most common methods are using `pip` or `conda`. Here are some examples:

To install packages using `pip`:

```bash
pip install leafmap
```

To install packages using `conda`:

```bash
conda install leafmap -c conda-forge
```

To install packages from a GitHub repository:

```bash
pip install git+https://github.com/opengeos/leafmap.git
```

To install packages from a `requirements.txt` file:

```bash
pip install -r requirements.txt
```
