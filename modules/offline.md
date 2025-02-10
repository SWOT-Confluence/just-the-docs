---
layout: home
title: "Offline"
nav_order: 2
parent: Modules
---

# Input

## Build and Run Commands

### Local or AWS
git clone https://github.com/SWOT-Confluence/offline-discharge-data-product-creation.git

cd offline-discharge-data-product-creation

docker build -t offline .

### HPC
singularity build postd-moi.simg docker://travissimmons/offline

singularity run --bind mnt/input:/mnt/data/input,mnt/flpe:/mnt/data/flpe,mnt/moi:/mnt/data/moi,mnt/offline:/mnt/data/output  offline.simg unconstrained timeseries integrator reaches.json 1

## Arguments

def main(input, output, index_to_run):
    """Main function to execute offline discharge product generation and
    storage.
    Command line arguments:
    run_type: options are `unconstrained` or `constrained` (argument 1)
    input_type: options are 'timeseries' or 'single_pass' (argument 2)
                - timeseries: timer-series swot observations in one NetCDF file,
                              cross-sectional area change (d_x_area) should be
                              already computed and saved in time-series files.
                              discharge params from different discharge models
                              will be extracted from either moi-sword or integrator
                - single-pass: single-pass swot observation shapefiles, this is
                               what the swot data will look like. sword database
                               will be pulled d_x_area and discharge will be computed.
    flp_source: options are 'sword' or 'integrator' (argument 3)
    reach_json: title of JSON file that contains reach data (argument 4)

    Note: if input_type = single_pass, run_type, flp_source and reach_json will not be used.
          Set them to None or any other strings will work
    """
    # Command line arguments
    try:
        run_type = sys.argv[1]
        input_type = sys.argv[2]
        flp_source = sys.argv[3] # options are 'sword' or 'integrator'
        if input_type == 'timeseries':
            reach_json = os.path.join(INPUT, sys.argv[4])
    except IndexError:
        run_type = None
        if input_type == 'timeseries':
            reach_json = os.path.join(INPUT, "reaches.json")

#### Dev notes....
