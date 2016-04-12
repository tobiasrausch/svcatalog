Structural Variant Catalog
==========================

A repository for human genetic structural variants (SVs) discovered by [Delly](http://github.com/tobiasrausch/delly) in the [1000 Genomes](http://www.1000genomes.org) cohort of samples. SV sites are provided for deletions (DEL), insertions (INS) and duplications (DUP).


Re-genotyping of SVs
--------------------

To re-genotype these SVs with [Delly](http://github.com/tobiasrausch/delly) in a different cohort of samples (e.g., the YRI trio):

`./delly -t DEL -g hg19.fa -v DEL.hg19.vcf.gz -o DEL.regeno.bcf NA19238.bam NA19239.bam NA19240.bam`

The genotyping can be run in parallel, using [BCFtools](http://github.com/samtools/bcftools) to merge the BCFs/VCFs:

`./delly -t DEL -g hg19.fa -v DEL.hg19.vcf.gz -o DEL.NA19238.bcf NA19238.bam`

`./delly -t DEL -g hg19.fa -v DEL.hg19.vcf.gz -o DEL.NA19239.bcf NA19239.bam`

`./delly -t DEL -g hg19.fa -v DEL.hg19.vcf.gz -o DEL.NA19240.bcf NA19240.bam`

`./bcftools merge -o DEL.regeno.bcf -O z DEL.NA19238.bcf DEL.NA19239.bcf DEL.NA19240.bcf`


SV properties
-------------

Visualizing the SV size and frequency spectrum using [svprops](http://github.com/tobiasrausch/svprops):

`./svprops INS.hg19.vcf.gz > INS.tsv`

`Rscript svprops/R/svprops.R INS.tsv`

To visualize multiple SV types in the same plot:

`cat DEL.tsv DUP.tsv INS.tsv | sort -r | uniq > All.tsv`

`Rscript ~/scripts/cpp/svprops/R/svprops.R All.tsv`

An example plot is shown [here](http://github.com/tobiasrausch/svcatalog/blob/master/svprops.pdf).
