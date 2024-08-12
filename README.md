# diy-transcriptomics
DIY Transcriptomics: RNA-seq Analysis  
Course link: https://diytranscriptomics.com/  


Welcome to my DIY Transcriptomics project repository! This repository contains code, scripts, and notes from my journey through the RNA-seq analysis section of the DIY transcriptomics course. The aim is to apply the concepts learned and create a resource for future reference. I also used harrisonized/diy-transcriptomics GitHub repository as a supplement to help me with parts that are hard to follow and reproduce for custom analysis. 
I will also diverge and analyze/visualize the data partly in Python aside from R.   


Project Structure  
/data: Raw and processed data files used in the analysis.  
/scripts: Custom scripts for processing RNA-seq data, including quality control, alignment, quantification, and differential expression analysis.  
/notebooks: Jupyter notebooks document the step-by-step analysis process, with explanations and visualizations. I will mainly use VSCode to write and execute the code.     
/results: Output files from the analysis, such as count matrices, plots, and differential expression results.  
/docs: Notes and additional documentation related to the RNA-Seq analysis.  

Tools & Packages  
This project uses the following tools and packages:  
Python: For scripting, data analysis, and visualization.  
R: For statistical analysis and visualization.  
Bioconductor: R packages for analyzing high-throughput genomic data.  
DESeq2: Differential expression analysis.  
STAR: RNA-seq read aligner.  
FastQC: Quality control for high-throughput sequence data.  

Notes:  
This repository is a work in progress as I continue learning and updating the analysis.
Feel free to contribute or provide feedback!  

## Library Installations  
As expected, it was quite complex for a beginner. 
1. Install Miniconda3 from here. I downloaded the Miniconda3-latest-MacOSX-arm64.sh and used chmod +x to make it executable.
See: https://protocols.hostmicrobe.org/conda.

2. Created the rnaseq conda environment. Here is an excellent guide to understand why we need to use conda for creating env--> https://www.freecodecamp.org/news/why-you-need-python-environments-and-how-to-manage-them-with-conda-85f155f4353c/

```
conda create --name rnaseq
conda activate rnaseq
conda config --add channels bioconda
conda install pip

# packages
pip install multiqc
conda install fastqc
pip install sourmash
```
3. Install Kallisto.
```
# install brew and add to $PATH
git clone https://github.com/Homebrew/brew homebrew
eval "$(homebrew/bin/brew shellenv)"
brew update --force --quiet
export PATH="~/homebrew/bin:$PATH"  # you can replace the ~ with your path to home if this doesn't work

brew install kallisto
```
4. Install Centrifuge with Rosetta 2.
```
# install Rosetta 2
/usr/sbin/softwareupdate --install-rosetta --agree-to-license

# Download Centrifuge from here: http://www.ccb.jhu.edu/software/centrifuge/index.shtml
# Releases > Mac OS X x86_64 binary
#if permission denied
#check Permissions: chmod -R +x path/centrifuge-1.0.4.1
cd path/centrifuge-1.0.4.1
#run the command
make
or
sudo make

```
5. Install renv
I decided to go for renv to manage packages in R as it's been mentioned that using conda can cause many package version conflicts in R.
```
install.packages("renv")
renv::init()
#install packages specifically for your project
install.packages('hexbin')
install.packages('cowplot')
install.packages('gt')
install.packages("webshot2")
install.packages('DT')
install.packages("tidyverse")
install.packages("plotly")
install.packages('textshape')
install.packages('R2HTML') #update R if not executing on the current R.

# biology-focused packages
#install BiocManager from Rstudio
install.packages("BiocManager", repos = "https://cloud.r-project.org/")
BiocManager::install("rhdf5")
BiocManager::install("tximport")
BiocManager::install("ensembldb")
BiocManager::install("beepr")
BiocManager::install("EnsDb.Hsapiens.v86")
BiocManager::install("BSgenome.Mfuro.UCSC.musFur1")  # Mustela putorius furo
BiocManager::install("biomaRt")  
BiocManager::install("edgeR")
BiocManager::install("DropletUtils")
BiocManager::install("scran")
BiocManager::install("SingleR")
BiocManager::install('celldex')
BiocManager::install("densvis") 
BiocManager::install("scater")  
```
6. Install Tensorflow and CellAssign

```
conda create --name r-reticulate python=3.9 #for creating env using conda
install.packages("tensorflow")
reticulate::use_condaenv('r-reticulate')  # IMPORTANT!
tensorflow::install_tensorflow(extra_packages='tensorflow-probability')
or
#install the R Packages within renv
renv::install("tensorflow")
renv::install("reticulate")

# It is also important to create an empty project directory beforehand to avoid getting the following warning when trying to snapshot renv environment due to the large number of unnecessary files in the project directory

> renv::snapshot()

A large number of files have been discovered.
It may take renv a long time to crawl these files for dependencies.
Consider using .renvignore to ignore irrelevant files.
See ?renv::dependencies for more information.
Set options(renv.config.dependencies.limit = Inf) to disable this warning.

reticulate::conda_create("r-reticulate")
reticulate::use_condaenv("r-reticulate", required = TRUE)
tensorflow::install_tensorflow(extra_packages = "tensorflow-probability")
renv::snapshot() #to record current state
renv::restore() #to restore the setup later
```
7. Backup to commit the updated renv.lock file to version control.
```
#done to ensure that all changes are tracked for future reference and reproducibility.
#bash commands

git init
git status
git add path/renv.lock #add your path directory
git commit -m "Add renv.lock file"
git checkout main
git merge renv
git push origin main
#to check the root directory files 
pwd
ls -a  

#The process was more complicated than expected as I kept making mistakes while creating a branch and merging it with the main at the git repository. 

```
   


   
