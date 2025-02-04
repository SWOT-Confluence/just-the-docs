---
layout: home
title: "Setfinder"
nav_order: 2
parent: Modules
---

# Setfinder


## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/setfinder.git

cd setfinder

docker build -t setfinder .

<!-- docker run -e AWS_BATCH_JOB_ID="foo" -v /mnt/input:/mnt/data/input travissimmons/metroman:latest -r metrosets.json -s local -v -i 0 -->

docker run -v /mnt/input:/data setfinder -r reaches_of_interest.json -c continent-setfinder.json -e -s 16 -o /data -a MetroMan HiVDI SIC NeoBAM -i 3 -n /data

### HPC
singularity build setfinder.simg docker://travissimmons/setfinder

singularity run --bind mnt/input:/data setfinder.simg -r reaches_of_interest.json -c continent.json -e -s 16 -o /data -n /data -a MetroMan HiVDI SIC NeoBAM -i 0
 
## Arguments

options:
  -h, --help            show this help message and exit
  -i index, --index index
                        Index that indicates what continent to run on (default: None)
  -a ALGORITHMS [ALGORITHMS ...], --algorithms ALGORITHMS [ALGORITHMS ...]
                        A list of algorithm names (default: None)
  -e, --expanded        Expanded mode (default: False)
  -n indir, --indir indir
                        Path to input directory (default: None)
  -o outdir, --outdir outdir
                        Path to output directory (default: None)
  -s sword_version, --sword_version sword_version
                        Sword version number (default: None)
  -g, --globalrun       Global execution so load reaches from SWORD (default: False)
  -c JSONFILE, --jsonfile JSONFILE
                        Name of continent JSON file (default: continent.json)
  -r REACHSUBSET, --reachsubset REACHSUBSET
                        Name of reach subset file (default: None)


#### Dev notes....

