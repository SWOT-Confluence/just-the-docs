---
layout: home
title: "Validation"
nav_order: 2
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/Validation.git

cd Validation

docker build -t validation .

### HPC
singularity build valdation.simg docker://travissimmons/validation

 singularity run --bind mnt/input:/mnt/data/input,mnt/flpe:/mnt/data/flpe,mnt/moi:/mnt/data/moi,mnt/offline:/mnt/data/offline,mnt/validation:/mnt/data/validation validation.simg reaches.json unconstrained 1000

## Arguments

#### Dev notes....
