.. _tm_working_vector_data:

Choropleth Mapping: Toronto Street Tree Density vs. socioeconomic variables
-------------------------------------------------------------------------------

So far we have discussed four different types of classification, including nominal,
ordinal, interval and ratio. The map for Lab 1 Part A was a nominal classification.
We also practiced making a ratio classification when we mapped area for the 
'ELC_campus' dataset in Lab 1 Part A.

Now we are going to create choropleth maps. A choropleth map is defined as "a 
thematic map that displays a quantitative attribute using ordinal classes. Areas 
are shaded according to their value and a range of shading classes'. Choropleth
maps are most often used for mapping statistical data across government or
administrative boundaries. Choropleth maps are created using normalized data,
never raw data. 

For Lab 2 Part A we will be creating two choropleth maps for the city of Toronto; 
one will be of Toronto Street Tree Density and the other will be your choice of either
median income or population density.  For this lab, we are exploring the concept of
unequal distribution of natural resources in urban spaces.  It is known that
areas of low income or high population density typically have lower access to green
infrastructure.  With the Toronto Street Tree Density map and your
choice of median income or population density, you will visually interpret
spatial patterns and determine whether you can see a pattern of low income and low
street tree density or high population density and low street tree density. 
You will then define a threshold value to subset your dataset for both variables, using 
standard query language (SQL). Once both datasets are subset, you will use the vector 
research tool called 'Select by Location' to identify areas that overlap from both maps.

The deliverable for this portion of the assignment will be three maps: (1) Street Tree
density map, (2) a median income or population density map and (3) a map showing
your 'Select by Location' output.

|basic| |FA| Preparing and processing census data
-------------------------------------------------------------------------------

At this point, you should have downloaded the 'Lab_2' folder from BlackBoard. 
This folder has a GeoPackage file called 'Lab_2', which contatins the data
needed for Lab 2. We will be working with two types of Canadian census data for 
this assignment: (1) a tabular dataset and (2) spatial dataset, as well as the 
Toronto Street Tree dataset, as previously mentioned.  

#. Let's start by opening a new QGIS session.
#. Navigate to the 'Browser' panel and add the three tables within the 'Lab_2'
   GeoPackage to your QGIS session.

   .. figure:: img/Lab2A_3files.png
     :align: center

#. Now go to the 'Layer Properties' for both spatial datasets, and check the
   Coordinate Reference System (CRS) under the 'Information' tab.  Are they
   both set to NAD83 UTM Zone 17N? Nope! We will have to reproject the 
   'CT_Canada' dataset.

   .. figure:: img/Lab2A_checkcrs.png
     :align: center

#. Navigate to the 'Vector' tab at the top of the QGIS session, then 'Data
   Management Tools --> Reproject Layer'

   .. figure:: img/Lab2A_reproject.png
     :align: center

#. Fill out the tool as shown below and click 'Run'. Be sure to add it to 
   your 'Lab_2' GeoPackage! Your new layer should be added to your session.

   .. figure:: img/Lab2A_reprojectsettings.png
     :align: center

   But wait, we want to look at just Toronto, and the dataset is for all of Canada.
   We want to subset the dataset, so that it is just showing polygon features from
   Toronto. We are now going to find a tool that extracts the data we want (i.e.,
   Toronto census tracts) based on the attribute information. But first, we need to
   verify that there is attribute information about Toronto.

#. Open the 'CT_Canada' attribute table and look at the different field names.
   'cmaname' seems like the most likely candidate to have data about 'Toronto'.

   .. figure:: img/Lab2A_lookatctatt.png
     :align: center
   
#. Click the field header 'cmaname' so that records in the column are sorted
   alphabetically. Scroll down until you find 'Toronto'.  Once you have verified
   that there is information about 'Toronto', we can go look for the tool we need.
   
   You may have noticed that we are starting to use more tools, especially tools
   found under the 'Vector' tab. However, this is just scratching the surface.
   There is something called a 'Processing Toolbox' that is full of hundreds of 
   different tools used for various types of GIS analyses. We are going to take a 
   look in the 'Processing Toolbox'.

#. Go to the 'Processing' tab at the top of the QGIS session, and then click
   'Toolbox'. Once opened, take a moment and look through it and read the names, 
   and try to guess what some of the tools are used for.

   .. figure:: img/Lab2A_usefultoolbox.png
     :align: center

#. Once you are done, go to the 'Search' bar at the top of the 'Processing
   Toolbox' panel and start typing in 'Extract by attribute'.  Once it appears,
   click it.

   .. figure:: img/Lab2A_searchtoolbox.png
     :align: center

#. Now enter the information as shown below. Again, be sure to same it to your
   'Lab_2' GeoPackage; the three images show this process below.

   .. figure:: img/Lab2A_exbyattsavetogp.png
     :align: center

   .. figure:: img/Lab2A_savetolab2.png
     :align: center

   .. figure:: img/Lab2A_exbyattsettings.png
     :align: center

#. Your new dataset called 'CT_Toronto' should have been added to your QGIS
   session. You can zoom to your new layer by right clicking on 'CT_Canada'
   and going to 'Zoom to Layer'

   .. figure:: img/Lab2A_zoomto.png
     :align: center

Oh no, what do you notice? What we actually did was subset the Toronto Census
Metropolitan Area (CMA), as opposed to the City of Toronto. That's OK, there is
a work-around - we will instead use the 'Street Trees' dataset to subset census
tract dataset so that it is only City of Toronto census tracts.

   .. figure:: img/Lab2A_wrongtoronto.png
     :align: center

#. Navigate to the 'Vector' tab, and click 'Research Tools --> Select by Location'

   .. figure:: img/Lab2A_selbylocpng.png
     :align: center

#. Fill in the tool as shown below. Be sure to save the output to the Lab_2 
   GeoPackage.

   .. figure:: img/Lab2A_selbylocsettings.png
     :align: center

The correct census tract polygons should be highlighted in yellow, as shown below:

   .. figure:: img/Lab2A_righttorontoselect.png
     :align: center

#. Now we want to save the selected features.  This can be done by right clicking
   on 'CT_Toronto' layer, and go to 'Export --> Save Selected Features As...'. Name 
   it 'CT_Toronto_City' and fill out the dialog box as you have done before, and be 
   sure to save it to the 'Lab_2' GeoPackage. 

   .. figure:: img/Lab2A_saveselfeatas.png
     :align: center

   Once saved, check your 'Lab_2' GeoPackage in the 'Browser' panel.  If it is not
   there, use click the 'Refresh' button.

   .. figure:: img/Lab2A_refresh.png
     :align: center

   If the new layer has a strange name, change it to 'CT_Toronto_City' the same way
   you have done before.

We now want to get a count of the number of street trees that fall within each 
census tract.  We want to do this so we can calculate density (# of trees/CT area 
(km2).

#. Navigate to the 'Vector' tab, then go to 'Analysis Tools --> Count Points in
   Polygon'.

   .. figure:: img/Lab2A_cntpntpoly.png
     :align: center

#. Name the new layer CT_Toronto_City_pntcnt, and fill in the tool as shown below. 
   Remember to add your new layer to the 'Lab_2' GeoPackage. Make sure the new layer
   is added to the 'Map Canvas'.

   .. figure:: img/Lab2A_cntpntsettings.png
     :align: center

We now want to use the non-spatial, or tabular dataset.  But how do we incorporate
non-spatial data in GIS? Remember at the end of Lab 1 Part C, we performed a table
join? We will now do that to link the non-spatial data with a spatial dataset.

Open both the 'CT_data' and 'CT_Toronto_City_pntcnt' attribute tables and take a look
at the different fields. Between the two attribute tables, do you notice any two fields
that look similar?

   .. figure:: img/Lab2A_tablecompare.png
     :align: center

I would say, fields 'ctuid' and 'GEO_UID' look fairly similar. Let's try to join them.

#. Do the same as we did at the end of Lab 1 Part C.  Right click on 'CT_Toronto_City_pntcnt'
   and click 'Properties'.  Once the window opens, click the 'Join' tab.

#. Click the '+' and fill out the tool.  Remember, we are joining the 'CT_Toronto_City_pntcnt'
   and 'CT_data' by the fields 'ctuid' and 'GEO_UID'.

#. Once you have completed the 'Join', go look at the attribute table for 'CT_Toronto_City_pntcnt'
   and scroll through the joined fields.

   .. figure:: img/Lab2A_joinnullspng.png
     :align: center
   
   What do you notice? That's right, there are NULL values. Something went wrong with our
   Join. Let's compare the two tables again. You may notice that certain values of the
   'GEO_UID' are only seven characters in length, compared to the 'ctuid' that are all
   consistenty 10 characters.  We need to create a new column with values that match 
   'ctuid' perfectly. Here's how.

   .. figure:: img/Lab2A_tablecompare.png
     :align: center

#. Open the 'CT_Data' attribute table and go to the 'Field Calculator'.

#. Once open, fill out the field calculator as shown below. What the formula is doing,
   is adding '.00' to the end of all values in the 'GEO_UID' field that have a length
   of seven characters.

   .. figure:: img/Lab2A_fieldcalc.png
     :align: center

   Check your new 'ctuid' values and make sure each value as 10 characters. Yes? Let's 
   try that Join again.

#. We have to remove this join. Go back to the 'Join' tab, and remove the join by selecting 
   'Join Layer' and then click the '-'.

   .. figure:: img/Lab2A_removejoin.png
     :align: center

#. Now redo the Join. Remember, the 'Join Field' and 'Target Field' will now both be 
   'ctuid'. Check your results and make sure there are no more (or very few) NULL values.

#. Now that we have the data joined, we need to export the joined file. Do as you have done
   before. Name the file 'CT_Toronto_join', and save it in your 'Lab_2' GeoPackage.

We now want to calculate tree density. The new 'CT_Toronto_join' layer has a field that
represents the area of the census tract, 'AREA_KM2'.  We will perform a field calculation 
to determine tree density.

#. Let's start by adding a new field called 'TREES_KM2' to the 'CT_Toronto_join' layer.

   .. figure:: img/Lab2A_newfielddensity.png
     :align: center

#. Once the new field is added, go to the field calculator and populate the tool with
   the information shown below.

   .. figure:: img/Lab2A_treedensity.png
     :align: center

   The formula is dividing the number of trees within each census tract by the census tract
   area.

#. Now we want to do the same calculations, but for population density this time. Repeat
   the two previous steps, using the same formula, except instead of number of trees, use
   POPULATION/AREA_KM2.

We have finally completed our data processing! We are ready to perform our classification.

|basic| |FA| Creating a choropleth map
-------------------------------------------------------------------------------
  
As we did with Lab 1, we will classify our data.  Remember, you only have to create maps for
Street Tree density and either median income or population density.  However, I would like
you to classify all three variables.

#. We are going to the change symbology for 'CT_Toronto_join'. Navigate to 'Properties -->
   Symbology'.

#. Set the symbol type to 'Graduated', and then change the value to 'MEDIAN_INCOME'. But wait,
   'MEDIAN_INCOME', does not show up. Why do you think that is?

   .. figure:: img/Lab2A_noincome.png
     :align: center

#. While in 'Properties', navigate to the 'General Information' tab, and inspect the metadata.
   What type of data is 'MEDIAN_INCOME'? String! So it is technically qualitative, therefore can
   not be classified using graduated symbology. We will need to add a new field with the same
   'MEDIAN_INCOME' values, but make it a numeric value. 

#. To do this, we need to create a new field, call it 'MEDIAN_INCOME_num', make it type 'Decimal
   Number'.

#. Once the field is created, you can populate it in the 'Field Calculator', by entering this 
   formula: 'MEDIAN_INCOME_num = 'MEDIAN_INCOME'.

#. Once that is completed proceed to the Symbology window again, and classify 'MEDIAN_INCOME_num'
   using 'Graduated' symbology. 

#. However, we want to classify the same layer using three different variables, so let's duplicate
   'CT_Canada_join' twice, so there are three copies.

#. We then want to rename each copy so we don't get them confused.  One at a time, right click on 
   both copies and the original, and go to 'Rename'.  Give them each a name associated with the
   variable being classified.

   .. figure:: img/Lab2A_renamelayer.png
     :align: center

#. Select an appropriate classification. As we discussed in class, quantile, is likely the most
   appropriate classification technique, but Natural Breaks is also acceptable. We also discussed
   that 5 classes is generally the most appropriate number of classes, but sometimes 6 works as 
   well.  Just remember, whatever you decided on, you need to have the same classification and number
   of classes for each of the 3 variables.

   .. figure:: img/Lab2A_classification.png
     :align: center

   Be sure to look at the histogram while you are trying to decide number of classes and classification.

   .. figure:: img/Lab2A_hist.png
     :align: center

   You have now classified your three variables! Now take a moment and look at how spatial patterns
   of high/low street tree density coincides with areas of both high/low median income and population 
   density. Do you notice any interesting patterns? Based on what you observe, select either median
   income or population density to (1) create a map and (2) use in the next section of Lab 2
   Part A.


|moderate| |TY| Introduction to Vector Overlay Analyses and Expressions
-------------------------------------------------------------------------------

We are now going to start exploring overlay analyses! We are going to use the 'Select by Location' 
tool to enhance our ability to extract patterns of occurence.  So far we have used our eyes to 
explore patterns of occurrence between street tree density and population density/median income.  
However, we now want to know exactly where these patterns are occuring.

*The following instructions outline an EXAMPLE to complete this assignment.*

In my example for this assignment, I have chosen to look at areas of low street tree density and
low median income. I want to subset my two spatial datasets so that they only show the census
tracts that have low street tree density amd low median income.  To start, I will subset my 
street tree density layer. To do this, I will use the 'Select by Expression' tool found in 
the attribute table dialog, and use a standard query language (SQL) expression to subset my dataset.
However, to be able to subset my dataset, I need to select a 'Threshold' value that defines 
'low street tree density'.  This value has to come from somewhere meaningful - you can never just
select an arbitrary value to use as a threshold. In this case it is importat to look at your histogram.

#. Start by opening your 'Properties' window and navigating to the 'Symbology' tab. 

#. Select the 'Histogram' tab and click 'Load Values'.

   .. figure:: img/Lab2A_hist.png
     :align: center

What do you observe about this histogram? I see a small clustering of low, similar values on the
left side of the histogram. Perhaps that could be your threshold value? 

   .. figure:: img/Lab2A_classification.png
     :align: center

Alternatively, you could use the upper value of your lowest class range. That is what I decided to
do, therefore 592 is my threshold that defines 'low street tree density'. You can choose another
method for determining a threshold, so long as you can back it up with a reason for your decision. 

Now that we have our threshold, we can subset our dataset using an expression.

#. Close your 'Properties' window and open your 'Attribute Table'.

#. Click on the 'Select by Expression' icon.


   .. figure:: img/Lab2A_selectbyexp.png
     :align: center


#. A dialog box will open. Enter the expression as shown below but *USE YOUR THRESHOLD VALUE*
   and click 'Select Features'. 


   .. figure:: img/Lab2A_lessthan592.png
     :align: center


#. Exit out of the 'Select by Expression' window and 'Attribute Table'.  You should notice a series
   of census tract polygons are highlighted yellow. These are all of your lowest street tree
   density values!

#. We want to save these selected features as a layer in our GeoPackage. Right click on your
   Street Tree Density layer, and go to 'Export --> Save Selected Features As', and save your
   new layer in your 'Lab_2' GeoPackage, giving it a meaningful name e.g., 'TreeDensity_low'.

   .. figure:: img/Lab2A_saveselect.png
     :align: center

   *Now, you have to do all of the same steps listed above to create a new layer for either median
   income or population density.*  Once that is completed, we can move onto the final step of our
   analysis.

   We will now use our two new layers e.g., 'TreeDensity_low' and 'MedianIncome_low' to perform
   a 'spatial selection' to identify areas where there are both low tree density and low median
   income.

#. Navigate to the 'Vector' tab, and go to 'Research Tools --> Select by Location'. A dialog window
   will open.

   The 'Select by Location' tool works by comparing two layers and determing which features
   spatially interact based on a seletec 'spatial relationship'.  In the dialog window, you 
   will see there are several options for 'Where the features (geomtric predicate)'.  These 
   options are called 'spatial relationships'. For our project, we will use 'contain' for our 
   spatial relationship, as we want to know which census tracts have both low income and low 
   tree density. Based on what we know about topology, if we used 'intersect' or 'touch', 
   polygons that share boundaries would also be selected, which we do not want for this analysis.

#. Use the settings below, and click run.

   .. figure:: img/Lab2A_saveselect.png
     :align: center

#. Exit out of the 'Select by Location' window. You should see census tracts that are both
   low tree density and low median income highlighted in yellow.

#. Now, as you did for both 'TreeDensity_low' and 'MedianIncome_low' layers, create a new
   layer for your 'Select by Location' selection.  Call it something like, 
   'Toronto_lowtrees_lowincome'.  This is what my layer looks like - but yours will likely
   look different!

   .. figure:: img/Lab2A_lowselectbyloc.png
     :align: center

You have now completed your analysis! Congratulations! Now, create (1) a map showing 'Street Tree
Density' classification, (2) a map showing either 'Median Income' or 'Population Density'
classification, and (3) a map of your 'Select by Location' selection.

In addition to the three maps, please write a brief paragraph describing the parameters you used
for this analysis, including:

   #. Classification mode used to classify both classified maps (i.e., street tree density and 
      median income OR population density),
   #. Thresholds used to subset both datasets (i.e., street tree density and 
      median income OR population density) and
   #. The method used to select both Thresholds.
   


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
