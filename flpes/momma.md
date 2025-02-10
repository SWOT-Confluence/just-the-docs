---
layout: home
title: "momma"
nav_order: 2
parent: flpes
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/momma.git

cd momma

docker build -t momma .

sudo docker run -v /mnt/input/:/mnt/data/input -v /mnt/flpe/momma:/mnt/data/output -v ~/.aws:/root/.aws travissimmons/momma:latest -r reaches.json -m 3 -b confluence-sos/unconstrained/0000 -i 0


### HPC
singularity build momma.simg docker://travissimmons/momma

singularity run --bind mnt/input:/mnt/data/input,mnt/flpe/momma:/mnt/data/output momma.simg -i 1 -r reaches.json -m 3
 
## Arguments


#### Dev notes....
"""
  option_list <- list(
    make_option(c("-i", "--index"), type = "integer", default = -256, help = "Index to run on"),
    make_option(c("-b", "--bucket_key"), type = "character", default = "", help = "Bucket key to find the sos"),
    make_option(c("-r", "--reaches_json"), type = "character", default = NULL, help = "Name of reaches.json"),
    make_option(c("-m", "--min_nobs"), type = "character", default = NULL, help = "Minimum number of observations for a reach to have to be considered valid"),
    make_option(c("-c", "--constrained"), action = "store_true", default = FALSE, help = "Indicate constrained run")
  )
  """