---
layout: home
title: "Priors"
nav_order: 2
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/priors.git

cd priors

docker build -t priors .

docker run -v /mnt/input:/mnt/data priors -i 0 -r unconstrained -p usgs riggs gbpriors -l 000 -g

### HPC
singularity build priors.simg docker://travissimmons/priors

singularity run -c --writable-tmpfs  --bind mnt/input:/mnt/data priors.simg -i 2 -r unconstrained -p riggs -g -s local


## Arguments

def create_args():
    """Create and return argparser with arguments."""

    arg_parser = argparse.ArgumentParser(description="Update Confluence SoS priors.")
    arg_parser.add_argument("-i",
                            "--index",
                            type=int,
                            help="Index value to select continent to run on")
    arg_parser.add_argument("-r",
                            "--runtype",
                            type=str,
                            choices=["constrained", "unconstrained"],
                            help="Indicates what type of run to generate priors for.",
                            default="constrained")
    arg_parser.add_argument("-p",
                            "--priors",
                            type=str,
                            nargs="+",
                            default=[],
                            help="List: usgs, grdc, riggs, gbpriors")
    arg_parser.add_argument("-o",
                            "--sosversion",
                            type=str,
                            default='0001',
                            help="Priors version to create SoS for")
    arg_parser.add_argument("-m",
                            "--metadatajson",
                            type=Path,
                            default=Path(__file__).parent / "metadata" / "metadata.json",
                            help="Path to JSON file that contains global attribute values")
    arg_parser.add_argument("-qt",
                            "--historicqt",
                            type=Path,
                            default=Path(__file__).parent / "metadata" / "historicQt.json",
                            help="Path to JSON file that contains historic timestamps for discharge from gage agencies")
    arg_parser.add_argument("-g",
                            "--addgeospatial",
                            action="store_true",
                            help="Indicate requirement to add geospatial data")
    arg_parser.add_argument("-u",
                            "--podaacupload",
                            action="store_true",
                            help="Indicate requirement to upload to PO.DAAC S3 Bucket")
    arg_parser.add_argument("-b",
                            "--podaacbucket",
                            type=str,
                            help="Name of PO.DAAC S3 bucket to upload to")
    arg_parser.add_argument("-s",
                            "--sosbucket",
                            type=str,
                            default="confluence-sos",
                            help="Name of SoS S3 bucket to upload to")
    arg_parser.add_argument("--swordversion",
                            type=str,
                            default="16",
                            help="Version of sword to run on")
    return arg_parser


#### Dev notes....
Had to turn of hydat and upload functions in order to get it running, need to make an hpc or offline flag...not currently on a branch...