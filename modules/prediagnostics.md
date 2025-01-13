---
layout: home
title: "Prediagnostics"
nav_order: 2
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/prediagnostics.git

cd prediagnostics

docker build -t prediagnostics .

----------------docker run -v /mnt/input:/mnt/data priors -i 0 -r unconstrained -p usgs riggs gbpriors -l 000 -g-------------

### HPC
singularity build prediagnostics.simg docker://travissimmons/prediagnostics

singularity run --bind mnt/input:/mnt/data/input,mnt/diagnostics/prediagnostics:/mnt/data/output prediagnostics.simg 1 reaches.json



## Arguments


#### Dev notes....
Had to turn of hydat and upload functions in order to get it running, need to make an hpc or offline flag...not currently on a branch...