Project : Analysis of Bracovirus proviral segments in the genus Cotesia

I) Data : 

  1. Genomes : 

Studied species : Cotesia congregata, Cotesia icipe (Collaboration Clément Gilbert), Cotesia whitfield77 (Horizon Project), Cotesia whitfield24 (Horizon Project), Cotesia whitfield28 (Horizon Project), Cotesia whitfield31 (Horizon Project), Cotesia rubecula, Cotesia glomerata, Cotesia flavipes, Cotesia vestalis, Cotesia sesamiae, Cotesia typhae, Cotesia chilonis.

Positive control species :  Cotesia congregata, Cotesia typhae, Cotesia sesamiae, Cotesia vestalis.
Outgroup for phylogeny : Microplitis demolitor 

  2. Bracovirus proviral segments and circles : 
  
Proviral segments : congregata (5) , typhae (37), sesamiae (26) → 68
Circles : congregata (30), plutellae (24), vestalis (65, pool of two different studies) → 119
Proviral segments genes : congregata (40), flavipes (12), glomerata (14), vestalis (40) → 106
  
  3. Conserved patterns : 

DRJ : 
 - DRJ3 : congregata (35), sesamiae (19), typhae (22) → 76
 - DRJ5 : congregata (36), sesamiae (20), typhae (23) → 79
HIM : congregata (12), sesamiae (14), typhae (16) → 42
Amplification pattern : 
 - Type 1 head : congregata (5) 
 - Type 1 tail : congregata (5) 
 - Type 2 head : congregata (7) 
 - Type 2 tail : congregata (7) 

II) Genomes Quality control : 

Quast 5.0.2 analysis (for alignment size, N50, GC percentage) and BUSCO 5.4.5 analysis (for conserved genes) with the dataset insecta_odb10 (1367 genes) were performed on all 14 genomes. 
Script : Snakemake_BUSCO_Quast
Input : {Genome_ID}.fasta, Species_list
Output : 
  - Rule BUSCO : BUSCO/{Genome_ID}/run_insecta_odb10/full_table.tsv
  - Rule Quast : Quast/{Genome_ID}/report.tsv
 
III) Species phylogeny : 

This step relies on genes predicted by the BUSCO analysis. 
BUSCO genes complete for all species were chosen to infer the phylogeny. If the number of these genes is > to 350, a random subset of 350 genes are chosen to perform the analysis. 
The DNA sequences of these genes for all species are regrouped in a folder with one file per gene. 

Script : BUSCO_phylogeny_choose_genes.sh
Input : BUSCO results directories, Species_list
Output : Directory with one file per gene containing sequences for all species. $Gene.fasta

Sequences for each gene are aligned using Clustal Omega (version?) 




  


