# Milling PCBs with the Makera Z1! 

---

Traditionally PCBs are etched.  You start with a composite sheet with copper on one or both sides of it.  Deposit a layer of photo resist which is optically cured above the copper that you want to keep, then immerse the whole board in a vat of acid that etches away the copper that you do not want to keep.  This process is rather hazardous and very water intensive so for quick turn options on campus we choose another method.

Small CNC mills are quickly gaining popularity and while there are many options this guide will focus on the Makera Z1.  This machine is technically capable of milling many/most materials that you would on a larger machine but this particular guide will keep things simple and exclusively focus on a PCB related workflow.  This process is subject to change as our tools improve.

## File conversions
This step has a bit of friction as we need to go from our finished PCB to gcode to run the machine.  The currently available tools don't support this in one step so we will have a short series of tasks in order to make this happen.  
1. Export your PCB into gerbers  
2. Turn the gerbers into an image  
3. Use mods to convert that image into g code for our machine  
4. Setup the machine and start milling!  

## Export your PCB
Gerbers are the typical files that you would give to a board house in order to get your design manufactured.  Because this is so commonly used any PCB creation tool should be able to export designs easily.  Before continuing do ensure that all your polygons are poured and your file is saved.  Unsaved changes will not make it into the resulting gerber files.  This is the source of much frustration.  
![](images/makera/kicad_logo_small.png)  
In Kicad with the PCB design open we're going to head to the top left corner and hit file/Fabrication Outputs/Gerbers  
![](images/makera/fabricationOutputs_small.jpg)  
In the resulting window we are first going to generate our drill files with the button in the lower right.  
![](images/makera/Gerbers_small.jpg)  
We'll want to hit the PTH and NPTH in single file checkbox and ensure that our units are in millimeters then click generate in the lower right corner.   
![](images/makera/drill_small.jpg)  
Now we can close that out and go back to the main Gerber window.  The defaults here will generate some files that we don't need but it isn't a big deal so we can just keep all the defaults and hit the plot button at the bottom of the window.  
![](images/makera/Plot_small.jpg)  
The resulting files will end up in whatever location you have your PCB saves.  If you're unsure you can expand the section that says "Output Messages" and see the file path listed there.  

![](images/makera/fusionLogo_small.jpg)  
Fusion will have a very similar process:  First again remember to save your most recent file.  In the top toolbar hit the manufacturing tab then this button with the crazy long name.  
![](images/makera/fusionGerber_small.jpg)  
This will auto export a zip file of all the default gerber files which will contain everything we need.  Crucially this is a .zip file which is usually what a normal PCB vendor would want but you'll need to extract it before grabbing the contents for our tools.  The file path is also kinda ridiculous.  Most of the files you need will end up in the CAMOutputs/Gerbers subfolder but if you have any holes in your board then you will also need the file in the CAMOutputs/DrillFiles subfolder.  To keep things easy later go ahead and grab the drill file and drag it into the Gerbers folder with the rest of the files.

## Convert gerbers into images
Now that we have gerber files ready we'll want to convert them into PNGs.  In order to make this easy we're going to use Quentin's sweet [Gerber2Img converter.](https://quentinbolsee.pages.cba.mit.edu/gerber2img/)  As the gerber files are different dimensions the order of operations here is important!  Failure to follow these steps will cause your traces/outline/holes to be misaligned.  

First we will grab both the board outline and the holes files.  
In Kicad the board outline file will have -Edge_Cuts.gbr as the end of the file name and the holes file will have the .drl file extension.  Select both of those files together and drag them into the the window on Quentin's tool.  

In Fusion the board outline file is in the CAMOutputs/Gerbers folder and called profile.gbr and the drill file is called drill_1_16_xln. Select both of those files together, which is why we moved the drill file into the same folder earlier, and drag them into the the window on Quentin's tool.  

Check the Black and white checkbox and ensure you lock both the origin and Dimensions after loading these files.  Then press Download render in the bottom left.  I suggest naming this file after your design and noting that it is the outline.  Something like test_outline.png but really it is up to you.  
![](images/makera/QuentinOutlineHoles_small.jpg)  

Now without refreshing the page we'll take the top copper layer which has all your traces and pads and make an image for that too.  In KiCad that file will have the suffix -F_Cu while in Fusion that file will just be called copper_top.gbr.  Moving that file in should give you a window that looks something like this:
![](images/makera/QuentinTraces_small.jpg)  
Go ahead and download this file as well and name it something like test_traces.png so you remember which one is which.  If your board is double sided then repeat this process with the -B_Cu file for KiCad or the copper_bottom.gbr for Fusion.


# WIP needs MODS and machine workflow once they are sorted.





<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-YT7Z6VQ5M4"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-YT7Z6VQ5M4');
</script>