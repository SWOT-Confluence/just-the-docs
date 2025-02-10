---
layout: home
title: "metroman"
nav_order: 2
parent: FLPE Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/metroman.git

cd metroman

docker build -t metroman .

docker run -e AWS_BATCH_JOB_ID="foo" -v /mnt/input:/mnt/data/input travissimmons/metroman:latest -r metrosets.json -s local -v -i 0

### HPC
singularity build metroman.simg docker://travissimmons/metroman

singularity run --env AWS_BATCH_JOB_ID="foo" --bind mnt/input:/mnt/data/input,mnt/flpe/metroman:/mnt/data/output metroman.simg -i 0 -r metrosets.json -s local -v
 
## Arguments

def create_args():
    """Create and return argparsers with command line arguments."""
    
    arg_parser = argparse.ArgumentParser(description='Integrate FLPE')
    arg_parser.add_argument('-i',
                            '--index',
                            type=int,
                            default = -235,
                            help='Index to specify input data to execute on')
    arg_parser.add_argument('-r',
                            '--reachjson',
                            type=str,
                            help='Name of the reach.json',
                            default='metrosets.json')
    arg_parser.add_argument('-v',
                            '--verbose',
                            help='Indicates verbose logging',
                            action='store_true')
    arg_parser.add_argument('-s',
                            '--sosbucket',
                            type=str,
                            help='Name of the SoS bucket and key to download from',
                            default='')
    return arg_parser


#### Dev notes....