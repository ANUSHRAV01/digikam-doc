.. meta::
   :description: Color Management and Working Space
   :keywords: digiKam, documentation, user manual, photo management, open source, free, learn, easy, image editor, color management, icc, profile, working space

.. metadata-placeholder

   :authors: - digiKam Team

   :license: see Credits and License page for details (https://docs.digikam.org/en/credits_license.html)

.. _working_space:

The Working Space
=================

Color Workflow
--------------

So we told digiKam where to find my monitor profile and we have a camera profile that we applied to the image file produced by my RAW processing software. What's the next step in color management?

You need to choose a working color space so you can edit your image. `Lcms <https://www.littlecms.com/>`_ will transform your image from your camera color space to your chosen working space, via the **Profile Connection Space** specified by your camera color profile. Why cannot to just edit images in the color space described by the camera profile?

After all, the camera profile should provide the best *fit* to the colors recorded by my camera, as processed by my RAW processing procedure, right? Working spaces, such as sRGB or Adobe RGB, are color spaces that facilitate good results while editing. For instance, pixels with equal values of RGB should appear neutral. This just want means that for any given pixel in an image that has been converted to a suitable working space, if R=G=B you should see grey or black or white on your screen. Many camera profiles violate this *neutral* condition.

.. figure:: images/cm_editor_convert_menu.webp
    :alt:
    :align: center

    digiKam Image Editor has a Menu to Switch Quickly an Image from a Color Space to Another one

However, there is one other good reason to not want to edit your image in your camera profile color space. If you look at the size of a typical camera profile, it is on the order of a quarter to a half a megabyte or more. It's got a lot of information about all the changes that need to be made at different regions of color and tonality in the original scene, to get accurate color rendition from the RGB values that come out of the RAW processor. The camera profile is accurate (at least for colors in the original target) but not particularly mathematically smooth. Working space color profiles, on the other hand, are very small in size (half a kilobyte instead of half a megabyte) because they describe a color gamut in terms of smooth, continuous mathematical functions. Working space profiles don't need to make allowances for the *messiness* of real world sensors, so the mathematical manipulations performed during image editing will go much more smoothly and accurately than if you try to edit your image while it is still in the camera color space.

Working space profiles are characterized by:

    - **Gamma** (or other transfer function), which dictates how much the original linear intensity values captured by the camera sensor (and subjected to the in-camera A-to-D conversion, then interpolated by the RAW processing program to produce the image file) are altered to make editing easier or more precise.

    - RGB primaries which dictate the range of colors, that is, the color **Gamut**, covered by a given profile.

    - **White point** (usually D50 or D65 though other values may be used), which specifies the color temperature of the white point of the working space.

Confusions Terminology
----------------------

Before talking more about working spaces, some confusions and confusing terminology needs to be cleared up:

    1. sRGB is both a working color space and an output color space for images intended for the web and for monitor display. If you have a spiffy new monitor with a gamut larger than the gamut covered by sRGB, obviously you might want to reconsider what output profile to use to best take advantage of your wonderful and hopefully calibrated and profiled monitor, but please convert your image to sRGB before sending it on to your friends. sRGB is also the color space that a lot of home and mass-production commercial printers expect image files to be in when sent to the printer. It is also the color space that most programs assume if an image does not have an embedded color profile telling the program what color space should be used to interpret (translate) the RGB numbers. So if you choose to not use color-management, your color-management choices are simple - set everything to sRGB.

    2. All JPEGs coming straight out of a camera (even if produced by point-and-shoots cameras that don't allow you to save a RAW file) start life inside the camera as a RAW file produced by the camera's A to D converter. The processor inside the camera interpolates the RAW file, assigns a camera profile, translates the resulting RGB numbers to a working space (usually sRGB but sometimes you can choose AdobeRGB, depending on the camera), does the JPEG compression, and stores the JPEG file on your camera card. So JPEGs from your camera never need to be assigned a camera or input profile which is then translated to a working space via a Profile Connection Space. JPEGs from a camera are already in a working space.

    3. In case anyone is unsure on this point, note that an interpolated RAW file is no longer a RAW file - it has been interpolated and then output as a TIFF whose RGB values need to be translated to a working space, using the camera profile, the Profile Connection Space, and Lcms.

    4. To introduce a bit of commonly heard color-management terminology here - the camera profile and your printer's color profile are both device dependent, whereas the working space will be device-independent - it can be used with any image, with any properly color-managed software, without regard for where the image originated.

    5. Above we have used the words translate and translation as a descriptive metaphor for what Lcms does when it translates RGB values from one color space to another via the Profile Connection Space. The usual and correct terminology is convert and conversion. The four methods of conversion from one color space to another are: perceptual, relative colorimetric, absolute colorimetric, and saturation. Which method of conversion you should use for any given image processing step from RAW file to final output image is beyond the scope of this manual. The standard advice is: when in doubt, use perceptual.

    6. Assign a profile means change the meaning of the RGB numbers in an image by embedding a new profile without changing the actual RGB numbers associated with each pixel in the image; convert means embed a new profile, but also change the RGB numbers at the same time so that the meaning of the RGB values - that is, the real-world visible color represented by the trio of RGB numbers associated with each pixel in an image - remains the same before and after the conversion from one space to another. You should be able to do multiple conversions of an image from one working space to another, and with a properly color-managed image editor, even though all the RGB numbers in the image will change with each conversion, the image on your screen should look the same (leaving aside the usually unnoticeable small but inevitable changes from accumulated gamut mismatches and mathematical rounding errors). However, every time you assign a new working space profile rather than convert to a new working space, the appearance of the image should more or less drastically change.

    7. Color management is not only relevant if you shoot RAW. Color management affects every stage of the image processing pipeline, whether you start with a RAW file that you, yourself interpolate and translate into a TIFF, or if you start with a JPEG or TIFF produced by your camera.

Selecting a Working Space
-------------------------

Which working space do you need to use in digiKam? Working spaces, such as sRGB or Adobe RGB, are color spaces that facilitate good results while editing. For instance, pixels with equal values of RGB should appear neutral. Using a large gamut working space will lead to posterization, while using a small working space will lead to clipping. This trade-off is a consideration for the Image Editor.

Most working space profiles are characterized by:

    - The place of the gamut into the **Diagram** `(1)` of all colors visible to the average human eyes.

    - The **Gamut** `(2)` triangle to define the range of RGB colors of the profile. Red point is on the bottom right corner, Green is on the top, Blue is on the left bottom. Values given around the edge of the gamut passing from the blue, the green and the red points, are the spectral colors in nanometers.

    - The **White point** `(3)` to define the total dynamic range of the profile.

    - The **Gamma** to define the transfer function of the profile (not displayed in the gamut).

.. figure:: images/cm_gamut_details.webp
    :alt:
    :align: center

    The Color Profile Details of CIE Chromaticity Diagram Show in digiKam

The practical consequences that result from using different RGB primaries, leading to larger or smaller working spaces, are discussed below. The practical consequences for different choices for the working space white point are beyond the scope of this manual. Here we will talk a little bit about the practical consequences of the working space gamma.

The gamma of a color profile dictates what power transform needs to take place to properly convert from an image's embedded color profile (perhaps your working color space) to another color profile with a different gamma, such as (i) the display profile used to display the image on the screen or (ii) perhaps to a new working space, or (iii) perhaps from your working space to your printer's color space.

.. tip::

    Mathematically speaking, for a power transform you normalize the RGB numbers and raise the resulting numbers to an appropriate power depending on the respective gammas of the starting and ending color space, then re-normalize the results to a new set of RGB numbers. `Lcms <https://www.littlecms.com/>`_ does this for you when there is a need to convert from one color space to another in your workflow.

One practical consequence of the gamma of a working space is that the higher the gamma, the more tones are available for editing in the shadows, with consequently fewer tones available in the highlights. So theoretically, if you are working on a very dark-toned (low key) image you might want a working space with a higher gamma. And if you are working on a high key image, say a picture taken in full noon sunlight of a wedding dress with snow as a backdrop, you might want to choose a working space with a lower gamma, so you have more available tonal gradations in the highlights. But in the real world of real image editing, almost everyone uses working spaces with either gamma 1.8 or 2.2.

Some people are trying to standardize on gamma 2.0. sRGB and LStar-RGB are not gamma-based working spaces. Rather, sRGB uses a hybrid gamma, and LStar-RGB uses a luminosity-based tonal response curve instead of a gamma value.

In addition to gamma 1.8 and gamma 2.2 the only other gamma for a working space that gets much mention or use is gamma 1.0, also called linear gamma. Linear gamma is used in HDR (high dynamic range) imaging and also if one wants to avoid introducing gamma-induced errors into one's regular low dynamic range editing. Gamma-induced errors is a topic outside the scope of this manual, but see Gamma errors in picture scaling, for gamma-induced color shifts.

Unfortunately and despite their undeniable mathematical advantages, linear gamma working spaces have so few tones in the shadows that they are impossible to use for editing if one is working in 8-bits, and still problematic at 16-bits. When the day comes when we are all doing our editing on 32-bit files produced by our HDR cameras on our personal supercomputers, we predict that we will all be using working spaces with gamma 1.

.. figure:: images/cm_editor_profile_missmatch.webp
    :alt:
    :align: center

    Depending of the Settings digiKam Can Ask you to Convert to Working Space When Loading in Image Editor

Large or Small Gamut
--------------------

One major consideration in choosing a working space is that some working spaces are bigger than others, meaning they cover more of the visible spectrum (and perhaps even include some imaginary colors - mathematical constructs that don't really exist). These bigger spaces offer the advantage of allowing you to keep all the colors captured by your camera and preserved by the Lcms conversion from your camera profile to the really big profile connection space.

.. figure:: images/cm_working_space_gamuts.webp
    :alt:
    :align: center

    For the Left to Right: sRGB, AbodeRGB, WideGammutRGB, and ProPhotoRGB Color Profile Show in digiKam

But keeping all the possible colors comes at a price. It seems that any given digital image (pictures of daffodils with saturated yellows being one common exception) likely only contains a small subset of all the possible visible colors that your camera is capable of capturing. This small subset is easily contained in one of the smaller working spaces. Using a very large working space mean that editing your image (applying curves, saturation, etc.) can easily produce colors that your eventual output device (printer, monitor) simply cannot display.

So the conversion from your working space to your output device space (say your printer) will have to remap the out of gamut colors in your edited image, some of which might even be totally imaginary, to your printer color space with its much smaller gamut, leading to inaccurate colors at best and at worst to banding (posterization - gaps in what should be a smooth color transition, say, across an expanse of blue sky) and clipping (your carefully crafted muted transitions across delicate shades of red, for example, might get remapped to a solid block of dull red after conversion to your printer's color space).

In other words, large gamut working spaces, improperly handled, can lead to lost information on output. Small gamut working spaces can clip information on input. Here is some oft-repeated advice:

    - For images intended for the web, use sRGB.

    - For the most accuracy in your image editing (that is, making the most of your *bits* with the least risk of banding or clipping when you convert your image from your working space to an output space), use the smallest working space that includes all the colors in the scene that you photographed, plus a little extra room for those new colors you intentionally produce as you edit.

    - If you are working in 8-bits rather than 16-bits, choose a smaller space rather than a larger space.

    - For archival purposes, convert your RAW file to a 16-bit TIFF with a large gamut working space to avoid loosing color information. Then convert this archival TIFF to your working space of choice (saving the converted working TIFF under a new name, of course). See here for more details.

    .. figure:: images/cm_bqm_convert_space.webp
        :alt:
        :align: center

        digiKam Queue Manager Allows to Batch Convert Color Space

Gamma Properties
----------------

The gamma of a color profile dictates what power transform needs to take place to properly convert from an image's embedded color profile (perhaps your working color space or your camera color profile) to another color profile with a different gamma, such as your chosen working space, or the display profile used to display the image on the screen or perhaps from one working space to another, or perhaps from your working space to your printer's color space. `Libraw <https://www.libraw.org/>`_ outputs a 16-bit image with a linear gamma, which means that a histogram of the resulting image file shows the actual amount of light that each pixel on the camera sensor captured during the exposure (paraphrasing this page). (Which is why at present applying a camera profile to the Libraw output also requires applying an appropriate gamma transform to get to the desired working space, unless the camera profile also uses gamma=1.)

One practical consequence of the gamma of a working space is that the higher the gamma, the more discrete tones are available for editing in the shadows, with consequently fewer tones available in the highlights. Changing the gamma of an image redistributes the number of tones available in the lighter and darker areas of an image. Theoretically, if you are working on a very dark-toned (low key) image you might want a working space with a higher gamma. And if you are working on a high key image, say a picture taken in full noon sunlight of a wedding dress with snow as a backdrop, you might want to choose a working space with a lower gamma, so you have more available tonal gradations in the highlights.

Theory aside, in the real world of real image editing, almost everyone uses working spaces with either a gamma of either 1.8 or 2.2. sRGB and L*-RGB are two notable exceptions.

sRGB uses a transfer function close to that of a CRT (and thus not necessarily relevant to image editing or to display on an LCD). Unlike most other RGB color spaces the sRGB gamma can not be expressed as a single numerical value. The overall gamma is approximately 2.2, consisting of a linear (gamma 1.0) section near black, and a non-linear section elsewhere involving a 2.4 exponent and a gamma (slope of log output versus log input) changing from 1.0 through about 2.3, which makes for some complicated math during image processing.

L*-RGB uses as its transfer function the same perceptually uniform transfer function as the CIELab color space. *When storing colors in limited precision values* using a perceptually uniform transfer function *can improve the reproduction of tones*.

In addition to gamma=1.8 and gamma=2.2, the only other gamma for a working space that gets much mention or use is linear gamma, or gamma=1.0. As noted above, `Libraw <https://www.libraw.org/>`_ outputs linear gamma files if you ask for 16-bit output. Linear gamma is used in HDR (high dynamic range) imaging and also if one wants to avoid introducing gamma-induced errors into one's regular low dynamic range editing.

**Gamma-induced errors** is a topic outside the scope of this manual but it's commonly-encountered that gamma-induced error that is caused by incorrectly calculating luminance in a nonlinear RGB working space. And in a similar vein, the calculations involved in mixing colors together to produce new colors (such as using a digital filter to add warmth to an image) result in gamma errors unless the new colors are calculated by first transforming all the relevant values back to their linear values.

Unfortunately and despite their undeniable mathematical advantages, linear gamma working spaces have so few tones in the shadows that they are impossible to use for editing if one is working in 8-bit, and still problematic at 16-bit. When the day comes when we are all doing our editing on 32-bit files produced by our HDR cameras on our personal supercomputers, We can predict that we will all be using working spaces with gamma=1.

Tonal Steps and Gamut Size
--------------------------

How many discrete tonal steps are there in a digital image? In an 8-bit image, you have 256 tonal steps from solid black to solid white. In a 16-bit image theoretically you have 65536 steps. But remember, those 16-bit started out as either 10-bit (=1024 steps), 12-bit (=4096 steps), or 14-bit (=16384 steps) as produced by the camera's A-to-D converter - the extra bits to reach 16-bit start out as just padding. The available tones are not distributed evenly from light to dark. In linear gamma mode (as the camera sensor sees things), there's a whole lot more tones in the highlights than in the shadows. Hence the advice, if you shoot RAW, to expose to the right but don't blow the highlights.

One major consideration in choosing a working space is that some working spaces are bigger than others, meaning they cover more of the visible spectrum (and as a consequence include some imaginary colors - mathematical constructs that don't really exist). These bigger spaces offer the advantage of allowing you to keep all the colors captured by your camera and preserved by the `Lcms <https://www.littlecms.com/>`_ conversion from your camera profile to the super-wide-gamut profile connection space and out again to your chosen working space.

But keeping all the possible colors comes at a price, as explained below. And it seems that any given digital image likely only contains a small subset of all the possible visible colors that your camera is capable of capturing. This small subset is easily contained in one of the smaller working spaces.

Using a very large working space means that editing your image (applying curves, increasing saturation, etc.) can easily produce colors that your eventual output device (printer, monitor) simply cannot reproduce (you cannot see these colors while you're editing, either). So the conversion from your working space to your output device space (say your printer) will have to remap the out-of-gamut colors in your edited image, some of which might even be totally imaginary, to your printer color space with its much smaller color gamut.

This remapping process will lead to inaccurate colors and loss of saturation at best. Even worse, the remapping can easily lead to banding (posterization - gaps in what should be a smooth color transition, across an expanse of blue sky) and clipping (e.g. your carefully crafted muted transitions across delicate shades of red, for example, might get remapped to a solid block of dull red after conversion to your printer's color space). Also, the experts say that 8-bit images just don't have enough tones to stretch across a wide gamut working space without banding and loss of saturation, even before conversion to an output space. So if you choose a large gamut working space, make sure you start with a 16-bit image.

.. figure:: images/cm_color_profile_info_dialog.webp
    :width: 300px
    :alt:
    :align: center

    The digiKam Color Profile Properties Dialog Displaying BestRGB Information

To summarize, large gamut working spaces, improperly handled, can lead to lost information on output. Small gamut working spaces can clip information on input. Medium-sized gamut working spaces try to strike a happy medium.

Here are some oft-repeated bits of advice on choosing a working space:

    - For images intended for the web, use (or at least convert the final image to) sRGB.

    - For the most accuracy in your image editing (that is, making the most of your limited *bits* with the least risk of banding or clipping when you convert your image from your working space to an output space), use the smallest working space that includes all the colors in the scene that you photographed, plus a little extra room for those new colors you intentionally produce as you edit.

    - If you are working in 8-bits rather than 16-bits, choose a smaller rather than a larger working space to avoid clipping and banding.

    - For archival purposes, convert your RAW file to a 16-bit TIFF with a large gamut working space to avoid loosing color information. Then convert this archival TIFF to your medium-gamut or large-gamut working space of choice (saving the converted working TIFF under a new name, of course).
