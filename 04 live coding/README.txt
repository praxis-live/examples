04 live coding
----------------------------------
Praxis has an embedded compiler for adding Java snippets to the graph 
'on the fly'.  Run this project and open the video.pxr file into the 
editor.  You'll notice there are two code components that are composited 
together - the background one is running a simple particle system 
(derived from [1]), and the foreground one is just a simple animated circle.

To view the code you can select one of the code components in the graph,
and click on the button next to the code property in the Properties tab. 
A window will open with the code.  Any edits you make will be immediately 
reflected in the video window - if you make any mistakes the code will just 
revert to what it was previously set to.  

The Praxis live coding API should be familiar to anyone who has used 
Processing.  Praxis provides a subset of the Processing API, although the 
graphics elements are re-implemented on the Praxis video pipeline.  There 
are also two additional features that the Praxis environment provides - 
animatable parameters and additional blend modes.  Documentation of the full 
range of features will be added to Praxis' Google Code site soon.  Live 
coding components are video:code:composite for graphical programming, and 
core:code:custom for working with control signals.

NB.  There is nothing to stop you writing "System.exit();" or "while(true){}"
in the code window - my advice is don't! :-)

If coding isn't your thing, this is also a good patch to experiment with the 
settings of the composite component.  Highlight the composite component and 
see the effects of the different blend modes, force-alpha, etc.


[1] Noisy by jordan bilich, licensed under Creative Commons Attribution-Share 
Alike 3.0 and GNU GPL license. Work: http://openprocessing.org/visuals/?visualID=2922
License: http://creativecommons.org/licenses/by-sa/3.0/
http://creativecommons.org/licenses/GPL/2.0/
