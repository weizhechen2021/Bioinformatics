# I writting my Homework 

Homework is a little bit challenging for me. I just write something randomly. 
changechange

The RiboWave workflow consists of:


- Pre-processing :
  - Create the annotation file for the subsequent analysis. [`create_annotation.sh`]
  - Determine the P-site position of Ribo-seq. [`P-site_determination.sh`]
  - Generate P-site tracks from Ribo-seq.[`create_track_Ribo.sh`]

- Main function :
  - Denoise [`Ribowave`]
  - Predict translated ORFs [`Ribowave`]
  - Estimate reads density for each given ORF [`Ribowave`]
  - Estimate frameshift potential for each given ORF [`Ribowave`]


## Requirements
### software
* R 
* bedtools v2.25.0 

### R packages
* reshape
* ggplot2
* rhdf5
* methods
* wmtsa
* parallel

## Before running 
It is **recommanded** to make a new directory and move the `Ribo-seq bam file` into that directory;

## Pre-processing

### 0. Create annotation

This step scans for and annotates all putative ORFs as well as define annotated ORF according to the annotation file

```
./create_annotation.sh -h
```

A helper message is shown:

```
----------------------------------------------------------------------------------------------------
RiboWave : version 1.0 
This step is set for the purpose of genome annotation.                                
Several of the output is necessary for the following steps.                         
----------------------------------------------------------------------------------------------------

Usage:
	 create_annotation.sh [-h] -G annotation.gtf -f fasta -o annotation_dir -s scripts_dir

Options:
	-G	<filename>	(annotation.gtf                                    )
	-f	<filename>	(genome fasta                                      )
	-o	<directory>	(Output annotation directory                       )
	-s	<directory>	(Script directory                                  )
	-h	          	(Help                                              )
----------------------------------------------------------------------------------------------------
```

Run `create_annotation.sh` on example:

```
scripts/create_annotation.sh -G annotation_fly/dmel-all-r6.18.gtf -f annotation_fly/dmel-all-chromosome-r6.18.fasta  -o annotation_fly  -s scripts;
```

