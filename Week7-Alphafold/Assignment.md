# Week 7

## This week we will use alphafold to predict structures, and learn how to use VMD to visualize these structures

The PDB: https://www.rcsb.org/

Alphafold3 server: https://alphafoldserver.com/

Colabfold server: https://colab.research.google.com/github/sokrypton/ColabFold/blob/main/AlphaFold2.ipynb

Refs:
- Alphafold2: https://www.nature.com/articles/s41586-021-03819-2
- Alphafold3: https://www.nature.com/articles/s41586-024-07487-w (perspective: https://www.nature.com/articles/s41594-024-01350-2)
- Colabfold:  https://www.nature.com/articles/s41592-022-01488-1
- Colabfold protocol: https://www.nature.com/articles/s41596-024-01060-5

Overall instructions:

For this assignment, you'll mainly be using web servers. Put all the FASTA files you use for this lab into an `Inputs` folder. 

Make a different folder for each of the other parts. If you are comparing to a PDB file, also put the PDB file in the folder for that protein. When you make images for each protein, put those in an Images folder within each of the protein subfolders.

Note that the alphafold server outputs `.cif` files, which you can open in VMD the same way you open PDB files.

Put your alphafold cif and pdb predictions that you are using into your git as well, but first check using `du` that nothing is more than a few MBs before you do `git add`.

Lab steps:

0. While waiting for one of the later parts, make sure you know everything in the VMD tutorial from "Working with a Single Molecule" through "Working with Multiple Molecules", `https://www.ks.uiuc.edu/Training/Tutorials/vmd/tutorial-html/`

1. Studying an important viral protein:
- This page has the structure and sequence of SARS-Cov-2 Helicase NSP 13, however it is an unbound form
- Use the alphafold server to predict the structure of bound to the RNA sequence UUUUUUUU, and include 1 ATP molecule
- Use VMD to superimpose one of the bound predictions from AF3 with the crystal structure. Color the RNA, AF3 prediction, and PDB structure differently. Put an image of this in your Images folder
- Use VMD to load all 5 cif predictions and show all of them on top of each other, aligned. Color by BETA aka the plDDT score. Save an image in the Images folder
- In a jupyter notebook, use mdtraj to find and print out the amino acids in NSP13 which are within 0.5 nm of RNA phosphate atoms. Also find those within 0.5 nm of the uricil oxygens. _Note down if there is anything special about these amino acids or not, what you expect, and why._

2. Using alphafold3 to study a protein-protein interaction 
- We will study the interaction of the protein Actin with Profilin in Alphafold2 and Alphafold3. There are several crystal structures to compare to, e.g. https://www.rcsb.org/structure/2BTF
- Generate a prediction of Actin bound to profilin with an ATP and Magnesium using AF3 (hint, you can paste the whole FASTA of both proteins into the input box. Remove the X's)
- Generate a prediction of Actin bound to profilin with an ADP and Magnesium using AF3
- Overlay a prediction with ATP and ADP and see how they differ. In VMD, use ribbon diagrams, but also show with CPK representation the amino acids within 5 angstroms of the nucleotide, and also show the nucleotide. Color them so they are distinguishable. Put this image in your Images directory

- Generate a prediction of Actin bound to profilin using Colabfold. Here you have to give the FASTA sequences separated by a ':'. The rest of the options should be okay. This might take a little while to run (~10 min for me).
- When done, align the AF2 and AF3 predictions, coloring differently, and put an image in the Images directory. 
- In a jupyter notebook, align an AF2 and AF3 prediction using the actin (chain A). Compute the distance between actin residue i in the two models for all i. Make a bar chart of this distance vs residue number. Are there any regions that are very different? Note if these are disordered regions based on what you see in VMD or if they are near the nucleotide.

3. Using AF2 to generate an ensemble of structures
- Colabfold can be used to generate an ensemble of predictions for a protein. We previously studied the mini protein arp-est using MD. (https://www.rcsb.org/structure/1v1d), and you could see how part of it flops around and part of it stays stable. 
- Run a Colabfold prediction for this 31-amino acid sequence. *However-this time* select `max_msa: 32_64, num_seeds: 8` and select `use_dropout` as described in the Nature Protocols paper. Now you will have 8x5 predictions. 
- In VMD, superimpose all the proteins and save an image (you can load them all at once with `vmd *.pdb` but then you have to figure out in the Representations->Trajectory tab how to show them all at once. Which part is floppy, is it what you expect?
- In MDtraj, superimpose all the proteins and compute the root-mean-squared fluctuation for each residue. Plot this verses residue ID, similar to what was done in the previous part.

