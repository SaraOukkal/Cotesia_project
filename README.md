README

# Project Overview

This repository contains the scripts and methods used to annotate the proviral segments of the Cotesia icipe Bracovirus (CiBV). The analysis involves several key steps: reconstructing the phylogeny of Cotesia species, assessing genome quality, conducting homology searches, and detecting conserved motifs. The following sections detail the methods and corresponding scripts used for each step.

# Materials and Methods

## Data Acquisition
The data for this project includes genome assemblies from various Cotesia species and specific Bracovirus datasets. To annotate the proviral segments of Cotesia icipe Bracovirus (CiBV), the following steps were undertaken:

**Collected Data**

Genomes: Cotesia icipe, Cotesia congregata, Cotesia typhae, Cotesia sesamiae, Cotesia rubecula, Cotesia flavipes, Cotesia glomerata, Cotesia vestalis, Cotesia chilonis, Cotesia whitfield24, Cotesia whitfield28, Cotesia whitfield31, Cotesia whitfield77.

Circles: CcBV

PDV Proviral Segments: CcBV

PDV Proviral Segments CDS: CcBV

DRJ: CcBV, CtBV, CsBV

HIM: CcBV, CtBV, CsBV

Amplification Motifs: CcBV

## Phylogenetic Analysis
Objective: Reconstruct the phylogeny of Cotesia species to identify the closest relatives useful for annotation through homology.

Phylogenetic relationships were inferred from BUSCO genes. A subset of 350 BUSCO genes was used, with sequences aligned, concatenated, and analyzed to construct the phylogenetic tree. Details on the script usage are provided in the respective sections.

**Scripts:**
BUSCO_phylogeny_choose_genes.sh selects 350 BUSCO genes that are complete in all species for phylogenetic analysis.

Snakemake_BUSCO_phylogeny performs the alignment of genes using Clustal Omega, concatenates them into a supergene, creates a partition file using catfasta2phyml.pl, and infers the phylogenetic tree with IQ-TREE.

catfasta2phyml.pl is used to create the partition file for the IQ-TREE analysis.

## Genome Quality Control
Objective: Ensure the reliability and quality of genomic data.

The quality of genomic data was assessed using QUAST v5.0.2 for alignment metrics and BUSCO v5.4.5 for conserved gene completeness. Results were consolidated into summary tables using the scripts mentioned above.

**Scripts:**
Snakemake_BUSCO_Quast assesses the quality of genomes using QUAST and BUSCO.

Regroup_BUSCO.sh consolidates BUSCO results from all species into a single table.

Regroup_Quast.sh aggregates QUAST results from all species into a single table.

## Annotation of CiBV segments

### CDS Homology Search 
Objective: Detect homologies between circles and proviral segments using CDS.

**Scripts:**
Snakemake_Mmseqs_search performs homology searches with MMseqs2.

### Conserved patterns homology search
Objective: Search for conserved motifs within the Cotesia icipe genome.

**Scripts:**
Snakemake_HMMER_search aligns the motifs, builds HMM profiles, and searches for these profiles in the Cotesia icipe genome.


## References

### Data 

Genomes:
Cotesia congregata, Cotesia typhae, Cotesia sesamiae (Provided by Clément Gilbert)
Cotesia rubecula, Cotesia flavipes, Cotesia glomerata, Cotesia vestalis, Cotesia chilonis (NCBI)
Cotesia whitfield24, Cotesia whitfield28, Cotesia whitfield31, Cotesia whitfield77 (Horizon Project)


Circles: Espagne et al. (2004)


Segments: Bézier et al. (2013)


Segments CDS: Espagne et al. (2004)


DRJ/HIM: Provided by Clément


Amplification Motifs: Gauthier et al. (2021)


### Software:

BUSCO v5.4.5: Manni et al. (2021)

QUAST v5.0.2: Gurevich et al. (2013)

Clustal Omega v1.2.3: Sievers et al. (2011)

IQ-TREE v2.0.3: Nguyen et al. (2015)

MMseqs2 v5daca424b162cc5fdf0b9cd151aebed86975cbf6: Steinegger and Söding (2017)

HMMER v3.3.2: Finn et al. (2011)
