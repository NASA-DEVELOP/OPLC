# Osa Peninsula Water Resources II

### Land Cover Classification

Authors: Tanner Johnson, Taufiq Rashid, John Langstaff  
Date Created: August 7, 2018

This code classifies land use on the Osa peninsula based on Landsat 5 and 8 imagery. 
The code creates a cloud free, greenest pixel composite to use for classification. In addition to
standard Landsat 5 and 8 bands, it classifies based on NDVI, EVI, NDWI, NDMI, NDBI, slope and Tasseled-Cap 
indices (brightness, greenness, and wetness).

-------------
**Required Packages**
 - None. A free Google Earth Engine account is required to run this code.   

**Three Scripts**

1. _OsaWaterII_1987Training_ - Uses Landsat 5 imagery. Contains training data for 1987.
2. _OsaWaterII_1997Training_ - Classifies using Landsat 5 imagery. Contains training data for 1997.
3. _OsaWaterII_2018Training_ - Classifies using Landsat 8 imagery. Contains training data for 2018.

### Parameters
-------------
**Note:** Users can directly copy and paste the code into a new script in Google Earth Engine and press run. The below instructions are a guide to help the user personalize the code or troubleshoot issues while running the script. All assets have been directly added to the code and the default study area shapefile is connected to the NASA DEVELOP Google Earth Engine account.  

**To set up and run the code with a new Google Earth Engine (GEE) account:** 

1. Upload a shapefile of the Osa Peninsula as a GEE asset. To do this, choose the 'Assets' tab,
choose 'New', 'Table Upload'. With the unzipped shapefile, select the .shp, .shp.xml, .dbf, .cpg, 
.prj, .sbn, and .shx (if applicable). Leave out the .sbx file. This will take a while. 

2. Replace the study area path, for the 1987 script on line 1217 (1997: line 1200 and 2018: line 1106), with the path of the new EE asset. The address should be: 
'users/yourUsername/yourAssetName'. yourAssetName can be found in the 'Assets' Tab. 

3. Save the code with 'studyArea' changed. 

4. Select 'Run', and choose your year for study. Press 'Create Map'. Note that the training data has 
been selected for 1987, and may yield less accurate results for different years. Separate codes have
been provided containing training data for 1997 and 2018. 

5. To save the classified image or the Landsat composite, choose the 'Tasks' window and select 'Run'. 
Leave scale at 30, as this is the pixel resolution. 




**The training data used for the classification can be displayed on the map under 'Geometry Imports'. 
To edit training data areas used for the code:**

1. Select the class you would like to edit in 'Geometry Imports'.

2. To add new features, choose polygon or point and draw the areas on the map.

3. To delete features, be sure you do not have a class selected. Click 'Exit' if necessary. Select a 
point or polygon and click delete.


**To create new classes:**

1. Under geometry imports, select 'New Layer'. Hover the layer, select the settings wheel. Rename the
layer as desired.

2. Import as FeatureCollection. Add property named 'landcover' with a unique value (current code 
uses 1-8).

3. Add a new line to merge the class into 'newfc1' (on 1987:line 1229, 1997:line 1212, 2018:line 1118), following the formatting there. Add the new class name and value to 'classes' (on 1987:line 1425, 1997:line 1408, 2018:line 1318). Add a line to 'palette' (on 1987:line 1475, 1997:line 1458, 2018:line 1368), with the
CSS color code that you would like your class to display on the map. On 1987:line 1486 (1997:line 1469, 2018:line 1380), change 'max' to reflect the new maximum land cover value.



**To use the code for a different area altogether, extra steps are required.**

1. Change the 'study area' to the new area (1987:line 1217, 1997: line 1200, and 2018: line 1106) 

2. Remove the previous training data 'Geometry Imports'. Add new training data geometry (minimum value 
should be 1, 0 is NoData). 

3. Edit:  
  -  _'newfc1'_ on 1987:line 1229, 1997:line 1212, 2018:line 1118line 34 to reflect the new classes
  -  _'classes'_ on 1987:line 1425, 1997:line 1408, 2018:line 1318
  -  _'palette'_ on 1987:line 1475, 1997:line 1458, 2018:line 1368
  -  _'min'_ and _'max'_ values on 1987:line 1486, 1997:line 1469, and 2018:line 1380 (min >= 1)
