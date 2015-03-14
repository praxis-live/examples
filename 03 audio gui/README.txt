03 audio gui
------------------
A script that demonstrates Praxis' audio playback as well as a GUI control panel.  
Try triggering sounds with the buttons, altering the filter on the drumbeat with 
the XY pad, and controlling gain and distortion with the sliders.

Open audio.pxr to play with the audio graph, or gui.pxr to edit the control panel.
Notice how the GUI editor hijacks the control panel from its separate window.
Switch on the `edit` overlay to modify the GUI.

NB. the audio won't stop when you close the control panel, you also need to stop
the audio root in the Hub Manager, or restart the hub completely.

Speaking of graphical interfaces, try opening the Terminal from the Tools menu.
While the audio patch is running type 

/audio/filter.frequency

into the terminal, and click `Run`.  The filter component will respond with its
frequency setting.  Now try 

/audio/filter.frequency 2000

and notice the sound change, and the control panel sync to the new value. 
This is the basic message scheme used throughout the Praxis environment.
