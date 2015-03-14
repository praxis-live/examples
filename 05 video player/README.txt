05 video player
------------------

A project to demonstrate how to get video file into a praxis patch. 
This function relies on the GStreamer library, so you must have this 
installed already on your system, or on Windows you can install the 
GStreamer plugin from the Praxis downloads page.

No video file is included, so you will have to have a video file to 
hand. After running the project, use the 'Video File' field in the 
control panel to open a filebrowser and select the video, and then 
press 'Play' (once it has loaded). You can also use the 'Position' 
slider to scrub through the video file - the smoothness of this 
depends on the video codec in use (and with some codecs it plain 
doesn't work!)

NB. There isn't audio support for videos at the moment - it is 
planned but not a high priority for my uses - if anyone asks for it, 
it might get nearer the top of the pile! :-)

This project puts the video source through a code component to 
composite 2 animated rectangles over the top, just to make it a little 
more interesting!
