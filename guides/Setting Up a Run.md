---
layout: home
title: "Setting Up a Run"
nav_order: 1
parent: Guides
---

# Setting up a run


## Setup Commands

pip install gdown

gdown 1I3B9Cb9-5NV1xlxgE2Y-YFwtNNYeGvXM

tar -xzvf empty_mnt.tar.gz

git clone https://github.com/SWOT-Confluence/confluence-local.git

git checkout euro

## Running any module

setup and run confluence-local/local_confluence_notebook.ipynb

edit cfl_wrapper.sh for bulk submission or edit the generated .sh file to submit custom arrays

## Customizing a Module (need sudo and docker)

Install docker on local machine / server where you have sudo: 

Create a personal dockerhub (free): https://hub.docker.com/

Create a dockerhub repo named the module eg: for priors my dockerhub repo link is travissimmons/priors

Find the module you are interested in at https://github.com/SWOT-Confluence or fork it to your github so you can save changes

Git clone it

make changes

docker build -t travissimmons/{module name} .

docker push travissimmons/{module name}












- download input files
    - link to sword
        - https://drive.google.com/file/d/1Z7bAPSh4jcj0-jJ5ipcFMAsxTFTCJCxP/view?usp=drive_link
    - link to sos
        - https://drive.google.com/file/d/1MrRx6TrCEcAABE6TXg4YWGaeCJvPloAm/view
    - Link to startup mnt
        - download link for devset jsons in the correct file structure

Here I want to have a link to the most recent full mnt with files like reaches.json.template etc 





### Before moving on ensure you have this file structure
- setup file structure (this is taken care of if you download the startup jsons above)

    - mnt
        - input
            - sos (sos goes here)
            - sword (sword files go here)
            - swot (swot timeseries files will be generated here)
            - gage (gauge data go here)
            - reaches.json that lists what reaches you would like to produce discharge for
        - diagnostics
            - prediagnostics
            - postdiagnostics
                - basin
                - reach
        -flpe
            - metroman
            - neobam
            - sic4dvar
            - hivdi
            - sad
            - momma
        - output
            - sos
        - validation
            - stats
            - figs
        - offline
        - moi
        

- proceed to next section