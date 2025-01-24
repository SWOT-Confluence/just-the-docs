---
layout: home
title: "Offline"
nav_order: 2
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/offline-discharge-data-product-creation.git

cd offline-discharge-data-product-creation

docker build -t offline .

### HPC
singularity build postd-moi.simg docker://travissimmons/offline

singularity run --bind mnt/input:/mnt/data/input,mnt/flpe:/mnt/data/flpe,mnt/moi:/mnt/data/moi,mnt/offline:/mnt/data/output  offline.simg unconstrained timeseries integrator reaches.json 1

## Arguments

#### Dev notes....
