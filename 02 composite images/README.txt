02 Composite Images
------------------------

This is a more complex patch derived from a random slideshow that uses a 
variety of different composite modes to superimpose new image on old. 
This particular process has been used in a number of previous works of 
mine, in various guises (including in the Magoria project). 

Open up video.pxr to see the graph - feel free to tweak the patch and use
your own images with it.

This example was converted from a .PXS script. A commented version of that
script is included below for info.






@ /video root:video {
      # If you change the images you're working with (see below), you may
      # want to change the output width and height to match. The example
      # images are low resolution to save space.
      #
      # You may also want to comment out the full-screen line to take over
      # the screen. Make sure you know how to close a window from the
      # keyboard before you try this though! Often Alt-F4.
      # 
      .width 400
      .height 300
      .fps 20
      # /video.full-screen true

      @ ./screen video:output
      
      @ ./image video:still
      
      # Images are chosen at random from images directory. Change the
      # directory here, or replace the images in the directory with your
      # own to use this patch with your own images.
      @ ./files core:array:random {
            .values [file-list [file "images"]]
      }
            
      @ ./snap video:snapshot {
        .fade-time 4.5
      }
      
      # Composite component for mixing new image with previous frame
      # previous frame will be used as destination (background), new 
      # image as source (foreground).
      @ ./composite video:mix:composite   
      
      # Component to split video signal so that we can send it to 
      # screen and feed it back to composite.
      @ ./splitter video:splitter
      
      # Component to generate a random number between 0.35 and
      # 0.6 (0.35 + 0.25), giving us a composite mix between 
      # 35% and 60%. These are good numbers to tweak!
      @ ./mix-amount core:math:random {
            .minimum 0.35
            .range 0.25
      }
      
      # Component to generate a random composite mode to use. Possible
      # values are randomly picked from an array.
      #
      # Notice the duplication of Normal and Difference - this makes these
      # twice as likely to be chosen. This is a simple way of controlling
      # proportionality of certain outputs.
      @ ./compose-type core:array:random {
        .values [array Normal Normal Add Sub Multiply BitXor Difference Difference]
      }

            
      # A timer to control all changes of image
      @ ./timer core:timing:timer {
        .period 7
      }
      
      # Video connections, working back from screen can make it
      # easier to visualise the path of connections
      ~ ./splitter!out-1 ./screen!in
      ~ ./splitter!out-2 ./composite!in
      ~ ./snap!out ./splitter!in
      ~ ./composite!out ./snap!in
      ~ ./image!out ./composite!src

      # Connect timer to set random mix amount, random composite
      # mode and random image
      ~ ./timer!out ./mix-amount!trigger
      ~ ./mix-amount!out ./snap!mix
      
      ~ ./timer!out ./files!trigger
      ~ ./files!out ./image!uri
      
      ~ ./timer!out ./compose-type!trigger
      ~ ./compose-type!out ./composite!mode

      # Connect image ready port to trigger snapshot, and error
      # to trigger a new file to load.
      ~ ./image!ready ./snap!trigger
      ~ ./image!error ./files!trigger

}

# Start our patch running
/video.start

