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

#### Dev notes....
