---
layout: home
title: "sad"
nav_order: 2
parent: flpes
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/sad.git

cd sad

docker build -t sad .


### HPC
singularity build neoobam.simg docker://travissimmons/sad

singularity run --bind mnt_dir/input:/mnt/data/input,mnt/flpe/sad:/mnt/data/output sad.sif --index 0 --reachfile reaches.json

## Arguments
function parse_commandline()
    s = ArgParseSettings()
    @add_arg_table s begin
        "--index", "-i"
            help = "Index of reach to run on"
            arg_type = Int
            default = 0
        "--reachfile", "-r"
            help = "Name of reaches JSON file"
            arg_type = String
            default = "reaches.json"
        "--bucketkey", "-b"
            help = "Bucket and key prefix to download SoS from"
            arg_type = String
            default = ""
    end

    return parse_args(s)

#### Dev notes....