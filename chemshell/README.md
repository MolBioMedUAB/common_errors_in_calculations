# README.md
Summary of errors to easily check.

## No element in first column of .c file (no_element_in_c_file.md)
The .c file is the ChemShell's format to store the position and element of each atom in the system. 
It consists on an atom-per-line file that contains for columns: element, x, y, z

### Error
It can happen (I still don't know why) that the .c file is not properly written by ChemShell and 
instead of printing the element of the atom, a `(null)` string is written in the first column.


## unexpected torsion connectivity (unexpected_torsion_connectivity.md)

This error appears when connectivity of .c file (containing the coordinates in ChemShell format) and generated from a PDB does not match the connectivity in the parameters.

### Error
In this case, there is a torsion defined for a connection that does not appear in .c because atom 10599 has been moved too far.

```
unexpected torsion connectivity
param: connectivity pattern for atom sequence 5803 10596 10597 10599 :
 1 0 0
   1 0
     0
       does not match any recognised for a improper torsion
param: JUNCTION STATUS OF atom sequence 5803 10596 10597 10599 :
 0 0 0 0
param: QC STATUS OF atom sequence 5803 10596 10597 10599 :
 1 1 1 1
param.c: Error adding AMBER FF parameter cosine dihedral
trap
ChemShell exiting code 1
```
