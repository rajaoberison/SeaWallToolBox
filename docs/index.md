# Documentation
THIS SCRIPT CREATES SEAWALL SEGMENTS WITHIN A CHOSEN COASTAL REGION AND ASSESS THEIR ECONOMIC EFFICIENCY

--------------------------
## Getting Started
### Requirements
In order to use this tool, you need ESRI's ArcGIS installed on your computer. The Spatial Analyst Licence should also be available.

### Setup
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
|--------------------------------|--------------------|:-----------------------------|:----------------------------|:---------------------------------|
| Raster elevation data          | Raster Layer       | Input                        |                             |                                  |
| Mean High Water                | Long               | Input                        |  4                          |                                  | 
| Chosen surge level             | Long               | Input                        |  15                         |                                  |
| Shapefile of the properties    | Feature Layer      | Input                        |                             |                                  |
| Field with building values     | Field              | Input                        |                             | Shapefile of the properties      |
| Unique ID field of buildings   | Field              | Input                        |                             | Shapefile of the properties      |
| Set Your Workspace             | Workspace          | Input                        |                             |                                  |
| Save the final output          | Feature Class      | Output                       |                             |                                  |
           
   To later revise any of this, right-click to the tool's name and select Properties.

-------------------------------
## About the tool
### WHAT and WHY
Coastal areas are annually exposed to risk of flooding from storm surges.
With the expected increase on storm intensity due to climate change, more and more properties are at risk.
This tool will allow you to identify areas at risk and get insights on the efficiency of their protection.

### WHAT you’ll NEED
High resolution elevation data (ideally Lidar).
Geospatial data (shapefile) of the properties and their economic values.
Expert knowledge of the storm surges on the locality of interest.


------------------
### HOW it WORKS
Within a specific coastline there are main entry points where the storm surges can come in.
Each entry point will affect the decision in the design, nature, and feasibility of the seawall to be established.
One of the main challenge in coastal defense is the identification of these entry points and consequently the delimitation of the coastal segment for each seawall. 

![Sea water flooding](https://rajaoberison.github.io/images/seawalltbx/seawall0.png)

> As storm surge intensify, longer walls are needed. The ability to predict identify potential water entry during the design of the wall is therefore crucial as the storm intensity are expected to increase in the future.


Given these challenges, 3 main questions are to be answered prior to a seawall construction:
* How many segments are there within the study area?
* What and how much are the capital in harms’ way for each segment?
* Which of the segments are worth protecting economically and ecologically? <img align="right" width="240" height="157" src="https://rajaoberison.github.io/images/seawalltbx/seawall1.png">

Which requires the availability of these information: 
* Elevation data of the region
* Spatial data of property values (natural, public, and private capital)
* Economic model of damages and cost of seawall construction

<br/>

-------------------
#### 1. How many segments? <img align="right" width="188" height="282" src="https://rajaoberison.github.io/images/seawalltbx/seawall2.png"/>
Segments location and length depend on the scenario (defined by the expert) in the design of the seawall.

Two elevation values need to be identified in order to determine the segments:
* Mean High Water (which under US Law is where wall should be built)
* Local storm surge level potential within the timeframe

Then for each of the two elevation values, contour lines will be created and seawall segments are where they are the closest to each other (i.e. where the elevation gradient is highest and sea water split in two directions)

<br/>

----------------------
#### 2. What capitals are in harms’ way? <img align="right" width="212" height="282" src="https://rajaoberison.github.io/images/seawalltbx/seawall3.png">

When the segments is delimited, they will be connected with their corresponding storm surge line: which will produce a polygon, a region of interest for each segment.

_**Anything within that region will be in harms’ way.**_

With the spatial data of the properties available, ArcGIS’s Select by Location tool can highlight these at risk capitals. The tool will automatically do that for the user.

<br/>
<br/>
<br/>

----------------------
#### 3. How much are the potential damages? <img align="right" width="230" height="275" src="https://rajaoberison.github.io/images/seawalltbx/seawall4.png">
For the selected properties, average elevation can be calculated using Zonal Statistics as Table, and then damages from storm can be calculated. 

> This tool will use a simple Total Benefit Analysis for the wall by calculating total annual benefits/damages for each segment and the benefits per segment length units. These damages are caluculated based on the percent of damage given the average elevation of the property and the user-defined storm surge level. 

Wall considered feasible are the ones providing economic value.

<br/>
<br/>
<br/>

----------------------
Find the code here: http://bit.ly/SeaWallTB, and the .tbx file is available for download at: http://bit.ly/SeaWallTBX

Five hundred lines of codes and still developping. Please contact me if you wish to contribute.
