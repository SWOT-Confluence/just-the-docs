---
layout: home
title: "FLPE Postdiagnostics"
nav_order: 2
parent: Modules
---

# Input

## Build and Run Commands


### Local or AWS
git clone https://github.com/SWOT-Confluence/momma.git

cd momma

docker build -t momma .

### HPC
singularity build postd-flpe.simg docker://travissimmons/postd-flpe

singularity run --bind mnt/input:/mnt/data/input,mnt/flpe:/mnt/data/flpe,mnt/diagnostics/postdiagnostics/reach:/mnt/data/output,mnt/output/sos:/mnt/data/results postd-flpe.simg -r reaches.json -t 0.25 -i 0

## Arguments

#### Dev notes....

ERROR
2025-01-13T21:53:40 - credentials - : Found credentials in shared credentials file: ~/.aws/credentials
2025-01-13T21:53:41 - sos_read - : Could not download file: /app/postdiagnostics/oc_sword_v16_SOS_results.nc from confluence-sos/unconstrained/0001/oc_sword_v16_SOS_results.nc.
2025-01-13T21:53:41 - sos_read - : An error occurred (404) when calling the HeadObject operation: Not Found
2025-01-13T21:53:41 - sos_read - : Cannot proceed without previous results. Exiting program.
Error in py_call_impl(callable, call_args$unnamed, call_args$named) : 
  SystemExit: 1
Run `reticulate::py_last_error()` for details.
Calls: run_flpe_diagnostics ... get_data_flpe -> get_flpe_prev -> download_sos -> py_call_impl
Execution halted