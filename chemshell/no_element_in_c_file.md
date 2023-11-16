# No element in first column of .c file

The .c file is the ChemShell's format to store the position and element of each atom in the system. 
It consists on an atom-per-line file that contains for columns: element, x, y, z

## Error
It can happen (I still don't know why) that the .c file is not properly written by ChemShell and 
instead of printing the element of the atom, a `(null)` string is written in the first column.

## Solution
Use the [`repair_c_file.py`](https://github.com/MolBioMedUAB/scripts/blob/main/repair_c_file.py) script.
It requires the original `PDB` of the calculation and the `.c` file generated after the CheShell calculation. 
Additionally, the new, fixed `.c` file has to be converted into a `PDB` file. This can be done with the 
[`c_to_pdb.sh`](https://github.com/MolBioMedUAB/scripts/blob/main/c_to_pdb.sh) script.

## Future errors
It is possible that the new `.c` file doesn't contain a proper description of some bond, angles or torsions, 
so that ChemShell gives an error if the file is used for a further calculation. To solve this, and assuming
that the MM parameters are in AMBER format and that AmberTools is installed, the following steps will solve the problem:

```
c_to_pdb.sh coord_fixed.c initial_pdb.pdb                            ### coord_fixed.pdb is obtained as an output
cpptraj -p coord_fixed.pdb -x coord_fixed.pdb -y coord_fixed.rst     ### coord_fixed.rst is obtained as an output
ambpdb -p coord_fixed.pdb -c coord_fixed.rst > coord_fixed_amber.pdb ### coord_fixed_amber.pdb is obtained as an output
```

These series of commands have created a `.rst` file that can be understood by the `load_amber_coords` function of ChemShell 
and a `PDB` (`coord_fixed_amber.pdb`) that matches the `prmtop` specifications, so all files are aligned and ChemShell will
surely understand them and no further problem will be obtained.

