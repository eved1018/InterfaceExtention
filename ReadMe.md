### Interface Extension:

![ctla4](Media/ctla4cd80.png)
------

 
### Overview:

This program uses Intercaat (https://pubmed.ncbi.nlm.nih.gov/34499117/) to identify pharmacological relevant residues at the periphery of the protein interface. This is accomplished by defining the 'wt interface', expanding that interface by modulating the minimum interaction cutoff and/or the solvent radius, mutating the expanded positions to larger mutants (ARG and TRP by default) and assessing whether the mutant reaches the interface threshold.

![alg](Media/alg.png)
------


### Installation and Dependencies:
* Requires python 3.6 or later. Tested on python 3.9. 
* Requires Anocanda to install Modeller easily.(https://www.anaconda.com/)
1. Clone repo:
```sh
   git clone https://github.com/eved1018/InterfaceExtention
```
2. Download Modeller: https://salilab.org/modeller/download_installation.html
    * for Conda enviroment:
```sh 
        conda config --add channels salilab
        conda install modeller
```
3. Download python dependencies (pyhull, scipy, numpy):
```sh
    pip install -r requirements.txt 
```
4. Download SCRWL4 (optional): http://dunbrack.fccc.edu/lab/scwrl
5. Download qhull (optional): http://www.qhull.org/

------

### Usage:
1. Move to repo:
```sh
cd InterfaceExtension/
```
2. Run code:
```sh
python main.py 
```
------

### Command Line Arguments:
* `-pdb`: RCSB PDB id, if not provided you will be prompted to select one. If it is is in the input/ folder it will be used. Otherwise it will be downloaded from the RCSB.
* `-qc`: Query chain to find extended positions on.
* `-ic`: partner chain.
* `-sr`: solvent radius for extension (default 4.4).
* `-mi`: Interaction cutoff for extension (default 1).
* `-m:` Amino Acids used for extension (default TRP,ARG).
* `-r:` Output file name. 
* `-c:` Number of cores to use in parallel (default 4).
<br />

Add these flags to use certain features. 
*  `-p`: Run Interface Extention in parallel.  
* `-scwrl`: Use scrwl4 to remodel sidechain (default no sidechain remodeling).
* `-qh`: Use c++ qhull (default pyhull). 
* `-nomod`: (FOR TESTING ONLY) Dont use modeller and instead just change the names of the residue in the pdb. 
------

### Output:
![output](Media/results.png)

------

### Notes:
* Intercaat may not understand pdbs with insertion codes so pdb-tools fixinsert function is run to reformat the pdb. (https://github.com/haddocking/pdb-tools).
* for extended mutants argument(-m) please use upper case three letter amino acid name separated by a comma without spaces.
* if qhull is not downloaded then pyhull will be used (wrapper for qhull). For more info on pyhull see https://github.com/materialsvirtuallab/pyhull. To use qhull downloaded it (http://www.qhull.org/), update the contents of intercaat_config.ini in 'scripts/intercaatmaster' folder  and use the -qh flag in the command line.
* if Scrwl4 isnt working make sure it is properly alliased in your shell config (.bashrc or .zshrc). 

### Extension Parameters:
Increasing -sr increases the Rw.

![sr](Media/sr.png#gh-dark-mode-only)
![sr](Media/sr2.png#gh-light-mode-only)



------

Written by Evan Edelstein 
<br />
Please report any questions or complaints to steven.grudman@einsteinmed.org

------


![6waq](Media/6waq.gif)
<br/>
Extended interface highlighted in yellow.  

