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

option_list <- list(
  make_option(c("-i", "--index"), type = "integer", default = NULL, help = "Index to run on"),
  make_option(c("-t", "--tolerance"), type = "integer", default = 0.25, help = "Tolerance value for stability check"),
  make_option(c("-b", "--current_bucket"), type = "character", default = "", help = "Bucket key to find the sos"),
  make_option(c("-r", "--reaches_json"), type = "character", default = "reaches.json", help = "Name of reaches.json"),
  make_option(c("-l", "--local_bool"), type = "logical", default = FALSE, help = "Name of reaches.json"),
  make_option(c("-p", "--previous_bucket"), type = "character", default = "confluence-sos", help = "Name of SoS bucket to pull previous results")
)

#### Dev notes....
