.. _tm_working_vector_data:

|LS| Spatial Data Conversion and Building a GeoPackage
===============================================================================

We have now commenced Lab 1 Part C! We are almost done! For this part of the assignment
we will be converting different spatial data file formats to a GeoPackage. We will collect
spatial/field data using three different methods: QField on your cellphone,
a GPS unit and a Comma Delimited (CSV) file.

You will be heading to the field to perform groundtruthing of your ELC community series polygons you
digitized in Part B. Prior to heading out, you will have downloaded the QField app onto
your phone, obtained a GPS unit and have printed off the provided data sheet (you can also
record data in a notebook, or enter data directly into Excel on your phone).

Pick 3 polygons and record 3 locations in each polygon.  For my example, I chose to 
record tree species. At each of the 3 locations within the polygon, use each device to record 
a point in the same spot. So this means you will have 9 points in total for each polygon, 
3 for QField, 3 for the GPS unit and 3 for the CSV for 3 locations. 

The following instructions will explain how each device will be used to collect and import
data into QGIS.  Once the three datasets have been imported, you will create a GeoPackage.
At the end of the lab, you will be introduced to the measure tool, as well as a table join
and join attribute by location tool.


|moderate| |TY| Preparing QField for the field (TO BE COMPLETED PrIOR TO LAB ON FEBRUARY 14th or 15th)
-------------------------------------------------------------------------------

In our very first class you were asked to download the QField app onto your phone.  Please ensure
this has been done, as we are now going to package data in QGIS and import it into QField to 
perform field data collection. THIS SECTION NEEDS TO BE COMPLETED PRIOR TO ARRIVING TO LAB ON
FEBRUARY 14TH OR 15TH. BE SURE TO READ THE REST OF THE LAB AS WELL.

#. Start by opening up the same QGIS project you used for Part B.  This should have all your updated
   layers - most importantly your new ELC polygons. Now create a copy of QGIS project, by going to 
   'Project --> Save As...'. Save your new project as 'Lab_1_Part_C'.

Now that we have our new QGIS project, let's start with installing the 'Qfield Sync' plugin. This 
is done using the same process that we used to install the 'QuickMap Services' plugin. 

#. Navigate to 'Plugins' at the top of your QGIS session, click 'Manage and install
   Plugins...'.  This will open the Plugins dialog box.  In the search bar at the top
   of the page, enter 'QField Sync' as shown below:

   .. figure:: img/PartC_qfieldplugin.png
      :align: center

#. Click 'Install Plugin'.  A new toolbar will appear at the top of your QGIS session
   that looks like this:
   
   .. figure:: img/PartC_qfieldtools.png
      :align: center

Now we have to do some data prep to get it ready for QField.

#. Start by removing 'group2', which should have the 'ESRI Gray (light)'
   basemap, from your map. Also, if you haven't already, turn off your 'wild_species' labels. 
#. We also want to add a new basemap called 'ESRI Satellite'.  Navigate to the 'QuickMap Services'
   toolbar and select the basemap as shown below.

   .. figure:: img/PartC_esrisat.png
      :align: center

   Your 'Layers' panel should look like the image below:

   .. figure:: img/PartC_updatedlayerspanel.png
      :align: center

#. Now we are going to create an empty shapefile which we can use to collect data points in the
   field.  As you did in Lab 1 Part B, right click on your /Lab_1 folder in the browser panel,
   then click 'New... -> Shapefile'.

   .. figure:: img/PartC_newshapefile.png
      :align: center 

#. Once in the dialog box, be sure to give your file a meaningful name (e.g., QField_pnt), set 
   the geometry type and CRS and then add fields.  Refer to the image below to make sure your 
   settings are correct.

   .. figure:: img/PartC_newshapefilesettings.png
      :align: center 

#. Click OK.  Add your empty shapefile to your 'Layers' panel if it was not already automatically
   added.

Now we are going to format our 'Date' field so that when we collect a data point in the field,
the date is automatically populated.

#. Right click on your new point file, QField_pnt, and click 'Properties'.
#. Once the dialog box is open, click on the 'Forms' tab, which looks like this:

   .. figure:: img/PartC_formicon.png
      :align: center 

#. Now click on 'Date' under 'Fields', and fill out the dialog box so it matches the image below.

   .. figure:: img/PartC_formdate.png
      :align: center 

#. Click OK

Now we want to make sure all our project settings are properly formatted for our QField setup.

#. Navigate to the 'Project' tab at the top of your QGIS session, and click 'Properties'.

   .. figure:: img/PartC_profprop.png
      :align: center 

#. Open up 'Data Sources' to make sure all of our data are identifiable and searchable.

   .. figure:: img/PartC_datasources.png
      :align: center 

#. Now lets check that our CRS is set to NAD83 UTM Zone 17N. Click the 'CRS' tab to check.

   .. figure:: img/PartC_crs.png
      :align: center 

Ok, it all looks good! Now we are ready to package our project for QField!

#. Navigate to the QField toolbar, and click the 'Package for QField' icon.

   .. figure:: img/PartC_packageforqfield.png
      :align: center 

#. A dialog box will open.  At the bottom you will notice is says 'some layers in your project
   have not been configured...', so click the 'Configure Current Project' button below.

   .. figure:: img/PartC_configforproject.png
      :align: center 

#. A dialog box will open showing all your layers.  The column on the left called 'Action' needs
   to be set to 'Offline Editing'.  For the ESRI Satellite layer, set it as 'No Action'.

   .. figure:: img/PartC_offlineedit.png
      :align: center

#. Click OK. This will take you back to the 'Package Project for QField' dialog. Make note of the
   'Project' and 'Export Directory' sections.  In the image below, my project is called Campus_Ecology, 
    but your project may be called Lab_1, or something else. As for 'Export Directory', QField automatically
    creates a folder on your computer.  Make note of its location. Alternatively, you can continue
    to save your files in your /Lab_1 folder. However, if you do so, I suggest creating a new folder
    within your /Lab_1 folder titled export (e.g., /Lab_1/export). Regardless, just make sure you know
    where your QField Package is saved :).

#. Click OK.
#. Now we will navigate to where the export folder is saved. You should have the same files as shown
   below:

   .. figure:: img/PartC_offlineedit.png
      :align: center

#. We now need to get the two files highlighted in blue in the above photo on our phone. Your '.qgs' file may 
   have a different name from mine, so don't let this confuse you.
#. Data can be transfered on your phone in different ways: email, Google Drive, 
   iCloud or by plugging in your phone to your computer. You can use anyway to transfer your files, 
   just make sure you are able to access both those files on your phone.

The next part of this section will cover how to add the files from your phone into the 
mobile QField app.

#. On your phone, download the two files.  My downloads end up in my 'Downloads' folder on my phone.
#. Next open the 'QField' app.

   .. figure:: img/PartC_openqfield.png
      :align: center

#. Next click the 'Open local file' button.  This will take you to a new page titled 'Select a 
QGIS project or dataset'
#. You will upload your files by clicking 'Internal Storage'
#. Once on the 'Internal Storage' page navigate to the 'Downloads' folder (or whatever folder 
your data are stored in)

   .. figure:: img/PartC_download.png
      :align: center

#. Once your folder has been opened, navigate to and click on the '.qgs' file. Mine is titled 
'Campus_Ecology_qfield.qgs'

   .. figure:: img/PartC_qgs.png
      :align: center

This will open the file, so you should see something like the image below. Beautiful! You will
not have the ELC_campus layer, but rather your ELC community series polygons that you digitized. Make 
note that I kept my labels on, but see how crowded it makes the map? So that's why you 
were instructed to turn your labels off. 

   .. figure:: img/PartC_project.png
      :align: center

#. Click the 3 stacked lines to open the menu. You should see all your layers.  
   
   
   Take a moment and explore the different icons. The two icons in the top right corner 
   of the menu denote 'Map View' and 'Edit'.  By clicking on one of the layers
   and then clicking the pencil (i.e., Edit), you are able to edit that layer. If you
   click on the 'Settings' icon (the gear), you will see you have a measure tool. Now go
   back to the menu, and click 'QField_pnt' and then click the 'Edit' icon. Now click 
   the 'Back' arrow in the menu, this will take you to the map. Note the '+' and '-' buttons
   on the right side of the screen - this is to zoom in and out. You can also zoom in using
   two fingers on the screen. Now look in the bottom right corner. There is another 
   '+' button. Click this to add a new point. You will see a cross hair in the middle of 
   the screen - that is where your point will be placed. NOTE once you are in the field,
   there will be a blue GPS point indicating your location. When you are adding a new point,
   you should push the 'Center to current Location' button in the bottom right corner - it
   will be blue, but probably at this moment it is grey with a line through it. This button
   will centre your location on the screen, placing the crosshairs right where you are located.
   This is when you will push the '+' button to place your data point. Anyway, continue to
   explore the QField functionality. The next part of this section will cover how data points
   will be collected in the field. 

   .. figure:: img/PartC_legend.png
      :align: center

   THIS SECTION NEEDS TO BE COMPLETED PRIOR TO ARRIVING TO LAB ON
   FEBRUARY 14TH OR 15TH. BE SURE TO READ THE REST OF THE LAB AS WELL.


|basic| |FA| Preparing and using a GPS Unit for the Field
-------------------------------------------------------------------------------

This section will help you set up your GPS unit for the field to ensure you are 
collecting your data points in the correct coordinate system (NAD83). You will
receive your GPS unit the day of lab (February 14th or 15th).

The school has a variety of GPS units, so the following instructions may not apply 
directly to the unit you have. However, they should give you enough of an idea to 
be able to check your coordinate system.

#. Turn your GPS on
#. Using the joystick, start by navigating to the icon labelled 'Setup', and click on
   it.
#. Then navigate to the icon labelled 'Units' and click on it.
#. 'Position Format' should be set to UTM/UPS (Universal Transverse Mercator/Universal 
   Polar Stereographic)
#. 'Map Datum' should be set as NAD83
#. Once the coordinate system is set, go back to the main menu, and then click on 'Mark'
   This is where you can collect data points.

Your GPS unit is now setup for field use! 

#. Once you are out in the field and are in the location that you want to collect a data 
   point, click the joystick, and fill out the dialog box. 

   IMPORTANT

   With both your GPS unit and QField app, be sure to wait ~10 seconds before marking your
   point. Often, it takes GPS units a moment to find a precise location, so waiting before
   you mark your point will improve accuracy.

#. Before you click 'OK', fill out your field data sheet to include information on the ID,
   Easting, Northing and species.

Repeat this process for all 9 of your points.  Instructions on how to import these data will
follow in the next sections.


|basic| |FA| Collecting Field Data Points with QField 
-------------------------------------------------------------------------------

Now you are ready to head to the field! Once in the field you will notice that 
a blue marker shows up on your map - that is you! So as you walk around 
looking for your ELC polygons, you will see the GPS tracker moving. Take 
a moment and explore how your GPS tracker interacts with the different layers.
Do you notice that you are inside or outside of a polygon? Does your GPS tracker
seem accurate? Does your digitizing seem accurate?

#. We want to edit the 'QFied_pnt' file. So click on the 'QField_pnt' file in the legend
   menu and then click the pencil 'Edit' icon.
#. Click the back button so you are on the map.
#. Now naviagte to your first point location.  As mentioned in the previous section of this
   lesson which covered GPS use, you will collect a point using your GPS unit, QField and
   hand recording at this location.
#. As described in the previous section that went over QField set up, make sure the 
   crosshairs are centered on your location, and then click
   the '+' button. A dialog window will open and prompt you to enter an FID, ID, Species and
   ELC_Code. Date will already be populated. For your first point, give it the FID and ID of 1.
   Your point recorded with your GPS unit and by hand should be given the same ID and FID. Now record
   a species. Be sure to be consistent with your recording; decide whether you want to use latin
   or common names, and stick with that decision. Make sure the same species is recorded the same
   across all 3 methods of data collection. Record the ELC_class of the polygon that you are in.

   .. figure:: img/PartC_addfeature.png
      :align: center

#. With QField, as you enter information into each field, click the checkmark at the top left corner
   of the dialog window. This will allow you to move on to the next field to enter information
   If you want to get rid of the point altogether, click the red trash can at the top right 
   corner of the dialog box. 
#. Now continue on to collect the rest of your data points. Remember 3 polygons, 3 points in each
   polygon, and at each point location collect 1 point using QField, 1 point using GPS and 1 hand
   recorded.

You have now collected data points in 3 different ways! Let's head back to the class and upload our
data!

|basic| |FA| Uploading GPS Data to QGIS 
-------------------------------------------------------------------------------

Recall on the very first day, we downloaded a program called BaseCamp by Garmin.  We will now use this
program to upload our GPS data.

#. Let's start by plugging our GPS units into the computer.
#. Once plugged in, open up BaseCamp. In the top left corner you should see a browser panel that
   looks like the image below.  Under devices, you should see your GPS unit (because we have it plugged
   in). Double click the folder called 'Internal Storage' and that will automatically bring your
   data points into the Map View window. You will also notice a series of little flags in the 
   'Internal Device' panel on the left side of the screen. Those are you data points you collected.

   .. figure:: img/PartC_devices.png
      :align: center

#. Now select all of your data points you want to import in the 'Internal Device' panel by holding
   down CTRL and clicking each point you want to include.

   .. figure:: img/PartC_basecampselect.png
      :align: center

#. Next navigate to the 'File' tab at the top of the screen and click 'Export --> Export Selection'

   .. figure:: img/PartC_exportselection.png
      :align: center

#. Save the file as a '.gpx' file in your /Lab_1 folder as shown below.

   .. figure:: img/PartC_exportselectionsave.png
      :align: center

#. Now open your QGIS project you have been working in and navigate to the 'Browser' panel, and go to
   the /Lab_1 folder.
#. You should see your file titled 'GPS_groundtruth.gpx', click the dropdown arrow.  You will see
   that there are a series of files contained within the '.gpx' file. We are interested in the 
   'waypoints' file. Drag and drop it on your map canvas. You should see your points.

   .. figure:: img/PartC_gpximport.png
      :align: center

So, I am sure you have noticed that our 'GPS_groundtruth' file is saved as a '.gpx' format.
We want to convert this into a GeoPackage.  We will then store our other two groundtruth datasets
in the same GeoPackage.

#. Right click on 'waypoints' in your 'Layers' panel, and click 'Export --> Save Features As...'.
   A dialog window will open, which should look familiar as we have exported datasets before.
#. Fill out the dialog window as shown below:

   .. figure:: img/PartC_packagegps.png
      :align: center

#. Click OK.  You can remove the 'waypoints' layer.

What is strange about QGIS, is that you can't seem to make an empty Geopackage. We will have to
employ a little work-around.

#. Go to the 'Browser' panel, and click on the dropdown arrow for your new GeoPackage, which should
   be named 'Lab1_PartC'. You will see another layer within it with the same name. If your new GeoPackage
   is not there, click the 'Refresh' button at the top of the 'Browser' panel. 
#. Now right click on the layer within the GeoPackage and click 'Manage... -> Rename Layer'

   .. figure:: img/PartC_packagerename.png
      :align: center

#. A dialog window will open. Change the name to 'GPS_groundtruth' and click OK

   .. figure:: img/PartC_GPSnewname.png
      :align: center  

You have now successfully converted a '.gpx' file to a GeoPackage table! Now let's do the same for
our hand recorded dataset by uploading a 'Comma Delimited' (.csv) file.


|basic| |TY| Uploading Hand Recorded Data to QGIS
-------------------------------------------------------------------------------

For this part of the lesson, we are going to enter our hand recorded data into Excel,
and then import the Excel file into QGIS and create a point dataset.

#. Let's start by opening up Excel.  Now enter your data that you recorded during your
   time in the field. Be careful with entering the data - make sure species are spelt
   correctly and more importantly, that your Easting and Northing values are correct!
   Your final product should look similar to the image below.

   .. figure:: img/PartC_csvformat.png
      :align: center 

Note

My 'Field_ID' column starts at 2. This is because I did not include certain waypoints
I collected. Yours should start at 1, but if it does not, that is Ok!

#. Now this is the important part - we need to save our Excel file in a specific format.
   Go to 'Save As...' as you normally would, and save it in the /Lab_1 folder. However,
   make sure you save it as a '.csv', 'Comma Delimited' file. Call it CSV_groundtruth.
   
   .. figure:: img/PartC_csvsave.png
      :align: center 

#. Now go back to your QGIS session, and go to 'Layer' at the top of the window, then 
   click 'Add Layer --> Add a Delimited Text Layer'

   .. figure:: img/PartC_addcsv.png
      :align: center
   
#. A dialog window will open, and fill it out so that it matches what is shown below:

   .. figure:: img/PartC_addcsvsettings.png
      :align: center

#. If the layer wasn't automatically added to your map canvas, add your new 'CSV_groundtruth'
   layer.

#. Now to add the 'CSV_groundtruth' layer to your 'Lab1_PartC' GeoPackage, simply drag and drop
   it into the 'Lab1_PartC' Geopackage file in your 'Browser'

   .. figure:: img/PartC_dropcsv.png
      :align: center

You have now successfully converted a '.csv' file into a GeoPackage table! Now let's finally do the
same for our QField file.


|moderate| |TY| Uploading QField Data to QGIS
-------------------------------------------------------------------------------

After collecting data in the field with 'QField', the app automatically updates the associated
files. 

#. Once you are ready to upload your data back onto your computer, transfer the '.qgs'
   and 'data.gpkg' files you had originally downloaded back onto your computer somehow (e.g., email,
   Goodle Drive, iCloud, plugging in your phone)  
#. Once on your computer, create a new folder called 'import' where you had saved your 'export'
   folder (e.g., in /Lab_1 or in the automatically created QField folder). Transfer your files
   that you just uploaded onto your computer, into the 'import' folder. 
#. Now go to your QGIS session, and find your 'data.gpkg' file in the 'Browser' panel by navigating to your 'import'
   folder (e.g., /Lab_1/import). Click the dropdown arrow.  You will see a series of files saved 
   within the GeoPackage. We are interested in the one called 'QField_pnt'. You will notice an 
   id has been attached to it, but that is no issue.

   .. figure:: img/PartC_qfieldpntimport.png
      :align: center

#. Drag and drop the 'QField_pnt' file onto your map canvas. You will have all three datasets on your
   map now.

   .. figure:: img/PartC_all3.png
      :align: center

#. Now as you did with 'CSV_groundtruth' drag and drop your 'QField_pnt' file into your 
   'Lab1_PartC' GeoPackage, and change the name back to 'QField_pnt'.

   You have now added your final layer to your GeoPackage! Congrats! You are done Lab 1! Please
   review the Lab 1 marking scheme and make sure you have all required deliverables:
   
   (1) Part A map: Thematic map of Niagara College wild species monitoring projects in relation
      to ELC polygons.

   (2) Part B map: Thematic map of your five digitized ELC community series polygons, including
      all of your updated layers (e.g., roads, buildings, impervious surfaces, lakes)

   (3) Part C geopackage: A geopackage with your three field data layers

   (4) Data folder: Make sure deliverables (1), (2) and (3), along with all of your Lab 1 data 
      are in your /Lab_1 folder, and then zip it.

   **To submit your Lab 1, email the zipped folder to me.** 
   
   We are almost done, but there a few things I want you to try out before we move onto Lab 2.


|moderate| |TY| Exploring the Measure Tool and Joins
-------------------------------------------------------------------------------

This section is meant to introduce you to three new tools: Measure Tool, Table Join tool and Join
Attributes by Location tool. The latter two tools will be used in Lab 2, and are meant to exemplify
the  of data management and data structure.

#. If you haven't already, add your 3 new point files from your 'Lab1_PartC' GeoPackage.
#. Now let's toggle off all the layers in 'group1' EXCEPT 'ELC_Campus' and collapse 'group1'
   so all we see are the 3 point files and the 'ELC_Campus' file undernearth. This is just 
   to reduce distraction so we can focus on our next steps.

   .. figure:: img/PartC_only3.png
      :align: center

#. Let's start by clicking on the |addMeasure| tool.  This tool allows you to measure
   distances between features on your map. The units will be in your coordinate system,
   which is metres.

   I was curious to see the distance between points taken with a GPS unit vs. points
   taken with a cellphone. 
   
#. So let's measure and see! To do this, click on one of your 'GPS_groundtruth' points and then click on your
   'QField_pnt' that was taken in the "same" location.
   
   What do you notice? Are they similar?

Ok, moving on to the Join tools!

   Take a look at the image below - it is the 3 attribute tables for our 3 point files.
   What do you notice? What is the same and what is different?  You may notice that each file
   has an id field that labels each item 1 - 9. You may also notice that the 'GPS_groundtruth'
   file has a field called 'ele' which is elevation information.  We also may notice that
   the 'QField_pnt' file has the field 'ELC_Code', whereas the other two files do not.  What
   would we do if we wanted to transfer both elevation information and ELC_Code information
   to the 'CSV_groundtruth' file?  We could enter it manually, as there are only a few records,
   but imagine if we had 5000 records. 

   .. figure:: img/PartC_all3.png
      :align: center

   A more efficient approach would be to use something called a 'Table Join'.  A 'Table Join'
   works by linking two tables together based on a common ID. Therefore, if we did not record
   these IDs, we would not be able to do a table join. Let's practice a table join by linking
   the elevation information from the 'GPS_groundtruth' file to the 'CSV_grountruth' file.

#. Right click on 'CSV_groundtruth' and go to 'Properties'
#. Next, navigate to the tab on the left side that looks like this:

   .. figure:: img/PartC_joinicon.png
      :align: center

#. Click it. A dialog window will appear. Click the green '+' icon to add a new join, as shown below.

   .. figure:: img/PartC_addnewjoin.png
      :align: center

#. Another dialog window will appear, fill it out as shown below:

   .. figure:: img/PartC_addvectorjoin.png
      :align: center

   Note

   Join Layer =   the layer we are trying to get elevation from i.e., 'GPS_groundtruth'
   Join Field =   refers to the field from the 'GPS_groundtruth' layer that matches the 
                  field from the 'CSV_groundtruth' layer
   Target Field = The field from 'CSV_groundtruth' that matches the field of 'GPS_groundtruth'. 
                  In this example, they both happen to be called fid, but the names of the 
                  fields do not need to be the same, so long as the values match
   Joined Field=  You can select which fields you would like to add to your 'CSV_groundtruth' layer.
                  We only want ele (elevation)

#. Click OK. Then go and look at the attribute table for 'CSV_groundtruth':

   .. figure:: img/PartC_csvelevation.png
      :align: center

Nice! That's how the Table Join tool works.

Now we are going to transfer more attribute data into the attribute table of 'CSV_groundtruth'.
But instead of doing a Table Join, we will do a spatial join, using the tool called Join
Attributes by Location. This tool exemplifies how spatial databases vary from other database types.
Spatial databases are able to link information together simply based on location. So, if two layers
are touching each other, attribute information can be transfered to the attribute table of either
or both layers.

Let's look at an example. We did not record the 'ELC_Code' for the 'CSV_groundtruth' layer, as was
mentioned above. But, it just so happens that my 'CSV_groundtruth' points fall within or
"intersect" with the ELC_campus layer. So, we are going to use the 'CSV_groundtruth' points to
extract the 'ELC_Code' data from the 'ELC_campus' layer.

#. Navigate to the 'Vector' tab at the top of the QGIS session. Click it, and go to 'Data management
Tools --> Join Attributes by Location'

   .. figure:: img/PartC_vectorprocess.png
      :align: center

#. A dialog window will open.  Click the '...' icon next to 'Fields to Add' section. Another window 
   will open. Select 'ELC_class' and click the back arrow.
#. Fill out the window so it matches the information below.

   .. figure:: img/PartC_spjoinset.png
      :align: center

#. Click Run. A new temporary file called 'Join Layer' will be added to your 'Layers' panel.
   Open the attribute table.  What do you see?

   .. figure:: img/PartC_attcode.png
      :align: center


|moderate| |TY| Using Avenza for Groudtruthing: Uploading your Module 5 Map
-------------------------------------------------------------------------------

#. Start by sending your Module 5 map from your computer to your phone. This can be done by email, Airdrop,
   Google Drive, etc. If emailed, it must be then downloaded to your phone. 

#. We will then download the 'Avenza Maps: Offline Mapping' app from the Appstore
   on your phone.

#. Once downloaded, open Avenza.

You will see at the bottom of the app, there are three tabs: 'My Maps', 'Layers', 'Store'.

   .. figure:: img/PartC_attcode.png
      :align: center

#. Click the 'My Maps' tab. 

   .. figure:: img/PartC_attcode.png
      :align: center

#. You will see an orange button with '+' sign in the bottom right corner. Click it. 
   An option will appear that says 'Download or import a map'. Click that.

   .. figure:: img/PartC_attcode.png
      :align: center

#. This is where you will access your map. If downloaded to your phone, you can access
   it through your 'Downloads'. If sent through 'Google Drive', select the 'Google Drive'
   icon.  I am assuming their will be an Airdrop icon for those with IOS.

   .. figure:: img/PartC_attcode.png
      :align: center

#. Click your map PDF document. This will take you automatically back to your 'My Maps'
   tab.

   .. figure:: img/PartC_attcode.png
      :align: center

You have uploaded your map! This is all you need to do prior to coming to class. If you
are having issues with this, we can figure it out in class.


|moderate| |TY| Using Avenza for Groudtruthing: Collecting field data points
-------------------------------------------------------------------------------

Now let's head to the field!

#. Click your 'Lab1_PartB' map, which is found under the 'MyMaps' tab.

You should see a blue GPS point. That is you! Take a moment an look at the functions
of Avenza. The target symbol (bottom left corner) can be used to centre the map over
your GPS location. This should be clicked when dropping a pin. The pin immediately to
the right of the target symbol is used to drop a pin location. You will use this at
each of the 9 locations you will be visiting. 

   .. figure:: img/PartC_attcode.png
      :align: center

#. The coordinates to the right of the pin need to be set to UTM - NAD83. Single click on
   the coordinates, and a series of coordinate options will appear. Select UTM - NAD83, 17N.

#. Now you are ready to drop pins. Click the target symbol to centre your map over your
   GPS, then click the pin next to it. Once clicked, a new window will open. 
   Give it a name using this convention:

EXAMPLE:

FOD001, FOD002, FOD003, MAS001, MAS002, MAS003, etc.

   If you make a mistake and drop a pin in an incorrect location. Click the pin on the map.
   A label will appear. Click the label. A new editing window will open. In the top right
   corner, there will be a 3 stacked dots icon. Click the icon, and then click delete.

   .. figure:: img/PartC_attcode.png
      :align: center

   .. figure:: img/PartC_attcode.png
      :align: center
   
#. Continue collecting data points at all 9 locations, using the three methods.


|moderate| |TY| Using Avenza for Groudtruthing: Exporting field data points
-------------------------------------------------------------------------------

#. Once you are done collecting your 9 data points with Avenza, click the back
   arrow at the top left of the app.

#. This will take you back to 'MyMaps'. But now we want to export our layer. Click
   the 'Layers' tab at the bottom of the screen.

   .. figure:: img/PartC_attcode.png
      :align: center

#. Then click your 'Layer' file.

   .. figure:: img/PartC_attcode.png
      :align: center

#. A new window will open. Click the 3 stacked lines icon in the bottom right corner,
   and select 'Export Layers'.

   .. figure:: img/PartC_attcode.png
      :align: center

#. Change the file name to 'KML_groundtruth.kml'. Make syre the format is KML.

   .. figure:: img/PartC_attcode.png
      :align: center

#. Click 'Export'. Export options will appear. I used Google Drive to export my layer
   to my computer.


|moderate| |TY| Using Avenza for Groudtruthing: Importing field data points to QGIS
-------------------------------------------------------------------------------

#. Go back to your computer. Go to where you exported your layer, e.g., Google Drive.
   Download 'KML_groundtruth'.

#. Go to QGIS. As you would with a vector layer, drag and drop the 'KML_groundtruth'
   layer from your 'Browser' panel. Your file will probably be in your 'Downloads' folder.

#. Once the layer has been added, drag and drop the 'KML_groundtruth' into your 'Lab1_PartC'
   GeoPackage in the Browser panel. Once in the GeoPackage, rename it back to 'KML_groundtruth'.

|IC|
-------------------------------------------------------------------------------

You have now learned to collect, upload and convert three different formats of vector data into a 
GeoPackage. You also now have had a brief introduction to how table and spatial joins work.  You
also now have a sense of the quality of your phone's GPS ;)! Well done everyone, you have completed
Lab 1! Next week we will start working on Lab 2!


.. Substitutions definitions - AVOID EDITING PAST THIS LINE
   This will be automatically updated by the find_set_subst.py script.
   If you need to create a new substitution manually,
   please add it also to the substitutions.txt file in the
   source folder.

.. |FA| replace:: Follow Along:
.. |IC| replace:: In Conclusion
.. |LS| replace:: Lesson:
.. |TY| replace:: Try Yourself
.. |WN| replace:: What's Next?
.. |basic| image:: /static/common/basic.png
.. |deselectActiveLayer| image:: /static/common/mActionDeselectActiveLayer.png
   :width: 1.5em
.. |openTable| image:: /static/common/mActionOpenTable.png
   :width: 1.5em
.. |selectRectangle| image:: /static/common/mActionSelectRectangle.png
   :width: 1.5em
