# README.md


## No element in first column of .c file
The .c file is the ChemShell's format to store the position and element of each atom in the system. 
It consists on an atom-per-line file that contains for columns: element, x, y, z

### Error
It can happen (I still don't know why) that the .c file is not properly written by ChemShell and 
instead of printing the element of the atom, a `(null)` string is written in the first column.
