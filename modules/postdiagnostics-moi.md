---
layout: home
title: "MOI Postdiagnostics"
nav_order: 2
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/momma.git

cd momma

docker build -t momma .

### HPC
singularity build postd-moi.simg docker://travissimmons/postd-moi

singularity run --bind mnt/input:/mnt/data/input,mnt/flpe:/mnt/data/flpe,mnt/diagnostics/postdiagnostics/reach:/mnt/data/output,mnt/output/sos:/mnt/data/results postd-moi.simg -r reaches.json -t 0.25 -i 0 -l True

## Arguments

#### Dev notes....
