---
layout: home
title: "sad"
nav_order: 2
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/sad.git

cd sad

docker build -t sad .


### HPC
singularity build neoobam.simg docker://travissimmons/sad

singularity run --bind mnt_dir/input:/mnt/data/input,mnt/flpe/sad:/mnt/data/output sad.sif --index 0 --reachfile reaches.json

## Arguments


#### Dev notes....