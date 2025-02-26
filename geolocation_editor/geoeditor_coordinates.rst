.. meta::
   :description: digiKam Geolocation Editor Coordinates
   :keywords: digiKam, documentation, user manual, photo management, open source, free, learn, easy, gps, geolocation, coordinates, editor, correlator, gpx, trace, undo, redo

.. metadata-placeholder

   :authors: - digiKam Team

   :license: see Credits and License page for details (https://docs.digikam.org/en/credits_license.html)

.. _geoeditor_coordinates:

Coordinates Tools
=================

.. contents::

Edit Coordinates
----------------

The coordinates can be set manually in the **Details** tab. The location can be found and fixed iteratively with the displayed map. Move the mouse cursor to the region of interest, zoom in, adjust location, zoom in again, and so on until sufficient accuracy is achieved. Note that the zoom center will always be at the cursor position. Eventually you click with the right mouse button at the desired position and choose **Copy Coordinates**. Now you can go to the list of images below the map, select one or more images, click with the right mouse button on them and choose **Paste Coordinates**. The coordinates will then be displayed in the **Latitude** and **Longitude** fields to the right of the map. To save your changes you click the **Apply** button right under the DOP field.

.. figure:: images/geoeditor_details_view.webp
    :alt:
    :align: center

    The digiKam Geolocation Details View With a Map Using Off-Line Data

If you have one or more images that already have GPS data you can copy the coordinates from one of those and paste them to one or more other images by using the respective items from the context menu on the list of images. This comes in handy if there is a series of photos taken at the same location.

To the right of the map there are, beside latitude and longitude, fields for altitude, speed, number of satellites, fix type and uncertainty (DOP). You may see these fields already filled in if you select a photograph where your camera wrote these information into the Exif data. Otherwise you can fill them in manually if you have these data from somewhere else, e.g. a separate GPS receiver. Note that you have to check the relevant checkbox before you can edit a field (under Windows® you may have to double-click it). Only for **Altitude** the context menu on the list of images offers **Look Up Missing Altitude Values** which causes the editor to look up these data in the map data provided the position (latitude and longitude) is already assigned to the photograph.

To delete geolocation data you got to un-check the relevant checkbox and click the **Apply** button right under the **DOP** field. Other than that the context menu on the list of images offer items to remove some of the data from the image. Regarding the last item **Bookmarks** :ref:`see here <geoeditor_bookmarks>`.

.. _gps_correlator:

The Correlator
--------------

In order to correlate your images with geographic data you need to have a GPS tracking information available as a XML file in gpx format (`gpsbabel <https://www.gpsbabel.org/>`_ can download and convert tracking data from a GPS device for you). The idea is: while taking your pictures just keep a GPS device running and carry it around with the camera. Once you are done, download the pictures and the GPS tracks, and run the correlator.

.. figure:: images/geoeditor_correlate.webp
    :alt:
    :align: center

    The digiKam Geolocation Correlator

Select the images you want to correlate in the application main view, then call the geolocation editor with :kbd:`Ctrl+Shift+G` and switch to the **GPS Correlator** tab on the Right Sidebar. The above dialog will show up with the selected images in the list below the map. To indicate possible time/location correlation you have to load a track file with **Load GPX File** that contains GPS data taken at the same time and location as the pictures.

When the file is loaded and **Show Tracks On Map** is checked the track is displayed on the map. You can load more than one file and digiKam will assign different colors to them and display the tracks on the map accordingly.

GPS track data is invariably recorded in UTC (Universal Time Coordinated), so you need to match the camera time with UTC, which can be done with **Camera Time Zone**. Select **Same As System** if you took the photographs in your home time zone and digiKam will figure out the difference to UTC from your system time. If you took the photographs somewhere else you got to check **Manual** and choose the appropriate difference from the drop-down field to the right. You can use the same mechanism as well to correct a simple mis-adjustment of your camera time for whatever reasons or an offset of a gpx-file due to quirks of a software used to convert other track file formats into gpx. Here comes **Fine offset (mm:ss)** into play where you can add or subtract up to 59 minutes and 59 seconds to your time difference chosen in the field above.

The **Max. Time Gap (sec.)**: setting specifies the limit within which GPS time and camera time shall be deemed coincident. The maximum value is 2000 seconds. This means that if no entry in the gpx-file matches the time stamp of the photograph exactly, the position of the entry with the smallest time gap to the photograph will become assigned to it as long as this time gap is smaller than the **Max. time gap (sec.)** setting. If you wonder which value you should specify here a look into the settings of your track recording device/software or into the gpx-file (which is easily possible with a text editor) might help. The faster you were moving while taking the photograph(s) the more important this decision will be.

**Interpolate** offers another option in case there is no exact match between the time stamp of your photograph(s) and an entry in the gpx-file and as long as you were moving more or less straight between two recorded GPS positions it will be the more precise option. Here the position of the photograph is calculated (linear interpolated) from the positions of the two closest entries in the gpx-file and the respective differences in time. If, for instance, the time gaps between the two closest entries and the photograph are equal the position assigned will be on a straight line between the positions of the two entries right in the middle.

**Max. Interpol. Time Gap (min)**: has nothing to do with policeman Max from Interpol. Instead it determines whether a GPS point is eligible for interpolation. If its time is farther away from the picture time than this limit, it cannot be used. 240 minutes is the maximum time difference that can be introduced here.

Once your settings are done you click on the **Correlate** button. If there is no match at all you will get the message "Could not correlate any image - please make sure the timezone and gap settings are correct." Otherwise you will get something like "2 out of 4 images have been correlated. Please check the timezone and gap settings if you think that more images should have been correlated." Best case you get "All images have been correlated. You can now check their position on the map."

If you want to follow this recommendation it is a good idea to change to the **Details** tab since there you have a preview of the images which can help a lot to identify them on the map. Remember that you always have to click on an image in the list under the map to make its preview show up. Once you are satisfied with the results click the **Apply** button at the bottom of the Geolocation Editor to save the changes to the image file and the database.

Undo And Redo
-------------

In the **Undo/Redo** tab a history is being recorded about all the changes you apply to the images loaded into the Geolocation Editor. The history shows changes made in only one tab or in several tabs and will be deleted only once you leave the editor. After a few actions in the different tabs the record might look like this:

.. figure:: images/geoeditor_undo1.webp
    :alt:
    :align: center

    The digiKam Geolocation Correlator **Undo/Redo** View Example 1

The last step is highlighted when you enter the tab. The first step is always labeled “empty” and represents the status the images had when they were loaded. You can click on every step and, depending on what kind of changes you did, you might see the images appearing, disappearing or moving on the map or see the differences in the list of images under the map. Note that the list is configurable by clicking with the right mouse button on the header.

Now let's assume that you realize that the move in the last step was wrong. You just click on the step before (Details changed), you go to the **Search** tab (described further below) and you do another move. After returning to the **Undo/Redo** tab it might look like this:

.. figure:: images/geoeditor_undo2.webp
    :alt:
    :align: center

    The digiKam Geolocation Correlator **Undo/Redo** View Example 2
