---
layout: home
title: "Lakeflow"
nav_order: 2
parent: Modules
---

# Lakeflow Input

## Build and Run Commands

### Local or EC2 (Docker)
git clone https://github.com/SWOT-Confluence/LakeFlow_Confluence/tree/travis_dev

cd Lakeflow_Confluence

docker build -t lakeflow_input -f Dockerfile_input .

docker run -v /mnt/input/lakeflow:/data/input -v /mnt/input/sword:/data/sword/ lakeflow_input -c /data/input/reaches_of_interest.json -w 1 -i /data/input

### HPC (Singularity)

docker -t lakeflow_input travissimmons/lakeflow_input:latest

docker push travissimmons/lakeflow_input:latest

singularity build lakeflow_input.simg docker://travissimmons/lakeflow_input

singularity run --bind /mnt/input/lakeflow:/data/input,/mnt/input/sword:/data/sword lakeflow_input.sif -c /data/input/reaches_of_interest.json -w 1 -i /data/input


#### Dev notes....
/mnt/input/sword should have a the relevant sword for your continent
/mnt/input/lakeflow (-i flag) should have all of your auxilary input data like below


updated_pld = fread(file.path(indir,"/SWORDv16_PLDv103_wo_ghost_rch.csv"))
et = fread(file.path(indir, '/ancillary/et.csv'))
tributary = fread(file.path(indir,'/ancillary/tributaries.csv'))
sword_geoglows = fread(file.path(indir,'/ancillary/sword_geoglows.csv'))
dir.create(file.path(indir, "/clean"), showWarnings = FALSE)


# Lakeflow Deploy

## Build and Run Commands

### Local or EC2 (Docker)
git clone https://github.com/SWOT-Confluence/LakeFlow_Confluence/tree/travis_dev

cd Lakeflow_Confluence

docker build -t lakeflow_deploy -f Dockerfile_deploy .

docker run -v /mnt/input/lakeflow:/data/input -v /mnt/input/sos:/sos/input lakeflow_deploy -c /data/input/viable/viable_locations-255.csv -s /sos/input -w 1 -i /data/input -o /data/input/out --index 2

### HPC (Singularity)

docker -t lakeflow_deploy travissimmons/lakeflow_deploy:latest

docker push travissimmons/lakeflow_deploy:latest

singularity build lakeflow_deploy.simg docker://travissimmons/lakeflow_deploy

singularity run --bind /mnt/input/lakeflow:/data/input,/mnt/input/sos:/sos/input lakeflow_deploy.sif -c /data/input/viable/viable_locations-255.csv -s /sos/input -w 1 -i /data/input -o /data/input/out --index 2


#### Dev notes....
/mnt/input/sos (-s flag) should ahve the SOS file for the relevant continent


##
Here is a link to an empty mount with an sos and a copy of sword
https://drive.google.com/file/d/1xRltFZ1gyP_nvwHMJW-rIgClzXx8CSLC/view?usp=sharing

Here is a link to my last delivery notes, reading through the lakeflow sections may be helpful
https://umass-my.sharepoint.com/:w:/g/personal/tsimmons_umass_edu/EQXh6_zLNVRMjxdkHHI1PW0BSlifSnKlEiFuoLK_UA85-w?rtime=-U2lf--U3Ug
