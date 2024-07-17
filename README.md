# Tn-Seq
Analyzing transposon insertion data from DNA sequencing reads

Use the Genome_Processing code to ensure your genome files are in the correct format for use with the TnSeq_Mapping code.

Description of the prompts:
"What should the species file folder name be?:" Enter the name of the species/strain.  This folder name will be entered in a command line prompt during execution of the TnSeq_Mapping code
"Do you want to make unmappables (Y or N)?:" Type Y if you would like the software to generate a .bed file containing all of the sites which cannot be uniquely mapped using your selected kmer size
"What is the desired QScore cutoff:" Enter an integer value to designate the cutoff for acceptable Qscore for your mapped reads.  Example: Enter "20" to only accept reads with an error rate of 1 in 100 nucleotides or better.  
"What Kmer size do you want to use?:" Enter the number of nucleotides (kmer length) as an integer to generate the unmappable .bed track.  You should use the same Kmer size as the sequence read length from your instrument.
"What is the genome file:" Indicate which genome reference file you will be using.  This file needs to be a fastA file and in the home directory.  Example: "CBS138.fasta"

Use the TnSeq_Mapping code to demultiplex and map your .fastQ files to tabulate them genewise based on the supplied annotation file.

Description of prompts:
"What is the location (pathname) of the genomic files folder:" Enter the full file pathname for the genome files folder you created and named using the Genome_Processing code
"what is the location (pathname) of the Annotation File:" Enter the full file pathname for the annotation file in the .gff3 format (see example below)
"What is the Forward Read fild pathname (FastQ or FastQ Zip):" Enter the full file pathname for the forward read file obtained from the sequencing instrument
"What is the Reverse Read fild pathname (FastQ or FastQ Zip):" Enter the full file pathname for the reverse read file obtained from the sequencing instrument
"What is the prefix wanted for your file names:" Enter the desired file prefix for the output files without an extension and without spaces.  Example: "Micafungin_16ng_"
"What is the location of the index list?:"  Enter the full pathname for the .txt file containing a list of all of your indicies used for multiplexing your data.  This file should contain a string of characters with new line entry characters after each entry.  (See example below)
"Enter Index Count:" Enter an integer that indicates how many different indicies were used for a single sample.  Enter 1 if only 1 index was used, enter 2 if one sample has two separate indicies, ect.
"Enter index 1 as the index id:" Enter an integer that indicates which line entry in your index list file corresponds to the sample you are trying to demultiplex.  Enter 1 if you want to demultiplex samples containing the sequence in the first line entry in your index list file, etc.  This question repeats if you entered a number higher than 1 in the previous prompt.
"Will there be 5' or 3' trimming (Y or N):"  Enter Y if you would like to trim nucleotides off of your reads
"Five Prime Percentage to Discount for Mapping (Decimal Format):" Enter a decimal indicating which % of the total read length you would like to trim from each read in your fastQ file before mapping.  Example: Enter 12.5 if you want to trim off 6 nucleotides from a 75 nucleotide read
"Three Prime Percentage to Discount for Mapping (Decimal Format):" Same as above but for the 3' end of the read

Example of a properly formatted annotation file (as a tab separated file or .gff3 file):

ChrA  CAGL0A00099g      Gene  19457 3717  .     -     .     CAGL0A00099g
ChrA  CAGL0A00165g      Gene  33524 32685 .     -     .     CAGL0A00165g
ChrA  CAGL0A00187g      Gene  36405 34135 .     -     .     CAGL0A00187g
ChrA  CAGL0A00209g      Gene  36908 39088 .     +     .     CAGL0A00209g
ChrA  CAGL0A00231g      Gene  39889 42270 .     +     .     CAGL0A00231g
ChrA  CAGL0A00253g      Gene  43234 42563 .     -     .     CAGL0A00253g
ChrA  CAGL0A00275g      Gene  43717 44517 .     +     .     CAGL0A00275g
ChrA  CAGL0A00297g      Gene  45423 44827 .     -     .     CAGL0A00297g
ChrA  CAGL0A00319g      Gene  45626 47155 .     +     .     CAGL0A00319g

Example of an index list (as a .txt file):

TCGTGGAGCG
CTACAAGATA
TACGTTCATT
TGCCTGGTGG
TCCATCCGAG
GTCCACTTGT
TGGAACAGTA
CCTTGTTAAT
GTTGATAGTG
ACCAGCGACA
CATACACTGT
GTGTGGCGCT
ATCACGAAGG
CGGCTCTACT
GAATGCACGA
AAGACTATAG
TCGGCAGCAA
CTAATGATGG

