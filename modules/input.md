---
layout: home
title: "Input"
nav_order: 1
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/input.git

cd input

docker build -t input .

or

docker pull travissimmons/input:latest

docker run -v /mnt/input:/mnt/data input -r /mnt/data/reaches.json -i 0

### HPC
singularity build input.simg docker://travissimmons/input

singularity run -c --bind mnt/input:/mnt/data input.simg -r /mnt/data/reaches.json -i 0

## Arguments

def create_args():
    """Create and return argparser with arguments."""

    arg_parser = argparse.ArgumentParser(description="Retrieve a list of S3 URIs")
    arg_parser.add_argument("-i",
                            "--index",
                            type=int,
                            help="Index to specify input data to execute on, value of -235 indicates AWS selection")
    arg_parser.add_argument("-r",
                            "--reachesjson",
                            type=str,
                            help="Path to the reaches.json",
                            default="/mnt/data/reaches_of_interest.json")
    arg_parser.add_argument("-o",
                            "--outdir",
                            type=str,
                            help="Directory to output data to",
                            default="/mnt/data/swot/")
    arg_parser.add_argument("-s",
                            "--sworddir",
                            type=str,
                            help="Directory containing SWORD files",
                            default="/mnt/data/sword/")
    arg_parser.add_argument("-t",
                            "--time",
                            type=str,
                            help="Time parameter to search",
                            default="&start_time=2020-09-01T00:00:00Z&end_time=2025-10-30T00:00:00Z&")
    arg_parser.add_argument("-v",
                            "--swordversion",
                            type=str,
                            help="Version of sword we are using",
                            default="16")
    arg_parser.add_argument("-p",
                            "--prefix",
                            type=str,
                            help="Prefix for AWS environment.",
                            default="")
    return arg_parser


#### Dev notes....
