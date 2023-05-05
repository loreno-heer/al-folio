---
layout: post
title: Python in Markdown for live code
date: 2023-05-05 11:12:00+0200
description: Markdown offers plenty of options to add graphics and dynamic content
tags: math, physics, graphics
categories: drafts, publications
related_posts: false
---

Examples taken from respective websites.
Gantt chart using mermaid:

{% raw %}
```
{% mermaid %}
gantt
    dateFormat  YYYY-MM-DD
    title       Adding GANTT diagram functionality to mermaid

    section A section
    Completed task            :done,    des1, 2014-01-06,2014-01-08
    Active task               :active,  des2, 2014-01-09, 3d
    Future task               :         des3, after des2, 5d
    Future task2              :         des4, after des3, 5d

    section Critical tasks
    Completed task in the critical line :crit, done, 2014-01-06,24h
    Implement parser and jison          :crit, done, after des1, 2d
    Create tests for parser             :crit, active, 3d
    Future task in critical line        :crit, 5d
    Create tests for renderer           :2d
    Add to mermaid                      :1d
    Functionality added                 :milestone, 2014-01-25, 0d

    section Documentation
    Describe gantt syntax               :active, a1, after des1, 3d
    Add gantt diagram to demo page      :after a1  , 20h
    Add another diagram to demo page    :doc1, after a1  , 48h

    section Last section
    Describe gantt syntax               :after doc1, 3d
    Add gantt diagram to demo page      :20h
    Add another diagram to demo page    :48h
{% endmermaid %}
```
{% endraw %}

{% mermaid %}
gantt
    dateFormat  YYYY-MM-DD
    title       Adding GANTT diagram functionality to mermaid

    section A section
    Completed task            :done,    des1, 2014-01-06,2014-01-08
    Active task               :active,  des2, 2014-01-09, 3d
    Future task               :         des3, after des2, 5d
    Future task2              :         des4, after des3, 5d

    section Critical tasks
    Completed task in the critical line :crit, done, 2014-01-06,24h
    Implement parser and jison          :crit, done, after des1, 2d
    Create tests for parser             :crit, active, 3d
    Future task in critical line        :crit, 5d
    Create tests for renderer           :2d
    Add to mermaid                      :1d
    Functionality added                 :milestone, 2014-01-25, 0d

    section Documentation
    Describe gantt syntax               :active, a1, after des1, 3d
    Add gantt diagram to demo page      :after a1  , 20h
    Add another diagram to demo page    :doc1, after a1  , 48h

    section Last section
    Describe gantt syntax               :after doc1, 3d
    Add gantt diagram to demo page      :20h
    Add another diagram to demo page    :48h
{% endmermaid %}

{% raw %}
```
{% vegalite  %}
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "data": {
    "url": "data/stocks.csv"
  },
  "width": 400,
  "height": 300,
  "layer": [
    {
      "encoding": {
        "x": {"field": "date", "type": "temporal"},
        "y": {"field": "price", "type": "quantitative"},
        "color": {"field": "symbol", "type": "nominal"}
      },
      "layer": [
        {"mark": "line"},
        {
          "params": [{
            "name": "label",
            "select": {
              "type": "point",
              "encodings": ["x"],
              "nearest": true,
              "on": "mouseover"
            }
          }],
          "mark": "point",
          "encoding": {
            "opacity": {
              "condition": {
                "param": "label",
                "empty": false,
                "value": 1
              },
              "value": 0
            }
          }
        }
      ]
    },
    {
      "transform": [{"filter": {"param": "label", "empty": false}}],
      "layer": [
        {
          "mark": {"type": "rule", "color": "gray"},
          "encoding": {
            "x": {"type": "temporal", "field": "date", "aggregate": "min"}
          }
        },
        {
          "encoding": {
            "text": {"type": "quantitative", "field": "price"},
            "x": {"type": "temporal", "field": "date"},
            "y": {"type": "quantitative", "field": "price"}
          },
          "layer": [
            {
              "mark": {
                "type": "text",
                "stroke": "white",
                "strokeWidth": 2,
                "align": "left",
                "dx": 5,
                "dy": -5
              }
            },
            {
              "mark": {"type": "text", "align": "left", "dx": 5, "dy": -5},
              "encoding": {
                "color": {"type": "nominal", "field": "symbol"}
              }
            }
          ]
        }
      ]
    }
  ]
}
{% endvegalite %}
```
{% endraw %}


{% vegalite  %}
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "data": {
    "url": "data/stocks.csv"
  },
  "width": 400,
  "height": 300,
  "layer": [
    {
      "encoding": {
        "x": {"field": "date", "type": "temporal"},
        "y": {"field": "price", "type": "quantitative"},
        "color": {"field": "symbol", "type": "nominal"}
      },
      "layer": [
        {"mark": "line"},
        {
          "params": [{
            "name": "label",
            "select": {
              "type": "point",
              "encodings": ["x"],
              "nearest": true,
              "on": "mouseover"
            }
          }],
          "mark": "point",
          "encoding": {
            "opacity": {
              "condition": {
                "param": "label",
                "empty": false,
                "value": 1
              },
              "value": 0
            }
          }
        }
      ]
    },
    {
      "transform": [{"filter": {"param": "label", "empty": false}}],
      "layer": [
        {
          "mark": {"type": "rule", "color": "gray"},
          "encoding": {
            "x": {"type": "temporal", "field": "date", "aggregate": "min"}
          }
        },
        {
          "encoding": {
            "text": {"type": "quantitative", "field": "price"},
            "x": {"type": "temporal", "field": "date"},
            "y": {"type": "quantitative", "field": "price"}
          },
          "layer": [
            {
              "mark": {
                "type": "text",
                "stroke": "white",
                "strokeWidth": 2,
                "align": "left",
                "dx": 5,
                "dy": -5
              }
            },
            {
              "mark": {"type": "text", "align": "left", "dx": 5, "dy": -5},
              "encoding": {
                "color": {"type": "nominal", "field": "symbol"}
              }
            }
          ]
        }
      ]
    }
  ]
}
{% endvegalite %}

{% raw %}
```
{% vegalite  %}
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "repeat": {
    "row": ["Horsepower", "Acceleration", "Miles_per_Gallon"],
    "column": ["Miles_per_Gallon", "Acceleration", "Horsepower"]
  },
  "spec": {
    "data": {"url": "data/cars.json"},
    "mark": "point",
    "params": [
      {
        "name": "brush",
        "select": {
          "type": "interval",
          "resolve": "union",
          "on": "[mousedown[event.shiftKey], window:mouseup] > window:mousemove!",
          "translate": "[mousedown[event.shiftKey], window:mouseup] > window:mousemove!",
          "zoom": "wheel![event.shiftKey]"
        }
      },
      {
        "name": "grid",
        "select": {
          "type": "interval",
          "resolve": "global",
          "translate": "[mousedown[!event.shiftKey], window:mouseup] > window:mousemove!",
          "zoom": "wheel![!event.shiftKey]"
        },
        "bind": "scales"
      }
    ],
    "encoding": {
      "x": {"field": {"repeat": "column"}, "type": "quantitative"},
      "y": {
        "field": {"repeat": "row"},
        "type": "quantitative",
        "axis": {"minExtent": 30}
      },
      "color": {
        "condition": {
          "param": "brush",
          "field": "Origin",
          "type": "nominal"
        },
        "value": "grey"
      }
    }
  }
}
{% endvegalite %}
```
{% endraw %}

{% vegalite  %}
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "repeat": {
    "row": ["Horsepower", "Acceleration", "Miles_per_Gallon"],
    "column": ["Miles_per_Gallon", "Acceleration", "Horsepower"]
  },
  "spec": {
    "data": {"url": "data/cars.json"},
    "mark": "point",
    "params": [
      {
        "name": "brush",
        "select": {
          "type": "interval",
          "resolve": "union",
          "on": "[mousedown[event.shiftKey], window:mouseup] > window:mousemove!",
          "translate": "[mousedown[event.shiftKey], window:mouseup] > window:mousemove!",
          "zoom": "wheel![event.shiftKey]"
        }
      },
      {
        "name": "grid",
        "select": {
          "type": "interval",
          "resolve": "global",
          "translate": "[mousedown[!event.shiftKey], window:mouseup] > window:mousemove!",
          "zoom": "wheel![!event.shiftKey]"
        },
        "bind": "scales"
      }
    ],
    "encoding": {
      "x": {"field": {"repeat": "column"}, "type": "quantitative"},
      "y": {
        "field": {"repeat": "row"},
        "type": "quantitative",
        "axis": {"minExtent": 30}
      },
      "color": {
        "condition": {
          "param": "brush",
          "field": "Origin",
          "type": "nominal"
        },
        "value": "grey"
      }
    }
  }
}
{% endvegalite %}



{% raw %}
```
{% vegalite  %}
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "description": "A dashboard with cross-highlighting.",
  "data": {"url": "data/movies.json"},
  "vconcat": [
    {
      "layer": [{
        "mark": "rect",
        "encoding": {
          "x": {
            "bin": {"maxbins": 10},
            "field": "IMDB Rating"
          },
          "y": {
            "bin": {"maxbins": 10},
            "field": "Rotten Tomatoes Rating"
          },
          "color": {
            "aggregate": "count",
            "legend": {
              "title": "All Movies Count",
              "direction": "horizontal",
              "gradientLength": 120
            }
          }
        }
      }, {
        "transform": [{
          "filter": {"param": "pts"}
        }],
        "mark": "point",
        "encoding": {
          "x": {
            "bin": {"maxbins": 10},
            "field": "IMDB Rating"
          },
          "y": {
            "bin": {"maxbins": 10},
            "field": "Rotten Tomatoes Rating"
          },
          "size": {
            "aggregate": "count",
            "legend": {"title": "Selected Category Count"}
          },
          "color": {
            "value": "#666"
          }
        }
      }]
    }, {
      "width": 330,
      "height": 120,
      "mark": "bar",
      "params": [{
        "name": "pts",
        "select": {"type": "point", "encodings": ["x"]}
      }],
      "encoding": {
        "x": {"field": "Major Genre", "axis": {"labelAngle": -40}},
        "y": {"aggregate": "count"},
        "color": {
          "condition": {
            "param": "pts",
            "value": "steelblue"
          },
          "value": "grey"
        }
      }
    }
  ],
  "resolve": {
    "legend": {
      "color": "independent",
      "size": "independent"
    }
  }
}

{% endvegalite %}
```
{% endraw %}

{% vegalite  %}
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "description": "A dashboard with cross-highlighting.",
  "data": {"url": "data/movies.json"},
  "vconcat": [
    {
      "layer": [{
        "mark": "rect",
        "encoding": {
          "x": {
            "bin": {"maxbins": 10},
            "field": "IMDB Rating"
          },
          "y": {
            "bin": {"maxbins": 10},
            "field": "Rotten Tomatoes Rating"
          },
          "color": {
            "aggregate": "count",
            "legend": {
              "title": "All Movies Count",
              "direction": "horizontal",
              "gradientLength": 120
            }
          }
        }
      }, {
        "transform": [{
          "filter": {"param": "pts"}
        }],
        "mark": "point",
        "encoding": {
          "x": {
            "bin": {"maxbins": 10},
            "field": "IMDB Rating"
          },
          "y": {
            "bin": {"maxbins": 10},
            "field": "Rotten Tomatoes Rating"
          },
          "size": {
            "aggregate": "count",
            "legend": {"title": "Selected Category Count"}
          },
          "color": {
            "value": "#666"
          }
        }
      }]
    }, {
      "width": 330,
      "height": 120,
      "mark": "bar",
      "params": [{
        "name": "pts",
        "select": {"type": "point", "encodings": ["x"]}
      }],
      "encoding": {
        "x": {"field": "Major Genre", "axis": {"labelAngle": -40}},
        "y": {"aggregate": "count"},
        "color": {
          "condition": {
            "param": "pts",
            "value": "steelblue"
          },
          "value": "grey"
        }
      }
    }
  ],
  "resolve": {
    "legend": {
      "color": "independent",
      "size": "independent"
    }
  }
}

{% endvegalite %}

Using python using pyscript. Example from PyScript website.

```html
<html>
  <head>
    <title>Ice Cream Picker</title>
    <meta charset="utf-8">
    <link rel="stylesheet" href="https://pyscript.net/latest/pyscript.css" />
    <script defer src="https://pyscript.net/latest/pyscript.js"></script>
  </head>
  <body>

    <py-config>
      packages = ["matplotlib", "pandas"]
    </py-config>

    <py-script>
      import js
      import pandas as pd
      import matplotlib.pyplot as plt

      from pyodide.http import open_url
      from pyodide.ffi import create_proxy

      url = (
          "https://raw.githubusercontent.com/Cheukting/pyscript-ice-cream/main/bj-products.csv"
      )
      ice_data = pd.read_csv(open_url(url))

      current_selected = []
      flavour_elements = js.document.getElementsByName("flavour")

      def plot(data):
          plt.rcParams["figure.figsize"] = (22,20)
          fig, ax = plt.subplots()
          bars = ax.barh(data["name"], data["rating"], height=0.7)
          ax.bar_label(bars)
          plt.title("Rating of ice cream flavours of your choice")
          display(fig, target="graph-area", append=False)

      def select_flavour(event):
          for ele in flavour_elements:
              if ele.checked:
                  current_selected = ele.value
                  break
          if current_selected == "ALL":
              plot(ice_data)
          else:
              filter = ice_data.apply(lambda x: ele.value in x["ingredients"], axis=1)
              plot(ice_data[filter])

      ele_proxy = create_proxy(select_flavour)

      for ele in flavour_elements:
          if ele.value == "ALL":
            ele.checked = True
            current_selected = ele.value
          ele.addEventListener("change", ele_proxy)

      plot(ice_data)

    </py-script>

    <div id="input" style="margin: 20px;">
      Select your 🍨 flavour: <br/>
      <input type="radio" id="all" name="flavour" value="ALL">
      <label for="all"> All 🍧</label>
      <input type="radio" id="chocolate" name="flavour" value="COCOA">
      <label for="chocolate"> Chocolate 🍫</label>
      <input type="radio" id="cherrie" name="flavour" value="CHERRIES">
      <label for="cherrie"> Cherries 🍒</label>
      <input type="radio" id="berries" name="flavour" value="BERRY">
      <label for="berries"> Berries 🍓</label>
      <input type="radio" id="cheese" name="flavour" value="CHEESE">
      <label for="cheese"> Cheese 🧀</label>
      <input type="radio" id="peanut" name="flavour" value="PEANUT">
      <label for="peanut"> Peanut 🥜</label>
    </div>

    <py-repl>
      ice_data
    </py-repl>

    <div id="graph-area"></div>
  </body>
</html>
```

<html>
  <head>
    <title>Ice Cream Picker</title>
    <meta charset="utf-8">
    <link rel="stylesheet" href="https://pyscript.net/latest/pyscript.css" />
    <script defer src="https://pyscript.net/latest/pyscript.js"></script>
  </head>
  <body>

    <py-config>
      packages = ["matplotlib", "pandas"]
    </py-config>

    <py-script>
      import js
      import pandas as pd
      import matplotlib.pyplot as plt

      from pyodide.http import open_url
      from pyodide.ffi import create_proxy

      url = (
          "https://raw.githubusercontent.com/Cheukting/pyscript-ice-cream/main/bj-products.csv"
      )
      ice_data = pd.read_csv(open_url(url))

      current_selected = []
      flavour_elements = js.document.getElementsByName("flavour")

      def plot(data):
          plt.rcParams["figure.figsize"] = (22,20)
          fig, ax = plt.subplots()
          bars = ax.barh(data["name"], data["rating"], height=0.7)
          ax.bar_label(bars)
          plt.title("Rating of ice cream flavours of your choice")
          display(fig, target="graph-area", append=False)

      def select_flavour(event):
          for ele in flavour_elements:
              if ele.checked:
                  current_selected = ele.value
                  break
          if current_selected == "ALL":
              plot(ice_data)
          else:
              filter = ice_data.apply(lambda x: ele.value in x["ingredients"], axis=1)
              plot(ice_data[filter])

      ele_proxy = create_proxy(select_flavour)

      for ele in flavour_elements:
          if ele.value == "ALL":
            ele.checked = True
            current_selected = ele.value
          ele.addEventListener("change", ele_proxy)

      plot(ice_data)

    </py-script>

    <div id="input" style="margin: 20px;">
      Select your 🍨 flavour: <br/>
      <input type="radio" id="all" name="flavour" value="ALL">
      <label for="all"> All 🍧</label>
      <input type="radio" id="chocolate" name="flavour" value="COCOA">
      <label for="chocolate"> Chocolate 🍫</label>
      <input type="radio" id="cherrie" name="flavour" value="CHERRIES">
      <label for="cherrie"> Cherries 🍒</label>
      <input type="radio" id="berries" name="flavour" value="BERRY">
      <label for="berries"> Berries 🍓</label>
      <input type="radio" id="cheese" name="flavour" value="CHEESE">
      <label for="cheese"> Cheese 🧀</label>
      <input type="radio" id="peanut" name="flavour" value="PEANUT">
      <label for="peanut"> Peanut 🥜</label>
    </div>

    <py-repl>
      ice_data
    </py-repl>

    <div id="graph-area"></div>
  </body>
</html>
