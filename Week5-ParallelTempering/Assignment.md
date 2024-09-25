# Week 5 - Parallel Tempering
1) Run an MD simulation of alanine dipeptide at 300K for 15 ns on 1 cpu, using gromacs 2018. The files as input for grompp are provided in Input/. The simulation should take about 1 minute

2) Use mdtraj in a jupyter notebook to compute the phi and psi dihedral angles from these data. Make a plot of phi vs time and psi vs time.
- Load the trajectory in VMD and make a nice picture of alanine dipeptide for your Figures folder

3) Make a free energy surface in phi, psi space from this data. In otherwords, compute a 2d histogram of the phi, psi data compute `F(phi,psi)=-log(histogram)`, and plot `F(phi,psi)-min(F(phi,psi))` nicely labeled, with a colorbar, etc. 
- Try e.g. 25 bins in each direction spanning the *full range of allowed angles*.
- Warning: be careful about the shape of your arrays of phi and psi angles and what is in them
- If you are plotting with imshow, make sure your plot ends up with an orientation that makes it look like a Ramachandram map. If it is not that orientation, why? You have to look at the documentation/examples
- Once you get this working, turn the FES generation into a function that takes the mdtraj trajectory as input and returns the FES on a grid and the bin centers for plotting, this will make the next part very fast

4) Parallel tempering 
- Set up 3 directories called `T300` `T400` and `T600` which contain a file adp.tpr, except the temperature in adp.tpr is equal to 300, 363 or 440 respectively.
-- While doing this, write a script or README file saying the commands that you ran and what you changed
- Request an interactive node with 3 tasks-per-node and 1 cpu per task
- Run a 5 ns parallel tempering simulation that exchanges every 1000 fs by doing
 `mpirun -np 3 gmx_mpi mdrun -s adp -multidir T300/ T400/ T600/ -deffnm adp_exchange3temps -replex 500`
Check the log files to see what are in them. Is the exchange probability good?
- Note: this will take longer due to the exchanges
- Using 'gmx_mpi energy', calculate the potential energy in each replica. Compute a histogram of energy in each case, and plot all the histograms on the same plot. Do they overlap well?
- Make a free energy surface for T=300 using the data in T=300. Do you now see the whole surface? Set the maximum free energy to 6 kT
--Now make a free energy surface for the other temperatures. Do you see how these differ? 
- use the script demux.pl (available after loading gromacs module) on the log file in T300/ to generate files "replica_index.xvg  replica_temp.xvg". Plot how each replica is moving in temperature in replica_temp (you may have to do every 100 frame to see what's happening) and make sure it goes up and down

5) Save your results
- Include at least your Jupyter notebook for analysis, plots of replica exchanges and free energy surfaces, and a picture of alanine dipeptide. If you want you can also include a movie of alanine dipeptide at 300K from replica exchange for practice (don't forget to align the molecule to itself)
