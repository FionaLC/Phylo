PhyloCode contains scripts designed for the preparation, processing, and manipulation of phylogenetic data, and the visualisation of phylogenetic trees. 
Most scripts are designed to be used in conjunction with https://github.com/tjcreedy/pipelines. 
All scripts are designed for Command Line usage.




**RY_Recoder.py** Recodes nucleotide sequences from an input .fasta file replacing purines ("A", "a", "G", "g") with "R" and pyrimidines ("T", "t", "C", "c") with 'Y'. RY recoding aims to mitigate against the effect of base composition biases/heterogeneity in phylogenetic inference. 
###### Usage
    python RY_Recoder.py input.fasta datatype position
e.g. 
    python RY_Recoder.py input.fasta nt N
    python RY_Recoder.py input.fasta nt3r 1
(codons 1/2/3 or N (all))




**Remove_Codon3.R** is designed to allow for the removal of the 3rd codon since RAxML and other software don't support its removal through partitioning. The aligned input nucleotide supermatrix should in .fasta format and in the correct reading frame.
###### Usage
    Rscript Remove_Codon3.R --help|-h --input|-f input.fasta --output|-o output.fasta




**Repartitioner.py** is designed to expand on partitioner.py (see link above), it is designed specifically to be used with nexus formatted partitions produced by partitioner.py for nucleotide supermatrices. It takes an input partition and repartitions to match a .fasta with the 3rd codon position prior removed.
###### Usage
    python Repartitioner.py -f partition_type input.txt output.txt
e.g. 
    python Repartitioner.py -f gc input.txt output.txt
    python Repartitioner.py -f dc input.txt output.txt
    python Repartitioner.py -f c input.txt output.txt
(gc - g+codon12, dc - direction+codon12, c - codon12)
