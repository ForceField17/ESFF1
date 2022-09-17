#ESFF1 - Environmental Specific Force Field version 1

Recently, we developed the environmental specific force field ESFF1 based 
on AMBER ff14SB with dihedral energy map correction (CMAP) method 
to simulate both Intrinsically Disordered Proteins (IDPs) and structured proteins.
This force fields need to transplant CHARMM energy function to AMBER's, 
which can be realized by the "Trans_FF_IDPs.pl".


##Simple Usages:
1. Use Amber tLEaP or xLEaP to generate the normal PRMTOP file.
   Note: Please be sure to use ff14SB force field (source leaprc.ff14SB), 
	since the development is based on ff14SB.
2. Copy all the files to the same directory with the PRMTOP file
	or anywhere else. I will take the same directory as example.
3. Add executable permission onto Trans_FF_IDPs if it hasn't:
	
	$ chmod +x Trans_FF_IDPs
	
4. Run the script with "-p" flag to specify the NORMAL PRMTOP file
	and "-o" flag to name the new PRMTOP file with CMAP parameters,
	and "-c" flag to specify CMAP parameter file (ESFF1.para),
	and "-e" flag to option for environment-specific force field:

	$ perl ./Trans_FF_IDPs.pl -p OLD_PRMTOP -o NEW_PRMTOP -c ./ESFF1.para -e
	
	Then an interacting UI will guild you to finish the trans-planting.

5. Followings are the optional flags and their explanations:
	-s	Silent Mode, optional.
		Run the script silently without any interacting UI.
		Note: In silent mode, all the proteins in the PRMTOP would
			be considered as IDP. And all the modified amino acids
			will be omitted.

	-h	Show the help information.
	-v	Show version information.
	

## Reference
* [Song, Dong, et al. "Environment-specific force field for intrinsically disordered and ordered proteins." Journal of Chemical Information and Modeling 60.4 (2020): 2257-2267.](https://pubs.acs.org/doi/full/10.1021/acs.jcim.0c00059)
* [Song, Dong, Ray Luo, and Hai-Feng Chen. "The IDP-specific force field ff14IDPSFF improves the conformer sampling of intrinsically disordered proteins." Journal of chemical information and modeling 57.5 (2017): 1166-1178.](https://pubs.acs.org/doi/full/10.1021/acs.jcim.7b00135)
* [Song, Dong, et al. "ff14IDPs force field improving the conformation sampling of intrinsically disordered proteins." Chemical biology & drug design 89.1 (2017): 5-15.](https://onlinelibrary.wiley.com/doi/full/10.1111/cbdd.12832)