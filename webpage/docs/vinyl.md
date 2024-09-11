# Vinyl Cutting

## Getting an image  
This is an area where you have the utmost creative control.  Want to grab an image from somewhere of your favorite show/brand/game/team etc? Go for it.  Want to freehand something in Illustrator/inkscape/gimp?  Have at it.  The only rules are that you want it to be black and white and that you'll want a solid white boarder around the bounds of your image in order to have somewhere for the knife to cut.  If a black portion of your image extends all the way to the boundary then you'll find that edge missing from your toolpath.  Certainly not the end of the world  if you spot it before you start peeling as you can always freehand with some scissors or a knife but it doesn't take much to fix and make the machine do the work for you.

## Running the machine  
We'll use the windows machine attached to the cutter to run everything this year.  The password to this machine (and most in our shop) is "eds"  Go ahead and open Google Chrome (must be a cromium derrived brower to enable web USB support) and go to mods.cba.mit.edu  Mods is a program originally written by Neil, now receiving community support, whose goal is to replace many proprietary machine control programs with some opensource javascript based alternatives.  Now right click and go to programs->open program->Roland->GX-GS 24 Vinyl cutters->cut.  You should see a colorful block based gui that can be a little hard to swallow at first but generally flows from left to right and top to bottom with only a few areas for you to mess with along the way.  

### Load an Image
First let's get our image into mods and ready for parsing.  I'm starting with a png of a smiley face because it was free use and we can talk about pixels.  This is an png so we'll load it into the png box and if you look at the bottom you'll see some important info.  The image defaulted to a DPI (dots per inch) of nearly 72.  At this resolution the image has a size of ~28x28" which is too large to fit into our machine and we might not see the smoothest toolpaths given the relatively poor resolution.  There's also some weird background junk going on that is large enough to be cut at this scale.  If we increase the resolution to a more respectable 500 DPI the image will shrink to a more manageable 4"x4", the background noise is small enough that it disappears from our toolpaths, and we'll get much nicer curves and finer detail.

### Calculate the toolpaths
Mods takes the tool size as an input parameter then it is going to look at the boundary between white and black pixels, offset by the tool radius, and generate a toolpath to cut out your exact input.  If it is your first time hitting the button the toolpaths should automatically open in another tab for your viewing pleasure/confirmation otherwise you might need to hit the "view toolpaths" button.  It's worth a good 30-60 seconds of verification to make sure all the elements are there and seem to be of an appropriate resolution otherwise you might need to do some touchup by hand.

### Connecting to the machine  
Mods uses web USB so we'll need to tell it which device it should send the files to.  We do this with the menu labeled WebUSB by clicking get device and choosing the GS-24 in the corresponding pop-up.  After doing so you might dump the toolpaths from the cache so you may need to hit the calculate button again before you can continue.

### Setting up the physical machine
load the material
eyes
rollers
origin
force

### Send the file



<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-YT7Z6VQ5M4"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-YT7Z6VQ5M4');
</script>