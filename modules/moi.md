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
singularity build moi.simg docker://travissimmons/moi

singularity run --env AWS_BATCH_JOB_ID="foo" --bind mnt/input:/mnt/data/input,mnt/flpe:/mnt/data/flpe,mnt/moi:/mnt/data/output moi.simg -i 0 -j basin.json -v -b unconstrained -s local

## Arguments

def create_args():
    """Create and return argparsers with command line arguments."""
    
    arg_parser = argparse.ArgumentParser(description='Integrate FLPE')
    arg_parser.add_argument('-i',
                            '--index',
                            type=int,
                            help='Index to specify input data to execute on')
    arg_parser.add_argument('-j',
                            '--basinjson',
                            type=str,
                            help='Name of the basin.json',
                            default='basin.json')
    arg_parser.add_argument('-v',
                            '--verbose',
                            help='Indicates verbose logging',
                            action='store_true')
    arg_parser.add_argument('-b',
                            '--branch',
                            type=str,
                            help='Indicates constrained or unconstrained run',
                            choices=['constrained', 'unconstrained'],
                            default='unconstrained')
    arg_parser.add_argument('-s',
                            '--sosbucket',
                            type=str,
                            help='Name of the SoS bucket and key to download from',
                            default='')
    return arg_parser

#### Dev notes....
