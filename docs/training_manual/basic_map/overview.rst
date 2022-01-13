|LS| Welcome to GIS Applications: Lab 1 Part A
===============================================================================

You are now officially starting Lab 1! This lab will be broken down into several
sections and tackled over the first few weeks of the course.  Before 
starting, make sure you have QGIS version 3.22 installed and you have created a separate 
folder for Lab 1, as discussed in our first lecture. You should have the Lab_1 folder
downloaded from BlackBoard, as it contains all the data for this lab. For all of Lab 1, 
you will be working with several vector datasets associated with Niagara College Campus,
including:

#. wild species monitoring project locations
#. rivers
#. roads
#. lakes
#. buildings
#. parking lots
#. ELC polygons  

Lab 1 will be broken into three parts:

   Part A:  
   
#. Learn to load vector data, navigate QGIS and adjust layer symbology
#. Explore vector attribute tables, add labels and classify vector data
#. Create a map in Layout Manager with all necessary map elements and save as
   a Georeferenced PDF.

Deliverable 1: Create a thematic map of Niagara College Campus wild species monitoring 
project locations in relation to ELC classes.

   Part B:

#. Learn to edit vector data using topology
#. Learn to digitize features by interpreting aerial imagery
#. Produce a map based on your ENVR1108 Environmental Ecology term project.

Delieverable 2: Create a thematic map of habitat availability for an animal 
group found on campus.

   Part C:

#. Use the QGIS plugin QField or Avenza to perform ground truthing of your map 
   from Part B
#. Use a GPS unit to collect point locations
#. Record coordinates by hand and enter in a CSV document
#. Upload data from QField, GPS unit and CSV into QGIS
#. Create a GeoPackage 


The goal of Lab 1 Part A is to (1) introduce you to QGIS and (2) help you develop 
fundamental skills regarding thematic map creation and design. Part A will 
be broken down into 3 modules,and each consecutive week you will be given time 
to work on the module in class. This week, you will be working on Module 2 
(Module 1 was downloading the course software in Lecture 1). We will explore 
the QGIS user interface so that you are familiar with the menus, toolbars, 
map canvas and layers list that form the basic structure of the interface. 
When you are done this module, you will know how to:

#. Import vector data as a shapefile and from a GeoPackage
#. Navigate QGIS map canvas and use basic tools
#. Modify and select appropriate symbology for point, line and polygon spatial 
   entities

**The goal for this lesson:** To understand the basics of the QGIS user
interface.

|basic| |TY|: An Overview of the Interface
-------------------------------------------------------------------------------

.. _figure_gui_numbered:

.. figure:: img/gui_numbered.png
   :align: center

The elements identified in the figure above are:

#. Layers List / Browser Panel
#. Toolbars
#. Map canvas
#. Status bar
#. Side Toolbar
#. Locator bar

.. Don't reorder these list items! They refer to elements as numbered on an
   image.

|basic| The Layers List
...............................................................................

In the Layers list, you can see a list, at any time, of all the layers
available to you.

Expanding collapsed items (by clicking the arrow or plus symbol beside them)
will provide you with more information on the layer's current appearance.

Hovering over the layer will give you some basic information: layer name, type
of geometry, coordinate reference system and the complete path of the location
on your device.

Right-clicking on a layer will give you a menu with lots of extra options. You
will be using some of them before long, so take a look around!

.. note::  A vector layer is a dataset, usually of a specific kind of object,
   such as roads, trees, etc. A vector layer can consist of either points,
   lines or polygons.

.. _browser_panel_tm:

|basic| The Browser Panel
...............................................................................

The QGIS Browser is a panel in QGIS that lets you easily navigate in your
database. You can have access to common vector files (e.g. ESRI Shapefile
or MapInfo files), databases (e.g. PostGIS, Oracle, SpatiaLite, GeoPackage or
MSSQL Spatial), etc.

If you have saved a project, the Browser Panel will also give you quick access to
all the layers stored in the same path of the project file under in the
|qgsProjectFile| :guilabel:`Project Home` item.

Moreover, you can set one or more folder as **Favorites**: search under your path
and once you have found the folder, right click on it and click on ``Add as a
Favorite``. You should then be able to see your folder in the |favourites|
:guilabel:`Favorites` item.

Now try to find your /Lab_1 folder!

.. tip:: It can happen that the folders added to Favorite item have a really
  long name: don't worry right-click on the path and choose ``Rename Favorite...``
  to set another name.

|basic| Toolbars
...............................................................................

Your most often used sets of tools can be turned into toolbars for basic access.
For example, the File toolbar allows you to save, load, print, and start a new
project. You can easily customize the interface to see only the tools you use
most often, adding or removing toolbars as necessary via the
:menuselection:`View --> Toolbars` menu.

Even if they are not visible in a toolbar, all of your tools will remain
accessible via the menus. For example, if you remove the :guilabel:`File`
toolbar (which contains the :guilabel:`Save` button), you can still save your
map by clicking on the :guilabel:`Project` menu and then clicking on
:guilabel:`Save`.

Now try turning on your 'Labels' toolbar!

|basic| The Map Canvas
...............................................................................

This is where the map itself is displayed and where layers are loaded. In the map
canvas you can interact with the visible layers: zoom in/out, move the map,
select features and many other operations that we will deeply see in the next
sections.

|basic| The Status Bar
...............................................................................

Shows you information about the current map. Also allows you to adjust the map
scale, the map rotation and see the mouse cursor's coordinates on the map.

|basic| The Side Toolbar
...............................................................................

By default the Side toolbar contains the buttons to load the layer and all the
buttons to create a new layer. But remember that you can move all the toolbars
wherever it is more comfortable for you.

|basic| The Locator Bar
...............................................................................

Within this bar you can access to almost all the objects of QGIS: layers, layer
features, algorithms, spatial bookmarks, etc. Check all the different options in
the :ref:`locator_options` section of the QGIS User Manual.

.. tip:: With the shortcut :kbd:`Ctrl+K` you can easily access the bar.


|basic| |TY| 1
-------------------------------------------------------------------------------

Try to identify the four elements listed above on your own screen, without
referring to the diagram above. See if you can identify their names and
functions. You will become more familiar with these elements as you use them in
the coming days.

.. admonition:: Answer
   :class: dropdown

   Refer back to the image showing the interface layout and check that you
   remember the names and functions of the screen elements.


|basic| |TY| 2
-------------------------------------------------------------------------------

Try to find each of these tools on your screen. What is their purpose?

1. |fileSaveAs|
2. |zoomToLayer|
3. |invertSelection|
4. |checkbox|:guilabel:`Render`
5. |measure|

.. note:: If any of these tools are not visible on the screen, try enabling
   some toolbars that are currently hidden. Also keep in mind that if there
   isn't enough space on the screen, a toolbar may be shortened by hiding some
   of its tools. You can see the hidden tools by clicking on the double right
   arrow button in any such collapsed toolbar. You can see a tooltip with the
   name of any tool by holding your mouse over the tool for a while.

.. admonition:: Answer
   :class: dropdown

   #. :guilabel:`Save as`
   #. :guilabel:`Zoom to layer(s)`
   #. :guilabel:`Invert selection`
   #. :guilabel:`Rendering on/off`
   #. :guilabel:`Measure line`


|WN|
-------------------------------------------------------------------------------

Now that you are familiar with the basics of the QGIS interface, in the next 
lesson we will see how to load some common data types.


.. Substitutions definitions - AVOID EDITING PAST THIS LINE
   This will be automatically updated by the find_set_subst.py script.
   If you need to create a new substitution manually,
   please add it also to the substitutions.txt file in the
   source folder.

.. |LS| replace:: Lesson:
.. |TY| replace:: Try Yourself
.. |WN| replace:: What's Next?
.. |basic| image:: /static/common/basic.png
.. |checkbox| image:: /static/common/checkbox.png
   :width: 1.3em
.. |favourites| image:: /static/common/mIconFavourites.png
   :width: 1.5em
.. |fileSaveAs| image:: /static/common/mActionFileSaveAs.png
   :width: 1.5em
.. |invertSelection| image:: /static/common/mActionInvertSelection.png
   :width: 1.5em
.. |measure| image:: /static/common/mActionMeasure.png
   :width: 1.5em
.. |qgsProjectFile| image:: /static/common/mIconQgsProjectFile.png
   :width: 1.5em
.. |zoomToLayer| image:: /static/common/mActionZoomToLayer.png
   :width: 1.5em
