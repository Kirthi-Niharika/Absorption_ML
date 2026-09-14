# Adsorption energy calculations

A structural relaxation or structure optimization is the process of iteratively updating atom positions to find the atom positions that minimize the energy of the structure. Standard optimization methods are used in structural relaxations, we use the Limited-Memory Broyden–Fletcher–Goldfarb–Shanno (LBFGS) algorithm. The step number, time, energy and force max are printed at each optimization step. 

Each step is considered one example because it provides all the information we need to train models for the S2EF task and the entire set of steps is referred to as a trajectory. 
Visualizing intermediate structures or viewing the entire trajectory can be illuminating to understand what is physically happening and to look for problems in the simulation, especially when we run ML-driven relaxations. 

## Setup and relaxation of a bare slab

First, we virtually set up a bare Cu(100) surface. We'll use ASE to make the initial structure, and LBFGS to do a quick relaxation to find the lowest energy configuration. 

We'll fix the bottom couple layers of the copper surface to approximate a very thick copper slab and prevent the surface from moving. This is a very common trick in the catalysis community. 

For this demonstration, we'll use the Effective Medium Theory (EMT) calculator from ASE. It works well for simple metal structures like Cu(100) and is very fast. 
However, it won't do a good job with the adsorbate later on in the example.

### Viewing a trajectory

Below we visualize the initial, middle and final steps in the structural relaxation trajectory from above. Copper atoms in the surface are colored orange. EMT does a good job here and gets a relaxed structure very quickly. It only takes a few steps, and if you look closely you can see just the top layer of Cu atoms move a bit.

`````{tip}
Visualizations can be used as a quick sanity check to ensure the initial system is set up correctly and there are no major issues with the simulation!
`````
## Relaxation of a slab and adsorbate ("adslab")

Now that we know how to run a simple relaxation of a bare slab with ASE and a toy calculator, let's do the same thing with a methoxy (CH3O*) intermediate on the surface.

### Viewing a trajectory

Below we visualize the initial, middle, and final steps in the structural relaxation trajectory from above. Copper atoms in the surface are colored orange, the propane adsorbate on the surface has grey colored carbon atoms and white colored hydrogen atoms. The adsorbate’s structure changes during the simulation and you can see how it relaxes on the surface. In this case, the relaxation looks normal; however, there can be instances where the adsorbate flies away (desorbs) from the surface or the adsorbate can break apart (dissociation), which are hard to detect without visualization. 

`````{tip}
Visualizations can be used as a quick sanity check to ensure the initial system is set up correctly and there are no major issues with the simulation!
`````
## OUTPUT1:
![image](https://github.com/user-attachments/assets/ebfb4858-eebf-45b7-be11-cca9c217d364)
