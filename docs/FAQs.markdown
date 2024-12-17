---
layout: page
title: 6. FAQs
permalink: /profiles/
---

# FAQs

## Profiles

### A word of caution: Local X-Z Orientation Mode

The Local X-Z Orientation Mode (`--orientation=localxz`) option is used in survey2gis commands to transform 3D survey data into 2D cross-sections suitable for GIS visualization. This method:

- Swaps the Z and Y axes.
- Recalculates X coordinates, starting from 0.
- Preserves the original Z values, enabling side-by-side dataset comparisons.

**Important Note**
When using this mode, your GIS data loses its real-world spatial reference. To ensure proper visualization, we recommend one of the following:

1. **Disable KBS**\
Go to the menu item `KBS` and select `No KBS in project settings`.
1. **Specify a Projection**\
Use the EPSG Code field in the _Process_ tab to define the projection of your input data.

If neither option is set, the layers might not appear in QGIS.

## Important Note for Linux and Mac Users
There is a known bug in Survey2GIS on Linux and Mac systems that can cause processing issues. When this occurs, Survey2GIS may continue running in the background without the extension being able to detect it.

**Temporary Workaround:**  
Add the `-i .` and `-g ,` options to your Survey2GIS commands.

For more details about this issue, please visit:  [https://groups.io/g/survey2gis](https://groups.io/g/survey2gis/topic/survey2gis_problems_with_test/106905239)