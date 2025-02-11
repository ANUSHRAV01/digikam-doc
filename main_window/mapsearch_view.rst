.. meta::
   :description: digiKam Main Window Map Search View
   :keywords: digiKam, documentation, user manual, photo management, open source, free, learn, easy, map, search, geolocation

.. metadata-placeholder

   :authors: - digiKam Team

   :license: see Credits and License page for details (https://docs.digikam.org/en/credits_license.html)

.. _mapsearch_view:

Map Search View
---------------

 The whole digiKam geolocation suite consists of four parts:

    - The **Map** mode of the Image Area which displays images with GPS data on a map depending on the selection on the Left Sidebar, e.g. the images in the album you selected in the Album View, the images with a certain tag assigned (selected in the Tag View), with a certain label and so on.

    - This view which is the search tool for finding images by their GPS data.

    - The :ref:`Geolocation Editor <geolocation_editor>` which is accessible via :menuselection:`Item --> Edit Geolocation...` :kbd:`Ctrl+Shift+G` and allows to set and to edit GPS data.

    - The :ref:`Map tab <maps_view>` on the Right Sidebar which shows the location of the image on a map and is purely informative.

.. figure:: images/mainwindow_mapsearch.webp
    :alt:
    :align: center

    The digiKam Map Search Tool from Left Sidebar

The earth view is a topographical map of our beautiful home planet. To allow for better orientation the map offers a scale bar in the lower left corner as well as a windrose on the top right. To navigate and to control the view you can use the tools on the Navigation info box at the right: Press the arrow buttons to rotate the globe. The Up and Down arrow buttons will tilt the earth axis back and forth. The Left and Right arrow buttons will make the earth spin around its physical axis.

You can accomplish the same behavior by pressing the left mouse button somewhere on the globe and by moving the mouse while keeping the left mouse button pressed. Using this drag and drop style navigation will allow you to adjust the viewing angle much easier and more precisely. The cursor keys on your keyboard offer another alternative way to quickly change directions.

Zoom in and out by moving the vertical slider up and down. If your mouse has got a mouse wheel you can use that one instead - or you just hold the left mouse button and the right mouse button down both at once while moving the mouse up and down. Changing the zoom level step by step can be done via the Zoom In and Zoom Out buttons which are placed above and below the zoom slider (or using the + and - keys on your keyboard).

Depending on the map's resolution zooming in will provide you with more detail. Smaller cities will appear and using the topographic map you might notice that coastlines are provided as vector graphics.

In case you should get lost you can always reset the viewing angle and zoom level back to the point where we started off: Just press the Home button (or the Home button on your keyboard). To set the home location to the current position (center of the map) select the Bookmarks → Set Home Location menu item.

The meaning of “GPS” and functions and buttons that apply to all three geolocation parts are described in the :ref:`Geolocation Editor <geolocation_editor>` chapter of this handbook. This applies to the context menu on the map and the first line of buttons under the map except the last three. The designations I use here for the buttons is the content of the respective tooltip.

Usually you will begin searching for images by defining a region on the map. From the **Search by area** buttons click the left one, the **Select images by drawing a rectangle** button, then click with the left mouse button over one corner on the map, draw open a rectangle and click with the left mouse button over another corner. All images falling within the coordinates of that rectangle will be shown in the Image Area (provided your images have been geo-coded of course).

The next button to the right is the **Create a region selection from a thumbnail** button which creates a small region around the position of a marker or thumbnail if you click on it. If there are other images hidden behind it because they have the same position or one very close to the image you click on they will be shown in the Image Area.

The last button in this row is the **Remove the current region selection** button. Well, do I still have to explain that after all? O.k., I should mention that it, of course, only removes the selection, not your precious pics.

Now let's have a look on the three buttons at the right end of the row right under the map. They control which images you see in the Image Area out of your defined region. Let's begin with the one at the very end of the row, the Select-images button. If you activate it, it will toggle the selection of a photograph (or a group of photographs if they are hidden behind each other) once you click on it on the map. This can be helpful to fine tune your selection before carrying out operations from the Right Sidebar or the menus.

The **Filter images** button (the one with the funnel on it) will, other than the **Select images** button who leaves all images from your defined region visible in the Image Area, switch off all other images and show only the one you clicked on. This is particular useful if the map is just showing markers or if the thumbnails are too small to clearly identify images.

The **Remove the current filter** button is self explaining but I want to mention here that these three last buttons won't affect your defined search region which means that once you click the button with the white cross in a red circle all images in that region should be displayed again in the Image Area.

The **Show Non Geolocated Items** button displays all images without GPS data in the Image Area. If this applies to many images from your collections it might be a good idea to use the **Filters** tab of the Right Sidebar and/or the sorting and grouping functions in the **View** menu additionally.

In the box below you can enter a name for your geo filter. It will be added to the list view below for future reference once you click the save button to the right of it, it acts as a live geo folder. The search field at the bottom searches in the Searches list above.
