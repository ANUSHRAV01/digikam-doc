.. meta::
   :description: Build a System to Organize and Find Your Photographs
   :keywords: digiKam, documentation, user manual, photo management, open source, free, learn, easy, hierarchy, tags, rating, captions, geolocation, date, albums, filenames, versioning, exporting

.. metadata-placeholder

   :authors: - digiKam Team

   :license: see Credits and License page for details (https://docs.digikam.org/en/credits_license.html)

.. _organize_find:

Organize and Find
=================

.. contents::

We dare-say if you have more than 1000 photographs on your computer in no-DAM fashion it takes you too long to find any particular image. And if you don't know how many images are in your files you're surely not using digiKam. The dual approach to store metadata in a database and in the image files guarantees ultra fast searching and secure archiving freely accessible to other applications, platforms and formats.

But as much as there is no such thing as a free lunch, there is no free cataloging or DAM - those who spend the initial time of building a systematic method of their own will be better off as time passes and the number of photographs multiplies. The ROI (return on investment) of DAM has been estimated in different studies to be better than 10. Keep in mind to be **concise, plan for the future (30-50y)**, do it once. The upcoming semantic web will totally integrate into and add value to a DAM environment.

Use-Cases with digiKam
~~~~~~~~~~~~~~~~~~~~~~

digiKam provides a number of methods to classify photographs: filenames, albums, collections, time-stamp, tags, rating, GPS position and captions. As if this was not enough, you can search many standard metadata items like camera model, lens, coordinates, image size and many more. Metadata categories as listed here are in fact different **views** of your photo library. Combining these views is the very powerful method to narrow down the search for a file and to find it quickly. Imagine having 800 photos of your loved one. Searching for **Salagou**, having more than **3 rating stars**, shot in **France** will surely leave you with very few candidates. In terms of selection criteria for a DAM system, digiKam fares very well in terms of completeness, versatility, speed, scalability, accuracy and openness.

.. figure:: images/dam_geo_search_filtered.webp
    :alt:
    :align: center

    A :ref:`Geolocation Search <mapsearch_view>` Results in France :ref:`Filtered <filters_view>` by a String and Rating Value

The key thing to remember is that you don't know how you or somebody else will try to find an image 2 years ahead of our time. You will remember past events in a different context, it's a fact of life. So if you can narrow down your search by remembering place or time or camera or theme or rating or owner you stand an infinitely better chance to find it quickly than by just one of those criteria or none. At the beginning, at the time of taking a photograph, all metadata is in your head (except for the Exif data). If you do not transcribe some of it into your DAM system, it will be lost eventually as much as every event fades into oblivion over time.

One distinction has to be interjected here between **private** and **public metadata**. One could say that all file-embedded attributes are potentially public since the images may be exported, sold, and copied to other places and people. On the other hand all non-embedded metadata in the database can be considered private as they stay in the database and go nowhere else. By adjusting digiKam's settings accordingly you can control what kind of data remains private and what will be embedded and eventually become public.

Folders Organization
~~~~~~~~~~~~~~~~~~~~

The first thing to do and to know before you put anything onto your system is to build an information structure (as opposed to data structure). Your image files have to be somehow organized within the computer, you have to decide if others should have access to your photographs (sharing), if you put them on a dedicated drive, on a network drive etc. Keep in mind that you have to migrate one day onto some bigger volume.

The organization should be simple, unified and scalable, and it should be independent of the storage medium on which you host them. In others words, the folders organization must be the physical information layout. Do not make the folders too small, several thousand images in one folder is not too much to ask for, but keep them small enough so that they can fit into a backup medium like an optical drive. Remember that the archive will grow all the time. The concrete type of structure depends on your use case of course: Lets take a simple yet frequent example: you are a casual photographer taking pictures of your private life, your family, holidays and so on. It could be efficient to create a structure based on years plus some holiday and export containers. It could look like this:

.. code-block:: text

    2006
    2007
    2008
    Holidays
    - A
    - B
    - C
    Export
    Fun stuff

Maybe you'll be happy with this structure. Holiday pictures can be quickly found by its location (unless you go to the same place every year), the rest will be organized by date. If you shoot enough pictures you want to create sub folders below the years as months e.g. 2008-01, 2008-02 etc. *Export* would be a container for images to print or to put onto a website.

The more professional photographer will have very different needs as there will be versions of photographs, archives, workflows, a constant influx of images of diverging themes, and a large quantity of everything. Within 10 year you'll have 95% archives and 5% work space files and you don't want to organize your structure around content.

The consideration are these:

    - What kind of files go together? Segregation of file type makes batch processing easier. Keep new and old files separate.

    - How can you make that structure scalable?

    - Segregation of original and working files makes it easier to allocate the backup strategy and migration. You will always know if you look for an original or a derivative.

.. figure:: images/dam_import_rename.webp
    :alt:
    :align: center

    The digiKam :ref:`Import Tool <advanced_import>` Allows to Create Albums and Rename Files Based on Items Properties

Automatic Metadata
~~~~~~~~~~~~~~~~~~

How to go about all this metadata business? Firstly, there are already a lot of **automatically generated metadata**: Exif data and Makernotes. If you have configured digiKam with your identity section all imported images will be imprinted with this data set which includes copyrights, all automatic. If you have a GPS track recorded in parallel to your taking the photographs, you can geolocate those images in a single action using the Geolocation tool. Even if you brought back 1000 images from a shooting session, so far you'll not have spent more than 10 minutes to do all that.

And by now you have all camera settings of every shot, lens data like zoom, focus, aperture etc., date and time, shooting location, copyrights, authorship, program used, and more. Not bad, isn't it? But we could have done more during the importing, we could have changed the file names to include the date, or place or theme, we could have changed the format to a lossless 16 bit per channel format, we could have automatically separated JPEG and RAW files into their folders.

.. figure:: images/dam_date_export_gdrive.webp
    :alt:
    :align: center

    digiKam Propose a Hierarchical View of :ref:`Shooting Dates <dates_view>` Which can be Exported Easily to a Remote Web Service

We actually recommend to auto-rename to match an event, a place or a theme. digiKam provides all date/calendar related grouping so that there's hardly a need for coding the date into the file name. Unless you'd like to do just that to browse your albums with another application that is not calendar savvy. You will buy a new camera one day or you have a second one already, sooner than you believe. The numbering scheme of that new camera will start over at typically IMG_0001.JPG again, creating identical file names to the ones you have already if you do not rename them. By renaming you lessen the chance of inadvertently overwriting them at a later date. Keep the new names clean, use alphanumerics, dashes, underscores and a single period prior to the file extension.

We also recommend to switch-on the **Save Metadata** options in the :ref:`digiKam settings page for metadata <metadata_settings>`. This will ensure that Exif, IPTC and XMP information is written into the file. If you forgot to do that you can always catch up by copying the metadata in the database to the files in one go (from the **Album** menu).

.. figure:: images/dam_metadata_workflow.webp
    :alt:
    :align: center

    The digiKam Metadata Workflow Settings Panel

Now we have a lot of stuff already in our database, but what if we need to change some of it? digiKam provides a :ref:`Metadata Editor <metadata_editor>` for a selected number of attributes, the most important ones of course.

.. figure:: images/dam_metadata_editor.webp
    :alt:
    :align: center

    The digiKam :ref:`Metadata Editor <metadata_editor>` Modify XMP Properties

The real work begins here as we will apply **Tags**, **Captions** and a **Rating** to every photograph. Of course, all images requiring the same attribute can be treated as a selection in one action. Lets start with rating or ranking. It's best to start with ranking because for further work you can concentrate on the good shots. 

.. _rating_ranking:

digiKam also provides **automatic tagging** features based on deep-learning:

    - :ref:`Image Quality Sorting <maintenance_quality>` to assign automatically a **Pick Label** to item based on aesthetic factors.
    - :ref:`Face Detection <face_detection>` to detect faces on image and record areas on database.
    - :ref:`Face recognition <face_recognition>` to assign people tags automatically based on already tagged ones 

    .. figure:: images/dam_maintenance_tool.webp
        :alt:
        :align: center

        digiKam Maintenance Tool is The Best Way to Auto-tag items by :ref:`Quality <maintenance_quality>` or for :ref:`Faces <maintenance_faces>`

These kind of tools requires extra data model files to run. digiKam will ask you to download models at first start.

Rating and Ranking
~~~~~~~~~~~~~~~~~~

A ranking systematic is implemented in digiKam by the 5 star rating tool. In fact there are 6 levels, zero through five stars (*) can be attributed (when saving them into IPTC metadata a translation of levels ensures compatibility with other programs). Rating is rapidly applied with digiKam using keyboard shortcuts or the mouse on single photographs or whole selections. The rating can then be entered as a search criterion or directly from the status bar quick filters.

However, before you start attributing stars everywhere take a moment to establish personal criteria for ranking. Best practice is to write down your personal match of stars to some qualitative expression, that will define what you actually mean when giving 5 stars. Generally there should be much less images rated with increasing star assignment. A ratio of 3-10 between each level has proven useful.

.. figure:: images/dam_rating_edit.webp
    :alt:
    :align: center

    The Edit :ref:`Rating Properties <labels_edit>` From Thumb-bar

That will get you quite far in distinguishing your rating pyramid. Say, you choose a ratio of 7 between levels. For every 5 star image you'll then have 7 4 stars, 49 3 stars and so on, resulting in almost 20000 pictures. Amazing? Yes, and 16807 of them you didn't have to rate at all! You even can define a different rating scheme depending on the kind of use, 2 stars for commercial use, may mean something else than 2 stars holiday photos. It is also a good practice to define a neutral rating, everything below is actually a negative rating.

This will help you culling and thinning your collection very efficiently. Or you could define purposes to ratings, like this:

    - 0 stars for *can throw away*.
    - 1 star for images in quarantine (decide later).
    - 2 stars for gallery export.
    - 3 stars for printing.
    - 4 stars for selling.
    - 5 stars for *have to work on*.

It must suit your needs. The following table illustrates a possible evolution for a professional photographer using a ranking ratio of roughly 7 over the next 12 years. It is evident that the good shots can be easily found, even within millions of photos.

.. figure:: images/dam_pyramid.webp
    :alt:
    :align: center

    The Rating Pyramid

Lets continue with **Tags** (or keywords as called by other applications, or categories, they are all synonymous).

.. _asset_tags:

Tagging and Keywords
~~~~~~~~~~~~~~~~~~~~

Tags are a hierarchical labeling system that you create as you add to it. The important thing to do is to create a system that suits your needs and habits. Are you a (semi) professional who wants to sell photographs to agencies, do you want to publish on a web gallery, or are you just the occasional amateur managing the visual family memory?

For all these different use cases you want to design a tag structure that is adapted to it. If you configure it so, digiKam will write the whole hierarchy into XMP fields so that they can be used by your photographic agency using a different application of to automatically create **Title** and **Caption** for web exports. In any case it will serve you well to quickly find a specific picture again.

.. figure:: images/dam_assign_tags.webp
    :alt:
    :align: center

    The digiKam Image Editor Assigning More Than One Tag at The Same Time Within :ref:`Right Sidebar <captions_view>`

The hierarchy will provide you with automatic groupings. For example, if you start a typical private use hierarchy with *Activities*, *People*, *Places*, *Themes* and *Projects* on the top level, everything you tag with a sub-tag of these will be grouped together into a virtual album. digiKam has a dedicated view in the left sidebar for these virtual albums. But it comes even better.

As you continue adding sub-tags into the hierarchies, not only will you be able to search and quick-filter for them, the right sidebar tag filter allows you to select combinations of tag groups. Lets say in the left sidebar tag panel you select the virtual album *People* and you have 12 different tags for people in there, then you can combine it with the right sidebar and just choose *Peter*, *Paul* and *Mary* out of the 12.

.. figure:: images/dam_tag_properties.webp
    :alt:
    :align: center

    The digiKam :ref:`Tag Properties Dialog <managing_tags>`

In the long run you will not remember the details of your pictures and their subject (essentially the metadata in your brain will break down). It is therefore paramount that you **choose general and generic categories**. You will always remember that a particular shot was set at a river bank in a country or continent (aka river, continent), but you'll have forgotten which river it was. Instead of only tagging it with *Okavango* you tag it with river/Africa or river/South Africa. The details you can either put into a tag as well or into the **Captions**. A trick may help you: How would you search for that river with an Internet search engine? That's the way to go!

Another categorization might be task-oriented as in *print jobs*, *web export*, *personal*, *galleryXYZ*, *clients*, *slideshow*, etc. Create groups as you need them but not more, you should be able to remember by heart the top level tags at least, otherwise the differentiation will become useless. Don't forget that you have all the other attributes to narrow down the search. The right sidebar tag filter combines with any view of left sidebar (albums, calendar, timeline, tag and search). This workflow categorizations can be easily delegated to **Color Labels** in digiKam.

.. figure:: images/dam_color_labels.webp
    :alt:
    :align: center

    The digiKam :ref:`Color Labels <labels_view>` Can be Used to Group Items For Your Workflow Stages

Another digiKam feature is the **Pick Labels** used to categorize shots by quality and identify which item will be **Rejected**, **Pending**, or **Accepted** in your workflow. You can assign this kind of properties manually of course, but there is a better solution: delegate the quality analysis to the computer using the deep-learning based tool named **Image Quality Sorter**. This one can parse image feature as noise, blur, form, shape, contents, etc, and give an evaluation of the quality of shot. This tool is available in **Maintenance Tool** and in **Batch Queue Manager**.

.. figure:: images/dam_quality_bqm.webp
    :alt:
    :align: center

    The digiKam Pick Labels can be Assigned Automatically Depending of the  :ref:`Quality of Shot in Batch Queue Manager <bqm_qualitysort>`

When you import cataloged images from other sources having embedded tags already, digiKam will automatically create the trees for you, respectively insert it into the right place. Rearranging the hierarchy within the tree is no problem, you can do that easily by dragging and dropping a sub-tree to another place in the hierarchy. The changed tags will be updated as digiKam ripples down the branches.

The graphics here shows how different digiKam item properties overlap. This is a very coarse representation, as each block of metadata will in itself be subdivided into many sections. **File-names** and **Files-dates** data are properties of all images taken from files-system.

.. figure:: images/dam_metadata.webp
    :alt:
    :align: center

    The Different Item Properties Available in digiKam

Enough of **Tags**. Lets move on to **Captions** or **Comments**, the third major tool for metadata cataloging.

.. _captions_comments:

Captions and Comments
~~~~~~~~~~~~~~~~~~~~~

This is already the 4th kind of metadata we present here. What is the distinction of **Captions** compared to **Tags** (*comments* can be used synonymously, but the IPTC vocabulary stipulates the term *caption*), keywords? Where **Tags** owe to a hierarchical and generalized description, **Captions** are the opposite: prose description, details, anecdotal stuff. Tags foremostly serve the finding, retrieval and grouping of assets, whereas captions shall entertain, inform, touch the beholder.

Naturally they can also be used to filter the catalog, but this is just a byproduct. Captions are to remember the story, the event, the emotions, it's what makes photographs much more interesting to look at, captions put photographs into a context and meaning. If the pictures are an aesthetic statement, caption should be the emotional and informational complement.

You rarely want nobody to see your photographs. You rather want to share them with friends, your family, other photographers, agencies, put them onto the Internet. And don't tell me you're not interested as to how your photos are being received!

So you might have the most beautiful portrait, sunset or landscape and nobody seems to care. Why is that? Look at some good photographs yourself without reading the title, comment or background information. How many of you are interested in depth of field, exposure time, white balance etc.? Some, of course. But anybody will be interested in the story the pictures tell, you want to remember a photograph, meaningless images bombard us too much anyways. You have to give the viewer something that explains it all.

Lets look at this panorama. From far it is not even a nice beach panorama. If you go closer you start to see some details, people, the space.

.. figure:: images/dam_captions_titles.webp
    :alt:
    :align: center

    digiKam Editing Panorama :ref:`Title From Captions Sidebar <comment_editors>` Tab Within Image Editor

And now we tell you that this is the Allies landing site *Omaha Beach* in the French Normandie 60 years after the disembarkation. One starts to dream, have associations, memories, the historical time span is present, you may hear the silence. The **Caption** has totally reframed to perception of this panorama.

For others to appreciate your photographs, the **Title** is probably more important than the image itself for the interest it creates. When you show pictures, tell a story. Remember that the key is to convey the meaning to viewers, to help them understand what you understand about the subject and what moved you.

    - Let people know what you understand about the subject, why you love it.

    - Create a red line between the photographs.

    - Oppose or relate them to different epochs.

    - Take notes shortly after shooting to remember.

    - Contemplate, research, watch, and talk - but mostly listen.

    - It's okay if the image is less than perfect because it has the strength to stand on its own merit described in the **caption**.

With digiKam you can enter unlimited amounts of text using internationalized alphabet (UTF-8) as caption. You can enter it for a selection of photos at the same time. When you export images to web services, the captions will be exported at choice into either/or/and caption/title of the web gallery system, no need to re-write the story for publishing.

Geolocation and Geo-tagging
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Do you still remember the times before GPS? When you would find your way to another city without navigation system? Wasn't the earth a dull blue ball before Google Earth? Well then, with images, the train of spatial representation is running at cruising speed alright.

A few cameras have a GPS receiver built-in, the images come tagged with 3-dimensional coordinates. And with almost any GPS device you're able to extract a trace (of course the receiver needs to be switched-on and carried with you whilst taking the photographs, and for good matching the camera time must be accurately set) and save it onto a computer. You have to store it in GPX format, that's easily done with `gpsbabel <https://www.gpsbabel.org/>`_, gpsman and other tools.

You then can automatically match a whole bunch of photos with that track using digiKam. The coordinates are written into the JFIF part of JPG files (settings choice) and into the database. digiKam will enable searches based on locations and coordinates, you can create virtual albums of geographical areas! In the right sidebar under the metadata tab you'll find your image located on a local zoom of the world map. A further click brings on anyone of several mapping services on the web, zooming in on details. Even if you don't have a GPS trace you can geo-tag multiple images with a geo-editor. Just navigate on the map to the spot of shooting and click to fix it as a geo-tag.

.. figure:: images/dam_reverse_geocoding.webp
    :alt:
    :align: center

    digiKam Editing Geolocation and Processing :ref:`Reverse Geocoding <geoeditor_reverse>` with OpenStreetMap

The possibilities of exploiting this geolocation are already innumerable and will become pervasive in the future. I'm sure one day not too far away we can revisit in a virtual reality our travels through geo-tagged pictures. The digiKam features include :ref:`exporting to KML files <geoeditor_kmlexport>` that can be opened by GoogleEarth (which in turn will show the photos on their shooting site), exporting to Piwigo, Google Photo, Flickr etc. with OpenStreetMap viewer and more.
