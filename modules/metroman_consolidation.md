---
layout: home
title: "Metroman Consolidation"
nav_order: 2
parent: Modules
---

# Metroman Consolidation

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/metroman_consolidation.git

cd metroman_consolidation

docker build -t metroman_consolidation .

<!-- docker run -e AWS_BATCH_JOB_ID="foo" -v /mnt/input:/mnt/data/input travissimmons/metroman:latest -r metrosets.json -s local -v -i 0 -->

### HPC
singularity build metroman_consolidation.simg docker://travissimmons/metroman_consolidation

singularity run --bind mnt/input:/mnt/input,mnt/flpe/metroman:/mnt/flpe metroman_consolidation.simg -i 0
 
## Arguments

def get_args():
    """Get command-line arguments"""

    parser = argparse.ArgumentParser(
        description='Rock the Casbah',
        formatter_class=argparse.ArgumentDefaultsHelpFormatter)

    parser.add_argument('-i',
                        '--index',
                        help='index of continent to process',
                        metavar='int',
                        type=int,
                        )


    return parser.parse_args()


#### Dev notes....
