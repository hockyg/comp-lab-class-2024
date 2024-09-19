# Assignment for Week 3

## Setup reminder ##
- First, get the latest changes synchronized to your Github
- Then, run `git pull' in your github folder on greene (use the terminal app)
- At the end, you will organize your results in the folder `Week3-IntroToMD` using the provided folders

## Using gromacs on Greene ##
Gromacs is already installed on greene. They are installed within "modules". To see the gromacs modules, type `module avail gromacs`

The tutorial below uses gromacs version 2018, but we will use gromacs 2020 since it is working on the cluster. You can type ` module load gromacs/openmpi/intel/2020.4` to make gromacs commands available. 

In the tutorial, whenever it says to type `gmx` you will type `gmx_mpi` since that is the name of the executable on Greene.

## Running on an interactive node ##
Do this tutorial on a compute node. The steps of file preparation etc could be done on the login node, but we will be doing actual simulations now, so you should request compute resources. 

To get an interactive node, you can type something like this:

`srun --cpus-per-task 4 --mem 8GB –t 4:00:00 --pty /bin/bash`

Which, once it starts, will give you a compute node for four hours, with 8 gigabytpes of RAM and 4 CPUs.

When we do even more serious simulations, we need to use SBATCH scripts, where you will set up a set of commands and submit those commands to the queue. There is an example in this week's lecture, and you can also now read the page https://sites.google.com/nyu.edu/nyu-hpc/training-support/tutorials/slurm-tutorial


## Week 3 assignment ##

Do the Lysozyme tutorial for Gromacs on HPC, adapting as needed
http://www.mdtutorials.com/gmx/lysozyme/index.html

Instead of using the file names in the tutorial, try to give good file names rather than just e.g. em.gro

At the end, run a 50 ns MD simulation, and then make a trajectory and gro file without water with the molecule wrapped in the box (check in VMD)

Make all the plots in the tutorial within a Jupyter notebook.

Organize your results as follows
- Input: Put the inputs from the tutorial here in an organized way
- Setup: Put the setup steps of your work here
- Data: Put your 50ns trajectory without water here. Also put all the files you would need to run again here.
- Analysis: Put jupyter notebooks for analyzing the trajectory here
- Figures: Save you figures here

Edit the README.md files in each folder to explain what you have done and what the files in those directories mean.
