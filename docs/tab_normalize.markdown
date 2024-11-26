---
title: 2. Tab Normalize
permalink: /tab_normalize/
---

# 2. Tab Normalize

The _Normalize_ tab combines individual measurement data into a single file. The combined file can be cleaned up using various tasks. Furthermore, possible *.qml (QGIS) styles can be copied to a defined output folder. 

<img src="/assets/img/normalize.jpg" alt="Normalize GUI" style="border: 1px solid black" />

1. **Open Normalize**\
Click to open the _Normalize_ tool.
2. **Select input files**\
Choose your input files from your hard drive. Supported file extensions are `*.dat` and `*.txt`.
3. **Select the output folder**\
Select the folder where the combined data will be saved.\
> Use the same output folder in the _Process_ tab for all generated `*.shp` files.
1. **Name your output file**\
Give your output file a meaningful name.\
> If you specify a name here, it will also be used in the Process tab for naming the generated GeoPackage.
1. **Add optional QML files**\
If you have a folder containing `*.qml` files (optionally with an svg subfolder), you can select it here. The tool will copy these files to your output folder. If a `*.qml` file matches the name of a generated GIS layer, it will automatically be applied to the layer when loaded in QGIS.
1. **Replace special characters**\
This option replaces the character `&` with `$`. This may be necessary when working with older tachymeters.
1. **Renumber input lines**\
This option rewrites all lines to start from 1 and increment to N.
1. **Define additional fields**\
If your parser defines fields that are not present in your input data but are required, specify them here. Each space represents a column in the merged output and will be inserted directly after the line number. Don't forget a space after the last word, otherwise the characters are direftly placed before the next word.
\
    ```
    Original line in input file:
    1 1_1 x…

    020_21 1_ with space at the end will become:
    1 2020_21 1_ 1_1 x…

    2020_21 1_ without space at the end will become:
    1 2020_21 1_1_1 x…
    ```

1. **Start the process**\
A button click starts the process. Errors will be written to Tab _Logs_.