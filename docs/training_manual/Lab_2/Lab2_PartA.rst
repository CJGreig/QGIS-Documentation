.. _tm_working_vector_data:

|LS| Choropleth Mapping: Toronto Street Tree Density in Relation to Median Income 
and Population Density
===============================================================================

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
#. Navigate to the 'Browser' panel and add the three tables within it to your
   QGIS session

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

#. Now 

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
