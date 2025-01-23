---
layout: home
title: "hivdi"
nav_order: 2
parent: flpes
---

# Input

## Build and Run Commands

### Local or AWS
<!-- git clone https://github.com/SWOT-Confluence/neobam.git

cd neobam

docker build -t neobam . -->

docker run -v /mnt/input:/mnt/data/input -v /mnt/flpe/hivdi:/mnt/data/output hivdi /mnt/data/input/reaches.json -i 0


### HPC
<!-- singularity build neoobam.simg docker://travissimmons/neobam

singularity run --bind mnt/input:/mnt/data/input,mnt/flpe//geobam:/mnt/data/output neobam.simg -i 1 -r reaches.json -->

## Arguments


#### Dev notes....