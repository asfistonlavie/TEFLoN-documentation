.. TEFLoN2 documentation master file, created by
   sphinx-quickstart on Wed Oct  5 11:10:24 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to TEFLoN2's documentation!
============================================

TEFLoN2 is an improvement of `TEFLoN <https://github.com/jradrion/TEFLoN>`_. All improvements will allow it to be up to date, easier to use and more efficient.

Like TEFLoN, TEFLoN2 uses paired-end illumina sequences to both discover and analyse individual transposable element (TE) insertions. While TEFLoN requires fashion input data (cf. figure 1.A) corresponding to the mapping of the reads on a reference and TE sequences.

The first step allow detecting all TE insertions (cf. figure 1.B; de novo and references TE insertions). At the second step, the low quality data then filter out to create a catalog for all accurate TE insertions. The third step is the genotyping. The fourth and last step finally estimates the allele frequency for each individual TE insertions.

NEWS:  TEFLoN2 requires now only one command line to launch four individually scripts in an automatic way. It can also now handle pool and individual samples for the TE frequency estimation. 

.. image:: images/TEFLoN2_architecture.png

TEFLoN2 can be run on high performance computers (bigmem) or clusters and for all kind of species.

---------------
Getting started
---------------

.. toctree::
   :caption: Getting started
   :name: getting_started
   :hidden:
   :maxdepth: 1

   getting_started/installation
   getting_started/teflon2_tutorial




.. toctree::
   :caption: Basic concepts
   :name: basic_concepts
   :hidden:
   :maxdepth: 1

   basic_concepts/steps_of_TEFLoN
   basic_concepts/output_file_summary


.. toctree::
   :caption: Executing
   :name: executing
   :hidden:
   :maxdepth: 1

   executing/configure_parameter_file.rst
   executing/command_line_interface.rst

.. toctree::
   :caption: Project Info
   :name: project_info
   :hidden:
   :maxdepth: 1

   project_info/citations.rst
