# Week 1

## Getting github set up
- Get GitHub student developer pack working
- Fork this github repository to your own repository by clicking "fork" and following the instructions
- Create a personal access token using these instructions (https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic) - selecting the top box so that it can read and write repositories, and make sure it expires after this class ends
- Keep a copy of this token, for example, message it to yourself in Slack. This will be your password for Github submissions

##  Set up your work folder on Greene
- ssh into greene: `ssh netid@greene.hpc.nyu.edu` on campus or using the VPN, or you can access the terminal by using `https://ood.hpc.nyu.edu`
- set up a link to your personal class folder by running `ln -s /scratch/work/courses/CHEM-GA-2671-2024fa/students/$USER $HOME/comp-lab-class`
- Now you can always get to your personal folder when you log in by typing `cd ~/comp-lab-class`
- Run the following command to set up the class python environment: `bash /scratch/work/courses/CHEM-GA-2671-2024fa/jupyter-setup/install_kernel.sh`, now this should be available when you start jupyter notebooks from ood
- Go to your class directory (`cd ~/comp-lab-class`) and clone your github repository: (`git clone https://github.com/YOUR-USER-NAME/comp-lab-class-2024.git`)

## Get some practice with the command line
- Brush up on command line. Do Command line, text-fu, and advanced-text fu (VIM part) on https://linuxjourney.com/
- Command line text editing - I suggest you learn to use the program VIM. The best tutorial is the built in one, which you can get by just typing vimvtutor on greene

## Git tutorial
Now that you know a bit about the command line, 

Follow this tutorial (https://www.w3schools.com/git/default.asp?remote=github) 

From the first lesson through `branch merge` in a fresh directory.

## Homework, due next week

1) Send your github url to the TA via slack
2) Fill out the course survey
3) Within your copy of the comp-lab-class-2024 git repository, create the folder `Week1-Introduction/AboutMe`
4) Create a new file `AboutMe/AboutMe.txt` and add some piece of information about yourself such as where you went to college and what you majored in.
5) Use git to add and commit this file and then push it to your personal github

## Extra - some programming practice:
If you've never programmed, learn a little python. A decent tutorial to follow might be https://www.w3schools.com/python/python_intro.asp from beginning to Arrays; to get regular python on greene run the command `module load python/intel/3.8.6`

Alternatively you could do this shorter one which is written by chemistry people (part 1-8) https://education.molssi.org/python_scripting_cms/. 

For this, you can get a notebook started by https://ood.hpc.nyu.edu/ -> Interactive Apps -> Jupyter Notebook on greene
