# Reproductive-failure-and-lethal-haplotypes
The change in the expected Mendelian inheritance patterns
The ability of parents to contribute equally to the next generations may alter the expected Mendelian inheritance patterns, resulting in a decline in reproductive performance. The availability of genomic markers has facilitated the way to investigate such phenomena as well as to highlight potential lethal alleles. The assessment could be done based on SNP markers or haplotypes. The latter could be more useful with low-density genotypes.


DevHaplotype calculates the observed number from each possible mating. User needs to provide three files:

**Pedigree file**: No header. Three columns for animal, sire and dam (at least one space or tab between the columns). The animal ID must start from 1 to n, where n is the number of animals that have genotypes. Pedigree can be genotyped using pedRenum.

**Example for 4 animals**:
```
1 0 0
2 1 0
3 1 2
4 3 2
```
**Genotypes file**: No header or row names and no spaces between genotypes. The genotypes should be phased and in the format 0234 and 5 for missing (as shown in the example file).

**Example for 5 SNPs**:
```
30224
24402
40332
30232
```
Map file: Chromosome, SNP ID and position.

Example:
```
1  SNP1 7523 
1  SNP2 65632
1  SNP3 85631
2  SNP4 96363
2  SNP5 118563
```
Outputs are saved in **DevHapOut_WinSize_X.txt**, where **X** is the window size.
```
Headers ... 
1 1 SNP1 2 7523 65632 0 0 2 0 0 0 0 0 0 0 0 0 0 0 0 11 0.375
1 1 SNP1 2 7523 65632 0 0 0 0 0 0 0 0 0 2 0 0 0 0 0 21 0.5
1 1 SNP1 2 7523 65632 0 0 0 0 0 0 0 2 0 0 0 0 0 0 0 22 0.125
1 2 SNP2 2 65632 85631 0 0 0 0 0 0 1 0 0 0 1 0 0 0 0 11 0.25
1 2 SNP2 2 65632 85631 0 0 0 0 0 0 0 0 0 0 0 0 1 0 0 12 0.625
1 2 SNP2 2 65632 85631 0 0 0 0 0 0 0 2 0 0 0 0 0 0 0 22 0.125
2 4 SNP4 2 96363 118563 0 0 0 0 0 0 1 0 0 0 1 0 0 0 0 11 0.25
2 4 SNP4 2 96363 118563 0 0 0 0 0 0 1 1 0 0 0 0 0 0 0 21 0.25
2 4 SNP4 2 96363 118563 0 0 1 0 0 0 0 0 0 0 0 0 1 0 0 22 0.5
```

DevHaplotype is a python 3 program and can be run, using Python 3, as: **python DevHaplotype**
