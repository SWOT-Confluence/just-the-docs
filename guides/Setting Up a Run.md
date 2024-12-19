---
layout: home
title: "Setting Up a Run"
nav_order: 1
parent: Guides
---

# Setting up a run

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