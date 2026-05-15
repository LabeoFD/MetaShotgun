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

# DBs installation

# syldb
# Sylph Pre-built Databases
> Hosted at `http://faust.compbio.cs.cmu.edu/sylph-stuff/` and at `https://storage.googleapis.com/sylph-stuff`

---

## 🦠 Prokaryotic (GTDB)

| Database | Date | Size | c-param | Download |
|---|---|---|---|---|
| GTDB r232 | 2026-04-18 | 24 GB | c200 | [gtdb-r232-c200-dbv1.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/gtdb-r232-c200-dbv1.syldb) |
| GTDB r232 (fast) | 2026-04-18 | 4.9 GB | c1000 | [gtdb-r232-c1000-dbv1.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/gtdb-r232-c1000-dbv1.syldb) |
| GTDB r226 | 2025-05-01 | 18.4 GB | c200 | [gtdb-r226-c200-dbv1.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/gtdb-r226-c200-dbv1.syldb) |
| GTDB r226 (fast) | 2025-05-01 | 3.7 GB | c1000 | [gtdb-r226-c1000-dbv1.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/gtdb-r226-c1000-dbv1.syldb) |
| GTDB r220 | 2024-04-24 | 13.1 GB | c200 | [gtdb-r220-c200-dbv1.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/gtdb-r220-c200-dbv1.syldb) |
| GTDB r220 (fast) | 2024-04-24 | 2.7 GB | c1000 | [gtdb-r220-c1000-dbv1.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/gtdb-r220-c1000-dbv1.syldb) |
| GTDB r214 | 2023-10-01 | 10.1 GB | c200 | [v0.3-c200-gtdb-r214.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/v0.3-c200-gtdb-r214.syldb) |
| GTDB r214 (fast) | 2023-10-01 | 2.1 GB | c1000 | [v0.3-c1000-gtdb-r214.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/v0.3-c1000-gtdb-r214.syldb) |

> **c200** = higher sensitivity (recommended) | **c1000** = faster, uses less RAM

---

## 🦠 Viral

| Database | Date | Size | Best for | Primary (faust) | Mirror (Google Cloud) |
|---|---|---|---|---|---|
| IMG/VR 4.0 | 2023-10-17 | 2 GB | Environmental / pathogenic ⭐ | [imgvr_c200_v0.3.0.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/imgvr_c200_v0.3.0.syldb) | [mirror](https://storage.googleapis.com/sylph-stuff/imgvr_c200_v0.3.0.syldb) |
| viral RefSeq | 2023-10-17 | 23 MB | Known pathogens (NCBI annotated) ⭐ | ⚠️ 404 on faust | [mirror](https://storage.googleapis.com/sylph-stuff/viral_refseq.syldb) |
| UHGV (c200) | 2025-06-15 | 217 MB | Human gut viruses | [uhgv_c200_dbv1.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/uhgv_c200_dbv1.syldb) | [mirror](https://storage.googleapis.com/sylph-stuff/uhgv_c200_dbv1.syldb) |
| UHGV (c100) | 2025-06-15 | 415 MB | Human gut viruses (sensitive) | [uhgv_c100_dbv1.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/uhgv_c100_dbv1.syldb) | [mirror](https://storage.googleapis.com/sylph-stuff/uhgv_c100_dbv1.syldb) |

> ⭐ **For environmental + pathogenic samples: download both IMG/VR 4.0 and viral RefSeq**

---

## 🍄 Eukaryotic / Fungi

| Database | Date | Size | Primary (faust) | Mirror (Google Cloud) |
|---|---|---|---|---|
| RefSeq Fungi 2025 ⭐ newest | 2025-10-12 | 747 MB | [fungi-refseq-2025-10-11-c200-dbv1.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/fungi-refseq-2025-10-11-c200-dbv1.syldb) | [mirror](https://storage.googleapis.com/sylph-stuff/fungi-refseq-2025-10-11-c200-dbv1.syldb) |
| RefSeq Fungi 2024 | 2024-07-25 | 677 MB | [fungi-refseq-2024-07-25-c200-v0.3.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/fungi-refseq-2024-07-25-c200-v0.3.syldb) | [mirror](https://storage.googleapis.com/sylph-stuff/fungi-refseq-2024-07-25-c200-v0.3.syldb) |

---

## 🌍 Environmental MAGs

| Database | Date | Size | Best for | Download |
|---|---|---|---|---|
| SMAG | 2023-11-29 | 2.6 GB | Soil samples | [SMAG-c200-v0.3.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/SMAG-c200-v0.3.syldb) |
| OceanDNA | 2023-11-29 | 789 MB | Ocean samples | [OceanDNA-c200-v0.3.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/OceanDNA-c200-v0.3.syldb) |
| TARA Euk MAGs | 2023-11-29 | 927 MB | Ocean eukaryotes | [tara-eukmags-c200-v0.3.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/tara-eukmags-c200-v0.3.syldb) |
| UHGG (all) | 2023-10-19 | 26.7 GB | Human gut (all genomes) | [uhgg_all_c200_v0.3.0.syldb](http://faust.compbio.cs.cmu.edu/sylph-stuff/uhgg_all_c200_v0.3.0.syldb) |

---

## ✅ Recommended Downloads by Sample Type

| Sample Type | Must Have | Optional |
|---|---|---|
| **Environmental** (soil, water, etc.) | `gtdb-r232-c200` + `imgvr_c200_v0.3.0` | `SMAG`, `OceanDNA`, `fungi-refseq-2025` |
| **Human gut** | `gtdb-r232-c200` + `uhgv_c200_dbv1` | `uhgg_all_c200`, `fungi-refseq-2025` |
| **Clinical / mixed** | `gtdb-r232-c200` + `imgvr_c200_v0.3.0` | `fungi-refseq-2025` |
| **Low RAM (<32 GB)** | `gtdb-r232-c1000` + `imgvr_c200_v0.3.0` | — |

---

Under the `DBs` repository create a `sylph` folder. 

Then proceed to download the databases 

```
# Prokaryotes — GTDB r232 (latest, 24 GB)
sudo wget -c http://faust.compbio.cs.cmu.edu/sylph-stuff/gtdb-r232-c200-dbv1.syldb
# Viruses — IMG/VR 4.0
wget -c http://faust.compbio.cs.cmu.edu/sylph-stuff/imgvr_c200_v0.3.0.syldb

```

You can find all the databases to download from under this [link](http://faust.compbio.cs.cmu.edu/sylph-stuff/)

# References 
https://github.com/ZimmermannHH/BeringSea_shotgun_sequencing

https://github.com/Sydney-Informatics-Hub/Shotgun-Metagenomics-Analysis

https://ccb.jhu.edu/data/kraken2_protocol/

https://github.com/martin-steinegger/kraken-protocol/tree/main

https://github.com/metagenomics/denbi-nanopore-training

https://benlangmead.github.io/aws-indexes/k2

https://github.com/barbarahelena/metagenomicspipeline

