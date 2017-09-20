Title: faq
Slug: about/faq
Date: 2017-09-20T16:18:43-06:00 
author: smn
link: http://www.darktable.org/about/faq/
wordpress_id: 1536

![](http://www.darktable.org/wp-content/uploads/2012/01/darktable-v2.png)

* **What's the best way to contact the developers/report bugs?**

    For fast discussions and short questions it's best to visit us in IRC (on Freenode, channel #darktable), especially in the Western European evening hours. If you don't want to use IRC, don't know what it is or want something less transient you can use our mailing lists. See our [contact page](http://www.darktable.org/contact/).

* **How do I move/rename/... files on my hard disk?**

    Use your file manager (or the command line). You already know how to do that. We have image editing code to write so we don't spend time to rewrite a file manager.

* **Will you add file manager capabilities in the future?**

    No.

* **Pretty please?**

    No.

* **How do I change the order in which modules are applied to an image?**

    You don't. The order of the processing pixel pipeline is fixed and supposed to "just work". If you have a (valid) use case where the order doesn't work feel free to tell us. And if you really want to know the reason why this is fixed you may want to have a look at the output SVG of `tools/iop_dependencies.py`

* **Modules? What modules?**

    See the section below about the manual, book and tutorial videos.

* **About that file manager...**

    No.

* **What about a Windows port?**

    Please refer to [this blog post](http://www.darktable.org/2015/07/why-dont-you-provide-a-windows-build/) for a detailed explanation of the status of Windows builds.

* **darktable crashes with SIGILL. What's up?**

    Due to the large number of mathematically intense operations which the Image Operators (IOPs) perform, the minimum requirement for a CPU to run Darktable is one which supports SSE2. If your cpu does not support SSE2 more than ten years after the feature's introducion, then it really is time for you to upgrade. Please see [the Wikipedia page](http://en.wikipedia.org/wiki/SSE2) for more details on SSE2-capable CPUs.

* **How do I open images? I only see a white canvas.**

    You have to import a single image or a film roll (directory) using the buttons on the left side of the lighttable.

* **Ok, I imported some images, but I still don't see anything, though after importing a single image it is shown in darkroom mode.**

    Try to set the display filter in the top panel to "all" and check the "initial rating when importing filmrolls" setting in the preference pane (the small gear wheel at the top).

* **How do I save my changes?**

    You don't have to. Everything you do is immediately stored on disk. You can just quit darktable and go on editing later. Once you are done you have to _export_ your final image (while in lighttable mode) using the export module.

* **What happened to the demosaic module in darkroom? How can I select more demosaicing algorithms?**

    We moved the demosaicing into our internal pixel pipeline. The benefit is that it is faster and more accurate. The downside is that we have to implement the demosaicing algorithms ourselves. Since the differences are really small with real world photos we didn't bother to port more than PPG and AMaZE. If anyone feels the need for more choice we will gladly accept patches.

* **This confuses me. Is there a manual?**

    Yes, [here](http://www.darktable.org/usermanual/index.html.php). There is also [a book](http://www.darktable.org/resources/#book) in finished PDF format or .zip file containing the Open Document source and image files.Pascal has created some [screencast tutorials](http://www.darktable.org/resources/#screencasts) that cover many fundamental use cases and descriptions of technical expressions.

* **My auto-applied presets aren't enabled for pictures imported before upgrade to version 1.1 (or higher), what's happening?**

    This is intended. In pre-1.1 era enabled by default modules didn't get recorded in history stack, which meant that changing these presets would retroactively change your pictures. It was decided that this is totally broken behaviour and since darktable version 1.1 auto-enabled modules for newly imported pictures are saved in history stack. However this change left all old photos without any user-defined auto-applied presets enabled. To fix this you will have to manually edit them. I suggest making a style out of preset, filtering photos to which it should apply using collect module, then selecting all in resulting collection and applying the style, repeat for every needed preset.

* **I attached and turned on my camera, but it doesn't show up in darktable, what's wrong?**

    If the camera in question is supported by libgphoto2, then the most likely cause is that some other process is blocking the device. If you're using Linux, check that your desktop environment hasn't auto-mounted it. In case of OS X, there's PTPCamera daemon which starts for every attached camera, so you must kill it before you can use the camera in darktable. Either run "killall PTPCamera" or implement more automated solution like described at the bottom of this page: [http://valelab.ucsf.edu/~MM/MMwiki/index.php/GPhoto](http://valelab.ucsf.edu/~MM/MMwiki/index.php/GPhoto).