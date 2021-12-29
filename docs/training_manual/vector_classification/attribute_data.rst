.. _tm_working_vector_data:

|LS| Vector Attribute Data
===============================================================================

Vector data is arguably the most common kind of data in the daily
use of GIS. The vector model represents the location and shape of geographic
features using points, lines and polygons (and for 3D data also surfaces and
volumes), while their other properties are included as attributes (often presented
as a table in QGIS).

Up to now, none of the changes we have made to the map have been influenced by
the objects that are being shown. In other words, all the land use areas look
alike, and all the roads look alike. When looking at the map, the viewers don't
know anything about the roads they are seeing; only that there is a road of a
certain shape in a certain area.

But the whole strength of GIS is that all the objects that are visible on the
map also have attributes. Maps in a GIS aren't just pictures. They represent
not only objects in locations, but also information about those objects.


**The goal for this lesson:** To learn about the structure of vector data and
explore the attribute data of an object

|basic| |FA| Viewing Layer Attributes
-------------------------------------------------------------------------------

It's important to know that the data you will be working with does not only
represent **where** objects are in space, but also tells you **what** those
objects are.

From the previous exercise, you should have the ``ELC_campus`` layer
loaded in your map. If it is not loaded, then you can find the 
:file:`ELC_campus.shp` *ESRI Shapefile* format dataset in directory 
:file:`exercise_data/shapefile`.

The polygons representing the ELC polygons constitute the **spatial data**,
but we can learn more about the ELC polygons by exploring the
**attribute table**.

#. In the :guilabel:`Layers` panel, click on the ``ELC_campus`` layer to 
   select it.
#. In the :guilabel:`Attributes Toolbar` click the |openTable| 
   :sup:`Open Attribute Table` button. This will open a new window showing 
   the attribute table of the ``ELC_campus`` layer.  

   .. figure:: img/ELC_campus_vector_class.png
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
