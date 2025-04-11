# Lab 8

In this lab, you'll enrich your interactive map by implementing a **dynamic basemap selector** using a dropdown menu. You’ll also practice writing proper docstrings and showcasing your work in a **shareable Colab notebook**.

---

## Objectives

By the end of this lab, you will be able to:

- Add an interactive dropdown for switching basemaps.
- Implement a close/hide button to control UI elements.
- Write clear and professional docstrings.
- Share your work via a Google Colab notebook with an embedded badge.

---

## 🛠️ Task Instructions

### 1. **Create a Basemap Selection Dropdown**

- Add a dropdown widget that lets users choose from at least the following basemaps:
  - `"OpenStreetMap"`
  - `"OpenTopoMap"`
  - `"Esri.WorldImagery"`
  - `"CartoDB.DarkMatter"`
- Ensure that the selected basemap updates the map dynamically.

### 2. **Add a Close/Toggle Button for the Dropdown**

- Implement a button to **close the dropdown menu**.
- This allows users to remove the dropdown from the UI when not needed.

### 3. **Add Docstrings to Your Functions**

- Write proper Python docstrings for all custom functions or classes.
- Your docstrings should describe:
  - The purpose of the function.
  - The parameters (with types).
  - The return value (if any).

📌 Example format:

```python
def add_basemap_gui(self, position="topright"):
    """
    Adds the selected basemap to the map.

    Params:
        position (str): Position of the dropdown menu on the map.

    Returns:
        None
    """
```

### 4. **Create and Share a Google Colab Notebook**

- Create a notebook that demonstrates:
  - The interactive dropdown functionality.
  - The toggle button for hiding/showing the UI.
- Add an **"Open in Colab" badge** at the top so users can easily run it themselves.

🔗 **Instructions to add a Colab badge**:

```markdown
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](YOUR_NOTEBOOK_LINK_HERE)
```

## 📝 Submission Checklist

Your submission should include links to the following:

- A GitHub link to your added functionality in the `Map` class
- A link to the Jupyter Notebook demonstrating the new functionalities on your package website
