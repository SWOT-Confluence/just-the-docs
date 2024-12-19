---
layout: home
title: "Running on HPC"
nav_order: 3
parent: Guides
---

# Running Confluence on an HPC

All confluence modules are containerized and hosted on my personal dockerhub (https://hub.docker.com/repositories/travissimmons). 

You can build and run these using the commands below. If you would like to make edits to the code:
 
- fork your repo of interest from https://github.com/SWOT-Confluence
- edit the code locally
- build it using docker
- upload it to your personal dockerhub (https://hub.docker.com/) Its free!
- then run the commands below, replacing travissimmons with your dockerhub 


## Running Using SLURM

Once you have all of your docker images on a dockerhub, you can use the notebook below to generate slurm files for running each module based off of your node limitations.

<iframe
    src="https://nbviewer.org/github/SWOT-Confluence/just-the-docs/blob/main/guides/local_confluence_notebook.ipynb"
    width="100%"
    height="600px">
</iframe>