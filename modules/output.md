---
layout: home
title: "Output"
nav_order: 2
parent: Modules
---

# Output

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/output.git

cd output

docker build -t output .

### HPC
singularity build output.simg docker://travissimmons/output

singularity run --bind mnt/input:/mnt/data/input,mnt/flpe:/mnt/data/flpe,mnt/moi:/mnt/data/moi,mnt/diagnostics:/mnt/data/diagnostics,mnt/offline:/mnt/data/offline,mnt/validation:/mnt/data/validation,mnt/output:/mnt/data/output output.simg -s local -j /app/metadata/metadata.json -m input priors prediagnostics momma neobam metroman sic4dvar sad moi offline validation swot -i 0

## Arguments


def create_args():
    """Create and return argparser with arguments."""

    arg_parser = argparse.ArgumentParser(description="Append results of Confluence workflow execution to the SoS.")
    arg_parser.add_argument("-i",
                            "--index",
                            type=int,
                            help="Index to specify input data to execute on, value of -235 indicates AWS selection")
    arg_parser.add_argument("-c",
                            "--contjson",
                            type=str,
                            help="Name of the continent JSON file",
                            default="continent.json")
    arg_parser.add_argument("-r",
                            "--runtype",
                            type=str,
                            choices=["constrained", "unconstrained"],
                            help="Current run type of workflow: 'constrained' or 'unconstrained'",
                            default="constrained")
    arg_parser.add_argument("-m",
                            "--modules",
                            nargs="+",
                            default=[],
                            help="List of modules executed in current workflow.")
    arg_parser.add_argument("-j",
                            "--metadatajson",
                            type=Path,
                            default=Path(__file__).parent / "metadata" / "metadata.json",
                            help="Path to JSON file that contains global attribute values")
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
    return arg_parser

#### Dev notes....
