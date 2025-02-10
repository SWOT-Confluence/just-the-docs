---
layout: home
title: "Validation"
nav_order: 2
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/Validation.git

cd Validation

docker build -t validation .

### HPC
singularity build valdation.simg docker://travissimmons/validation

 singularity run --bind mnt/input:/mnt/data/input,mnt/flpe:/mnt/data/flpe,mnt/moi:/mnt/data/moi,mnt/offline:/mnt/data/offline,mnt/validation:/mnt/data/validation validation.simg reaches.json unconstrained 1000

## Arguments

def create_args():
    """Create and return argparsers with command line arguments."""
    
    arg_parser = argparse.ArgumentParser(description='Integrate FLPE')
    arg_parser.add_argument('-i',
                            '--index',
                            type=int,
                            # default=-235,
                            help='Index to specify input data to execute on')
    arg_parser.add_argument('-r',
                            '--reachjson',
                            type=str,
                            help='Name of the reaches.json',
                            default='reaches.json')
    arg_parser.add_argument('-t',
                            '--runtype',
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
