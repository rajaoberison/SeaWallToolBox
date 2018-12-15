## Documentation
THIS SCRIPT CREATES SEAWALL SEGMENTS WITHIN A CHOSEN COASTAL REGION AND ASSESS THEIR ECONOMIC EFFICIENCY

### Getting Started
#### Requirements
In order to use this tool, you need ESRI's ArcGIS installed on your computer. The Spatial Analyst Licence should also be available.

#### Setup
To create an ArcToolbox tool with which to execute this script, do the following.
1   In  ArcMap > Catalog > Toolboxes > My Toolboxes, either select an existing toolbox
    or right-click on My Toolboxes and use New > Toolbox to create (then rename) a new one.
2   Drag (or use ArcToolbox > Add Toolbox to add) this toolbox to ArcToolbox.
3   Right-click on the toolbox in ArcToolbox, and use Add > Script to open a dialog box.
4   In this Add Script dialog box, use Label to name the tool being created, and press Next.
5   In a new dialog box, browse to the .py file to be invoked by this tool, and press Next.
6   In the next dialog box, specify the following inputs (using dropdown menus wherever possible)
    before pressing OK or Finish.
        
| DISPLAY NAME                   | DATA TYPE          | PROPERTY > DIRECTION > VALUE | PROPERTY > DEFAULT > VALUE  | PROPERTY > OBTAINED FROM > VALUE |   
|--------------------------------|--------------------|------------------------------|----------------------------:|----------------------------------|
| Raster elevation data          | Raster Layer       | Input                        |                             |                                  |
| Mean High Water                | Long               | Input                        | 4                           |                                  | 
| Chosen surge level             | Long               | Input                        | 15                          |                                  |
| Shapefile of the properties    | Feature Layer      | Input                        |                             |                                  |
| Field with building values     | Field              | Input                        |                             | Shapefile of the properties      |
| Unique ID field of buildings   | Field              | Input                        |                             | Shapefile of the properties      |
| Set Your Workspace             | Workspace          | Input                        |                             |                                  |
| Save the final output          | Feature Class      | Output                       |                             |                                  |
           
   To later revise any of this, right-click to the tool's name and select Properties.
