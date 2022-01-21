.. _tm_working_vector_data:

|LS| Choropleth Mapping: Toronto Street Tree Density in Relation to Median Income 
and Population Density
-------------------------------------------------------------------------------

So far we have discussed four different types of classification, including nominal,
ordinal, interval and ratio. The map for Lab 1 Part A was a nominal classification.
We also practiced making a ratio classification when we mapped area for the 
'ELC_campus' dataset in Lab 1 Part A.

Now we are going to create choropleth maps. A choropleth map is defined as "a 
thematic map that displays a quantitative attribute using ordinal classes. Areas 
are shaded according to their value and a range of shading classes'. Choropleth
maps are most often 

For Lab 2 Part A we will be creating two choropleth maps for the city of Toronto; 
one will be Toronto Street Tree Density and the other will be your choice of either
median income or population density.  With these two maps, we will visually interpret
spatial patterns and determine whether there is an association between both variables.
You will then choose a pattern you would like to investigate further, by picking a
threshold value to subset your dataset, using standard query language (SQL). Once data
are subset, you will used the geoprocessing tool called 'Intersection' to identify
areas that overlap from both maps.

The deliverable for this portion of the assignment will be three maps: (1) Street Tree
density map, (2) a median income or population density map and (3) a map showing
your 'Intersection' output.

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

#. To do this, we need to create a new field, call it 'MEDIAN_INCOME_num', make it type 'integer'.

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

   Be sure to look at the histogram while you are trying to decide number of classes and classification

   .. figure:: img/Lab2A_hist.png
     :align: center

   A row is called a **record** and is associated with a **feature**
   in the Canvas Map, such as a polygon.
   A column is called a **field** (or an **attribute**), and has a name that helps
   describe it, such as ``name`` or ``id``.
   Values in the cells are known as **attribute values**.
   These definitions are commonly used in GIS, so it is good to become
   familiar with them.

   In the ``ELC_campus`` layer, there are 82 **features** (noted at the top of the 
   attribute table window), which are represented by the polygons we see on the Map Canvas. 

   .. Note:: In order to understand what the **fields** and **attribute values** 
      represent, one may need to find documentation (or metadata) describing 
      the meaning of the attribute values.

      The ``ELC_campus`` layer was obtained fromt the Niagara Peninsula Conservation 
      Authority open data portal: https://gis-npca-camaps.opendata.arcgis.com/. The website
      has many natural resources spatial datasets available for online viewing and download.
      There is metadata available for each dataset, which helps users better understand 
      the data they are working with.

      For the ``ELC_campus`` dataset, the abstract is as follows:

      The NPCA Natural Areas Inventory (NAI) Ecological Land Classification (ELC) Community 
      Series (CS) level DRAFT feature class is a polygon fabric serving as base inventory of
      natural area features (i.e. Mixed Meadow, Swamp Thicket).
      
      The NPCA Natural Areas Inventory (NAI) Ecological Land Classification (ELC)
      Community Series (CS) level DRAFT feature class is a polygon fabric serving as 
      base inventory of natural area features (i.e. Mixed Meadow, Swamp Thicket). 
      Communities are interpreted from 2006 10 cm (Niagara) and 30 cm (Haldimand) 
      colour orthoimagery using a 1:1000 interpretive threshold. Feature geometry 
      linework was specified to meet a 1:2000 scale generalization threshold and the 
      minimum mapping unit used was 0.1 hectares although features may have been captured 
      beyond (better than) these standards. Some wetland community polygons come from the 
      MNR Ontario Wetland Evaluation System data. The data forms a scientifically-defensible 
      baseline for use in planning decisions and policy development and will be linked to 
      associated ecological survey data collected in the field under various protocols. 
      The dataset when completed will correspond to the extent of the Niagara Watershed. 
      

Next, let's see how a record in the attribute table is linked to a polygon 
feature that we see on the Map Canvas.

#. Go back to the main QGIS window.
#. In the :guilabel:`Attributes Toolbar`, click on the |selectRectangle| 
   :sup:`Select Feature` button.  
#. Make sure the ``ELC_campus`` layer is still selected in the 
   :guilabel:`Layers` panel.
#. Move your mouse to the Map Canvas and left click on the largest polygon
   covering Woodend Conservation Area.  The polygon will turn yellow 
   indicating it is selected.
   
   .. figure:: img/Classification_woodend.png
      :align: center
   
#. Go back to the :guilabel:`Attribute Table` window, and if you scroll down
   to the bottom of the table you should see a record (row) highlighted.  
   These are the attribute values of the selected polygon.
   
   .. figure:: img/ELC_campus_vector_class_selectrecord1.png
     :align: center

You can also select a feature using the Attribute Table.

#. In the :guilabel:`Attribute Table` window, on the far left, click on a 
   row number of a record that is currently not selected.

   .. figure:: img/ELC_campus_vector_class_selectrecord2.png
     :align: center

#. Go back to the main QGIS window and look at the Map Canvas. You should 
   see a different polygon colored yellow.  
#. To deselect the feature, go to the :guilabel:`Attribute Table` window 
   and click on |deselectActiveLayer| :sup:`Deselect all features from the layer` button.

Sometimes there are many features shown on the Map Canvas and it might be difficult
to see which feature is selected from the Attribute Table.  Another way to 
identify the location of a feature is to use the :guilabel:`Flash Feature`
tool.

#. In the :guilabel:`Attribute Table`, right-click on any cell in the
   row that has the attribute value ``113554`` for the field ``OBJECTID``.
#. In the context menu, click on :guilabel:`Flash Feature` and watch the 
   Map Canvas.  

   .. figure:: img/ELC_campus_vector_class_flashfeature.png
     :align: center
   
   You should see the polygon flash red a few times.  If you missed it, 
   try it again.

Another useful tool is the :guilabel:`Zoom to Feature` tool, that tells QGIS to 
zoom to the feature of interest.

#. In the :guilabel:`Attribute Table`, right-click on  any cell in the
   row that has the attribute value ``113554`` for the field ``OBJECTID``.
#. In the context menu, click on :guilabel:`Zoom to Feature`

   .. figure:: img/ELC_campus_vector_class_zoomtofeature.png
     :align: center

   Look at the Map Canvas.  The polygon should now occupy the extent
   of the Map Canvas area.  
   
You may now close the attribute table.

.. _backlink-vector-explore-attribute-data:

|basic| |TY| Exploring Vector Data Attributes
-------------------------------------------------------------------------------

#. How many fields are available in the :guilabel:`rivers` layer?
#. Open the attribute table for the :guilabel:`wild_species` layer.
   Tell us a bit about the ``ELC_ClassCode`` of the wood ducks in the wild_species 
   dataset. 
   If we are creating a map showing the location of different field project monitoring sites,
   Which field would be the most useful to represent in label form, and why?

.. admonition:: Answer
   :class: dropdown

   * There should be 45 fields in the :guilabel:`rivers` layer:

     #. Select the layer in the :guilabel:`Layers` panel.
     #. Right-click and choose :guilabel:`Open Attribute Table`, or press the |openTable|
        button on the :guilabel:`Attributes Toolbar`.
     #. Count the number of columns.

     A quicker approach could be to double-click the :guilabel:`rivers` layer, 
     open the :menuselection:`Layer properties --> Fields` tab, where you will 
     find a numbered list of the table's fields.

   * Information about ELC class code for wood ducks is available in the :guilabel:`wild_species` layer. Open its
     attribute table as you did with the :guilabel:`rivers` layer:
     there is a field called ``CSCode1``.  By clicking on the ``species`` field name,
     records are automatically sorted alphabetically.  If you scroll down to wood duck records, you will find the
     ELC class codes associated with the wood ducks in the adjacent field. We can see that wood ducks are found in
     FOD (Deciduous Forest) and OAO (Open Aquatic).

   * The ``Species`` field is the most useful to show as labels for the purpose of our hypothetical map.

|IC|
-------------------------------------------------------------------------------

You now know how to use the attribute table to see what is actually in the data
you're using. Any dataset will only be useful to you if it has the attributes
that you care about. If you know which attributes you need, you can quickly
decide if you're able to use a given dataset, or if you need to look for
another one that has the required attribute data.

|WN|
-------------------------------------------------------------------------------

Different attributes are useful for different purposes. Some of them can be
represented directly as text for the map user to see. You'll learn how to do
this in the next lesson.


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
