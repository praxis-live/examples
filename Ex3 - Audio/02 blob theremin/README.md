blob theremin
----------------

A simple blob tracking example.  This relies on access to a webcam. 
The video patch removes the background, and thresholds and blurs the 
image before passing to the blob tracker. 

**MAKE SURE TO GIVE THE PATCH 10s TO ADJUST TO THE BACKGROUND BEFORE MOVING!**

The position and width of the blob is sent to the audio patch to create 
a simple theremin effect.  Note the use of `core:timing:animator` to smooth 
out the incoming signals.
