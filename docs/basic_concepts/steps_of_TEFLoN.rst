===============
Steps of TEFLoN
===============


.. _RepeatMasker: https://www.repeatmasker.org/

Required input data to TEFLoN2 are :

* Reference genome (.fasta)
* Short paired-end reads (.fastq) or/and binary alignment map (.bam)
* TEs annotation of reference (.bed6) or/and TEs library (.fasta)


TEFLoN2 requires to prepare a specific mapping dataset. 
It detects all TE insertions (de novo and references TEs), then
filter out low quality data to create a catalog of TE insertion, genotype them and finally estime their allele frequency.


Data preparation
----------------

Depending on the input you have TEFLoN2 uses teflon_preparation_annotation or teflon_preparation_custom.

Preparation annotation
^^^^^^^^^^^^^^^^^^^^^^

If you use TEs annotation of reference, TEFLoN2 will use teflon_prep_annoation.

You should place your files as follows:

.. code-block:: none

	data_input/
	├── library
	│	├── sample_reference_hierarchy.txt [required]
	│	├── REFERENCE_TE_ANNOTATION.bed
	│	└── TE_LIBRARY.fasta
	├── reference
	│	└── REFERENCE_GENOME.fasta
	└── samples
	    ├── bam
	    │	└── SAMPLE_NAME.bam
	    ├── read1
	    │	└── SAMPLE_NAME_r1.fastq
	    └── read2
	        └── SAMPLE_NAME_r2.fastq

In this step, TEFLoN2 uses the TE annotations to extract them from the reference, remove them and use them as TE sequences. 

At the end, we obtain a multi fasta which contains the reference without TE sequences and TE sequences.

.. code-block:: none

	WORK_DIRECTORY/data_output_PREFIX/
	└── 0-reference
		├── PREFIX.prep_MP
		│	├── PREFIX.annotatedTE.fa
		│	├── PREFIX.mappingRef.fa
		│	├── PREFIX.mappingRef.fa.amb
		│	├── PREFIX.mappingRef.fa.ann
		│	├── PREFIX.mappingRef.fa.bwt
		│	├── PREFIX.mappingRef.fa.pac
		│	├── PREFIX.mappingRef.fa.sa
		│	└── PREFIX.pseudo.fa
		└── PREFIX.prep_TF
		    ├── PREFIX.genomeSize.txt
		    ├── PREFIX.hier
		    ├── PREFIX.pseudo2ref.txt
		    ├── PREFIX.ref2pseudo.txt
		    └── PREFIX.te.pseudo.bed


Preparation custom
^^^^^^^^^^^^^^^^^^
If you do not use TEs annotation of refrence, it is required that you use an TEs library.

You should place your files as follows:

.. code-block:: none

	data_input/
	├── library
	│	└── TE_LIBRARY.fasta
	├── reference
	│	└── REFERENCE_GENOME.fasta
	└── samples
	    ├── bam
	    │	└── SAMPLE2_NAME.bam
	    ├── read1
	    │	└── SAMPLE_NAME_r1.fastq
	    └── read2
	        └── SAMPLE_NAME_r2.fastq


In this step, TEFLoN2 uses RepeatMasker_  which, together with the TE consensus library, masks the TE sequences of the reference and then removes them.

At the end, we obtain a multi fasta which contains the reference without TE sequences and TE sequences.

.. code-block:: none

	WORK_DIRECTORY/data_output_PREFIX/
	└── 0-reference
		├── PREFIX.prep_MP
		│	├── PREFIX.annotatedTE.fa
		│	├── PREFIX.mappingRef.fa
		│	├── PREFIX.mappingRef.fa.amb
		│	├── PREFIX.mappingRef.fa.ann
		│	├── PREFIX.mappingRef.fa.bwt
		│	├── PREFIX.mappingRef.fa.pac
		│	├── PREFIX.mappingRef.fa.sa
		│	└── PREFIX.pseudo.fa
		├── PREFIX.prep_TF
		│   ├── PREFIX.genomeSize.txt
		│   ├── PREFIX.hier
		│   ├── PREFIX.pseudo2ref.txt
		│   ├── PREFIX.ref2pseudo.txt
		│   └── PREFIX.te.pseudo.bed
		└── PREFIX.prep_RM
		    ├── GENOME.fasta
		    ├── GENOME.fasta.align
		    ├── GENOME.fasta.cat.gz
		    ├── GENOME.fasta.masked
		    ├── GENOME.fasta.out
		    ├── GENOME.fasta.tbl
		    └── PREFIX.bed



Mapping
^^^^^^^

.. code-block:: none

	WORK_DIRECTORY/data_output_PREFIX/
	├── 0-reference
	├── 1-mapping
	│	├── SAMPLE_NAME.sorted.bam
	│	└── SAMPLE_NAME.sorted.bam.bai
	└── sample_names.txt



Discover
--------


.. code-block:: none

	WORK_DIRECTORY/data_output_PREFIX/
	├── 0-reference
	├── 1-mapping
	│	├── SAMPLE_NAME.sorted.cov.txt
	│	├── SAMPLE_NAME.sorted.stats.txt
	└── 3-countPos
		├── SAMPLE_NAME.all_positions_sorted.txt
		└── SAMPLE_NAME.all_positions.txt


Collapse
--------

.. code-block:: none

	WORK_DIRECTORY/data_output_PREFIX/
	├── 0-reference
	├── 1-mapping
	│	├── SAMPLE_NAME.sorted.subsmpl.bam
	│	├── SAMPLE_NAME.sorted.subsmpl.bam.bai
	│	├── SAMPLE_NAME.sorted.subsmpl.cov.txt
	│	└── SAMPLE_NAME.sorted.subsmpl.stats.txt
	└── 3-countPos
		├── SAMPLE_NAME.all_positions_sorted.collapsed.txt
		├── union_sorted.collapsed.txt
		├── union_sorted.txt
		└── union.txt


Count
-----

.. code-block:: none

	WORK_DIRECTORY/data_output_PREFIX/
	├── 0-reference
	├── 1-mapping
	└── 3-countPos
		└── SAMPLE_NAME.counts.txt


Genotype
--------


.. code-block:: none

	WORK_DIRECTORY/data_output_PREFIX/
	├── 0-reference
	├── 1-mapping
	├── 3-countPos
	│	└── SAMPLE_NAME.pseudoSpace.genotypes.txt
	└── 4-genotypes
		└── SAMPLE_NAME.genotypes.txt