---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Study design

Live kidney donors (OPTN), N=180,000

     1. Registry
     2. Screened
     3. Healthy

Matached nondonors (NHANES), N=150,000

     1. Survey
     2. Unscreened

Key outcomes (LINKAGE)

     1. Perioperative complications [^1]
     2. ESRD
     3. Survival
     
```{hide-input}
from IPython.display import HTML

# Define the Sankey diagram as before
import pandas as pd
import plotly.express as px
import plotly.graph_objects as go 
import urllib, json
import numpy as np
import sqlite3 as sq3

label = ['Donors',
         "General Population", 
         "Healthy Controls", 
         "Centers for Medicare",
         "National Death Index", 
         "ESRD", 
         "Death"]

source = [0,1,2,   0,1,2,
          3, 4]  

target = [3,3,3,   4,4,4, 
          5, 6]  

value = [57.1,38.1,4.8,  57.1,38.1,4.8, 
         10,90]   

# Define colors for links and nodes
link_color = ['#1f77b4', '#1f77b4', '#1f77b4', 
              '#ff7f0e', '#ff7f0e', '#ff7f0e', 
              '#2ca02c']
node_color = ['#aec7e8', '#ffbb78', '#98df8a', 
              '#ff9896', '#c5b0d5', '#c49c94', 
              '#c7c7c7']

link = dict(source=source, target=target, value=value, 
            color=link_color)
node = dict(label=label, pad=50, thickness=30, 
            color=node_color, 
            line=dict(color='white', width=0.5))

# Define figure layout
layout = dict(title=dict(text="Sankey Diagram"), 
              font=dict(size=14, family="Arial"), 
              height=600, width=800, 
              margin=dict(l=50, r=50, t=50, b=50))

data = go.Sankey(link=link, node=node)

fig = go.Figure(data=data, layout=layout)

# Save the figure as an HTML file
html_sankey = fig.to_html(full_html=False)

# Embed the HTML file in the Jupyter Book
HTML(html_sankey)
```

graçias, chatGPT!

[^1]: An issue of [resilience](https://journals.lww.com/journalacs/Abstract/2010/06000/Frailty_as_a_Predictor_of_Surgical_Outcomes_in.3.aspx) to surgical stress
