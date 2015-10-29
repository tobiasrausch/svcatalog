Structural Variant Catalog
==========================

A repository for human genetic structural variants (SVs) discovered by [Delly](https://github.com/tobiasrausch/delly) in the [1000 Genomes](www.1000genomes.org) cohort of samples. SV sites are provided for deletions (DEL), insertions (INS) and duplications (DUP).


Re-genotyping of SVs
--------------------

To re-genotype these SVs with [Delly](https://github.com/tobiasrausch/delly) in a different cohort of samples (e.g., the YRI trio):

`./delly -t DEL -g hg19.fa -v DEL.hg19.vcf -o DEL.regeno.vcf NA19238.bam NA19239.bam NA19240.bam`




