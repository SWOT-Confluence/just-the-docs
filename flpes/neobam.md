---
layout: home
title: "neobam"
nav_order: 2
parent: flpes
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/neobam.git

cd neobam

docker build -t neobam .

docker run -v /mnt/input:/mnt/data/input -v /mnt/flpe/geobam:/mnt/data/output neobam -i 1 -r reaches.json


### HPC
singularity build neoobam.simg docker://travissimmons/neobam

singularity run --bind mnt/input:/mnt/data/input,mnt/flpe//geobam:/mnt/data/output neobam.simg -i 1 -r reaches.json

## Arguments

"""
  option_list <- list(
    make_option(c("-i", "--index"), type = "integer", default = NULL, help = "Index to run on"),
    make_option(c("-b", "--bucket_key"), type = "character", default = "", help = "Bucket key to find the sos"),
    make_option(c("-r", "--reaches_json"), type = "character", default = "reaches.json", help = "Name of reaches.json")
  )
  """


#### Dev notes....