---
layout: home
title: "MOI"
nav_order: 2
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/MOI.git

cd MOI

docker build -t moi .

### HPC
singularity build moi.simg docker://travissimmons/moi

singularity run --env AWS_BATCH_JOB_ID="foo" --bind mnt/input:/mnt/data/input,mnt/flpe:/mnt/data/flpe,mnt/moi:/mnt/data/output moi.simg -i 0 -j basin.json -v -b unconstrained -s local

## Arguments

#### Dev notes....
