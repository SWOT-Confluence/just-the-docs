---
layout: home
title: "Running a custom module locally"
nav_order: 1
parent: Guides
---

## Customizing a module, and then running on your local machine (you need sudo)

### Install docker on local machine / server where you have sudo
https://docs.docker.com/engine/install/

### Git clone the run-confluence-locally repo

''' git Command here '''

###  Git clone the modules that you are intersted in running, 
'' git Coommand here '''

if you are starting with empty_mnt and are interestd in running a module in the middle of a run, you must run all the previous modules once. 

Priors takes forever to run, so I included the output files for that module in the empty_mnt (aka you can skip it). Also, prediagnostics is destructive so if you are experimenting with filtering, make a copy of /mnt/input/swot before you run prediagnostics to have a 'clean/non-filtered' 

If there is a branch name at the end of the command at run-confluence-locally/run_confluence_docker.ipynb do : git checkout {branch_name}

make changes to the module (or don't!)

Fill out and run run-confluence-locally/run_confluence_docker.ipynb

This generates a script that loops through your specified reaches from reaches_of_inerest.json

Run the generated python script, move on to the next module