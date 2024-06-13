Script for compressing images with imageMagick on windows machines
First download from here https://imagemagick.org/script/download.php#windows
To match some of Neil's tutorials make sure to click "install legacy utilities" as you go through the windows.
Make a note of the install location as we will likely want to add it to our path later 

Now there are a couple ways to convert and compress your files.  First it is important to understand what we are trying to do and why.  The tldr is PNG is a pretty format that is kinda bloated and far higher quality than you really need on a webpage.  In order to be nice to both our server and the visitors to your site we'll convert it to a jpeg and do a little compression which will speed up load times, reduce file sizes, and not really impact your file quality.  Neil is a stickler for this as small deltas times ~100 students have big repurcussions.
If you installed the legacy commands his scripts here are super helpful https://academy.cba.mit.edu/classes/computer_design/image.html
If those fail it is probably because you forgot to hit that checkbox while installing but don't worry as there is a perhaps even cooler way to handle this upcoming.
First the new commands for those of you that want individual control:
magick input.png output.jpg    Would convert a given file from png to jpg.
sticking a resize flag in there will change the physical size of the image (many of your phones take images that default to far larger than your laptop screen)  Resize can take either percentages or XX*YY pixel sizes
magick input.png resize 50% output.jpg
finally the quality tag is used to specify the amount of compression to apply to your image.  
A full command might look like:
magick input.png -resize 50% -quality 50% output.jpg

In my quick testing this brought an image from 500KB to 22KB without much issue.

to verify this works we can inspect the sizes of all the files in a directory by using ls -la if you're in a unix friendly command shell.  The output is in bytes.
Now it is important that we don't throw away our efforts by accidentally committing both the compressed and uncompressed files in our repo.  Something like git add * is dangerous here because it will do exactly what you tell it to which is add everything.  There are many workarounds, only add specific files, move uncompressed images to another directory, update your git ignore, I'll leave that up to the discretion of the reader.  My 2 cents is to not delete the original image in case you learn that something in the process broke, you compressed a bit too much, or some other issue popped up.  You may however decide that I am a digital hoarder and you see no need for the original file anymore.  To each their own.

Now with a little extra magic (no k) and .bat files we can make a quick script that runs through a folder, converts and compresses every png, and is callable from anywhere in our system.  For some this may sound daunting but let me remind you that I am technically a mechanical engieer and I figured this out so you certainly can too!
So .bat files are just scripts that we can bundle and call and if we add them to our default path we can do this from anywhere in our system.  A little extra trick is that you can actually call a script right from your file explorer without even opening a terminal!  Kinda nifty.
For me the script looks like:
@ECHO OFF

FOR %%a in (*.png) DO magick %%a -quality 50%% -resize 50%% %%~na_small.jpg


and I saved this as compressAll.bat because I thought the name was appropriate.  You could make some tweaks here if you say normally saved images in another format or wanted to play with compression rates ec.  This is a template for you to have fun with as well as a useful tool.
It is a little annoying with the escaping % characters but what this does is parse the folder, find all png files, resize, compress, and convert them to jpg files and append _small to their file names.  I don't recall why I added that last bit but earlier Anthony thought it was a good idea for some reason.

Now let's make this script callable from anywhere by adding it to your path which is essentially the list of places your computer will look if you try to call a file or command that isn't located where your terminal currently is.  You can kinda think of this as the difference between local and global variables in most languages.\
First lets make a permanent home for this script that is easy to access and has room to make more changes in the future.  I just made a folder in Documents called Scripts.  Short, simple, easy to remember.  The path to this folder is then C:\Users\Anthony\Documents\Scripts.  Some of y'all use things like onedrive or have other kinda funky installs so an easy way to see the file path in the file explorer is to just click in the bar at the top and copy it from there.  Make sure to copy compressAll.bat into this folder.  Now we need to update your path to include this location.
The route to get here is a little convoluted but it isn't too bad.  First open the windows search bar and type path.  The top option should be "edit the system enviornment variables"  Open that and click the "enviornment variables" button in the bottom right.  The second element in the top list should be PATH.  click that and then click edit and a new window will open.  Hit new and paste the folder path into the cell then save and close everything.  Now if you have any terminal instances open you should close them in order for the changes to take effect.

Finally a little bonus on using .gitignore:
Sometimes I like being lazy.  I don't want to deal with remembering what not to git add and just use that nice wildcard to get everything.  That would be a bit of an issue here because my uncompressed images still exist and it would defeat the whole point of this endeavor to compress and convert them if they ended up in the repo anyway.  To fix this we'll leverage the .gitignore file.  This is really designed to not track files with your credentials or API keys etc (which are embarassingly easy to find across public git repos these days)

