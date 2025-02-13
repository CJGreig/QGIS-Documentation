|LS| Symbology
===============================================================================

The symbology of a layer is its visual appearance on the map.
The basic strength of GIS over other ways of representing data with spatial
aspects is that with GIS, you have a dynamic visual representation of the data
you're working with.

Therefore, the visual appearance of the map (which depends on the symbology of
the individual layers) is very important. The end user of the maps you produce
will need to be able to easily see what the map represents. Equally as
important, you need to be able to explore the data as you're working with it,
and good symbology helps a lot.

In other words, having proper symbology is not a luxury or just nice to have.
In fact, it's essential for you to use a GIS properly and produce maps and
information that people will be able to use.

**The goal for this lesson:** To be able to create any symbology you want for
any vector layer.

|basic| |FA| Changing Colors
-------------------------------------------------------------------------------

To change a layer's symbology, open its :guilabel:`Layer Properties`. Let's
begin by changing the color of the :guilabel:`impervious_surfaces` layer.

#. Right-click on the :guilabel:`impervious_surfaces` layer in the layers list.
#. Select the menu item :guilabel:`Properties...` in the menu that appears.

   .. note:: By default, you can also access a layer's properties by
     double-clicking on the layer in the Layers list.

   .. tip:: The |symbology| button at the top of the :guilabel:`Layers`
     panel will open the :guilabel:`Layer Styling` panel. You can use this
     panel to change some properties of the layer: by default, changes will be
     applied immediately!

#. In the :guilabel:`Layer Properties` window, select the |symbology|
   :guilabel:`Symbology` tab:

   .. figure:: img/ELC_campus_symbology.png
      :align: center

#. Click the color select button next to the :guilabel:`Color` label.
   A standard color dialog will appear.
#. Choose a gray color and click :guilabel:`OK`.
#. Click :guilabel:`OK` again in the :guilabel:`Layer Properties` window, and
   you will see the color change being applied to the layer.

|basic| |TY|
-------------------------------------------------------------------------------

Change the color of the :guilabel:`Lakes` layer to light blue. Try to use the
:guilabel:`Layer Styling` panel instead of the :guilabel:`Layer Properties` menu.

.. admonition:: Solution
   :class: dropdown

   * Verify that the colors are changing as you expect them to change.
   * It is enough to select the :guilabel:`Lakes` layer in the legend and then click
     on the |symbology| :sup:`Open the Layer Styling panel` button. Change the color
     to one that fits the Lakes layer.

   .. figure:: img/Basic_map_lakesstyling.png
      :align: center

   If you want to work on only one layer at a time and don't want the
   other layers to distract you, you can hide a layer by clicking in the checkbox
   next to its name in the layers list. If the box is blank, then the layer
   is hidden.


|basic| |FA| Changing Symbol Structure
-------------------------------------------------------------------------------

This is good stuff so far, but there's more to a layer's symbology than just
its color. Next we want to eliminate the lines between the different impervious surfaces so as to make the map less visually cluttered.

#. Open the :guilabel:`Layer Properties` window for the :guilabel:`impervious_surfaces`
   layer.
   
   Under the |symbology| :guilabel:`Symbology` tab, you will see the same kind
   of dialog as before. This time, however, you're doing more than just quickly
   changing the color.
#. In the symbol layers tree, expand the :guilabel:`Fill` dropdown
   and select the :guilabel:`Simple fill` option.
#. Click on the :guilabel:`Stroke style` dropdown. At the moment, it should be
   showing a short line and the words :guilabel:`Solid Line`.
#. Change this to :guilabel:`No Pen`.

   .. figure:: img/simple_fill_selected.png
      :align: center

#. Click :guilabel:`OK`.

Now the :guilabel:`impervious_surfaces` layer won't have any lines between areas.


|basic| |TY|
-------------------------------------------------------------------------------

* Change the :guilabel:`Lakes` layer's symbology again so that it has a
  darker blue outline.
* Change the :guilabel:`rivers` layer's symbology to a sensible representation
  of waterways.

Remember: you can use the |symbology| :sup:`Open the Layer Styling panel`
button and see all the changes instantly. That panel also allows you to undo
individual changes while symbolizing a layer.

.. admonition:: Answer
   :class: dropdown

   Your map should now look like this:

   .. figure:: img/Basic_map_lakesstylingdark.png
      :align: center

   * Use the method above to change the colors and styles for all the remaining
     layers.
   * Try using natural colors for the objects. For example, a road should not be
     red or blue, but can be gray or black.
   * Also feel free to experiment with different :guilabel:`Fill style` and
     :guilabel:`Stroke style` settings for the other polygons.

|moderate| |FA| Adding Symbol Layers
-------------------------------------------------------------------------------

Now that you know how to change simple symbology for layers, the next step is
to create more complex symbology. QGIS allows you to do this using symbol
layers.  This exercise is meant to teach you how to customize symbology, but DOES
NOT need to be used when creating your final map product for Lab 1.

#. Go back to the :guilabel:`impervious_surfaces` layer's symbol properties panel (by clicking
   :guilabel:`Simple fill` in the symbol layers tree).

   In this example, the current symbol has no outline (i.e., it uses the
   :guilabel:`No Pen` border style).

   .. figure:: img/simple_fill_selected.png
      :align: center

#. Select the :guilabel:`Fill` level in the tree and click
   the |signPlus| :sup:`Add symbol layer` button.
   The dialog will change to look something like this, with a new symbol layer
   added:

   .. figure:: img/new_symbol_layer.png
      :align: center

   It may appear somewhat different in color, for example, but you're going
   to change that anyway.

Now there's a second symbol layer. Being a solid color, it will of course
completely hide the previous kind of symbol. Plus, it has a :guilabel:`Solid
Line` border style, which we don't want. Clearly this symbol has to be changed.

.. note::  It's important not to get confused between a map layer and a symbol
   layer. A map layer is a vector (or raster) that has been loaded into the
   map. A symbol layer is part of the symbol used to represent a map layer.
   This course will usually refer to a map layer as just a layer, but a symbol
   layer will always be called a symbol layer, to prevent confusion.

With the new :guilabel:`Simple Fill` symbol layer selected:

#. Set the border style to :guilabel:`No Pen`, as before.
#. Change the fill style to something other than :guilabel:`Solid` or
   :guilabel:`No brush`. For example:

   .. figure:: img/new_fill_settings.png
      :align: center

#. Click :guilabel:`OK`.

Now you can see your results and tweak them as needed.
You can even add multiple extra symbol layers and create a kind of texture for
your layer that way.

.. figure:: img/multiple_symbol_layers.png
   :align: center

It's fun! But it probably has too many colors to use in a real map...


|moderate| |TY|
-------------------------------------------------------------------------------

Remembering to zoom in if necessary, create a simple, but not distracting
texture for the :guilabel:`buildings` layer using the methods above.  Remember,
this is for practice, so if you do not want to keep this symbology, you do not have to.

   Customize your :guilabel:`buildings` layer as you like, but remember that it
   has to be easy to tell different layers apart on the map.


|moderate| |FA| Ordering Symbol Levels
-------------------------------------------------------------------------------

When symbol layers are rendered, they are also rendered in a sequence, similar
to the way the different map layers are rendered. This means that in some cases,
having many symbol layers in one symbol can cause unexpected results.

#. Give the :guilabel:`roads` layer an extra symbol layer (using the method
   for adding symbol layers demonstrated above).
#. Give the base line a :guilabel:`Stroke width` of ``1.5`` and a black color.
#. Give the new, uppermost layer a thickness of ``0.8`` and a white color.

You'll notice that this happens:

.. figure:: img/Basic_map_roadoverlap.png
   :align: center

Well, roads have now a *street* like symbology, but you see that lines are
overlapping each others at each cross. That's not what we want at all!

To prevent this from happening, you can sort the symbol levels and thereby
control the order in which the different symbol layers are rendered.

To change the order of the symbol layers:

#. Select the topmost :guilabel:`Line` layer in the symbol layers tree.
#. Click :menuselection:`Advanced --> Symbol levels...` in the
   bottom right-hand corner of the window.

   .. figure:: img/symbol_levels_main_dialog.png
      :align: center

   This will open a dialog like this:

   .. figure:: img/symbol_levels_dialog.png
      :align: center

#. Check |checkbox| :guilabel:`Enable symbol levels`. You can then set the
   layer order of each symbol by entering the corresponding level number.
   0 is the bottom layer.

   In our case, we just want to activate the option, like this:

   .. figure:: img/correct_symbol_layers.png
      :align: center

   This will render the white line above the thick black line borders:

#. Click :guilabel:`OK` twice to return to the map.

   The map will now look like this:

   .. figure:: img/Basic_map_roadnooverlap.png
      :align: center

When you're done, remember to save the symbol itself so as not to lose your
work if you change the symbol again in the future. You can save your current
symbol style by clicking the :guilabel:`Save Style...` button at the bottom
of the :guilabel:`Layer Properties` dialog.
We will be using the :guilabel:`QGIS QML Style File` format.

.. TODO: imho there's a mix of saving symbols and saving styles here that could
 be misleading. Saving style should deserve its own section.

Save your style in the :file:`solution/styles/better_roads.qml` folder. You can load a
previously saved style at any time by clicking the :guilabel:`Load Style...`
button. Before you change a style, keep in mind that any unsaved style you are
replacing will be lost.

|moderate| |FA| Symbol layer types (Optional)
-------------------------------------------------------------------------------

In addition to setting fill colors and using predefined patterns, you can use
different symbol layer types entirely. The only type we've been using up to now
was the :guilabel:`Simple Fill` type. The more advanced symbol layer types allow
you to customize your symbols even further.

Each type of vector (point, line and polygon) has its own set of symbol layer
types. First we will look at the types available for points.

Point Symbol Layer Types
...............................................................................

#. Uncheck all the layers except for :guilabel:`wild_species`.
#. Change the symbol properties for the :guilabel:`wild_species` layer:

   .. figure:: img/places_layer_properties.png
      :align: center

#. You can access the various symbol layer types by selecting the
   :guilabel:`Simple marker` layer in the symbol layers tree, then
   click the :guilabel:`Symbol layer type` dropdown:

   .. figure:: img/marker_type_dropdown.png
      :align: center

#. Investigate the various options available to you, and choose a symbol with
   styling you think is appropriate.
#. If in doubt, use a round :guilabel:`Simple marker` with a white border and
   pale green fill, with a :guilabel:`Size` of ``3.00`` and a
   :guilabel:`Stroke width` of ``0.5``.


Line Symbol Layer Types
...............................................................................

To see the various options available for line data:

#. Change the :guilabel:`Symbol layer type` for the :guilabel:`roads` layer's
   topmost symbol layer to :guilabel:`Marker line`:

   .. figure:: img/change_to_marker_line.png
      :align: center

#. Select the :guilabel:`Simple marker` layer in the symbol layers
   tree. Change the symbol properties to match this dialog:

   .. figure:: img/simple_marker_line_properties.png
      :align: center

#. Select the :guilabel:`Marker line` layer and change the interval to ``1.00``:

   .. figure:: img/marker_line_interval.png
      :align: center

#. Ensure that the symbol levels are correct (via the
   :menuselection:`Advanced --> Symbol levels` dialog we used earlier) before
   applying the style.

Once you have applied the style, take a look at its results on the map. As you
can see, these symbols change direction along with the road but don't always
bend along with it. This is useful for some purposes, but not for others. If
you prefer, you can change the symbol layer in question back to the way it was
before.

Polygon Symbol Layer Types
...............................................................................

To see the various options available for polygon data:

#. Change the :guilabel:`Symbol layer type` for the :guilabel:`Lakes` layer, as
   before for the other layers.
#. Investigate what the different options on the list can do.
#. Choose one of them that you find suitable.
#. If in doubt, use the :guilabel:`Point pattern fill` with the following
   options:

   .. figure:: img/pattern_fill_size.png
      :align: center

   .. figure:: img/pattern_fill_distances.png
      :align: center

#. Add a new symbol layer with a normal :guilabel:`Simple fill`.
#. Make it the same light blue with a darker blue border.
#. Move it underneath the point pattern symbol layer with the :guilabel:`Move
   down` button:

   .. figure:: img/simple_fill_move_down.png
      :align: center

As a result, you have a textured symbol for the Lakes layer, with the added
benefit that you can change the size, shape and distance of the individual dots
that make up the texture.


.. _backlink-symbology-marker-line:

|IC|
-------------------------------------------------------------------------------

Changing the symbology for the different layers has transformed a collection of
vector files into a legible map. Not only can you see what's happening, it's
even nice to look at!

|FR|
-------------------------------------------------------------------------------

`Examples of Beautiful Maps
<https://gis.stackexchange.com/questions/3083/seeking-examples-of-beautiful-maps>`_

|WN|
-------------------------------------------------------------------------------

Changing symbols for whole layers is useful, but the information contained
within each layer is not yet available to someone reading these maps. What are
the streets called? Which administrative regions do certain areas belong to?
What are the relative surface areas of the farms? All of this information is
still hidden. The next lesson will explain how to represent this data on your
map.

.. note::  Did you remember to save your map recently?


.. Substitutions definitions - AVOID EDITING PAST THIS LINE
   This will be automatically updated by the find_set_subst.py script.
   If you need to create a new substitution manually,
   please add it also to the substitutions.txt file in the
   source folder.

.. |FA| replace:: Follow Along:
.. |FR| replace:: Further Reading
.. |IC| replace:: In Conclusion
.. |LS| replace:: Lesson:
.. |TY| replace:: Try Yourself
.. |WN| replace:: What's Next?
.. |arrowDown| image:: /static/common/mActionArrowDown.png
   :width: 1.5em
.. |basic| image:: /static/common/basic.png
.. |checkbox| image:: /static/common/checkbox.png
   :width: 1.3em
.. |hard| image:: /static/common/hard.png
.. |majorUrbanName| replace:: Swellendam
.. |moderate| image:: /static/common/moderate.png
.. |rendering| image:: /static/common/rendering.png
   :width: 1.5em
.. |signPlus| image:: /static/common/symbologyAdd.png
   :width: 1.5em
.. |symbology| image:: /static/common/symbology.png
   :width: 2em
.. |zoomIn| image:: /static/common/mActionZoomIn.png
   :width: 1.5em
.. |zoomOut| image:: /static/common/mActionZoomOut.png
   :width: 1.5em
