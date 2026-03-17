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

## Install package
In the terminal do the following steps:
1. git clone the [Cerberus package](https://github.com/ChiaraBecht/Cerberus/tree/main) with:
   ```
   git clone https://github.com/ChiaraBecht/Cerberus.git
   ```
2. navigate into the local clone of the Cerberus repo
3. install the dependencies that are listed in the requirements file
4. 
