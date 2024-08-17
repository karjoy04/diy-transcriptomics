Dataset for Lecture 2.
Data are available here: [https://diytranscriptomics.com/data](https://diytranscriptomics.com/data)

Download the following files:

1. [studyDesign.txt](https://drive.google.com/file/d/1t08Ysjrg-a7yw-_eQ9_KrAphPBVtVk48/view?usp=sharing)
2. [fastq](https://drive.google.com/drive/folders/1sEk1od1MJKLjqyCExYyfHc0n7DAIy_x7). There are a total of 10 normal-sized fastq files. Save the file named `SRR8668755_1M_subsample.fastq.gz` for the `leishmania_subsample` directory. Do not unzip the files, and move them to `leishmania/fastq`, such that your directory looks like this:

	```
	leishmania/
	├─ fastq/
	│   ├─ SRR8668755.fastq.gz
	│   ├─ SRR8668756.fastq.gz
	│   ├─ SRR8668757.fastq.gz
	│   ...
	└─ studyDesign.txt
	```
You can also download the fastq files from the ENA browser directly [here](https://www.ebi.ac.uk/ena/browser/view/PRJNA525604).
3. Use `map_reads.sh` to convert the fastq file to `mapped_reads` files.
4. Pre-mapped data [here](https://drive.google.com/drive/folders/1uUUeSd3DusJHqyKOAdBdh44eayvBnDXg).
