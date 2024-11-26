---
layout: page
title: 3. Tab Process
permalink: /tab_process/
---

# Tab Process

The _Process_ tab allows you to define survey2gis commands and execute each.

<img src="/assets/img/process.jpg" alt="Process GUI" style="border: 1px solid black" />

1. **Open Process**\
Click to open the _Process_ tool.
2. **Select the input file**\
The input file contains the merged measurement data. This field is automatically set if the _Normalize_ tab was used to prepare your data.
1. **Select a parser file**\
Each survey2gis command requires the specification of a valid parser file. If you are unsure, consult the survey2gis help pdf linked in the _Help_ tab. 
1. **Directory for shapefiles**\
Each call of survey2gis creates shape files as intermediate format. These files are then packed into a geopackage. 
> If a file named `keep_files` exists in the plugin directory, the shapefiles are not deleted which helps when 
> Find the plugin path: Go to `Settings > User Profiles > Open Active Profile Folder`, then open folder `python`. Here you will find all installed plugins. Navigate to the `s2g_data_processor` extension subfolder where the `keep_files` needs to be placed.
1. **Name of the generated file**\
survey2gis generates a shape file for each layer as mentioned in point 4. This field defines the name of the shape file, i.e. the name of the layer in the final geopackage that is loaded in QGIS. When using qml files, make sure that the style and layer names are identical.
1. **Path to the alias file**\
survey2gis limits the field names to 10 characters. We can work around this by defining an alias file. This applies globally for all command calls and must be created as follows:
```
[aliases]
key=value
...
```
Where `key` is the name of the defined parser field and `value` is the new name. Please note that your qml style may no longer work correctly or may need to be adapted.

1. **EPSG code**\
The following scenarios exist with regard to the projection.
- The user knows in which projection the input data is available and sets an EPSG code in this field. As a result, survey2gis does not take care of a new projection, but the extension writes the given EPSG code into the resulting geopackage for each layer. QGIS reads this information and will be able to integrate the layer correctly without asking.
- The user knows in which projection the data is available and uses the command options `--proj-in` and `--proj-out`. This causes survey2gis to re-project the data. The extension reads the value in `--proj-out` per command and writes it as an entry in the geopackage. QGIS understands this information and will be able to include the layer correctly without asking.
- The user executes the commands, leaves the field empty and makes no entry for `--proj-in` and `--proj-out`. In this case, the extension knows nothing about a projection and writes the data to the geopackage without it. Depending on how QGIS is configured, it will ask for the projection or use the projection of the project. See the [QGIS project settings](https://docs.qgis.org/3.34/en/docs/user_manual/working_with_projections/working_with_projections.html#id8).
1. **Pay attention to the scrollbars**
2. **Command options**\
Here, the survey2gis options can be set for each command call.
>  Unsure? Look in the _Help_ tab!
1.  **Add command**\
After a command has been defined in the fields above, this button adds the command to the code field (12) for execution. Each command needs to be defined in a separate line. The commands are proccessed sequentially in the order they are defined.
1.  **Save commands**\
When adding a command via the button (10), all commands created are automatically saved in a text file in the plugin directory under the name `command_history.txt`. When restarting, they are loaded from here and automatically added to the code field (12). If you make changes directly in the code field, you can use this button to write all currently defined commands of the code field to the `command_history.txt` file.
> Find the plugin path: Go to `Settings > User Profiles > Open Active Profile Folder`, then open folder `python`. Here you will find all installed plugins. Navigate to the `s2g_data_processor` extension subfolder to see the `command_history.txt` file.
1.  **Code field**\
This field contains all created commands that are processed when executed.
1.  **Start process**\
Pressing the button starts the processing of all commands. If successful, the data is written to the geopackage in the defined output folder and loaded into QGIS. If something goes wrong, visit the _Logs_ tab and look for errors. 