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

# Ipywidgets

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/giswqs/geog-510/blob/main/book/geospatial/ipywidgets.ipynb)

+++

## Import libraries

```{code-cell} ipython3
# !pip install geohey
```

```{code-cell} ipython3
import geohey
```

## Create an interactive map

```{code-cell} ipython3
m = geohey.Map()
m
```

```{code-cell} ipython3
url = "https://opendata.digitalglobe.com/events/mauritius-oil-spill/post-event/2020-08-12/105001001F1B5B00/105001001F1B5B00.tif"
# m.add_raster(url, name='Raster', fit_bounds=True)
```

## Change layer opacity

```{code-cell} ipython3
m.layers
```

```{code-cell} ipython3
raster_layer = m.layers[-1]
raster_layer.interact(opacity=(0, 1, 0.1))
```

## Widget list

Widget list: https://ipywidgets.readthedocs.io/en/latest/examples/Widget%20List.html

Icons: https://fontawesome.com/v4.7.0/icons

### Numeric widgets

#### IntSlider

```{code-cell} ipython3
import ipywidgets as widgets
```

```{code-cell} ipython3
int_slider = widgets.IntSlider(
    value=2000, min=1984, max=2020, step=1, description="Year:"
)
int_slider
```

```{code-cell} ipython3
int_slider
```

```{code-cell} ipython3
int_slider.value
```

```{code-cell} ipython3
int_slider.value = 2019
```

#### FloatSlider

```{code-cell} ipython3
float_slider = widgets.FloatSlider(
    value=0, min=-1, max=1, step=0.05, description="Threshold:"
)
float_slider
```

```{code-cell} ipython3
float_slider.value
```

#### IntProgress

```{code-cell} ipython3
int_progress = widgets.IntProgress(
    value=7,
    min=0,
    max=10,
    step=1,
    description="Loading:",
    bar_style="",  # 'success', 'info', 'warning', 'danger' or ''
    orientation="horizontal",
)
int_progress
```

```{code-cell} ipython3
int_progress.value = 10
```

```{code-cell} ipython3
int_text = widgets.IntText(
    value=7,
    description="Any:",
)
int_text
```

```{code-cell} ipython3
float_text = widgets.FloatText(
    value=7.5,
    step=2,
    description="Any:",
)
float_text
```

### Boolean widgets

#### ToggleButton

```{code-cell} ipython3
toggle_button = widgets.ToggleButton(
    value=False,
    description="Click me",
    disabled=False,
    button_style="warning",  # 'success', 'info', 'warning', 'danger' or ''
    tooltip="Description",
    icon="map",  # (FontAwesome names without the `fa-` prefix)
)
toggle_button
```

```{code-cell} ipython3
toggle_button.value
```

#### Checkbox

```{code-cell} ipython3
checkbox = widgets.Checkbox(
    value=False, description="Check me", disabled=False, indent=False
)
checkbox
```

```{code-cell} ipython3
checkbox.value
```

### Selection widgets

#### Dropdown

```{code-cell} ipython3
dropdown = widgets.Dropdown(
    options=["USA", "Canada", "Mexico"], value="Canada", description="Country:"
)
dropdown
```

```{code-cell} ipython3
dropdown.value
```

#### RadioButtons

```{code-cell} ipython3
radio_buttons = widgets.RadioButtons(
    options=["USA", "Canada", "Mexico"], value="Canada", description="Country:"
)
radio_buttons
```

```{code-cell} ipython3
radio_buttons.value
```

### String widgets

#### Text

```{code-cell} ipython3
text = widgets.Text(
    value="",
    placeholder="Enter a country name",
    description="Country:",
    disabled=False,
)
text
```

```{code-cell} ipython3
text.value
```

#### Textarea

```{code-cell} ipython3
widgets.Textarea(
    value="Hello World",
    placeholder="Type something",
    description="String:",
    disabled=False,
)
```

#### HTML

```{code-cell} ipython3
widgets.HTML(
    value="Hello <b>World</b>",
    placeholder="Some HTML",
    description="Some HTML",
)
```

```{code-cell} ipython3
widgets.HTML(
    value='<img src="https://earthengine.google.com/static/images/earth-engine-logo.png" width="200" height="200">'
)
```

### Button

```{code-cell} ipython3
button = widgets.Button(
    description="",
    button_style="primary",  # 'success', 'info', 'warning', 'danger' or ''
    tooltip="Click me",
    icon="wrench",  # (FontAwesome names without the `fa-` prefix)
)
button.layout.width = "35px"
button
```

### Date picker

```{code-cell} ipython3
date_picker = widgets.DatePicker(description="Pick a Date", disabled=False)
date_picker
```

```{code-cell} ipython3
date_picker.value
```

### Color picker

```{code-cell} ipython3
color_picker = widgets.ColorPicker(
    concise=False, description="Pick a color", value="blue", disabled=False
)
color_picker
```

```{code-cell} ipython3
color_picker.value
```

### Output widget

```{code-cell} ipython3
out = widgets.Output(layout={"border": "1px solid black"})
out
```

```{code-cell} ipython3
with out:
    out.clear_output()
    for i in range(10):
        print(i, "Hello world!")

    display(widgets.IntSlider())
    display(widgets.Button(description="Hello"))
```

```{code-cell} ipython3
from IPython.display import YouTubeVideo

out.clear_output()
with out:
    display(YouTubeVideo("mA21Us_3m28"))
out
```

```{code-cell} ipython3
out.clear_output()
with out:
    display(widgets.IntSlider())
out
```

## Add a widget to the map

```{code-cell} ipython3
import ipywidgets as widgets
from ipyleaflet import WidgetControl
```

```{code-cell} ipython3

```

```{code-cell} ipython3
m = geohey.Map()
m
```

```{code-cell} ipython3
output_widget = widgets.Output(layout={"border": "1px solid black"})
output_control = WidgetControl(widget=output_widget, position="bottomright")
m.add_control(output_control)
```

```{code-cell} ipython3
with output_widget:
    print("Nice map!")
```

```{code-cell} ipython3
output_widget.clear_output()
logo = widgets.HTML(
    value='<img src="https://earthengine.google.com/static/images/earth-engine-logo.png" width="100" height="100">'
)
with output_widget:
    display(logo)
```

```{code-cell} ipython3
def handle_interaction(**kwargs):
    latlon = kwargs.get("coordinates")
    # latlon = [round(x, 2) for x in latlon]
    if kwargs.get("type") == "click":
        with output_widget:
            output_widget.clear_output()
            print("You clicked at: {}".format(latlon))


m.on_interaction(handle_interaction)
```

```{code-cell} ipython3
items = [widgets.Button(description=str(i + 1)) for i in range(4)]
widgets.HBox(items)
```

```{code-cell} ipython3
items = [widgets.Button(description=str(i + 1)) for i in range(4)]
widgets.VBox(items)
```

```{code-cell} ipython3
btn = widgets.Button(icon="times", button_style="primary")
btn.layout.width = "35px"
btn
```

```{code-cell} ipython3
dropdown = widgets.Dropdown(
    options=["OpenStreetMap", "OpenTopoMap", "Esri.WorldImagery"],
    value="OpenStreetMap",
)
dropdown.layout.width = "150px"
dropdown
```

```{code-cell} ipython3
box = widgets.HBox([dropdown, btn])
box
```

```{code-cell} ipython3
m = geohey.Map()
m
```

```{code-cell} ipython3
m.add_widget(box)
```

```{code-cell} ipython3
m.controls = m.controls[:-1]
```
