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

ERROR-----
[1] "bucket_key:  "
[1] "index:  2"
[1] "reaches_json:  reaches.json"
[1] "min_nobs:  "
[1] "constrained:  FALSE"
[1] "reach_id:  56427001451"
[1] "swot_file:  /mnt/data/input/swot/56427001451_SWOT.nc"
[1] "sos_file:  /mnt/data/input/sos/oc_sword_v16_SOS_priors.nc"
Error in if (length(width) < min_nobs || length(wse) < min_nobs || length(slope2) <  : 
  missing value where TRUE/FALSE needed
Calls: run_momma -> get_input_data -> check_observations
Execution halted