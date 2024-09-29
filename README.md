# Genome-annotation


## Q 1
If given the amino acid sequence KVRMFTSELDIMLSVNGPADQIKYFCRHWT*, what is the number of amino acids in the encoded
peptide (not including the stop codon)? Additonally, how many bases are
contained in the open reading frame of the DNA sequence encoding the
amino acids (including the stop codon)?

```python
 #Define the amino acid sequence (without stop codon '*')
peptide_sequence = "KVRMFTSELDIMLSVNGPADQIKYFCRHWT"

#Calculate the number of amino acids (excluding the stop codon)
num_amino_acids = len(peptide_sequence)

#Each amino acid is encoded by 3 bases, so the number of bases for the amino acids
num_bases = num_amino_acids * 3

#Add 3 bases for the stop codon
total_bases_in_orf = num_bases + 3

#Output the results
print(f"Number of amino acids (excluding stop codon): {num_amino_acids}")
print(f"Total number of bases in the ORF (including stop codon): {total_bases_in_orf}")
```
Answer
```text
30
93
```

## Q 2
Run prodigal on one of the genomes you have previously downloaded. Using command line tools, count how many genes were annotated
(you can use any of the output formats for this but some are easier than
others).
```shell
brew install prodigal
prodigal -i GCA_000091085.2_ASM9108v2_genomic.fna -a genes.faa -d genes.fna -o prodigal_output.txt
grep -c "CDS" prodigal_output.txt
```
Answer
```text
1063
```
## Q 3
Run prodigal on all of the genomes you have previously downloaded. Using command line tools, find which genome has the highest number of genes. Put all your code into a shell script, and put your code on the repository on Github where you keep your README with the solutions to this assignment
```shell
for genome in *.fna; do
    prodigal -i "$genome" -a "${genome%.fna}_genes.faa" -d "${genome%.fna}_genes.fna" -o "${genome%.fna}_output_allGenomes.txt"
done

# do a shell script
nano find_highest_genome.sh
# run the script which calculate all the genomes
./find_highest_genome.sh

#to print the highest gene
cat gene_counts14.txt | sort -k2 -n | tail -n 1
```

Answer
```text
GCA_000006745.1_ASM674v1_genomic.fna: 3594 genes
GCA_000006745.1_ASM674v1_genomic_genes.fna: 3565 genes
GCA_000006825.1_ASM682v1_genomic.fna: 2032 genes
GCA_000006825.1_ASM682v1_genomic_genes.fna: 2024 genes
GCA_000006865.1_ASM686v1_genomic.fna: 2383 genes
GCA_000006865.1_ASM686v1_genomic_genes.fna: 2366 genes
GCA_000007125.1_ASM712v1_genomic.fna: 3152 genes
GCA_000007125.1_ASM712v1_genomic_genes.fna: 3097 genes
GCA_000008525.1_ASM852v1_genomic.fna: 1579 genes
GCA_000008525.1_ASM852v1_genomic_genes.fna: 1569 genes
GCA_000008545.1_ASM854v1_genomic.fna: 1866 genes
GCA_000008545.1_ASM854v1_genomic_genes.fna: 1859 genes
GCA_000008565.1_ASM856v1_genomic.fna: 3248 genes
GCA_000008565.1_ASM856v1_genomic_genes.fna: 3222 genes
GCA_000008605.1_ASM860v1_genomic.fna: 1009 genes
GCA_000008605.1_ASM860v1_genomic_genes.fna: 1004 genes
GCA_000008625.1_ASM862v1_genomic.fna: 1776 genes
GCA_000008625.1_ASM862v1_genomic_genes.fna: 1769 genes
GCA_000008725.1_ASM872v1_genomic.fna: 897 genes
GCA_000008725.1_ASM872v1_genomic_genes.fna: 895 genes
GCA_000008745.1_ASM874v1_genomic.fna: 1063 genes
GCA_000008745.1_ASM874v1_genomic_genes.fna: 1059 genes
GCA_000008785.1_ASM878v1_genomic.fna: 1505 genes
GCA_000008785.1_ASM878v1_genomic_genes.fna: 1498 genes
GCA_000027305.1_ASM2730v1_genomic.fna: 1748 genes
GCA_000027305.1_ASM2730v1_genomic_genes.fna: 1737 genes
GCA_000091085.2_ASM9108v2_genomic.fna: 1063 genes
GCA_000091085.2_ASM9108v2_genomic_genes.fna: 1058 genes
ORF.fna: 0 genes
ORF_genes.fna: 0 genes
genes.fna: 1058 genes
genes_genes.fna: 1058 genes

GCA_000006745.1_ASM674v1_genomic.fna: 3594 genes
```

## Q 4
Annotate all genomes you have previously downloaded using
prokka instead of prodigal. Using shell commands, count the number of
coding sequences (CDS) annotated by Prokka. Are the total number of
genes the same as they were with prodigal? What are the differences?

```shell
# to install Prokka
brew install prokka
# creat a shell script
nano run_prokka_genomes.sh



```
