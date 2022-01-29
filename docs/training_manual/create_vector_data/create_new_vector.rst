|LS| Creating a New Vector Dataset
===============================================================================

The data that you use has to come from somewhere. For most common applications,
the data exists already; but the more particular and specialized the project,
the less likely it is that the data will already be available. 

For this part of Lab 1 Part B, you will be digitizing five different Ecological
Land Classification (ELC) community series. If you recall, ELC is composed of six
nested levels, as shown below.


   .. figure:: img/Create_communityseries.png
     :align: center

Read the following information to learn more about a community series.
   
   .. figure:: img/Create_communityseriesdescrip.png
     :align: center


For Part B, you will be required to digitize five polygons for five different
community series:

MEM: Mixed Meadow 
MAS: Shallow Marsh
FOD: Deciduous Forest
THD: Deciduous Thicket
HOD: Deciduous Hedgerow

Please review the PDF, 'ELCCodes_new' found on BlackBoard under Assignments/
Lab 1 to gain a better understanding of characteristics of these classes. Also,
please refer to the images below to get an idea of % cover for when you are doing
your interpretation.


   .. figure:: img/Create_cover.png
     :align: center


   .. figure:: img/Create_covertable.png
     :align: center


In Part C, you will visit three of the five polygons and collect three GPS points
and QField points in each. So make sure you digitize areas that are accessible by foot
(i.e., avoid digitizing areas in Woodend Conservation Area).



|basic| |FA| Data Sources
-------------------------------------------------------------------------------

When you create new data, it obviously has to be about objects that really
exist on the ground. Therefore, you'll need to get your information from
somewhere.

There are many different ways to obtain data about objects. For example, you
could use a GPS to capture points in the real world, then import the data into
QGIS afterwards. Or you could use the digitizing process to trace objects from 
remote sensing data, such as satellite imagery or aerial photography, as we have
discussed in class.

For our example, you'll be using the digitizing approach. We will use the basemap
we used in Module 5.1 to digitize our community series polygons.  However, we will 
also import an image from 2006 to give you the opportunity to observe changes that 
have occurred between 2006 and 2020. Also, as discussed, the 'ELC_campus' layer
was created using 2006 imagery, so you will get the chance to observe the mapping
accuracy and technique used when developing the 'ELC_campus' layer. 

#. We are going to add the 2006 image, 'NCCampus_Pan2006.tif'. Use your 'Browser' panel
   to navigate to your /Lab_1 folder and drag and drop the 'NCCampus_Pan2006' image
   onto your map canvas.
   
#. Alternative, you can Click on |dataSourceManager| :sup:`Data Source Manager` button.

#. Select |raster| :guilabel:`Raster` on the left side.

#. In the :guilabel:`Source` panel, click on the :guilabel:`...` button: 

#. Navigate to :file:`/Lab_1`.

#. Select the file :file:`NCCampus_Pan2006`.

#. Click :guilabel:`Open` to close the dialogue window.

#. Click :guilabel:`Add` and :guilabel:`Close`. An image will load into your map.

   .. figure:: img/Create_pan2006.png
     :align: center

#. Organize your layers so that appear as shown below:

   .. figure:: img/Create_layerorder.png
     :align: center


Now, turn off all the layers, except for 'ELC_campus' and 'NCCampus_Pan2006'. Take
a moment and examine how the boundaries of 'ELC_campus' line up with the 2006
aerial image. Once you have examined how the boundaries align with vegetation in the
image, turn off the ELC layer, and turn on the 'ESRI Satellite' layer. Toggle the
'ESRI Satellite' on and off to observe changes that have occurred between 2006 and
2020.


|basic| |FA| The Layer Creation Dialog
-------------------------------------------------------------------------------

Before you can add new vector data, you need a vector dataset to add it to. In
our case, you'll begin by creating new data entirely, rather than editing an
existing dataset. Therefore, you'll need to define your new dataset first.

#. Building on your Lab 1 Part B assignment, navigate to your /Lab_1
   folder in the Browser panel.

#. Right click on your /Lab_1 folder and go to :menuselection:`New --> Shapefile`.
   You'll be presented with the :guilabel:`New Shapefile Layer` dialog, which will
   allow you to define a new layer.

   .. figure:: img/Topo_newshapefile.png
     :align: center

#. Click :guilabel:`...` for the :guilabel:`File name` field.
   A save dialog will appear.
#. You should already be in your /Lab_1 folder, but if not, navigate to 
   the /Lab_1 folder.
#. Save your new layer as :file:`ELC_communityseries.shp`, or a name that you feel is
   appropriate and has meaning.

   It's important to decide which kind of dataset you want at this stage. Each
   different vector layer type is "built differently" in the background, so once
   you've created the layer, you can't change its type.

   For the next step, we're going to create new features which describe
   areas. For such features, you'll need to create a polygon dataset.

#. For :guilabel:`Geometry Type`, select :guilabel:`Polygon` from the drop down menu:

   .. figure:: img/Topo_newshapepoly.png
     :align: center

   This has no impact on the rest of the dialog, but it will cause the correct
   type of geometry to be used when the vector dataset is created.

   The next field allows you to specify the Coordinate Reference System,
   or CRS. If you recall, we set the project projection in our very first module. Therefore,
   your CRS should already be set to NAD83 UTM Zone 17N.

   Next there is a collection of fields grouped under :guilabel:`New Field`.
   By default, a new layer has only one attribute, the ``id`` field (which you
   should see in the :guilabel:`Fields list`) below. However, in order for the
   data you create to be useful, you actually need to say something about the
   features you'll be creating in this new layer. For our current purposes, it
   will be enough to add one field called ``ClassCode`` that will hold ``Text data``
   and will be limited to text length of ``80`` characters.

#. Replicate the setup below, then click the :guilabel:`Add to Fields List` button.
   Check that your dialog now looks like this:

   .. figure:: img/Topo_newshapesettings.png
     :align: center

#. Click :guilabel:`OK`

The new layer should appear in your :guilabel:`Layers` panel. It is empty,
so there will be nothing on your 'Map Canvas'.

Now you are ready to digitize your community series polygons.

Before starting to digitize, be sure to toggle of the ``ELC_campus`` layer and
make sure your new shapefile is above the 'ESRI_Satellite' in the 'Layers' panel, by 
selecting ``ELC_communityseries`` layer and dragging it to the top.

Also, make sure 'Snapping' is on, so if your polygons share nodes and edges, you can
add topology.


In order to begin digitizing, you'll need to enter 'Edit' mode for the ``ELC_communityseries`` 
layer, as you did while editing your other layers from the previous lesson. 

#. Click on the |capturePolygon| :sup:`Capture Polygon` button to begin digitizing
   your community series polygons.

   You'll notice that your mouse cursor has become a crosshair. This allows you to
   more accurately place the points you'll be digitizing. Remember that even when
   you're using the digitizing tool, you can zoom in and out on your map by
   rolling the mouse wheel, and you can pan around by holding down the mouse wheel
   and dragging around in the map.

   Typically you want to digitize at a fixed scale that balances accuracy but also
   allows you to digitize fairly quickly, without getting too caught up in fine details.
   For this assignment, let's set our scale to 1:1500, as shown below, and lock it, by
   clicking the lock.

   .. figure:: img/Topo_lockscale.png  
     :align: center

   You can still zoom in and out, but we want to maintain a relatively constant scale to
   ensure our digitizing is consistent.

#. Start digitizing by clicking on a point somewhere along the edge of your habitat polygon.
#. Place more points by clicking further along the edge, until the shape you're
   drawing completely encapsulates your habitat area.
#. After placing your last point, right click to finish drawing the polygon.
   This will finalize the feature and show you the :guilabel:`Attributes` dialog.
#. For 'id' enter '001' and for ClassCode enter the ELC class you think it is. I entered
   FOD for my example polygon.

#. Click :guilabel:`OK`, and you have created a new feature!

   .. figure:: img/Topo_polyexample.png
     :align: center

#. In the :guilabel:`Layers` panel select the ``ELC_communityseries`` layer.
#. Right click and choose :guilabel:`Open Attribute Table` in the context menu.

   In the table you will see the feature you just added.
   While in edit mode you can update the attributes data by double click on the cell
   you want to update.

#. Close the attribute table.
#. To save the new feature we just created, click on |saveEdits| :sup:`Save Edits` button.

Remember, if you've made a mistake while digitizing a feature, you can always
edit it after you're done creating it. If you've made a mistake, continue
digitizing until you're done creating the feature as above. Then:

#. Click on |vertexToolActiveLayer| :sup:`Vertex Tool` button.
#. Hover the mouse over a vertex you want to move and left click on the vertex.
#. Move the mouse to the correct location of the vertex, and left click.
   This will move the vertex to the new location.

   If you want to undo a change, you can press the |undo| :sup:`Undo` button or :kbd:`Ctrl+Z`.

#. Remember to save your changes by clicking the |saveEdits| :sup:`Save Edits` button.
#. Now continue to digitize the rest of your community series polygons.
#. When done editing, click the |toggleEditing| :sup:`Toggle Editing` button
   to get out of edit mode.


|IC|
-------------------------------------------------------------------------------

Now you know how to create features! We won't practice digitizing point
features, because that's not really necessary once you've worked with more
complicated features (lines and polygons). It works exactly the same, except
that you only click once where you want the point to be, give it attributes as
usual, and then the feature is created.

Knowing how to digitize is important because it's a very common activity in GIS
programs.

You are now almost done Lab 1 Part B. Please create a map showing your five community
series polygons in relation to the wild species management projects. Be sure to include
all of your updated layers. Feel free to use the same 'Map Layout'from Lab 1 Part A, 
or go ahead and change the layout completely - so long as you have all the required 
map elements.

Well done!

|WN|
-------------------------------------------------------------------------------

Next week we will be grounthruthing our community series polygons to see if our
photo interpretation was correct. Please have your data loaded in QField before you
come to class next week!


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
.. |captureLine| image:: /static/common/mActionCaptureLine.png
   :width: 1.5em
.. |capturePolygon| image:: /static/common/mActionCapturePolygon.png
   :width: 1.5em
.. |dataSourceManager| image:: /static/common/mActionDataSourceManager.png
   :width: 1.5em
.. |moderate| image:: /static/common/moderate.png
.. |raster| image:: /static/common/mIconRaster.png
   :width: 1.5em
.. |saveEdits| image:: /static/common/mActionSaveEdits.png
   :width: 1.5em
.. |schoolAreaType1| replace:: athletics field
.. |toggleEditing| image:: /static/common/mActionToggleEditing.png
   :width: 1.5em
.. |undo| image:: /static/common/mActionUndo.png
   :width: 1.5em
.. |vertexToolActiveLayer| image:: /static/common/mActionVertexToolActiveLayer.png
   :width: 1.5em
.. |zoomIn| image:: /static/common/mActionZoomIn.png
   :width: 1.5em
