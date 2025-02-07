---
layout: home
title: "Setting Up a Run"
nav_order: 1
parent: Guides
---

# Setting up a run


## Setup Commands

(pip or conda) install gdown

gdown 1xRltFZ1gyP_nvwHMJW-rIgClzXx8CSLC

tar -xzvf empty_mnt.tar.gz

git clone https://github.com/SWOT-Confluence/run-confluence-locally.git

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


| Module                 | Number of Jobs                   | Description                                                                                                                    |
|------------------------|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| Expanded Setfinder     | 7                                | Creates sets (groups of connected reaches) starting with your reaches of interest and looking up and down the river            |
| Expanded Combine Data  | 1                                | Combines the files generated in the setfinder into continent level data                                                        |
| Input                  | Number of Reaches                | Pulls reach data from hydrocron and stores them in netcdfs, outputs to /mnt/input/swot                                         |
| Setfinder              | 7                                | Creates sets (groups of connected reaches) only using the reaches that were pulled successfully using Input                    |
| Combine Data           | 1                                | Combines files generated in the setfinder into continent level data                                                            |
| Prediagnostics         | Number of Reaches                | Filters reach data netcdfs based on a series of bitwise filters and outlier detectors. OVERWRITES NETCDFS                      |
| Priors                 | 7                                | Pulls gauge data from external gauge agencies and builds the prior database (Priors SoS) which is eventually hosted on PO.DAAC |
| Metroman               | Number of Sets in metrosets.json | Runs the metroman FLPE algorithm, outputs to /mnt/flpe/metroman/sets                                                           |
| Metroman Consolidation | Number of Reaches                | Takes the set level results of metroman and turns them into individual files, outputs to /mnt/flpe/metroman                    |
| Momma, Neobam, SAD     | Number of Reaches                | Runs the corrisponding FLPE algorithm                                                                                          |
| MOI                    | Number of basins in basins.json  | Combines FLPE algorithm results (not currently working because of SWORD v16 topology issues)                                   |
| Offline                | Number of Reaches                | Runs NASA SDS's discharge algorithm.                                                                                           |
| Validation             | Number of Reaches                | If there is a validation gauge on the reach then summary stats are produced. (All gauges are validation in unconstrained runs) |
| Output                 | 7                                | Outputs results netcdf files that store all previous results data, outputs to /mnt/output/sos                                  |









<!-- - download input files
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
        

- proceed to next section -->