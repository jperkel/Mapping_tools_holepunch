# Mapping-tools-examples

  <!-- badges: start -->
  [![Launch Rstudio Binder](http://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/jperkel/Mapping_tools_holepunch/master?urlpath=rstudio)
  <!-- badges: end -->

This Binder-capable repo was built using [holepunch](https://github.com/karthik/holepunch), Karthik Ram's tool for creating Docker containers for R projects. Thanks to a tip from [Tim Head](https://twitter.com/betatim), I was able to update the Dockerfile to run the postBuild file during Docker creation. Once RStudio launches, open either of the two RMarkdown files, and select 'Run > Run All' to execute the code. ~~Since `holepunch` doesn't execute the instructions contained in the `postBuild` file, you have to run them manually. After clicking 'Launch Binder' (it may take a while to start!), open the 'Terminal' window at the left of the RStudio interface. Type `./postBuild` to load the necessary data files. Then, open either of the two RMarkdown files, and select 'Run > Run All' to execute the code.~~

Simple examples of mapping in R, created for a Nature Toolbox article by Jeffrey Perkel, published 5 June 2018. [https://www.nature.com/articles/d41586-018-05331-6]

Click the 'Launch Binder' button above to launch an interactive RStudio session in the cloud, in which you can explore and execute two RMarkdown notebooks. (Executable versions of these examples also are available on [Code Ocean](https://codeocean.com/capsule/4725205/tree/v1) and [Nextjournal](https://nextjournal.com/jperkel/mapping-examples-in-nextjournal).)

The JSON files in this directory were created using the Ogre ogr2ogr web app (https://ogre.adc4gis.com/), using Shape files from [al112017_5day_020.zip](https://www.nhc.noaa.gov/gis/forecast/archive/al112017_5day_020.zip).

Live versions of these documents are also available at:  
https://rpubs.com/j_perkel/London  
https://rpubs.com/j_perkel/irma_map  

Thanks to Anthony Gitter ([@anthonygitter](https://twitter.com/anthonygitter)) for help getting the Binder implementation to work.
