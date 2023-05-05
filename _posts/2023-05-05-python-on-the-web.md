---
layout: post
title: Python in Markdown for live code
date: 2023-05-05 11:12:00-0400
description: Markdown offers plenty of options to add graphics and dynamic content
tags: math, physics, graphics
categories: drafts, publications
related_posts: false
---

Gantt chart using mermaid:

{% raw %}
```
{% mermaid %}
gantt
    dateFormat  YYYY-MM-DD
    title       Adding GANTT diagram functionality to mermaid
    excludes    weekends
    %% (`excludes` accepts specific dates in YYYY-MM-DD format, days of the week ("sunday") or "weekends", but not the word "weekdays".)

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
    excludes    weekends
    %% (`excludes` accepts specific dates in YYYY-MM-DD format, days of the week ("sunday") or "weekends", but not the word "weekdays".)

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
