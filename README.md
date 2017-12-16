## TaxClipper
#Workflow Outline
Build FASTA sequence database
Build Taxonomic Index of FASTA database
Use Indexed NCBI Taxonomic Tree to Parse sequences from FASTA database

#Database building
In order to build a desired FASTA sequence database this tool requires a file list containing paths to compressed GenBank Flat Files that can be downloaded from ftp://ftp.ncbi.nlm.nih.gov/genbank/. After obtaining the desired files and creating a file list of paths. the FASTA db can be created with the command -t is optional and defaults to 1:

python clipper.py -bdb -fl <file-list> -o <output name without extension> -t <thread count>

#Index Building
The next step is to build a index of the created FASTA database using the NCBI taxonomic tree. The file containing the taxonomic tree information can be found ftp://ftp.ncbi.nlm.nih.gov/pub/taxonomy/taxdump.tar.gz. The other required file associates sequences with a NCBI taxid.
For Accession numbers the files can be found ftp://ftp.ncbi.nlm.nih.gov/pub/taxonomy/accession2taxid/
For GI numbers the files can be found ftp://ftp.ncbi.nlm.nih.gov/pub/taxonomy/

Use of Accession numbers is suggested.
If using accession numbers use the command:

python clipper.py -biacc -a2t <list of *accession2taxi*gz> -tp <path to taxfump.tar.gz> -fp <path to FASTA database> -o <name of serialization without extension>
  
If using GI numbers use the command:

python clipper.py -bigi -a2t <list of gi_taxid*gz> -tp <path to taxfump.tar.gz> -fp <path to FASTA database> -o <name of serialization without extension>

#Clipping
To obtain sequences of a associated NCBI taxonomic subtree use command -txe is an optional parameter:

python clipper.py -c -txi <list of taxids to include> -txe <list of taxids to exclude> -fp <fasta database path> -sp <index path> -o <output name with extension> 
