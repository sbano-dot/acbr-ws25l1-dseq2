# Create Conda Environment with Miniconda
Iam creating a conda environment for DESeq2 data analysis
with R and Bioconductor in my windows system using Windows 
subsystem Linux (WSL)
## Code in WSL terminal
-Start the WSL Windows
-Type the following to creat a conda environment for R4.5 names as R4.5WS
```{cmd}
Condea creat --name R4.5WS
```
-Activate the R4. 5WS Conda environmentas follows
```{CMD}
conda activate R4.5WS
```{CMD}
conda install conda-forge::r-base
```
'conda-forge' is the channel from anaconda.org.[conda-forge for rbaser4.5] {https://anaconda.org/conda-forge/r-base}