# Mapping-tools-examples

  <!-- badges: start -->
  [![Launch Rstudio Binder](http://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/jperkel/Mapping_tools_holepunch/master?urlpath=rstudio)
  <!-- badges: end -->

Simple examples of mapping in R, created for a [Nature Toolbox](https://www.nature.com/articles/d41586-018-05331-6) article by Jeffrey Perkel, published 5 June 2018. Click the 'Launch Binder' button above to launch an interactive RStudio session in the cloud, in which you can explore and execute two RMarkdown notebooks. 

This Binder-capable repo was built using [holepunch](https://github.com/karthik/holepunch), Karthik Ram's tool for creating Docker containers for R projects. ~~Since `holepunch` doesn't execute the instructions contained in the `postBuild` file, you have to run them manually. After clicking 'Launch Binder' (it may take a while to start!), open the 'Terminal' window at the left of the RStudio interface. Type `./postBuild` to load the necessary data files. Then, open either of the two RMarkdown files, and select 'Run > Run All' to execute the code.~~ ETA: Thanks to a tip from [Tim Head](https://twitter.com/betatim), I was able to update the `Dockerfile` to execute `postBuild` during Docker creation. Once RStudio launches, open either of the two RMarkdown files, and select 'Run > Run All' to execute the code. 

Executable versions of these examples also are available on [Code Ocean](https://codeocean.com/capsule/4725205/tree/v1), [Nextjournal](https://nextjournal.com/jperkel/mapping-examples-in-nextjournal), and [Gigantum](https://gigantum.com/tinydav/mapping-tools-examples-rough-cut). Static versions of these documents are available on RPubs: [London](https://rpubs.com/j_perkel/London) and [irma_map](https://rpubs.com/j_perkel/irma_map).

Anthony Gitter ([@anthonygitter](https://twitter.com/anthonygitter)) helped get the Binder implementation to work, while Seth Green ([@setgree](https://twitter.com/setgree)) helped with the Code Ocean compute capsule and the tech support team at Nextjournal assisted on their platform. Special thanks to Dav Clark ([@davclark](https://twitter.com/davclark)) at Gigantum for building the Gigantum environment on his own.

The JSON files in this directory were created using the Ogre ogr2ogr web app (https://ogre.adc4gis.com/), using Shape files from [al112017_5day_020.zip](https://www.nhc.noaa.gov/gis/forecast/archive/al112017_5day_020.zip).

## Instructions for creating a local Docker container from this GitHub repo
1. Install [Docker](https://www.docker.com). 

2. In a terminal window, create a new directory called ‘maptools’ (e.g., `mkdir maptools`), navigate to that directory (`cd maptools`), and download the `Mapping_tools_holepunch` Dockerfile from GitHub by executing the following command: 
```
curl https://raw.githubusercontent.com/jperkel/Mapping_tools_holepunch/master/.binder/Dockerfile -o Dockerfile
```

3. The last line of the Dockerfile directs Binder to download key files by executing the commands in a file called `postBuild`; as we are not using Binder, we will have to perform that step manually (see step 8). Open the Dockerfile in a plaintext editor (not a word processor!), such as TextEdit (Mac) or Notepad (Windows). Delete the final instruction (`RUN ./postBuild`) and save the file.

4. Build the Docker image, which we will call 'maptools'. Note the period at the end of the command: 
```
docker build -t maptools .
```

5. Launch the container. The username and password can be anything you like:
```
docker run -d -p 8787:8787 -e USER=username -e PASSWORD=password maptools /usr/lib/rstudio-server/bin/rserver
```

6. Launch RStudio in your browser with the address: `localhost:8787`. Note that RStudio need not be installed on your computer, it is present within the container.

7. Our container represents a computational environment. Now we must import the code we want to run within it. Select the Terminal tab in the left-hand RStudio pane and execute: 
```
git clone https://github.com/jperkel/Mapping_tools_holepunch.git
```

8. Switch to the newly created `Mapping_tools_holepunch` directory (`cd Mapping_tools_holepunch`) and run the `postBuild` script to download the required data: `sh ./postBuild`.

9. Now you can run the code. In the 'Files' pane, select `London research landmarks.Rmd` and `hurricane_sst_v2.Rmd`. The documents will open in a pane to the left. For each file, select 'Run > Run All' in the toolbar at the top of the pane. You can view the resulting maps by scrolling the document.

10. The final cell in each file details the computational environment, including the operating system used. This highlights the containerization process: Though my computer runs MacOS, the operating system for this session is "Debian GNU/Linux 9".

11. Stop and delete the Docker container by executing 
```
docker stop $(docker ps -a -q) 
docker rm $(docker ps -a -q)
```
