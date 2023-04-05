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
     
```     
import plotly.graph_objects as go

# Define the labels, source, target, and value for each link
labels = ['Donors', 'General Population', 'Healthy Controls', 'Centers for Medicare', 
          'National Death Index', 'ESRD', 'Death']
source = [0, 1, 2, 0, 1, 2, 3, 4]
target = [3, 3, 3, 4, 4, 4, 5, 6]
value = [57.1, 38.1, 4.8, 57.1, 38.1, 4.8, 10, 90]

# Define the color for each node
color = ['#aec7e8', '#ffbb78', '#98df8a', '#ff9896', '#c5b0d5', '#c49c94', '#c7c7c7']

# Create the Sankey diagram figure
fig = go.Figure(data=[go.Sankey(
    node = dict(
      pad = 15,
      thickness = 20,
      line = dict(color = "black", width = 0.5),
      label = labels,
      color = color
    ),
    link = dict(
      source = source,
      target = target,
      value = value,
      color = color
  ))])

# Customize the figure layout
fig.update_layout(
    title={
        'text': "Interactive Sankey Diagram",
        'x': 0.5,
        'y': 0.9,
        'font': {'size': 24}
    },
    font=dict(size=14),
    height=600,
    width=800,
    margin=dict(l=50, r=50, t=50, b=50)
)

# Display the Sankey diagram
fig.show()

```

[^1]: An issue of [resilience](https://journals.lww.com/journalacs/Abstract/2010/06000/Frailty_as_a_Predictor_of_Surgical_Outcomes_in.3.aspx) to surgical stress
