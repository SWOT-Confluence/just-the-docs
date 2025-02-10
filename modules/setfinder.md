---
layout: home
title: "Setfinder"
nav_order: 2
parent: Modules
---

# Setfinder


## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/setfinder.git

cd setfinder

docker build -t setfinder .

or

docker pull travissimmons/setfinder:latest
<!-- docker run -e AWS_BATCH_JOB_ID="foo" -v /mnt/input:/mnt/data/input travissimmons/metroman:latest -r metrosets.json -s local -v -i 0 -->

**Expanded**
docker run -v /mnt/input:/data setfinder -r reaches_of_interest.json -c continent-setfinder.json -e -s 16 -o /data -a MetroMan HiVDI SIC NeoBAM -e -n /data -i 3

**Not Expanded**
docker run -v /mnt/input:/data setfinder -r reaches_of_interest.json -c continent-setfinder.json -e -s 16 -o /data -a MetroMan HiVDI SIC NeoBAM  -n /data -i 3

### HPC
singularity build setfinder.simg docker://travissimmons/setfinder

singularity run --bind mnt/input:/data setfinder.simg -r reaches_of_interest.json -c continent.json -e -s 16 -o /data -n /data -a MetroMan HiVDI SIC NeoBAM -i 0
 
## Arguments

def get_args():
    """Get command-line arguments"""

    parser = argparse.ArgumentParser(
        formatter_class=argparse.ArgumentDefaultsHelpFormatter)

    parser.add_argument('-i',
                        '--index',
                        help='Index that indicates what continent to run on',
                        metavar='index',
                        type=int)

    parser.add_argument('-a',
                        '--algorithms',
                        help='A list of algorithm names',
                        nargs='+')
    
    parser.add_argument('-e', 
                        '--expanded', 
                        action='store_true', 
                        help='Expanded mode')

    parser.add_argument('-n',
                        '--indir',
                        help='Path to input directory',
                        metavar='indir',
                        type=str)

    parser.add_argument('-o',
                        '--outdir',
                        help='Path to output directory',
                        metavar='outdir',
                        type=str)

    parser.add_argument('-s',
                        '--sword_version',
                        help='Sword version number',
                        metavar='sword_version',
                        type=int)
    
    parser.add_argument('-g', 
                        '--globalrun', 
                        action='store_true', 
                        help='Global execution so load reaches from SWORD')
    
    parser.add_argument("-c",
                        "--jsonfile",
                        type=str,
                        help="Name of continent JSON file",
                        default="continent.json")
    
    parser.add_argument("-r",
                        "--reachsubset",
                        type=str,
                        help="Name of reach subset file")

    return parser.parse_args()

#### Dev notes....

