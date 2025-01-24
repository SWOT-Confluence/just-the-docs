---
layout: home
title: "Combine Data"
nav_order: 2
parent: modules
---

# Combine Data



## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/combine_data.git

cd combine_data

docker build -t combine_data .

<!-- docker run -e AWS_BATCH_JOB_ID="foo" -v /mnt/input:/mnt/data/input travissimmons/metroman:latest -r metrosets.json -s local -v -i 0 -->

### HPC
singularity build combine_data.simg docker://travissimmons/combine_data

singularity run --bind mnt/input:/data combine_data.simg -d /data  -e -s 16
 
## Arguments

Combine continent JSON files

optional arguments:
  -h, --help            show this help message and exit
  -c CONTFILE, --contfile CONTFILE
                        Name of continent.json file.
  -d DATADIR, --datadir DATADIR
                        Path to directory that contains datagen data.
  -u UPLOADBUCKET, --uploadbucket UPLOADBUCKET
                        Name of S3 bucket to upload JSON files to.
  -s SWORD_VERSION, --sword_version SWORD_VERSION
                        version of sword to use.
  -x, --delete          Indicate if continent-level JSON files should be deleted.
  -e, --expanded        Indicate we are looking for expanded set files.
  --ssc_combine         Indicate we are looking for hls files for ssc prediction.


#### Dev notes....

