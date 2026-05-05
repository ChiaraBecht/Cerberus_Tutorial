# Install
Cerberus package can be obtained from github. the Repository already contains the Dockerfile required for running with docker as well as all relevant modules except the statistics for calling GIs on Gene level. This part is written in R and is developed by our collaborator.  

Requirements to run Cerberus
- python
- R
- [Cerberus package](https://github.com/ChiaraBecht/Cerberus/tree/main) + dependencies
- [CeRberus package](https://github.com/thorohde/CeRberus) + dependencies
  
## Install with docker
In the terminal do the following steps:
1. git clone the [Cerberus package](https://github.com/ChiaraBecht/Cerberus/tree/main) with:
   ```
   git clone https://github.com/ChiaraBecht/Cerberus.git
   ```
2. navigate into the local clone of the Cerberus repo
   ´´´
   cd /ful/path/to/clone/Cerberus
   ´´´
3. build docker container (only once)
   ```
   docker build -t cerberus .
   ```
4. run docker container interactively, mounting data to the container
   ```
   docker run -it -v /path/to/data/folder/:/Data cerberus bash
   ```
5. now run cerberus command using sample sheet and data from the mounted location
   ```
   python3 ./objects.py -s /Data/your_sample_sheet.yaml
   ```
Explanation on steps:
xxx

## Install package (usage of virtual environment recommended)
In the terminal do the following steps:
1. (optional) create a virtual environement (we demonstrate conda, but choose whichever you like)
   ```
   conda create -n cerberus
   ```
2. actiavte the virtual environment:
   ```
   conda activate cerberus
   ```
3. Install Python and R
   ```
   conda install python=3.12.3
   conda install conda-forge r-base=4.3
   ```
4. git clone the [Cerberus package](https://github.com/ChiaraBecht/Cerberus/tree/main) with:
   ```
   git clone https://github.com/ChiaraBecht/Cerberus.git
   ```
5. navigate into the local clone of the Cerberus repo
   ```
   cd ./Cerberus
   ```
6. install the dependencies
   ```
   pip install -e .
   ```
7. install R dependencies
   ```
   conda install -c conda-forge r-abind r-data.table r-ggplot2 r-purrr r-reshape2 r-stringr r-yaml r-remotes
   ```
8. start R terminal to install Bioconductor, Bioconductor package limma and the GI aggregation and statistics package CeRberus
   ```
   R
   install.packages("BiocManager", repos="https://cloud.r-project.org")
   BiocManager::install("limma")
   remotes::install_github("thorohde/CeRberus")
   ```
