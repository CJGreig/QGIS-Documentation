.. index:: Expressions

.. _vector_expressions:

************
Expressions
************

.. only:: html

   .. contents::
      :local:
      :depth: 2

Based on layer data and prebuilt or user defined functions, **Expressions**
offer a powerful way to manipulate attribute value, geometry and variables
in order to dynamically change the geometry style, the content or position
of the label, the value for diagram, the height of a layout item,
select some features, create virtual field, ...

.. note:: A list of the default functions and variables for writing expressions
   can be found at :ref:`functions_list`, with detailed information and examples.

.. _expression_builder:

The Expression string builder
=============================

Main dialog to build expressions, the :guilabel:`Expression string builder`
is available from many parts in QGIS and, can particularly be accessed when:

* clicking the |expression| button;
* :ref:`selecting features <sec_selection>` with the |expressionSelect|
  :sup:`Select By Expression...` tool;
* :ref:`editing attributes <calculate_fields_values>` with e.g. the
  |calculateField| :sup:`Field calculator` tool;
* manipulating symbology, label or layout item parameters with the |dataDefined|
  :sup:`Data defined override` tool (see :ref:`data_defined`);
* building a :ref:`geometry generator <geometry_generator_symbol>` symbol layer;
* doing some :ref:`geoprocessing <label_processing>`.

The Expression builder dialog offers access to the:

* :ref:`Expression tab <functions_list>` which, thanks to a list of predefined
  functions, helps to write and check the expression to use;
* :ref:`Function Editor tab <function_editor>` which helps to extend the list of
  functions by creating custom ones.

The Interface
-------------

The :guilabel:`Expression` tab provides the main interface to write expressions
using functions, layer fields and values. It contains the following widgets:

.. _figure_expression_tab:

.. figure:: img/function_list.png
   :align: center
   :width: 100%

   The Expression tab

* An expression editor area for typing or pasting expressions. Autocompletion is
  available to speed expression writing:

  * Corresponding variables, function names and field names to the input text
    are shown below: use the :kbd:`Up` and :kbd:`Down` arrows to browse the
    items and press :kbd:`Tab` to insert in the expression or simply click
    on the wished item.
  * Function parameters are shown while filling them.

  QGIS also checks the expression rightness and highlights all the errors using:

  * *Underline*: for unknown functions, wrong or invalid arguments;
  * *Marker*: for every other error (eg, missing parenthesis, unexpected
    character) at a single location.

* Above the expression editor, a set of tools helps you:

  * |fileNew|:sup:`Clear the expression editor`
  * create and manage :ref:`user expressions <user_expressions_functions>`

* Under the expression editor, you find:

  * a set of basic operators to help you build the expression
  * an indication of the expected format of output when you are data-defining
    feature properties
  * a live :guilabel:`Output preview` of the expression, evaluated
    on the first feature of the Layer by default.
    You can browse and evaluate other features of the layer using the
    :guilabel:`Feature` combobox (the values are taken from the
    :ref:`display name <maptips>` property of the layer).

    In case of error, it indicates it and you can access the details with the
    provided hyperlink.

* A function selector displays the list of functions, variables, fields...
  organized in groups. A search box is available to filter the list and quickly
  find a particular function or field.
  Double-clicking an item adds it to the expression editor.
* A help panel displays help for each selected item in the function selector.

  .. tip::

   Press :kbd:`Ctrl+Click` when hovering a function name in an expression to
   automatically display its help in the dialog.

  A field's values widget shown when a field is selected in the function selector
  helps to fetch features attributes:

  * Look for a particular field value
  * Display the list of :guilabel:`All Unique` or :guilabel:`10 Samples` values.
    Also available from right-click.

    When the field is mapped with another layer or a set of values, i.e. if the
    :ref:`field widget <edit_widgets>` is of *RelationReference*, *ValueRelation*
    or *ValueMap* type, it's possible to list all the values of the mapped field
    (from the referenced layer, table or list). Moreover, you can filter this
    list to |checkbox| :guilabel:`Only show values in use` in the current field.

  Double-clicking a field value in the widget adds it to the expression editor.

  .. tip::

   The right panel, showing functions help or field values, can be
   collapsed (invisible) in the dialog. Press the :guilabel:`Show Values`
   or :guilabel:`Show Help` button to get it back.


Writing an expression
---------------------

QGIS expressions are used to select features or set values.
Writing an expression in QGIS follows some rules:

#. **The dialog defines the context**: if you are used to SQL, you probably
   know queries of the type *select features from layer where condition*
   or *update layer set field = new_value where condition*.
   A QGIS expression also needs all these information but the tool you use
   to open the expression builder dialog provides parts of them.
   For example, giving a layer (``buildings``) with a field (``height``):

   * pressing the |expressionSelect|:sup:`Select by expression` tool means that
     you want to "select features from buildings". The **condition** is the
     only information you need to provide in the expression text widget,
     e.g. type ``"height" > 20`` to select buildings that are higher than 20.
   * with this selection made, pressing the |calculateField| :sup:`Field calculator`
     button and choosing "height" as :guilabel:`Update existing field`, you already
     provide the command "update buildings set height = ??? where height > 20".
     The only remaining bits you have to provide in this case is the **new value**,
     e.g. just enter ``50`` in the expression editor textbox to set the height
     of the previously selected buildings.

#. **Pay attention to quotes**: single quotes return a literal, so a
   text placed between single quotes (``'145'``) is interpreted as a string.
   Double quotes will give you the value of that text so use them for fields
   (``"myfield"``). Fields can also be used without quotes (``myfield``).
   No quotes for numbers (``3.16``).

   .. note:: Functions normally take as argument a string for field name.
       Do::

        attribute( @atlas_feature, 'height' ) -- returns the value stored in the "height" attribute of the current atlas feature

       And not::

        attribute( @atlas_feature, "height" ) -- fetches the value of the attribute named "height" (e.g. 100), and use that value as a field
                                              -- from which to return the atlas feature value. Probably wrong as a field named "100" may not exist.


.. index:: Named parameters
   single: Expressions; Named parameters
   single: Functions; Named parameters


Some use cases of expressions
-----------------------------

* From the Field Calculator, calculate a "pop_density" field using the existing "total_pop"
  and "area_km2" fields::

    "total_pop" / "area_km2"

* Label or categorize features based on their area::

    CASE WHEN $area > 10 000 THEN 'Larger' ELSE 'Smaller' END

* Update the field "density_level" with categories according to the "pop_density" values::

    CASE WHEN "pop_density" < 50 THEN 'Low population density'
         WHEN "pop_density" >= 50 and "pop_density" < 150 THEN 'Medium population density'
         WHEN "pop_density" >= 150 THEN 'High population density'
    END

* Apply a categorized style to all the features according to whether their average house
  price is smaller or higher than 10000€ per square metre::

    "price_m2" > 10000

* Using the "Select By Expression..." tool, select all the features representing
  areas of “High population density” and whose average house price is higher than
  10000€ per square metre::

    "density_level" = 'High population density' and "price_m2" > 10000

  The previous expression could also be used to define which features
  to label or show on the map.

.. Substitutions definitions - AVOID EDITING PAST THIS LINE
   This will be automatically updated by the find_set_subst.py script.
   If you need to create a new substitution manually,
   please add it also to the substitutions.txt file in the
   source folder.

.. |calculateField| image:: /static/common/mActionCalculateField.png
   :width: 1.5em
.. |checkbox| image:: /static/common/checkbox.png
   :width: 1.3em
.. |dataDefined| image:: /static/common/mIconDataDefine.png
   :width: 1.5em
.. |deleteSelected| image:: /static/common/mActionDeleteSelected.png
   :width: 1.5em
.. |expression| image:: /static/common/mIconExpression.png
   :width: 1.5em
.. |expressionSelect| image:: /static/common/mIconExpressionSelect.png
   :width: 1.5em
.. |fileNew| image:: /static/common/mActionFileNew.png
   :width: 1.5em
.. |fileSave| image:: /static/common/mActionFileSave.png
   :width: 1.5em
.. |sharingExport| image:: /static/common/mActionSharingExport.png
   :width: 1.5em
.. |sharingImport| image:: /static/common/mActionSharingImport.png
   :width: 1.5em
.. |signMinus| image:: /static/common/symbologyRemove.png
   :width: 1.5em
.. |signPlus| image:: /static/common/symbologyAdd.png
   :width: 1.5em
.. |start| image:: /static/common/mActionStart.png
   :width: 1.5em
.. |symbologyEdit| image:: /static/common/symbologyEdit.png
   :width: 1.5em
