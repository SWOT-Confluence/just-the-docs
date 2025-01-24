---
layout: home
title: "metroman"
nav_order: 2
parent: flpes
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/metroman.git

cd metroman

docker build -t metroman .

docker run -e AWS_BATCH_JOB_ID="foo" -v /mnt/input:/mnt/data/input travissimmons/metroman:latest -r metrosets.json -s local -v -i 0

### HPC
singularity build metroman.simg docker://travissimmons/metroman

singularity run --env AWS_BATCH_JOB_ID="foo" --bind mnt/input:/mnt/data/input,mnt/flpe/metroman:/mnt/data/output metroman.simg -i 0 -r metrosets.json -s local -v
 
## Arguments


#### Dev notes....