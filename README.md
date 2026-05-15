# MetaShotgun Analysis

# Create a conda environement

create an `ont_meta.yml`

```
name: ont_meta
channels:
  - conda-forge
  - bioconda
  - defaults

dependencies:
  # ── Java (required by Nextflow) 
  - openjdk>=17

  # ── Core language & base
  - python=3.11
  - pip

  # ── Workflow manager 
  - nextflow>=24.0

  # ── Read QC 
  - nanostat
  - nanoplot
  - fastqc
  - multiqc

  # ── ONT Preprocessing 
  - porechop_abi
  - nanoq
  - filtlong

  # ── Host removal
  - minimap2
  - samtools

  # ── Taxonomic classification 
  - sylph
  - sylph-tax
  - kaiju

  # ── Python utilities 
  - pandas
  - numpy

  # ── File utilities 
  - pigz
  - seqkit

```

on the terminal type:

```
mamba env create -f ont_meta.yml
```

then to activate the conda environement use:

```
conda activate ont_meta
```

and check all the tools have been installed

```
sylph --version
minimap2 --version
samtools --version | head -1
NanoStat --version
nanoq --version
porechop_abi --version
seqkit version
multiqc --version
```




# References 
https://github.com/ZimmermannHH/BeringSea_shotgun_sequencing

https://github.com/Sydney-Informatics-Hub/Shotgun-Metagenomics-Analysis

https://ccb.jhu.edu/data/kraken2_protocol/

https://github.com/martin-steinegger/kraken-protocol/tree/main

https://github.com/metagenomics/denbi-nanopore-training

https://benlangmead.github.io/aws-indexes/k2

https://github.com/barbarahelena/metagenomicspipeline

