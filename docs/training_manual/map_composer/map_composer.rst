|LS| Using Print Layout
======================================================================

Now that you've got a map, you need to be able to print it or to
export it to a document.
The reason is, a GIS map file is not an image. Rather, it saves the
state of the GIS program, with references to all the layers, their
labels,colors, etc.
So for someone who doesn't have the data or the same GIS program
(such as QGIS), the map file will be useless.
Luckily, QGIS can export its map file to a format that anyone's
computer can read, as well as printing out the map if you have a
printer connected.
Both exporting and printing is handled via the *Print Layout*.

**The goal for this lesson:** To use the QGIS *Print Layout* to create
a map with all the required map items, including a map inset.

|basic| |FA| Preparing Data to Create a Inset Map
----------------------------------------------------------------------

Inset maps are useful to provide spatial orientation for the map user. For
Lab 1, Part A, we will add an inset to our map. Before we can do that,
we need to organize our data in the 'Map Canvas'.  To start, we are going
to create two data groups.

#. Right click on the 'Layers' panel and then navigate to 'Add Group'.

   .. figure:: img/Layout_addgroup.png
      :align: center

#. Click 'Add Group', and a new item called 'group1' will appear in your 
   'Layers' panel.
#. Now you want to add your map layers to your new group. To do this, 
   click and drag your layers onto of 'group1'.  Your new group should
   look like this:

   .. figure:: img/Layout_group1.png
      :align: center

#. Now create a second group, 'group2', which will be used for our map inset.

Next we are going to learn to install a Plugin so that we can add 
a basemap to our map inset. 

#. Navigate to the top of the QGIS session and click 'Plugins' --> 'Manage
   and Install Plugins'.

   .. figure:: img/Layout_plugins.png
      :align: center

#. A dialogue box will appear; enter the information as shown below and click 
   'Install Plugin'.

   .. figure:: img/Layout_quickmap.png
      :align: center

Look for the QuickMap Services tool bar amongst your other toolbars near the
top of your QGIS session.

   .. figure:: img/Layout_quickmapicons.png
      :align: center

#. Now click on the QuickMap Services icon, and navigate to the 'ESRI Gray (light)'
   map option as shown below. This will add the basemap to your canvas.

   .. figure:: img/Layout_graylight.png
      :align: center

#. For now, we do not want the basemap visible, so toggle it off, and drag it onto
   the 'group2' layer.  Your 'Layers' panel should look like this:

   .. figure:: img/Layout_group12.png
      :align: center

One last thing, before we start to learn about the 'Layout Manager', we need to add
the 'NCCampus_Boundary' layer.  This will be in your /Lab_1/ folder.  Order it so it
is just below the 'wild_species' layer.


|basic| |FA| The Layout Manager
----------------------------------------------------------------------

QGIS allows you to create multiple maps using the same map file.
For this reason, it has a tool called the *Layout Manager*.

#. Click on the :menuselection:`Project --> Layout Manager...` menu
   entry to open this tool.
   You'll see a blank :guilabel:`Layout manager` dialog appear.

   .. figure:: img/layout_manager_dialog.png
      :align: center

#. Under :guilabel:`New from Template`, select
   :guilabel:`Empty layout` and press the :guilabel:`Create...` button.
#. Give the new layout the name of 'Lab_1' and
   click :guilabel:`OK`.
#. You will now see the *Print Layout* window:

   .. figure:: img/Layout_blank.png
      :align: center
   
You could also create this new layout via the
:menuselection:`Project --> New Print Layout...` menu.

Whichever route you take, the new print layout is now accessible from
the :menuselection:`Project --> Layouts -->` menu, as in the image below 
(please ignore my other templates).

.. figure:: img/Layout_layouts.png
   :align: center


|basic| |FA| Basic Map Composition
----------------------------------------------------------------------

The goal of our map is to show wild species monitoring locations in relation
to ELC classes.  Below is my interpretation of the assignment. Feel free to use
a similar layout, or shuffle it around to make it your own. However, be sure to
include all the same map elements that my map has.  The for the remainder of this
lesson will walk you through how to add each element to create your final product
for Lab 1 Part A.


.. figure:: img/Layout_final.png
      :align: center


Previously, we had performed an ordinal classification of ELC 
polygon area.  Prior to that,we performed a categorical classification of 
ELC_campus by CSCODE1, and had saved the style.  The style can be reloaded 
by going to Style at the bottom of the Symbology window. Use this classification
for the map layout.

#. Right-click on the sheet in the central part of the layout window
   and choose :guilabel:`Page properties...` in the context menu.
#. Check that the values in the :guilabel:`Item Properties` tab are
   set to the following:

   * :guilabel:`Size`: ``A4``
   * :guilabel:`Orientation`: ``Landscape``

   Now you've got the page layout the way you wanted it, but this
   page is still blank.
   It clearly lacks a map. Let's fix that!

#. Click on the |addMap| :sup:`Add Map` button.

   With this tool activated, you will be able to place a map on the
   page.

#. Click and drag a box on the blank page:

   .. figure:: img/Layout_addmap.png
      :align: center

   The map will appear on the page.

#. Move the map by clicking and dragging it around:

#. Resize it by clicking and dragging the boxes on the edges:

   .. note::  As we go along, your map may look a lot different, of course!
      This depends on how your own project is set up.
      But not to worry! These instructions are general, so they will
      work the same regardless of what the map itself looks like.

#. Be sure to leave margins along the edges, and a space for the title.

#. Zoom in and out on the page (but not the map!) by using these
   buttons:

   |zoomFullExtent| |zoomIn| |zoomOut|

#. Zoom and pan the map in the main QGIS window.
   You can also pan the map using the |moveItemContent|
   :sup:`Move item content` tool.

   The map view updates as you zoom in or zoom out.
#. If, for any reason, the map view does not refresh correctly,
   you can force the map to refresh by clicking the
   |refresh| :sup:`Refresh view` button.

   Remember that the size and position you've given the map doesn't
   need to be final.
   You can always come back and change it later if you're not
   satisfied.
   For now, you need to ensure that you've saved your work on this
   map.
   Because a *Print Layout* in QGIS is part of the main map file,
   you must save your project.

#. Go to the :menuselection:`Layout -->` |fileSave|
   :menuselection:`Save Project`.
   This is a convenient shortcut to the one in the main dialog.

|basic| |FA| Adding a Title
----------------------------------------------------------------------

Now your map is looking good on the page, but your readers/users are
not being told what's going on yet.
They need some context, which is what you'll provide for them by
adding map elements.
First, let us add a title.

#. Click on the |label| :sup:`Add Label` button
#. Click on the page, above the map, accept the suggested values in
   the :guilabel:`New Item Properties` dialog, and a label will
   appear at the top of the map.
#. Resize it and place it in the top center of the page.
   It can be resized and moved in the same way that you resized and
   moved the map.

   As you move the title, you'll notice that guidelines appear to
   help you position the title in the center of the page.

   However, there is also a tool in the Actions Toolbar to help
   position the title relative to the map (not the page):

   |alignLeft|

#. Click the map to select it
#. Hold in :kbd:`Shift` on your keyboard and click on the label so
   that both the map and the label are selected.
#. Look for the |alignLeft| :sup:`Align selected items left` button
   and click on the dropdown arrow next to it to reveal the
   positioning options and click either |alignHCenter| or |alignLeft|.
   :guilabel:`Align center`:

   .. figure:: img/align_center_dropdown.png
      :align: center

   Now the label frame is centered on the map, but not the contents.
   To center the contents of the label:

   #. Select the label by clicking on it.
   #. Click on the :guilabel:`Item Properties` tab in the side panel
      of the layout window.
   #. Change the text of the label to something that conveys the theme of our
      map. I chose "Niagara College Campus Wild Species Monitoring Project Locations":
   #. Use this interface to set the font and alignment options
      under the :guilabel:`Appearance` section:

      .. figure:: img/Layout_titlesettings.png
         :align: center

      #. Choose a large but sensible font (the example will use the
         default font with a size of ``20``)
      #. Set the :guilabel:`Horizontal Alignment` to :guilabel:`Center`.

      You can also change the font color, but it's probably best to
      keep it black as per the default.

   #. The default setting is not to add a frame to the title's text box.
      However, if you wish to add a frame, you can do so:

      #. In the :guilabel:`Item Properties` tab, scroll down until you
         see the :guilabel:`Frame` option.
      #. Click the :guilabel:`Frame` checkbox to enable the frame.
         You can also change the frame's color and width.

   To make sure that you don't accidentally move these elements
   around now that you've aligned them, you can lock items into place:

   #. Select both the label and the map items
   #. Click the |lockItems| :sup:`Lock Selected Items` button in
      the *Actions* Toolbar.

      .. note:: Click the |unlockAll| :sup:`Unlock All Items` button
       in the *Actions* Toolbar to be able to edit the items again.
       Use this tool as you add new elements to your map.


|basic| |FA| Adding a Legend
----------------------------------------------------------------------

The map reader also needs to be able to see what various things on
the map actually mean. Let's add a new legend!

#. Click on the |addLegend| :sup:`Add Legend` button
#. Click on the page to place the legend, accept the suggested values
   in the :guilabel:`New Item Properties` dialog,
#. A legend is added to the layout page, showing layers symbology
   as set in the main dialog.
#. As usual, you can click and move the item to where you want it:
      

|moderate| |FA| Customizing Legend Items
----------------------------------------------------------------------

Not everything on the legend is necessary, so let's remove some
unwanted items.

#. In the :guilabel:`Item Properties` tab, you'll find the
   :guilabel:`Legend items` group.
#. Uncheck the |unchecked| :guilabel:`Auto update` box, allowing you
   to directly modify the legend items
#. Select the entry with 'group2'
#. Delete it from the legend by clicking the |signMinus| button

You can also rename items.

#. Select a layer from the same list.
#. Click the |symbologyEdit| :sup:`Edit selected item properties` button.
#. Rename the layers and reorder them so they match the image below.


.. figure:: img/Layout_legenditemorder.png
   :align: center
   

As the legend will likely be widened by the new layer names, you may
wish to move and resize the legend and or map.

|basic| |FA| Adding a Scale Bar
----------------------------------------------------------------------

The map reader also needs to be able to understand the relationship of the 
distance on the map to the actual distance on the ground.  By adding a
scale bar, the reader is able to visually interpet the actual distance on
the ground, which will help them better understand the message the map is trying
to convey.

Let's add a new scale bar.

#. Click on the|addScalebar| :sup:`Add Scale Bar` button
#. Click on the page and drag a box to place the Scale Bar
#. Ensure the scale bar units are appropriate for your map (e.g., meters)
#. The scale bar can be further customized, so take a moment and look at the
   different item properties and adjust them until you find a format you like.
   The image below shows the settings I used, but I encourage you to make your
   own design choices.

   .. figure:: img/Layout_scalesettings.png
      :align: center
      

#. To adjust the font, navigate to the 'Display' section, shown below.
   
   .. figure:: img/Layout_scaledisplay.png
      :align: center
      

#. Click on 'Font' and then adjust the font size.

   .. figure:: img/Layout_scalefont.png
      :align: center
      


|basic| |FA| Adding a North Arrow
----------------------------------------------------------------------

A North Arrow is also required on your map to provide directional Orientation
for the user.

#. Click on the |northArrow| :sup:`Add North Arrow` button
#. Click on the page and drag a box to place the North Arrow
#. Like the other map elements, the North Arrow can be customized, so take a
   moment and play with different options until you are pleased with your North
   Arrow appearance. Below are the settings I chose to use:

   .. figure:: img/Layout_Narrow.png
      :align: center
      

|basic| |FA| Adding a Text Box
----------------------------------------------------------------------

Each map also needs information regarding Map Author, Map Projection and Data
Source.  For this map, 
Map Author: *Your Name*, Environmental Technician Candidate, Niagara College
Projection: UTM NAD83 Zone 17N
Data Source: Niagara Peninsula Conservation Authority Open Data Portal, 
St. Catharines Open data Portal, Ontario GeoHub, M. McNight (2021) 

#. Click on the |Label| :sup:`Add Label` button, as you did for your title
#. Click on the page and drag a box to place the text box
#. In the Item Properties tab, you can edit the text to include the information
   written above.  Feel free to change text size; typically this information is
   meant to be discrete, but easily read. The image below shows the settings I
   chose:

   .. figure:: img/Layout_mapinfo.png
      :align: center
      

The font can be modified by clicking on 'Font' in the 'Appearance' section.


|basic| |FA| Adding an Map Inset
----------------------------------------------------------------------

To add an inset map, navigate back to your 'Map Canvas' window. Toggle off your
'group1' layer, and toggle on your 'group 2' layer, which will activate your basemap.  
Now zoom out so you can see most of Ontario.

#. Now add the inset map the same way you added your initial map.
#. Place it in a corner, and set the settings so they are the same as/similar 
   to the image below:

   .. figure:: img/Layout_map2setting.png
      :align: center
      

Once you are happy with your map inset position and scale, add a rectangle to show
roughly where Niagara College campus is located in the map inset.

#. Click on the |addBasicShape| :sup:`Add Shape` button
#. Click on the basemap and drag a box around the approximate area of Niagara College 
   campus.

.. figure:: img/Layout_mapinset.png
      :align: center



|basic| |FA| Adding a Polyline Feature
----------------------------------------------------------------------

To create bracket to denote that the single wood duck label is associated with
multiple points, we can use the Add Node tool. 

#. Click on the |addNode| :sup:`Add Node tool` button
#. Select 'Add Polyline'.
#. Now, using the same approach used when digitizing/editing your vector data,
   create a polyline feature that resembles the image below.

   .. figure:: img/Layout_polylines.png
      :align: center


The feature is actually in 2 parts. The symbology can be edited by clicking 
on the dropdown arrow of the 'Main Properties' and then clicking on 
'Configure Symbol...'. You can design it to look however you like,
but feel free to use the settings I used, shown below.  

 .. figure:: img/Layout_polylinessettings.png
      :align: center
      :width: 100%


|basic| |FA| Adding a Neatline
----------------------------------------------------------------------

Optionally, you can add a Neatline, or border, around your map. 

#. Click on the |addBasicShape| :sup:`Add Shape` button
#. Click on the page and drag a box around all your map elements.
#. However, you may notice that this box covers all your map elements. To fix
   this go to the 'Items Browser' on the right side of the window. Items can 
   be reorganized by dragging them up or down. Reorder all of your layers so they 
   look similar to the image below.


   .. figure:: img/Layout_itemorder.png
      :align: center

   

|basic| |FA| Exporting Your Map
----------------------------------------------------------------------

.. note::  Did you remember to save your work often?

Finally the map is ready for export! Take a good look at your map and ask yourself,
Is the initial question asked being answered? The initial question was:

Where are the wild species monitoring projects located on campus in relation to
different ecosystems?

Make sure your map is tidy, organized and logically presented so the user immediately
understands what they are looking at. If you feel all these factors are met, it is
time to export the map.

You'll see the export buttons near the top left corner of the layout window:

* |filePrint| :sup:`Print Layout`: interfaces with a printer.
  Since the printer options will differ depending on the model of
  printer that you're working with, it's probably better to consult the
  printer manual or a general guide to printing for more information on
  this topic.

  The other buttons allow you to export the map page to a file.
* |saveMapAsImage| :sup:`Export as Image`: gives you a selection
  of various common image formats to choose from.
  This is probably the simplest option, but the image it creates is
  "dead" and difficult to edit.
* |saveAsSVG| :sup:`Export as SVG`: If you're sending the map to a
  cartographer (who may want to edit the map for publication),
  it's best to export as an SVG. SVG stands for "Scalable Vector Graphic",
  and can be imported to programs like `Inkscape <https://inkscape.org/>`_
  or other vector image editing software.
* |saveAsPDF| :sup:`Export as PDF`: If you need to send the map to a client,
  it's most common to use a PDF, because it's easier to set up printing
  options for a PDF.
  Some cartographers may prefer PDF as well, if they have a program
  that allows them to import and edit this format.

For our purposes, we're going to use PDF.

#. Click the |saveAsPDF| :sup:`Export as PDF` button
#. Choose a save location and a file name as usual.
#. Check the box next to Create Geospatial PDF. In the next lab we will be
   using this file to perform ground truthing.
   The following dialog will show up.

   .. figure:: img/Layout_pdfexport.png
      :align: center
   
#. You can safely use the default values now and click
   :guilabel:`Save`.
   
   QGIS will proceed to the map export and push a message
   on top of the print layout dialog as soon as it finishes.
#. Click the hyperlink in the message to open the folder in which
   the PDF has been saved in your system's file manager
#. Open it and see how your layout looks.

   Everything is OK?

   Congratulations on your first completed QGIS map project!

#. Anything unsatisfying? Go back to the QGIS window, do the
   appropriate modifications and export again.
#. Remember to save your project file.


|IC|
----------------------------------------------------------------------
Now you know how to create a basic static map layout. We can go a step
further and create a map layout that adapts dynamically, with more
layout items.


.. Substitutions definitions - AVOID EDITING PAST THIS LINE
   This will be automatically updated by the find_set_subst.py script.
   If you need to create a new substitution manually,
   please add it also to the substitutions.txt file in the
   source folder.

.. |FA| replace:: Follow Along:
.. |IC| replace:: In Conclusion
.. |LS| replace:: Lesson:
.. |addLegend| image:: /static/common/mActionAddLegend.png
   :width: 1.5em
.. |addMap| image:: /static/common/mActionAddMap.png
   :width: 1.5em
.. |alignHCenter| image:: /static/common/mActionAlignHCenter.png
   :width: 1.5em
.. |alignLeft| image:: /static/common/mActionAlignLeft.png
   :width: 1.5em
.. |basic| image:: /static/common/basic.png
.. |filePrint| image:: /static/common/mActionFilePrint.png
   :width: 1.5em
.. |fileSave| image:: /static/common/mActionFileSave.png
   :width: 1.5em
.. |label| image:: /static/common/mActionLabel.png
   :width: 1.5em
.. |lockItems| image:: /static/common/mActionLockItems.png
   :width: 1.5em
.. |majorUrbanName| replace:: Swellendam
.. |moderate| image:: /static/common/moderate.png
.. |moveItemContent| image:: /static/common/mActionMoveItemContent.png
   :width: 1.5em
.. |refresh| image:: /static/common/mActionRefresh.png
   :width: 1.5em
.. |saveAsPDF| image:: /static/common/mActionSaveAsPDF.png
   :width: 1.5em
.. |saveAsSVG| image:: /static/common/mActionSaveAsSVG.png
   :width: 1.5em
.. |saveMapAsImage| image:: /static/common/mActionSaveMapAsImage.png
   :width: 1.5em
.. |signMinus| image:: /static/common/symbologyRemove.png
   :width: 1.5em
.. |symbologyEdit| image:: /static/common/symbologyEdit.png
   :width: 1.5em
.. |unchecked| image:: /static/common/checkbox_unchecked.png
   :width: 1.3em
.. |unlockAll| image:: /static/common/mActionUnlockAll.png
   :width: 1.5em
.. |zoomFullExtent| image:: /static/common/mActionZoomFullExtent.png
   :width: 1.5em
.. |zoomIn| image:: /static/common/mActionZoomIn.png
   :width: 1.5em
.. |zoomOut| image:: /static/common/mActionZoomOut.png
   :width: 1.5em
