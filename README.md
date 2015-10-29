Structural Variant Catalog
==========================

A repository for human genetic structural variants (SVs) discovered by [Delly](http://github.com/tobiasrausch/delly) in the [1000 Genomes](http://www.1000genomes.org) cohort of samples. SV sites are provided for deletions (DEL), insertions (INS) and duplications (DUP).


Re-genotyping of SVs
--------------------

To re-genotype these SVs with [Delly](http://github.com/tobiasrausch/delly) in a different cohort of samples (e.g., the YRI trio):

`./delly -t DEL -g hg19.fa -v DEL.hg19.vcf -o DEL.regeno.vcf NA19238.bam NA19239.bam NA19240.bam`

The genotyping can be run in parallel, using [BCFtools](http://github.com/samtools/bcftools) to merge the VCFs:

`./delly -t DEL -g hg19.fa -v DEL.hg19.vcf -o DEL.NA19238.vcf NA19238.bam`

`./delly -t DEL -g hg19.fa -v DEL.hg19.vcf -o DEL.NA19239.vcf NA19239.bam`

`./delly -t DEL -g hg19.fa -v DEL.hg19.vcf -o DEL.NA19240.vcf NA19240.bam`

`./bcftools merge -o DEL.regeno.vcf.gz -O z DEL.NA19238.vcf.gz DEL.NA19239.vcf.gz DEL.NA19240.vcf.gz`
