# unexpected torsion connectivity

This error appears when connectivity of .c file (containing the coordinates in ChemShell format) and generated from a PDB does not match the connectivity in the parameters.

## Error
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
´´´
## Solution

Since this error comes from the creation of a pdb with modified coordinates, where connectivity has changed, 
you have to be sure that the atoms with different coordinates are QM atoms and that their connections (bonds, angles and torsions) 
only envolve QM atoms. If this is the case, a .c file from the prmtop and inpcrd can be created so it is used in the conn= key of the
mm_theory in ChemShell. Thus, the connectivity will be read correctly and the error will be bypassed even though you are working with the
desired coordinates.
