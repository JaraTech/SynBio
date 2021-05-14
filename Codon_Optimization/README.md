# PIPELINE FOR CODON OPTIMIZATION

This code is a tool to optimize the codons of any given
nucleotide sequence for any host species. The script is divided into
several steps:
1. Install de required packages
2. Download the libraries of the installed packages
3. Input data for the pipeline
4. Get the codon usage of the host species:
   - Retrieve CDSs. The sequences will be sourced from the database "refseq"
     and are predicted CDSs.
   - Get the number of counts for every codon. Based only on in-frame and
     M-starting CDSs.
   - Quality check. Randomly select a CDS and an aminoacid. Same number of
     synonym codons as selected aminoacid.
5. Build the data table with as many rows as different codons (64).
6. Prepare gene of interest (GOI):
   - Scan the fasta file and convert into a 1-64 code sequence.
7. Optimization. There are two methods:

   A) Sampling: this method substitute every codon by a codon encoding for the same aminoacid, taking the relative frequence as the probability for substitution. A given position might remain the same. It is a randomized process and everytime will result something different.
    - Generate list of probabilities.
    - Substitute every position. Get codon and code sequences.
        
   B) Threshold: this method acts on those codons whose relative frequency is below the threshold. Every position in the sequence with such a codon is substituted by the synonym codon with the highest frequency. It is a fixed process based on the last four columns of the data table. It is needed to set the threshold.
      
8. Quality checks. Detection of code errors and defective results.
9. Save the files in a new directory.


You can find the file [here!](https://github.com/JaraTech/SynBio/blob/main/Codon_Optimization/codon_optimization.Rmd)
