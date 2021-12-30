|LS| Classification
======================================================================

Labels are a good way to communicate information such as the names of
individual places, but they can't be used for everything.
For example, let us say that someone wants to know what each
``ELC_campus`` area is used for.
Using labels, you would get this:

.. figure:: img/Classification_crowdedlabels.png
   :align: center

This makes the map's labeling difficult to read and even overwhelming
if there are numerous different ELC polygons on the map.

**The goal for this lesson:** To learn how to classify vector data
effectively.

|basic| |FA| Classifying Nominal Data
----------------------------------------------------------------------

#. Open the :guilabel:`Layer Properties` dialog for the ``ELC_campus``
   layer
#. Go to the :guilabel:`Symbology` tab
#. Click on the dropdown that says :guilabel:`Single Symbol` and
   change it to :guilabel:`Categorized`:

   .. figure:: img/ELC_campus_vector_class_categorized.png
      :align: center

#. In the new panel, change the :guilabel:`Value` to ``CSCODE1`` and
   the :guilabel:`Color ramp` to :guilabel:`Random colors`
#. Click the button labeled :guilabel:`Classify`

   .. figure:: img/Classification_randomcolor.png
      :align: center

#. Alternatively, you may want to take some time to explore different color
   ramps. You can click on the :guilabel:`Color ramp` and navigate to
   `Create new color ramp`, as shown below:

   .. figure:: img/Classification_newramp.png
      :align: center

#. A 'Color ramp type' dialog box will appear.  Click the dropdown menu,
   and select Catalog: ColorBrewer, as shown below.
   
   .. figure:: img/Classification_colorbrewer.png
      :align: center
   
   ColorBrewer is a catalog of colour schemes for creating maps.
   There is a website which I recommend visiting, that is
   great for colour scheme visualization and selection. 
   Color Brewer 2: https://colorbrewer2.org/#type=sequential&scheme=BuGn&n=3 

#. Scroll through the different options and make sure to select a colour scheme
   that is appropriate for nominal data.

   .. figure:: img/Classification_goodcolours.png
   
#. Click :guilabel:`OK`
   
   This is the colour scheme I decided to use:

   .. figure:: img/Classification_result.png
      :align: center

#. Click the arrow (or plus sign) next to ``ELC_campus`` in the
   :guilabel:`Layers` panel, you'll see the categories explained 
   (refer to layers panel in the above photo).

#. If you wish to, you can change the color of each ELC
   class by double-clicking the relevant color block in the
   `Layers` panel or in the :guilabel:`Layer Properties`
   dialog:

   .. figure:: img/Classification_symbolselector.png
      :align: center

   Spend some time picking a nice colour scheme, as map aethetics are
   very important for conveying information effectively. Once you are
   satisfied with your colour selection, take a look at your map.  
   Now our ELC polygons are colored and are classified so that
   areas with the same ELC are the same color.

   Note
   
   You may have noticed that there is one category that's empty:

   .. figure:: img/ELC_campus_vector_class_emptyclass.png
      :align: center

   This empty category is used to color any objects which do not have a
   ELC class value defined or which have a *NULL* value.
   It can be useful to keep this empty category so that areas with a
   *NULL* value are still represented on the map.
   You may like to change the color to more obviously represent a blank
   or *NULL* value. Or, you may choose to remove it.

Remember to save your map now so that you don't lose all your
hard-earned changes!

|moderate| |FA| Ratio Classification
----------------------------------------------------------------------

There are four types of classification: *nominal*, *ordinal*,
*interval* and *ratio*.

In **nominal** classification, the categories that objects are
classified into are name-based; they have no order.
For example: town names, district codes, etc.
Symbols that are used for nominal data should not imply any order or
magnitude.

* For points, we can use symbols of different shape.
* For polygons, we can use different types of hatching or different
  colours (avoid mixing light and dark colours).
* For lines, we can use different dash patterns, different colours
  (avoid mixing light and dark colours) and different symbols along
  the lines.

In **ordinal** classification, the categories are arranged in a
certain order.
For example, world cities are given a rank depending on their
importance for world trade, travel, culture, etc.
Symbols that are used for ordinal data should imply order, but not
magnitude.

* For points, we can use symbols with light to dark colours.
* For polygons, we can use graduated colours (light to dark).
* For lines, we can use graduated colours (light to dark).

In **interval** classification, the numbers are on a scale with
positive, negative and zero values.
For example: height above/below sea level, temperature in degrees
Celsius.
Symbols that are used for interval data should imply order and
magnitude.

* For points, we can use symbols with varying size (small to big).
* For polygons, we can use graduated colours (light to dark) or
  add diagrams of varying size.
* For lines, we can use thickness (thin to thick).

In **ratio** classification, the numbers are on a scale with only
positive and zero values.
For example: temperature above absolute zero (0 degrees Kelvin),
distance from a point, the average amount of traffic on a given
street per month, etc.
Symbols that are used for ratio data should imply order and
magnitude.

* For points, we can use symbols with varying size (small to big).
* For polygons, we can use graduated colours (light to dark) or
  add diagrams of varying size.
* For lines, we can use thickness (thin to thick).

In the example above, we used nominal classification to color each
record in the ``ELC_campus`` layer based on its ``CSCODE1`` attribute.
Now we will use ratio classification to classify the records by area m2.

We are going to reclassify the layer, so existing classes will be lost
if not saved. To store the current classification:

#. Open the layer's properties dialog
#. Click the :guilabel:`Save Style ...` button in the :guilabel:`Style`
   drop-down menu.
#. Select :guilabel:`Rename Current...`, enter ``ELC class`` and press
   :guilabel:`OK`.

   The categories and their symbols are now saved in the layer's properties.
#. Click now on the :guilabel:`Add...` entry of the :guilabel:`Style`
   drop-down menu and create a new style named ``ratio``.
   This will store the new classification.
#. Close the :guilabel:`Layer Properties` dialog

We want to classify the ELC polygons by size, but there is a
problem: they don't have a size field, so we'll have to make one.

#. Open the Attributes Table for the ``ELC_campus`` layer.
#. Enter edit mode by clicking the |toggleEditing|  :sup:`Toggle editing`
   button
#. Add a new column of decimal type, called ``AREA``, using the
   |newAttribute| :sup:`New field` button: 

   .. figure:: img/ELC_campus_vector_class_addfield.png
      :align: center

Note

Take a moment and examine the different field types.  You will notice there
are five different types:

   Whole number (integer)
   Whole number (integer 64 bit)
   Decimal number (real)
   Text (string)
   Date 

Attribute data can be stored as one of these five field types.  The five
data types and their uses will be discussed in later lectures.  For now,
understand that data can be stored as numbers, characters or dates, and
based on the data type, data can be manipulated, classified and categorized
in different ways. 

#. Click :guilabel:`OK`

   The new field will be added (at the far right of the table; you may
   need to scroll horizontally to see it).
   However, at the moment it is not populated, it just has a lot of
   *NULL* values.

   To solve this problem, we will need to calculate the areas.

   #. Open the field calculator with the |calculateField| button.

      You will get this dialog:

      .. figure:: img/ELC_campus_vector_class_fieldcalc.png
         :align: center

   #. Check the |checkbox| :guilabel:`Update existing fields`
   #. Select :guilabel:`AREA` in the fields drop-down menu

      .. figure:: img/ELC_campus_vector_class_updatefield.png
         :align: center

   #. Under the :guilabel:`Expression` tab, expand the :guilabel:`Geometry`
      functions group in the list and find :menuselection:`$area`
   #. Double-click on it so that it appears in the :guilabel:`Expression`
      field

      .. figure:: img/ELC_campus_vector_class_area.png
         :align: center

   #. Click :guilabel:`OK`
   #. Scroll to the ``AREA`` field in the attribute table and you will
      notice that it is populated with values (you may need to
      click the column header to refresh the data).

   .. note:: If you recall, at the beginning of this project we set the
      ellipsoid to WGS84 and the project's area unit to meters, therefore
      the rendered area values will be in square meters.

#. Press |saveEdits| to save the edits and exit the edit mode with
   |toggleEditing| :sup:`Toggle editing`
#. Close the attribute table

Now that we have the data, let's use them to render the ``ELC_campus`` layer.

#. Open the :guilabel:`Layer properties` dialog's
   :guilabel:`Symbology` tab for the ``ELC_campus`` layer
#. Change the classification style from :guilabel:`Categorized` to
   :guilabel:`Graduated`

#. Change the :guilabel:`Value` to ``AREA``

#. As you did before for your nominal classification, under `Color ramp`, 
   choose the option :guilabel:`Create New Color Ramp...`.  

#. Feel free to choose the ColorBrewer catalog again, or try `Gradient` 
   (if it's not selected already) and click :guilabel:`OK`.  If you choose
   'Gradient', you will see this:

   .. figure:: img/gradient_color_select.png
      :align: center

   You'll be using this to denote area, with small areas as
   :guilabel:`Color 1` and large areas as :guilabel:`Color 2`. If you decide 
   to use ColorBrewer, be sure to select a gradient colour scheme from 
   the options.

#. Click :guilabel:`OK`

#. If you create a custom colour ramp, you can save the colour ramp by selecting
   :guilabel:`Save Color Ramp...` under the :guilabel:`Color ramp`
   tab. 
   
   Choose an appropriate name for the colour ramp and click
   :guilabel:`Save`.
   
   You will now be able to select the same colour ramp easily under
   :guilabel:`All Color Ramps`.

#. Click :guilabel:`Classify`

   Now you will have something like this:

   .. figure:: img/Classification_areaclassified.png
      :align: center

   Leave everything else as-is.

#. Click :guilabel:`OK`:

.. figure:: img/Classification_areamap.png
   :align: center


|moderate| |TY| Refine the Classification
----------------------------------------------------------------------

* Change the values of :guilabel:`Mode` and :guilabel:`Classes` until
  you get a classification that makes sense.

.. admonition:: Answer
   :class: dropdown

   The settings you used might not be the same, but with the values
   :guilabel:`Classes` = ``6`` and :guilabel:`Mode` = :guilabel:`Natural Breaks
   (Jenks)` (and using the same colors, of course), the map will look like this:

   .. figure:: img/gradient_map_new_mode.png
      :align: center

|IC|
----------------------------------------------------------------------

Symbology allows us to represent the attributes of a layer in an
easy-to-read way.

It allows us as well as the map reader to understand the significance
of features, using any relevant attributes that we choose.
Depending on the problems you face, you'll apply different
classification techniques to solve them.

|WN|
----------------------------------------------------------------------

Now we have a nice-looking map, but how are we going to get it out of
QGIS and into a format we can print out, or make into an image or PDF? That's the topic of the next lesson!


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
.. |calculateField| image:: /static/common/mActionCalculateField.png
   :width: 1.5em
.. |checkbox| image:: /static/common/checkbox.png
   :width: 1.3em
.. |expression| image:: /static/common/mIconExpression.png
   :width: 1.5em
.. |hard| image:: /static/common/hard.png
.. |majorUrbanName| replace:: Swellendam
.. |moderate| image:: /static/common/moderate.png
.. |newAttribute| image:: /static/common/mActionNewAttribute.png
   :width: 1.5em
.. |radioButtonOn| image:: /static/common/radiobuttonon.png
   :width: 1.5em
.. |saveEdits| image:: /static/common/mActionSaveEdits.png
   :width: 1.5em
.. |signMinus| image:: /static/common/symbologyRemove.png
   :width: 1.5em
.. |signPlus| image:: /static/common/symbologyAdd.png
   :width: 1.5em
.. |toggleEditing| image:: /static/common/mActionToggleEditing.png
   :width: 1.5em
