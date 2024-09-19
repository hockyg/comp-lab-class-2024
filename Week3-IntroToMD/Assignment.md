# Assignment for Week 3

## Setup reminder ##
- First, get the latest changes synchronized to your Github
- Then, run `git pull` in your github folder on greene (use the terminal app)
- At the end, you will organize your results in the folder `Week3-IntroToMD` using the provided folders

## Using gromacs on Greene ##
Gromacs is already installed on greene. They are installed within "modules". To see the gromacs modules, type `module avail gromacs`

The tutorial below uses gromacs version 2018, but we will use gromacs 2020 since it is working on the cluster. You can type ` module load gromacs/openmpi/intel/2020.4` to make gromacs commands available. 

In the tutorial, whenever it says to type `gmx` you will type `gmx_mpi` since that is the name of the executable on Greene.

## Running on an interactive node ##
Do this tutorial on a compute node. The steps of file preparation etc could be done on the login node, but we will be doing actual simulations now, so you should request compute resources. 

To get an interactive node, you can type something like this:

`srun --cpus-per-task 1 --tasks-per-node 1 --mem 8GB –t 4:00:00 --pty /bin/bash`

Which, once it starts, will give you a compute node for four hours, with 8 gigabytpes of RAM and 4 CPUs.

For the final simulation for this exercise, you may need to do it using an SBATCH script so that it can run overnight (and for bigger simulations you could request more than 1 CPU, but trp-cage below is small)

 In an SBATCH Script you will set up a set of commands and submit those commands to the queue. There is an example in this week's lecture, and you can also now read the page https://sites.google.com/nyu.edu/nyu-hpc/training-support/tutorials/slurm-tutorial


## Week 3 assignment ##

1) Do the Lysozyme tutorial for Gromacs on HPC, adapting as needed. http://www.mdtutorials.com/gmx/lysozyme/index.html
- *HOWEVER*, do not use lysozyme but rather the smaller protein trp-cage, pdb ID 2JOF
- For the first step of `pdb2gmx` you will have to add the flag `-ignh` as explained at the bottom of the page for NMR structures
- *For the whole tutorial, make the plots in one Jupyter notebook using matplotlib like last week.*
- If it says to 'use/get an mdp file', you can download that directly to the cluster using the `wget` command by typing `wget URL`
- Instead of using the file names in the tutorial, use good file naming practice (i.e. not em.gro but t4lysozyme_setup_energymin.gro). You can set this with the `-deffnm` flag, and then adjust subsequent commands. Or alternatively, rename files after using `mv`  
- At the end, *run a 10 nanosecond MD simulation*, (note this is much longer than the tutorial) and then make a trajectory and gro file without water as described in the Analysis step.
- Here the molecule will be wrapped in the box and left without solvent (check in VMD),  Render an image of the protein and put it in the Images folder using VMD. 
- Also note, you can do your analysis while the simulation is running.
- While simulations are running, you can also read (https://livecomsjournal.org/index.php/livecoms/article/view/v1i1e5957)

### Note on timing ### 
- Minimization should take seconds
- 100 ps NVT equilibration step should take about 4-5 minutes
- 100 ps NPT equilibration step should take about 4-5 minutes
- 10 ns NPT production run should take about 8 hours on 1 CPU


2) Organize your results as follows
- Input: Put the inputs from the tutorial here in an organized way
- Setup: Put the setup steps of your work here
- Data: Put your 10ns trajectory without water here. Also put all the files you would need to run again here.
- Analysis: Put jupyter notebooks for analyzing the trajectory here
- Figures: Save you figures here

3) Edit the README.md files in each folder to explain what you have done and what the files in those directories mean.

4) Add these files to your project with `git add`. *do not* do `git add .` or `git add FOLDER` without checking that there are no large files. The raw simulation files will be too big for github and this will mess up your whole github repo. That is why you should only put the trajectory without water in the Data folder.

5) Commit and push these files to your github page.
