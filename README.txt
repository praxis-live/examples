Praxis LIVE Early Access examples.
==================================

This folder contains some simple example projects for Praxis, which should give you a basic introduction to Praxis and Praxis LIVE.  These projects can be opened in the Projects tab in Praxis LIVE.  Once the project is open, right click on the project and select `Run` to run it.

NB. Closing a window will not remove the project components from the Praxis hub - you can see the various root components within the Hub Manager tab at the bottom left.  Make sure to use the `Restart Hub` action or `Clear All` from the project menu before running other examples - this will be the most likely reason a project will appear not to run (it is possible to run multiple projects at once, as long as they don't try to create components with the same address, but it's better to ignore this for now!).  If you want to restart a window that you've closed, you can also use the Hub Manager for this - double-click on the component to start or stop.

With all of these projects, you can open the .pxr files into the graphical editor and play around with them as they run.  Highlight a component to change its properties (or click the background to change the properties of the root component).  Drag components from the palette to add them to the graph, drag to connect ports together, or right-click and select `delete` to remove any highlighted components or connections.  Hover over the top tabs of a component to find out its type (as shown in the palette), or connections to find out where they go.  Ctrl-mousewheel to zoom in and out, or navigate using the satellite view at the bottom right.

In addition to the simple tutorial examples, there are two example projects based on projects I use Praxis for. The first is a simplified version of Magoria, a generative image work created for Faces of Oxfordshire and on permanent display in Oxfordshire Museum (UK).  You might want to try running this before looking through the other examples.  The original script has been converted to a .pxr file, so you can open this and see the graph of all the components.

The second example project is the patch I use for performing Radio Access Memory (RAM) - it's a live audio sampler with control panel and MIDI control.  This project has not yet been converted from the original script file.



EXAMPLES
========

01 hello world
-----------------------
A simple patch which runs white noise through a mask image to spell out "Hello World" (well, there had to be one! :-) ).  Open up video.pxr to see the graph.



02 composite images
----------------------------
This is a more complex patch derived from a random slideshow that uses a variety of different composite modes to superimpose new image on old. This particular process has been used in a number of previous works of mine, in various guises (including in Magoria below). Open up video.pxr to see the graph - feel free to tweak the patch and use your own images with it.



03 audio gui
------------------
A script that demonstrates Praxis' audio playback as well as a GUI control panel.  Try triggering sounds with the buttons, altering the filter on the drumbeat with the XY pad, and controlling gain and distortion with the sliders.

Open audio.pxr to play with the audio graph, or gui.pxr to edit the control panel.  Notice how the GUI editor hijacks the control panel from its separate window.  Switch on the `edit` overlay to modify the GUI.

NB. the audio won't stop when you close the control panel, you also need to stop the audio root in the Hub Manager, or restart the hub completely.

Speaking of graphical interfaces, try opening the Terminal from the Tools menu.  While the audio patch is running type 

/audio/filter.frequency

into the terminal, and click `Run`.  The filter component will respond with its frequency setting.  Now try 

/audio/filter.frequency 2000

and notice the sound change, and the control panel sync to the new value.  This is the basic message scheme used throughout the Praxis environment.



04 live coding
----------------------------------
Praxis has an embedded compiler for adding Java snippets to the graph 'on the fly'.  Run this project and open the video.pxr file into the editor.  You'll notice there are two code components that are composited together - the background one is running a simple particle system (derived from [1]), and the foreground one is just a simple animated circle.

To view the code you can select one of the code components in the graph, and click on the button next to the code property in the Properties tab.  A window will open with the code.  Any edits you make will be immediately reflected in the video window - if you make any mistakes the code will just revert to what it was previously set to.  

The Praxis live coding API should be familiar to anyone who has used Processing.  Praxis provides a subset of the Processing API, although the graphics elements are re-implemented on the Praxis video pipeline.  There are also two additional features that the Praxis environment provides - animatable parameters and additional blend modes.  Documentation of the full range of features will be added to Praxis' Google Code site soon.  Live coding components are video:code:composite for graphical programming, and core:code:custom for working with control signals.

NB.  There is nothing to stop you writing "System.exit();" or "while(true){}" in the code window - my advice is don't! :-)

If coding isn't your thing, this is also a good patch to experiment with the settings of the composite component.  Highlight the composite component and see the effects of the different blend modes, force-alpha, etc.



05 video player & 06 video input
------------------------------------------------

These two projects demonstrate how to get video into a praxis patch. This function relies on the GStreamer library, so you must have this installed already on your system. The playback project should work on any platform with GStreamer. No video file is included, so you will have to have a video file to hand. After running the project, use the 'Video File' field in the control panel to open a filebrowser and select the video, and then press 'Play' (once it has loaded). You can also use the 'Position' slider to scrub through the video file - the smoothness of this depends on the video codec in use (and with some codecs it plain doesn't work!)

NB. There isn't audio support for videos at the moment - it is planned but not a high priority for my uses - if anyone asks for it, it might get nearer the top of the pile! :-)

Both of these projects put the video source through a code component to composite 2 animated rectangles over the top, just to make it a little more interesting!


07 audio seq
-----------------

A project to demonstrate some of the new components in the June 2012 release.  Praxis is not really aimed at sequencing music, but this project provides a simple drum machine and bass line with changing FX, as well as a visualization of the sound.

The core:routing:gate component is used to create simple trigger patterns (including some randomness).
The bassline is passed through an audio:modulation:chorus effect, and all the audio is passed through an audio:reverb:freeverb
Two audio:analysis:level components are used to pass the level of the bass and drums to the video patch.


08 blobs
------------

A simple blob tracking example.  This relies on access to a webcam.  The video patch removes the background, and thresholds and blurs the image before passing to the blob tracker.  MAKE SURE TO GIVE THE PATCH 10s TO ADJUST TO THE BACKGROUND BEFORE MOVING!

The position and width of the blob is sent to the audio patch to create a simple theremin effect.  Note the use of core:timing:animator to smooth out the incoming signals.


09 GLSL
----------

An example of the video:opengl:filter component.  A webcam image is passed through a continually changing colour mixer.  

This example requires use of the OpenGL pipeline.  Switch this on in the video section of the options window (Tools / Options).  NB.  This pipeline is still fairly experimental!

The GLSL fragment shader can be edited live.  Note how the shader can make use of the parameters on the component.




[1] Noisy by jordan bilich, licensed under Creative Commons Attribution-Share Alike 3.0 and GNU GPL license.
Work: http://openprocessing.org/visuals/?visualID=2922
License: http://creativecommons.org/licenses/by-sa/3.0/ http://creativecommons.org/licenses/GPL/2.0/



