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
singularity build postd-moi.simg docker://travissimmons/moi

singularity run --bind mnt/input:/mnt/data/input,mnt/flpe:/mnt/data/flpe,mnt/moi:/mnt/data/output moi.simg -j basin.json -v -b unconstrained -i 0

## Arguments

#### Dev notes....

index:  0
basin file:  basin.json
verbose flag:  True
branch:  unconstrained
sosbucket:  
index: -b
index_to_run:  0
Using /Users/mtd/Analysis/SWOT/Discharge/Confluence/ohio_offline_runs/mnt/input/basin.json
Running offline, with index =  0
Traceback (most recent call last):
  File "/app/run_MOI.py", line 301, in <module>
    main()
  File "/app/run_MOI.py", line 262, in main
    basin_data = get_basin_data(basin_json,index_to_run,TMP_DIR,args.sosbucket)
                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/app/run_MOI.py", line 37, in get_basin_data
    with open(basin_json) as json_file:
         ^^^^^^^^^^^^^^^^
FileNotFoundError: [Errno 2] No such file or directory: '/Users/mtd/Analysis/SWOT/Discharge/Confluence/ohio_offline_runs/mnt/input/basin.json'