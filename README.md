# buscoTree
Generate a core-BUSCO-gene phylogenetic tree 

Pipeline for generating a phylogenetic tree of numerous species/strains using commonly shared BUSCO genes.

Scripts are made for use on HPC machines and will need to be adapted for each individual user.

The pipeline should be run as follows:
1) runBusco.job
Run BUSCO software on selected genomes, using BUSCO v5.4.3 the Eurotiales odb10 database. This will identify all universal orthologs within the genome.

2) coreID.job
Concatenates ID's of all complete orthologs across all strains and identifies the ID's of core-orthologs.

3) alignCore.job
Concatenate core-orthologs across strains. SeqKit v2.0.0 was used to linearse sequences prior to appendage. Sequences of core-orthologs underwent multiple sequence alignment using MUSCLE v3.8.1551.

4) makeTree.job
Paste together alignments for each gene across all species and generate a tree from the multi-gene alignment using RAxML v8.2.12 (parameters -m GTRCAT -x 1 -p 1 -f a -N 1000)

References
Busco: https://academic.oup.com/bioinformatics/article/31/19/3210/211866
Seqkit: https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0163962
Muscle: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-5-113
RAxML: https://academic.oup.com/bioinformatics/article/30/9/1312/238053
