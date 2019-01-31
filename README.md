# gonya_phylo

Pipeline designed to process transcriptome sequencing libraries through trimming, assembly, QC, single gene identification, comparison to other transcriptomes, common single gene extraction & alignment.

Pipeline consists of two parts:
1) **transcriptome-process.nf** - Individual transcriptome trimming, assembly and QC. Optional: Digital normalization.
2) **bigmclargehuge-gvl.py** - Comparison of all target transcriptomes. Single copy gene identification, comparison to single copy genes in other trnascriptomes, extraction of relevant contigs and alignment of conserved regions. Optional: Alignment conversion to `.nexus` format.

**Important: The pipeline heavily relies on naming convention for processing. Please ensure your input library conforms to the following convention, to ensure correct source transcriptome tagging throughout the processing:**
`something_Genus-species_something-else` where 
- files names are split on `_` so placement is cruical and file name does not contain spaces
- `Genus-species` is taken as the ID that the transcriptomes and contigs will be tagged with
- `something` can be any descriptor and **cannot** include `_`
- `something-else` can be any descriptor


Software utilised as part of pipeline:
- Trimmomatic: Bolger et al. 2014 Bioinfo.
- Trinity: Haas et al. 2013 Nat. Protoc.
- BUSCO2: Simão et al. 2015 Bioinfo
- hmmer3.1b2: Eddy et al. 2015 hmmer.org
- Nextflow: info@nextflow.io
- Diginorm as part of Khmer-protocols: Brown et al. 2013 http://dx.doi.org/10.6084/m9.figshare.878460
- Readseq: Gilbert 2001 iubio.bio.indiana.edu/soft/molbio/readseq/
- FastQC: Andrews 2010 bioinformatics.babraham.ac.uk/projects/fastqc

Programming language:
Both parts of pipeline (will be) in Nextflow for compatibility with other clusters. Channels mostly written in Python 2.7

