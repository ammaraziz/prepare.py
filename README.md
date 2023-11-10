# prepare.py

`prepare.py` creates a tsv file for ingestion by scientific workflows.

It is a super stripped down version of `bactopia-prepare.py` from https://github.com/bactopia/bactopia-py. I butchered the script for my own needs. Full credit goes to `rpetit3` for writing this script. Please cite his work if you use this script. Make sure to checkout the `Bactopia`!

### Requirements:

- rich
- rich-click

```
pip install rich rich-click
```

Then either git clone this report or dub-get it.

### Example Usage

Example `*.fastq.gz` FASTQ files:
```
prepare.py --path fastqs/
sample          runtype         r1                            r2
sample01        paired-end      fastqs/sample01_R1.fastq.gz   fastqs/sample01_R2.fastq.gz
sample02        single-end      fastqs/sample02.fastq.gz
sample03        paired-end      fastqs/sample03_R1.fastq.gz   fastqs/sample03_R2.fastq.gz
```

Example `*_001.fastq.gz` FASTQ files:
```
prepare.py --path fastqs/ --fastq-ext '_001.fastq.gz'
sample          runtype         r1                                r2
sample01        paired-end      fastqs/sample01_R1_001.fastq.gz   fastqs/sample01_R2_001.fastq.gz
sample02        paired-end      fastqs/sample02_R1_001.fastq.gz   fastqs/sample02_R2_001.fastq.gz
sample03        paired-end      fastqs/sample03_R1_001.fastq.gz   fastqs/sample03_R2_001.fastq.gz
```
Example `*.fq.gz` FASTQ files:
```
prepare.py --path fastqs --fastq-ext '.fq.gz'
sample         runtype          r1                      r2   
sample01       single-end      fastqs/sample01.fq.gz
sample02       single-end      fastqs/sample02.fq.gz
sample03       single-end      fastqs/sample03.fq.gz
```

Example Nanopore FASTQ files:
```
prepare.py --path fastqs/ --ont
sample          runtype       r1                         r2
sample01        ont           fastqs/sample01.fastq.gz
sample02        ont           fastqs/sample02.fastq.gz
sample03        ont           fastqs/sample03.fastq.gz
```

Example changing the separator, do this if you have underscores in your sample names and you want SE reads:
```
prepare.py --path ext/ --fastq-separator '.'
sample          runtype         r1                          r2      
sample_01       single-end      fastqs/sample_01.fastq.gz
sample_02       single-end      fastqs/sample_02.fastq.gz
sample_03       single-end      fastqs/sample_03.fastq.gz
```

### Why?

Because I didn't want to reinvent the wheel, and `rpetit3` is a fantastic coder. So I went looking for something I could rework (butcher).

### Cite
https://github.com/bactopia/bactopia-py

Petit III RA, Read TD, Bactopia: a flexible pipeline for complete analysis of bacterial genomes. mSystems. 5 (2020), https://doi.org/10.1128/mSystems.00190-20.
