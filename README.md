# Hydrogen Capped Finite Cluster Model Generator
This code utilizes the Python packages ASE, Numpy, and Scipy to turn exported XYZ structures from VESTA into hydrogen capped finite clusters.
To use this code properly, You'll need to modify a few parameters and ensure your input files are saved in the right places as the correct formats.

Firstly, the input file should be located in the same place that the code is saved, in XYZ format. I'm using VESTA to expand optimized CONTCAR files from VASP and transform them into XYZ format such that I have a larger cluster to work with.
Next, you'll need to use the neighbor-list tool (cell 5) to determine if the scaling factor is the proper size. Only atoms truly bonded to one another should be included in the neighbor list. Use the view tool in ASE or VESTA to locate a few atoms. With the knowledge of a few atoms indices, the number and types of neighbors, use the neighbor list tool.

If not enough neighbors are shown in the list, increase the scaling factor. If too many show up, decrease the scaling factor. Play around with it to determine the proper amount.

Next, update the expected coordination numbers, or in other words expected amount of bonds to be formed in the system. In my case, it's a bit easier because each atom is supposed to form the same amount of bonds no matter what. Additionally in my case, oxygens are the only undercoordinated atoms.

Lastly, the code determines the optimal placements of hydrogens on undercoordinated oxygens in the system, with the assumption that it is tetrahedral in structure. It then allows you to view your cluster model and save it as a new .xyz file.

This code does have some flaws, as the tetrahedral vectors calculated may not always be correct for certain optimized structures, for example if the  oxygen atom is undercoordinated and the geometry shows that it is further into the cluster than sticking out, it will place a hydrogen on the inside of the cluster. These stragglers can easily be fixed in Avogadro or another similar viewing software if necessary.

Also in this repository is an imput file I'm using for lithium metasilicate.
Best of luck in your cluster endeavors!
-CF
