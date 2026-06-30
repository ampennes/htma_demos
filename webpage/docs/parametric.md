# Parametric design

## CAD packages

## Design ethos

## Evolving Design Documents
As you build you will encounter many patterns.  When you need a hole for an M3 bolt on a 3D print the traditional approach would be looking up the corresponding hole size, printing a test, adjusting that fit because printers dont give you true to dimension features and iterating until you have an acceptable size that both isn't too tight that you cannot cut threads while not being so loose that it can pull out.  This really doesn't take long but it is work that is repeated endlessly.  A slightly better approach often involves opening the CAD for the last project that you had that feature in, finding the actual up to date version, and getting the hole dimension.  This definitely works but is tedious.  Imagine a world where you just had a single spreadsheet in which you kept track of all the useful parameters like this that you have determined in your engineering journey.  This could be an excel sheet that you open and browse through, preferable stored somewhere that is available on more than one machine, this would even let you embed little diagrams to call out specific features if the naming gets too clunky.  Most CAD programs support importing a csv or json file with these associated parameters so your workflow could now be, open a new part, import a fresh copy of your personal design table, call out a properly toleranced hole for an M3 bolt on a bambu x1 carbon by simply typing in the parameter name "M3_hole_tap_Bambu_X1" and skipping the entire search process.  Certainly machine calibration isn't exactly identical across campus and may drift over time but you'll be much closer than with most other methods in a fraction of the time.  Building this document as you go can feel a little clunky but it will save you many hours, much frustration, and lots of scrapped building materials over the years.
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-YT7Z6VQ5M4"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-YT7Z6VQ5M4');
</script>