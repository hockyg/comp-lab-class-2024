1) Sync the latest class github changes to your github. Use git pull in your comp-lab-class-2024 directory on greene to get the data for this week

2) Use vmd to visualize the structure of ubiquitin, and the simulation of beta amyloid. These files are in the Data folder, you figure out which is which based on the file names.
	- This will be facilitated by the VMD tutorial - https://www.ks.uiuc.edu/Training/Tutorials/vmd/tutorial-html/
	- Look at 'Working with a Single Molecule' and 'Trajectories and Movie Making'

3) Do a small python tutorial as needed, e.g. https://education.molssi.org/python_scripting_cms/ 

4) Make a jupyter notebook that 
	a) reads in the data file Data/1hz3_T310.run.25000000.energy.xvg
	b) Make 6 separate plots for each quantity contained in this file vs time, with time in ns (Hint: open the file in a text editor and take a look at the header)
	c) Make a plot that has kinetic energy and temperature on the same plot, where the left axis is temperature and the right axis is kinetic energy, using different colors and different axis labels
	d) This is a good opportunity to test out ChatGPT or other such tools

6) Make a jupyter notebook that uses mdtraj to
	a) read in the ubiquitin structure
	b) print the total number of hydrogen bonds
	c) compute the number of helical amino acids

7) Make a jupyter notebook that uses mdtraj to 
	a) read in the md trajectory of beta amyloid in the Data folder
	b) compute the end-end distance at each time, and the radius of gyration at each time
	c) plot the end-end distance and radius of gyration vs time on the same plot, clearly labeled (same y axis is fine this time)
	d) plot a normalized histogram of end-end distance and another of radius of gyration
	

If this is too easy, explore some of the other features of mdtraj and mdanalysis, such as atom selection
