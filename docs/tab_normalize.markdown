---
title: 2. Tab Normalize
permalink: /tab_normalize/
---

# Tab Normalize

The _Normalize_ tab combines individual measurement data into a single file. The combined file can be cleaned up using various tasks. Furthermore, possible *.qml (QGIS) styles can be copied to a defined output folder. 

<img src="/assets/img/normalize.png" alt="Normalize GUI" style="border: 1px solid black" />

1. **Open Normalize**  
   Click to open the _Normalize_ tool.

2. **Select input files**  
   Choose your input files from your hard drive. Supported file extensions are `*.dat` and `*.txt`.

3. **Select the output folder**  
   Select the folder where the combined data will be saved.  
   > Use the same output folder in the _Process_ tab for all generated `*.shp` files.

4. **Name your output file**  
   Give your output file a meaningful name.  
   > If you specify a name here, it will also be used in the Process tab for naming the generated GeoPackage.

5. **Add optional QML files**  
   If you have a folder containing `*.qml` files (optionally with an svg subfolder), you can select it here. The tool will copy these files to your output folder. If a `*.qml` file matches the name of a generated GIS layer, it will automatically be applied to the layer when loaded in QGIS.

6. **Replace special characters**  
   The replacement rules work as follows:

   1. When the replace field (8) is empty:
      - Example: search="&", replace="" → "&" is deleted from the file

   2. When no spaces in both fields (7)(8):
      - Example: search="&", replace="$" → "&" is replaced with "$"
      - The strings are treated and replaced as a whole

   3. When spaces are present (character by character replacement):
      - Example with matching length: search="d o g s", replace="c a t s" → 
        * "d" is replaced with "c"
        * "o" is replaced with "a"
        * "g" is replaced with "t" 
        * "s" is replaced with "s"
      - Example:
        ```
        Input:  "The dogs run"
        Output: "The cats run"
        ```
      - Example with different length: search="d o g s", replace="c a t" →
        * "d" is replaced with "c"
        * "o" is replaced with "a"
        * "g" is replaced with "t"
        * "s" remains unchanged (no replacement character available)
      - Example:
        ```
        Input:  "The dogs run"
        Output: "The cats run"
        ```

   These rules allow for deletion of characters, complete replacements, and character-by-character replacements with multiple characters.

7. **Renumber input lines**  
   This option rewrites all lines to start from 1 and increment to N.

8.  **Define additional fields**  
   If your parser defines fields that are not present in your input data but are required, specify them here. Each space represents a column in the merged output and will be inserted directly after the line number. Don't forget a space after the last word, otherwise the characters are directly placed before the next word.\
    ```
    Original line in input file:
    1 1_1 x…

    020_21 1_ with space at the end will become:
    1 2020_21 1_ 1_1 x…

    2020_21 1_ without space at the end will become:
    1 2020_21 1_1_1 x…
    ```

9.  **Start the process**  
A button click starts the process. Errors will be written to Tab _Logs_.

1.  **Save settings**  
 When checked your configuration of tab _Normalize_ will be saved.