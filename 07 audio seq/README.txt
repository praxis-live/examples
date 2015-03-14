07 audio seq
-----------------

A project to demonstrate some of the new components in the June 2012 
release.  Praxis is not really aimed at sequencing music, but this 
project provides a simple drum machine and bass line with changing FX, 
as well as a visualization of the sound.

The core:routing:gate component is used to create simple trigger 
patterns (including some randomness).

The bassline is passed through an audio:modulation:chorus effect, and 
all the audio is passed through an audio:reverb:freeverb  

Two audio:analysis:level components are used to pass the level of the 
bass and drums to the video patch.
