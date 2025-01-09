---
layout: home
title: "Priors"
nav_order: 2
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/priors.git

cd priors

docker build -t priors .

docker run -v /mnt/input:/mnt/data priors -i 0 -r unconstrained -p usgs riggs gbpriors -l 000 -g

### HPC
singularity build priors.simg docker://travissimmons/priors

singularity run -c --bind mnt/input:/mnt/data priors.simg -i 0 -r unconstrained -p usgs riggs gbpriors -g


## Arguments


#### Dev notes....
Had to turn of hydat and upload functions in order to get it running, need to make an hpc or offline flag...not currently on a branch...