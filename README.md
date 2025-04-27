# MolecularBio1_1
BLAST searches: 2 performed with the contig nucleotide sequence (BLASTn and BLASTx)
- BLASTn: search for similar/identical sequences in a database of nucleotide sequences (results of the search: BLASTn_results.txt)
- BLASTx: search for orthologous proteins that can be synthesized by the contig sequence (o això crec) in a database of proteins (results of the search: BLASTx_results.txt)

NOTE: for picking up results, I downloaded a fasta with the first 10 sorted by E-value (determina quins resultats son més importants i significatius) in BLASTx and only the first in BLASTn as it was the only identical one

Ab-initio methods:

GeneID: run it with our contig as input and Aradibopsis Thaliana as species of interest (as it’s the one closest to our organism obtained from Blastx search)
RESULTS: 2 genes
1. Very short gene (only 6 aa): 1 exon
   Larger (341 aa): 7 exons

FGENESH: run it with our contig as input and brassica rapa as species of interest
RESULTS: 1 gene with 13 exons

GENESCAN: website does not work

Homology-based method:

We downloaded the first result of the Blastx search and exonerated it to find the exons of the gene and put all of them together (using an egrep command) in a .gff file that we then turned into a fasta file. 

COMMANDS used:

$ exonerate -m p2g --showtargetgff -q blastx.fa -t contig_11.fa -S F | egrep -w exon > contig.exonerate.gff

$ bedtools getfasta -fi contig_11.fa -bed contig.exonerate.gff > exonerate_contig.fa

$ sed -e '2,$s/>.*//' exonerate_contig.fa |grep -v '^$' > exonerate_contig_joint.fa

