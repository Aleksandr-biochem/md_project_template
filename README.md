# Molecular Dynamics project template

This is a template, which you can use (for tips and ideas) to organise your new MD project. 

You can clone this repository, edit it in a way that suits your work and store it as a template on your system to quick-start new projects.

## 1. Create file structure 

General file structure that I found convenient through the years:

```
project_name
│   README.md (could be used for project notes or general info for archiving)
│   simulation_setup_and_analysis.ipynb (lab notebook and analysis code)
│   
└───data (folder for input data, pdb files, some dataset on your molecules etc.)
│   │   protein1.pdb
│   │   ...
│    
└───simulations_group1 (you can create one folder with your simulations or group them in other way)
│   │   assemble_and_run.py (a script to assemble and run systems replicates in this group)
│   └───template (folder with template files, e.g. .mdp, to be copied in each replicate)
│   │
│   └───system1
│       └───rep1
|       │   │  assembly_minimisation
|       │   │  equilibration
|       │   │  production
│       │   │  production_analysis (data extracted from this system, e.g. rmsd, lipid data etc)
│       │   
│       │   rep2
│       │   ...
│   
└───simulations_group2
    │   ...
│   
└───scripts (used for postprocessing and analysis of the simulations)
│   │   postprocess_trjs.sh
│   │   ...
│   
└───analysis (folder for output data that you aggregated from trajectory analysis)
│   │   rmsd.csv
│   │   lipid_properties.csv
│   │   ...
│  
└───plots (plots generated in .ipynb file)
│   │   rmsd_plot.jpg
│   │   ...
│
└───env (separate environment for your project)

```

Create all the folders that suit your work:
```
mkdir analysis scripts data plots simulations_group1 simulations_group2
```

## 2. Create an environment for your project

Ideally, each project should have its' own environment. Especially if you are using some niche packages or developing code in course of the project.

For example, use template Python environment requirements to create a new one with your preferred tools:

```
# create new environment
python -m venv ./project_env

# activate
source project_env/bin/activate

# check that we use python from the environment
which python

# make sure pip is availabe
python -m pip install --upgrade pip

# install packages from list
python -m pip install -r requirements.txt
```

Albeit, this step can be skipped if you prefer to organise your environments in a different way. 

## 3. Script system assembly, simulation and postprocessing

Scripting assembly and simulation of your systems can be extremely helpful. 
If you want to rerun simulations with other parameters, add replicates, simulate altered composition etc. you can just take the script, edit it and launch.
Also, looking back you will know for fact, how the systems were generated. 

`assemble_and_run.py` is an example for setup of several repliacates of a solvated POPC bilayer in Martini2 force field using COBY. 

I also inlucded `scripts/postprocess_trjs.sh` as an example of how you can script postprocessing of trajectories. 

## 4. Document your work, analyse and plot data in `simulation_setup_and_analysis.ipynb`

I find jupyter notebooks very convenient as lab journals and for visual analysis of data extracted from simulations.
See the example file for template.
