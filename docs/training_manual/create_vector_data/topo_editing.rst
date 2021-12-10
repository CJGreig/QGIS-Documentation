|LS| Feature Topology
======================================================================

Topology is defined as the spatial relationships between neighbouring features.
Topology is a useful aspect of vector data layers, because it minimizes errors
such as overlap or gaps.

For example: if two features share a border, and you edit the border using
topology, then you won't need to edit first one feature, then another, and
carefully line up the borders so that they match. Instead, you can edit their
shared border and both features will change at the same time.

For part B of Lab 1 you will (1) edit existing shapefiles used to create your map
from Part A of Lab 1 and (2) create a new vector layer based on maps you created 
in your Environmental Ecology course.  When we started working with the campus data,
you may have noticed that the base map was from 2006.  However, we now want to
update our map so that your next map is current. 

First open up your existing QGIS file title Campus Ecology. Once it is open, navigate to
`Project --> Save as...`, and save a new copy of the project in the exercise_data folder.
Call is Campus Ecology 2018. Once you have saved your new QGIS project, you are ready to
start Part B. Building off of your existing map, you will remove the `ELC_campus` layer 
from your map.

**The goal for this lesson:** To understand topology using examples.

|basic| |FA| Data Sources
-------------------------------------------------------------------------------

When you create new data, it obviously has to be about objects that really
exist on the ground. Therefore, you'll need to get your information from
somewhere.

There are many different ways to obtain data about objects. For example, you
could use a GPS to capture points in the real world, then import the data into
QGIS afterwards. Or you could survey points using a theodolite, and enter the
coordinates manually to create new features. Or you could use the digitizing
process to trace objects from remote sensing data, such as satellite imagery
or aerial photography.

For our example, you'll be using the digitizing approach. Sample raster datasets
are provided, so you'll need to import them as necessary.

#. Click on |dataSourceManager| :sup:`Data Source Manager` button.
#. Select |raster| :guilabel:`Raster` on the left side.
#. In the :guilabel:`Source` panel, click on the :guilabel:`...` button: 
#. Navigate to :file:`exercise_data/raster/`.
#. Select the file :file:`3420C_2010_327_RGB_LATLNG.tif`.
#. Click :guilabel:`Open` to close the dialogue window.

   .. figure:: img/add_raster.png
     :align: center

#. Click :guilabel:`Add` and :guilabel:`Close`. An image will load into your map.

   .. figure:: img/raster_added.png
     :align: center

#. If you don't see an aerial image appear, select the new layer, right click,
   and choose :guilabel:`Zoom to Layer` in the context menu.

   .. figure:: img/zoom_to_raster.png
     :align: center

#. Click on the |zoomIn| :sup:`Zoom In` button, and zoom to the area highlighted in blue below:

   .. figure:: img/map_area_zoom.png
     :align: center


Now you are ready to digitize these three fields:

   .. figure:: img/field_outlines.png
     :align: center

Before starting to digitize, let's move the ``school_property`` layer above the aerial image.

#. Select ``school_property`` layer in the :guilabel:`Layers` pane and drag it to the top.

.. figure:: img/move_school_layer.png
     :align: center

Alternatively, raster data can be loaded with the :guilabel:`Browser` Panel. In fact, this
method is easier, and can also be used to load vector data.

#. Open the :guilabel:`Browser` Panel and expand the
   :file:`exercise_data/raster` folder.
#. Load all the data in this folder:

   * :file:`3320C_2010_314_RGB_LATLNG.tif`
   * :file:`3320D_2010_315_RGB_LATLNG.tif`
   * :file:`3420B_2010_328_RGB_LATLNG.tif`
   * :file:`3420C_2010_327_RGB_LATLNG.tif`

You should see the following map:

.. figure:: img/raster_step_one.png
   :align: center

|moderate| |FA| Snapping
----------------------------------------------------------------------

Snapping makes topological editing easier.
This will allow your mouse cursor to snap to other objects while you
digitize. It is good practice to set snapping options at the beginning
of each editing session

To set snapping options:

#. Navigate to the menu entry
   :menuselection:`Project --> Snapping Options...`.
#. Set up your :guilabel:`Snapping options` dialog to activate the
   all layers with :guilabel:`Type` *vertex* and tolerance
   ``12`` pixels:

   .. figure:: img/set_snapping_options.png
      :align: center

#. Make sure that the box in the :guilabel:`Avoid overlap` column is
   checked.
#. Leave the dialog.

If you experiment with the tool, you may notice that the snapping
options can prevent you from creating a ring inside a polygon.
So you are advised to turn off snapping before cutting a hole.

#. Disable snapping for the ``landuse`` layer using the |snapping|
   :sup:`Enable Snapping` button (or use the shortcut :kbd:`s`).
#. Use the |addRing| :sup:`Add Ring` tool to create a hole in the
   middle of a polygon geometry.
#. Draw a polygon over the target feature, as if you were using the
   |capturePolygon| :sup:`Add polygon` tool.
#. When you right-click, the hole will be visible.
#. Remove the hole you just created using the |deleteRing|
   :sup:`Delete Ring` tool.
   Click inside the hole to delete it.

|basic| |FA| Deleting Polygons and Editing Existing Shapefiles
----------------------------------------------------------------------

You probably noticed that there are a few extra buildings that are
no longer on the new base map.  We want to remove these buildings
from the ``buildings`` layer. However, we do not want to edit the
existing ``buildings`` shapefile. To avoid this, we will make a copy:

#. Right click on the ``buildings`` layer in the Layer panel and go to
   `Export --> Save Features As...`
#. Call the new ``buildings`` shapefile ``buildings_new``
#. Click OK and ensure the new layer is added to your QGIS session.

In order to begin editing ``buildings_new``, you'll need to enter **edit mode**. GIS software
commonly requires this to prevent you from accidentally editing or deleting
important data. Edit mode is switched on or off individually for each layer.

To enter edit mode for the ``buildings_new`` layer:

#. Click on the ``buildings_new`` layer in the :guilabel:`Layers` panel to select it.
#. Click on the |toggleEditing| :sup:`Toggle Editing` button.

   If you can't find this button, check that the :guilabel:`Digitizing` toolbar is
   enabled. There should be a check mark next to the :menuselection:`View -->
   Toolbars --> Digitizing` menu entry.

   As soon as you are in edit mode, you'll see that some editing tools have become
   active:

     - |capturePolygon| :sup:`Capture Polygon`
     - |vertexToolActiveLayer| :sup:`Vertex Tool`

   Other relevant buttons are still inactive, but will become active when
   we start interacting with our data.

   Notice that the layer ``buildings_new`` in the :guilabel:`Layers` panel now
   has the pencil icon, indicating that it is in edit mode.

Now that you are in edit mode, you are ready to delete a feature.

#. Click on |mActionSelectRectangle| :sup:`Select Features by Area or Single Click` button.
#. Navigate to the feature you would like to remove, and click it.
#. Once clicked, you can push delete on your keyboard. If you make an error, you can use
   keyboard short-cut CTRL Z to undo.

You will also notice there is a new building next to the campus barn in the new base map.

 .. figure:: img/school_area_one.png
     :align: center

#. To digitize a feature click on the |capturePolygon| :sup:`Capture Polygon` 
   button to begin digitizing the new buildings.

   You'll notice that your mouse cursor has become a crosshair. This allows you to
   more accurately place the points you'll be digitizing. Remember that even when
   you're using the digitizing tool, you can zoom in and out on your map by
   rolling the mouse wheel, and you can pan around by holding down the mouse wheel
   and dragging around in the map.

#. Start digitizing by clicking on a point somewhere along the edge of the building.
#. Place more points by clicking further along the edge, until the shape you're
   drawing completely covers the building.
  
   .. figure:: img/school_field_outline.png
     :align: center

#. After placing your last point, right click to finish drawing the polygon.
   This will finalize the feature and show you the :guilabel:`Attributes` dialog.
#. Fill in the values as below:

   .. figure:: img/school_area_one_attributes.png
     :align: center

#. Click :guilabel:`OK`, and you have created a new feature!

   .. figure:: img/new_feature.png
     :align: center

#. In the :guilabel:`Layers` panel select the ``buildings_new`` layer.
#. Right click and choose :guilabel:`Open Attribute Table` in the context menu.

   .. figure:: img/open_attribute_table.png
     :align: center

   In the table you will see the feature you just added.
   While in edit mode you can update the attributes data by double click on the cell
   you want to update.

   .. figure:: img/feature_table.png
     :align: center

#. Close the attribute table.
#. To save the new feature we just created, click on |saveEdits| :sup:`Save Edits` button.

Remember, if you've made a mistake while digitizing a feature, you can always
edit it after you're done creating it. If you've made a mistake, continue
digitizing until you're done creating the feature as above. Then:

#. Click on |vertexToolActiveLayer| :sup:`Vertex Tool` button.
#. Hover the mouse over a vertex you want to move and left click on the vertex.
#. Move the mouse to the correct location of the vertex, and left click.
   This will move the vertex to the new location.

   .. figure:: img/select_vertex.png
     :align: center
   .. figure:: img/moved_vertex.png
     :align: center

   The same procedure can be used to move a line segment, but you will need to
   hover over the midpoint of the line segment.

   If you want to undo a change, you can press the |undo| :sup:`Undo` button or :kbd:`Ctrl+Z`.

#. Remember to save your changes by clicking the |saveEdits| :sup:`Save Edits` button.
#. When done editing, click the |toggleEditing| :sup:`Toggle Editing` button
   to get out of edit mode.

|moderate| |FA| Correct Topological Features
----------------------------------------------------------------------

Topology features can sometimes need to be updated.
In our study area, you may notice that with the updated base map, the buildings, 
roads and impervious surfaces no longer align with the base map. We will start
by editing `impervious_surfaces`.

.. figure:: img/zoom_to.png
   :align: center

We are going to use the *Vertex Tool* to edit the existing polygons.

#. Select the |vertexToolActiveLayer| :sup:`Vertex Tool` tool.
#. Choose the north parking lot of ``impervious_surfaces``, select a vertex, and move it to the
   edge of the parking lot shown on the base map:

   .. figure:: img/corner_selected_move.png
      :align: center

#. Click on the other vertices and continue to drag them to the edge of the
   parking lot until the polygon covers the entire parking lot.

   The correct border looks like this:

   .. figure:: img/areas_joined.png
      :align: center


|moderate| |FA| Tool: Simplify Feature
----------------------------------------------------------------------

Continuing on the same layer, we will test the |simplifyFeatures|
:sup:`Simplify Feature` tool:

#. Click on it to activate it.
#. Click on one of the areas which you joined using either the
   *Vertex Tool* or *Add Feature* tool.
   You will see this dialog:

   .. figure:: img/simplify_line_dialog.png
      :align: center

#. Modify the :guilabel:`Tolerance` and watch what happens:

   .. figure:: img/simplify_line_example.png
      :align: center

   This allows you to reduce the number of vertices.

#. Click :guilabel:`OK`

The advantage of this tool is that it provides you with a simple and
intuitive interface for generalization.
But notice that the tool ruins topology.
The simplified polygon no longer shares boundaries with its adjacent
polygons, as it should.
So this tool is better suited for stand-alone features.

Before you go on, set the polygon back to its original state by
undoing the last change.


|moderate| |TY| Tool: Add Ring
----------------------------------------------------------------------

The |addRing| :sup:`Add Ring` tool allows you to add an interior ring
to a polygon feature (cut a hole in the polygon), as long as the hole
is completely contained within the polygon (touching the boundary is
OK).
For the parking lot along Taylor Rd., you may notice the polygon covers
areas that has trees.  Use the tool to cut out these areas.

.. admonition:: Answer
   :class: dropdown

   .. figure:: img/ring_tool_result.png
      :align: center


|moderate| |TY| Tool: Add Part
----------------------------------------------------------------------

The |addPart| :sup:`Add Part` tool allows you to add a new part to a
feature, that is not directly connected to the main feature.
For example, if you have digitized the boundaries of mainland South
Africa, but you haven't yet added the Prince Edward Islands, you
would use this tool to create them.

#. Select the polygon to which you wish to add the part by using the
   |selectRectangle| :sup:`Select Features by area or single click`
   tool.
#. Use the :guilabel:`Add Part` tool to add an outlying area.
#. Delete the part you just created using the |deletePart|
   :sup:`Delete Part` tool.

   .. Note:: Click inside the part to delete it.

.. admonition:: Answer
   :class: dropdown

   #. First select the |largeLandUseArea|:

      .. figure:: img/park_selected.png
         :align: center

   #. Now add your new part:

      .. figure:: img/new_park_area_answer.png
         :align: center

   #. Undo your edit before continuing with the exercise for the next tool.


|moderate| |FA| Tool: Reshape Features
----------------------------------------------------------------------

The |reshape| :sup:`Reshape Features` tool is used to extend a polygon
feature or cut away a part of it (along the boundary).

Extending:

#. Select the polygon using the |selectRectangle|
   :sup:`Select Features by area or single click` tool.
#. Left-click inside the polygon to start drawing.
#. Draw a shape outside the polygon. The last vertex should be back
   inside the polygon.
#. Right-click to finish the shape:

   .. figure:: img/reshape_step_one.png
      :align: center

   This will give a result similar to:

   .. figure:: img/reshape_result.png
      :align: center

Cut away a part:

#. Select the polygon using the |selectRectangle|
   :sup:`Select Features by area or single click` tool.
#. Click outside the polygon.
#. Draw a shape inside the polygon. The last vertex must be back
   outside the polygon.
#. Right-click outside the polygon:

   .. figure:: img/reshape_inverse_example.png
     :align: center

   The result of the above:

   .. figure:: img/reshape_inverse_result.png
      :align: center


|moderate| |TY| Tool: Split Features
----------------------------------------------------------------------

The |splitFeatures| :sup:`Split Features` tool is similar to the
|reshape| :sup:`Reshape Features` tool, except that it does not delete
either of the two parts.
Instead, it keeps them both.

We will use the tool to split a corner from a polygon.

#. First, select the ``landuse`` layer and re-enable snapping for it.

#. Select the |splitFeatures| :sup:`Split Features` tool and click on
   a vertex to begin drawing a line.

#. Draw the bounding line.

#. Click a vertex on the "opposite" side of the polygon you wish to
   split and right-click to complete the line:

   .. figure:: img/split_feature_example.png
      :align: center

#. At this point, it may seem as if nothing has happened.
   But remember that the ``landuse`` layer is rendered without
   border lines, so the new division line will not be shown.
#. Use the |selectRectangle|
   :sup:`Select Features by area or single click` tool to select the
   part you just split out; the new feature will now be highlighted:

   .. figure:: img/new_corner_selected.png
      :align: center


.. _backlink-create-vector-topology-4:

|hard| |TY| Tool: Merge Features
----------------------------------------------------------------------

Now we will re-join the feature you just split out to the remaining
part of the polygon:

#. Experiment with  the |mergeFeatures|:sup:`Merge Selected Features`
   and |mergeFeatAttributes|
   :sup:`Merge Attributes of Selected Features` tools.
#. Note the differences.


.. admonition:: Answer
   :class: dropdown

   * Use the :guilabel:`Merge Selected Features` tool, making sure to first select
     both of the polygons you wish to merge.
   * Use the feature with the :guilabel:`OGC_FID` of ``1`` as the source of your
     attributes (click on its entry in the dialog, then click the :guilabel:`Take
     attributes from selected feature` button):

   If you're using a different dataset, it is highly likely that your original
   polygon's :guilabel:`OGC_FID` will not be ``1``. Just choose the feature
   which has an :guilabel:`OGC_FID`.

   .. figure:: img/merge_feature_dialog.png
      :align: center

   Using the :guilabel:`Merge Attributes of Selected Features` tool will keep the
   geometries distinct, but give them the same attributes.

#. Select the :guilabel:`landuse` layer and enter edit mode
   (|toggleEditing|)
#. Check (under :menuselection:`View --> Toolbars`) that the
   :guilabel:`Advanced Digitizing` toolbar is enabled.
#. Zoom to this area (enable layers and labels if necessary):

   .. figure:: img/zoom_to.png
      :align: center

#. Digitize this new (fictional) area:

   .. figure:: img/new_park_area.png
      :align: center

#. When prompted, give it an *OGC_FID* of :kbd:`999`, but feel free to
   leave the other values unchanged.

   If you are careful while digitizing, and allow the cursor to snap to
   the vertices of adjoining areas, you'll notice that there won't be
   any gaps between your new area and the existing adjacent areas.

#. Note the |undo| :sup:`undo`
   and |redo| :sup:`redo` tools in the
   :guilabel:`Advanced Digitizing` toolbar.

Now that you have completed editing the ``impervious_surfaces`` layer, be sure to
save all changes by clicking on the |toggleEditing| :sup:`Toggle Editing` button. 

|moderate| |TY| Tool: Reshape a Line Feature
----------------------------------------------------------------------

Now, reshape the road so that it aligns with the new base map. Be sure
to save all your edits!


|IC|
----------------------------------------------------------------------

Topology editing is a powerful tool that allows you to create and modify
objects quickly and easily, while ensuring that they remain topologically
correct.


|WN|
----------------------------------------------------------------------

Now you know how to digitize the shape of the objects easily, but
adding attributes is still a bit of a headache!
Next we will show you how to use forms, making attribute editing
simpler and more effective.


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
.. |addPart| image:: /static/common/mActionAddPart.png
   :width: 1.5em
.. |addRing| image:: /static/common/mActionAddRing.png
   :width: 2em
.. |capturePolygon| image:: /static/common/mActionCapturePolygon.png
   :width: 1.5em
.. |deletePart| image:: /static/common/mActionDeletePart.png
   :width: 2em
.. |deleteRing| image:: /static/common/mActionDeleteRing.png
   :width: 2em
.. |hard| image:: /static/common/hard.png
.. |largeLandUseArea| replace:: Bontebok National Park
.. |mergeFeatAttributes| image:: /static/common/mActionMergeFeatureAttributes.png
   :width: 1.5em
.. |mergeFeatures| image:: /static/common/mActionMergeFeatures.png
   :width: 1.5em
.. |moderate| image:: /static/common/moderate.png
.. |redo| image:: /static/common/mActionRedo.png
   :width: 1.5em
.. |reshape| image:: /static/common/mActionReshape.png
   :width: 1.5em
.. |selectRectangle| image:: /static/common/mActionSelectRectangle.png
   :width: 1.5em
.. |simplifyFeatures| image:: /static/common/mActionSimplify.png
   :width: 1.5em
.. |snapping| image:: /static/common/mIconSnapping.png
   :width: 1.5em
.. |splitFeatures| image:: /static/common/mActionSplitFeatures.png
   :width: 1.5em
.. |toggleEditing| image:: /static/common/mActionToggleEditing.png
   :width: 1.5em
.. |undo| image:: /static/common/mActionUndo.png
   :width: 1.5em
.. |vertexToolActiveLayer| image:: /static/common/mActionVertexToolActiveLayer.png
   :width: 1.5em
