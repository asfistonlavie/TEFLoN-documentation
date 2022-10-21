====================
Output files summary
====================

Here is the structure of the output files obtained after running the pipeline.


.. code-block:: none

	WORK_DIRECTORY/data_output_PREFIX/
	├── 0-reference
	│	├── PREFIX.prep_MP
	│	│	├── PREFIX.annotatedTE.fa
	│	│	├── PREFIX.mappingRef.fa
	│	│	├── PREFIX.mappingRef.fa.amb
	│	│	├── PREFIX.mappingRef.fa.ann
	│	│	├── PREFIX.mappingRef.fa.bwt
	│	│	├── PREFIX.mappingRef.fa.pac
	│	│	├── PREFIX.mappingRef.fa.sa
	│	│	└── PREFIX.pseudo.fa
	│	├── PREFIX.prep_TF
	│	│   ├── PREFIX.genomeSize.txt
	│	│   ├── PREFIX.hier
	│	│   ├── PREFIX.pseudo2ref.txt
	│	│   ├── PREFIX.ref2pseudo.txt
	│	│   └── PREFIX.te.pseudo.bed
	│	└── PREFIX.prep_RM          --------
	│	    ├── GENOME.fasta               |
	│	    ├── GENOME.fasta.align         |
	│	    ├── GENOME.fasta.cat.gz        |--- Specific to prepration custom 
	│	    ├── GENOME.fasta.masked        |
	│	    ├── GENOME.fasta.out           |
	│	    ├── GENOME.fasta.tbl           |
	│	    └── PREFIX.bed        ----------
	├── 1-mapping
	│	├── SAMPLE_NAME.sorted.bam
	│	├── SAMPLE_NAME.sorted.bam.bai
	│	├── SAMPLE_NAME.sorted.cov.txt
	│	├── SAMPLE_NAME.sorted.stats.txt
	│	├── SAMPLE_NAME.sorted.subsmpl.bam
	│	├── SAMPLE_NAME.sorted.subsmpl.bam.bai
	│	├── SAMPLE_NAME.sorted.subsmpl.cov.txt
	│	└── SAMPLE_NAME.sorted.subsmpl.stats.txt
	├── 3-countPos
	│	├── SAMPLE_NAME.all_positions_sorted.collapsed.txt
	│	├── SAMPLE_NAME.all_positions_sorted.txt
	│	├── SAMPLE_NAME.all_positions.txt
	│	├── SAMPLE_NAME.counts.txt
	│	├── SAMPLE_NAME.pseudoSpace.genotypes.txt
	│	├── union_sorted.collapsed.txt
	│	├── union_sorted.txt
	│	└── union.txt
	├── 4-genotypes
	│	└── SAMPLE_NAME.genotypes.txt
	└── sample_names.txt


Most useful output
------------------


