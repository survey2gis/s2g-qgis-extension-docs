---
layout: page
title: 6. Profiles
permalink: /profiles/
---

# 6. Profiles

### A word of Caution: Local X-Z Orientation Mode

The Local X-Z Orientation Mode (localxz) option is used in survey2gis commands to transform 3D survey data into 2D cross-sections suitable for GIS visualization. This method:

- Swaps the Z and Y axes.
- Recalculates X coordinates, starting from 0.
- Preserves the original Z values, enabling side-by-side dataset comparisons.

**Important Note**
When using this mode, your GIS data loses its real-world spatial reference. To ensure proper visualization, we recommend one of the following:

1. **Disable KBS**\
Go to the menu item KBS and select No KBS in project settings.
1. **Specify a Projection**\
Use the EPSG Code field in the Process tab to define the projection of your input data.

If neither option is set, the layers might not appear in QGIS.