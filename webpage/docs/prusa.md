# Prusa Slicer Tutorial

***

[Prusa slicer](https://www.prusa3d.com/p/prusaslicer/) is the slicer that we use in order to control the array of Prusa machine thatwe have in the shop.  I find this strikes the best balance between ease of use and full control of complex features.  This tutorial will start with some simple parts and then progress to more advanced features that may become useful to you as you start making mroe specialized things.  A more general overview of 3D printing in general with fewer machine specifics can be found [here](3Dprinting.md)

The slicer itself looks like this:  
![](images/prusa/slicer_small.jpg)
There is kinda a lot going on here so we'll just start with the minium required steps to get a file printed and expand from there.  
## Importing a file
First import your stl or 3mf (or similar format) object using the file/import option in the top left or the hotkey control+i.  The file will generall be imported in whatever orientation you designed it in which may or may not be best suited for this manufacturing method.  In my case I'm printing a little hook that came in like this:  
![](images/prusa/hook_small.jpg)  
## Part Orientation  
In order to pick the proper orientation of our part we need to consider how a 3D printer actually functions.  Your part is more or less made layer by layer by squirting out molten plastic from something not that far off from a hot glue gun.  This means that the quality of layer N is incredibly dependent on the contents of the previous N-1 layers.  In this orientation most of the part will be well supported by the material beneath it until we get to the tip of the hook which might get a little dicey.  If we got to the slice preview by clicking the stacked sheets in the lower left corner here:  
![](images/prusa/sliceButton_small.jpg)  
Then after a few moments depending on how complicated your part is we'll transition to a view that looks like this:  
![](images/prusa/sliceView_small.jpg)  
Here I always do two tasks before proceeding with my job.  First I take the slider on the top right hand side and drag it all the way down to the bottom.  This will allow us to see what the first, and most crucial, layer of our part will look like:
![](images/prusa/layer0_small.jpg)  
We care a lot here about the surface area of this layer.  If it is too small then your part will likely break free from the bed while printing causing the job to fail.  Frequently parts will be imported at a slight angle such that a small sliver of your part is touching the bed.  If you see something that looks like this:  
![](images/prusa/badLayer0_small.jpg)  
then your job will almost certainly fail and you will need to adjust the part orientation before continuing.  We can do this adjustment using two tools.  First click the body you are trying to adjust, which should cause it to turn green, then choose either the upper rotate or the lower "place on face" tool.  
![](images/prusa/rotate_small.jpg)  
Generally the place on face tool is much easier and will work well in 99% of situations.  Once selected your part will highlight many white flat shapes.  
![](images/prusa/placeOnFace1_small.jpg)  
Clicking one will automatically snap it down to the surface of the bed.  This can be more straightforward than the rotate tool as you won't need to find whether something is at a 36.5 degree angle or something weird like that. Rotating the screen to view the bottom of the part and selecting the large shape there will snap it flat to the bed and ensure we get the best adhesion possible.   
![](images/prusa/placeOnFace2_small.jpg)  
When printing more advanced parts we may also want to think about filament direction in addition to adhesion but we'll cover that further down the page when it becomes relevant.  
The second thing that I do before advancing form this step is to just scroll through the layers from the bottom up looking for things that seem poorly supported.  Prusa will helpfull color this in a dark blue color.  On this model the tip of the hook is worth looking closely at as the subsequent layers might not have a ton of material under them as they are laid down. Dragging to the appropriate angle and switching to a side view:  
![](images/prusa/overhang_small.jpg)  
This actually doesn't look too bad.  There might be a tiny bit of sagging but it isn't on a critical part of the model and might not even be noticable. If we were to make a poor decision and print the hook upside down we would see a bright blue layer and Prusa helpfully calls out a message at the bottom denoting that we might experiece print stability issues as a result of our choice.  
![](images/prusa/upsidedown_small.jpg)  
This print will not survive. Plastic will continue to be extruded over open air and the part will fail unless we add support material which is described further down the page.

## Layer height
In the top right corner of the screen you'll see a box labeled print settings.  This sets how thick each layer of filament is as well as some mechanical properties.  A great default here is 0.2mm BALANCED.  This is small enough that the layer lines won't be super noticeable while also printing quickly.  For a finished prototype you could reduce the layer height to make it "prettier" while for a rough draft that you want done as fast as possible you could consider increasing the layer height.  In general nearly every part is ok to print at 0.2mm.  If you want to get better detail there is an adaptive layer height that will prove more useful than changing it as a gloab variable here.  We will cover that tool further down the page. I note this because the scaling is very linear.  If your part takes 8 hours to print at 0.2mm it will take ~16 hours to print at 0.1mm without playing some tricks to speed it up.  This can get very lengthy and we should strive to treat our lab mates with respect by not hogging a printer for an extended job when it isn't necessary.

## Filament  
The vast majority of jobs in our space will be printed in PLA.  This is a standard filament that is relatively strong, looks pretty good, and prints very quickly.  We also stock PETG which prints more slowly but has some better mechanical properties compared to PLA.  The slower print time usually causes a "prototype in PLA then transition to PETG for final models" approach for items that will be under heavy load or will be used outside in high UV enviornments.  Occasionally we will have TPU stock for flexible components and while a little annoying to get started this usually prints relatively well.

## Supports  
Supports can be enabled here:  
![](images/prusa/supports_small.jpg)  
But they should be avoided whenever possible.  Their job is to add extra plastic to ensure that we don't have unsupported overhangs.  They are useful when printing funky or very organic objects but fundamentally they make your job take longer and their job ends as soon as the print is complete so they become trash.  If we really needed to print the hook upsidedown for some reason supports like this might be enough to get the job to survive.  
![](images/prusa/support_upsidedown_small.jpg)  
This causes the job to jump from 19 minutes to 32 minutes which is a very hefty increase that we could avoid simply by changing our part orientation. If you do need supports choosing the option "on build plate only" will prevent supports from being generated on top of your model which will make them easier to remove.  I am also a fan of organic supports.  To enable them head to prints settings/support material/style and set it to organic.  
![](images/prusa/supportSettings_small.jpg)    
This will then generate supports that kinda look like an alien tree eating your part.  These tend to be much easier to remove than the traditional snug option.  
![](images/prusa/organicSupports_small.jpg)  


## Infill

## Brim











![](images/prusa/file.jpg)

<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-YT7Z6VQ5M4"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-YT7Z6VQ5M4');
</script>