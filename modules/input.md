---
layout: home
title: "Input"
nav_order: 1
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/input.git

cd input

docker build -t input .

docker run -v /mnt/input:/mnt/data input -r /mnt/data/reaches.json -i 0

### HPC
singularity build input.simg docker://travissimmons/input

singularity run -c --bind mnt/input:/mnt/data input.simg -r /mnt/data/reaches.json -i 0 
