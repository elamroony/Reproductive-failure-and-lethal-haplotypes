**Reproductive failure and lethal haplotypes**

Deviations from expected Mendelian inheritance patterns may indicate reduced reproductive performance or the presence of lethal alleles. Advances in genomic markers have enabled more efficient investigation of such phenomena, including the identification of potential lethal alleles. These assessments can be performed using either SNP markers or haplotypes, with the latter being particularly useful for low- to medium-density genotypes (Abdalla et. al., 2020)
https://onlinelibrary.wiley.com/doi/full/10.1111/age.13003.

**DevHap**: A tool for haplotype analysis: DevHap calculates the observed number of haplotypes from each possible mating. It requires four input files:

**1. Parameters file**:
Contains four lines specifying:
```
Pedigree file name
Map file name
genotypes file
window size (number of markers in the haplotype window)
```
An example of parameter file: 
```
ped_file = ped.txt
map_file = map.txt
geno_file = genotypes.txt
window_size = 3
```

**1. Pedigree file**:
Format: No header, three columns (animal, sire, dam) separated by at least one space.
ID numbering: Animals must be numbered sequentially from 1 to n, where n is the total number of genotyped animals.
Pedigree renumbering: Can be done using ped_sort_and_renumber.

Example (4 animals):
```
1 0 0
2 1 0
3 1 2
4 3 2
```
**2. Map file**
Format: No header, three columns (Chromosome, SNP ID, Position) separated by at least one space.
Example:
```
1 SNP1 100  
1 SNP2 110  
1 SNP3 125  
2 SNP1 135  
2 SNP2 140  
2 SNP2 165  
2 SNP2 170  
3 SNP1 280  
3 SNP1 290  
3 SNP1 300
```
**3. Genotypes file**:
Format: No header or row names; genotypes must be phased and space-free (e.g., 0234).
Phasing:
```
0 (AA) → 0
1 (AB) → 3 or 4 (AB ≠ BA)
2 (BB) → 2
```
***Order: Genotype rows must match the pedigree file order.***


Example (10 SNPs, 4 animals):
```
4220402322  
0433432233  
4334000034  
2042243324
```
**4. Window size**: An integer


**Outputs**:
Results are saved in ***out_devHap_win_size_<window_size>.csv***, with columns including:
```
Chromosome
SNP order (Order in the map file)
Window size
Start window position
End window position
Observed haplotype inheritance patterns (e.g., AB_AA:AA, AB_BB:BB)
Haplotype frequency
Number of sires
Number of dams
Number of sire carry the haplotype
Number of dams carry the haplotype
Number of progeny carry the haplotype 
```

Example Output:
```
chr,snpOrder,snpID,windowSize,startPosition,endPosition,AB_AA:AA,AB_AA:AB,AB_BB:AB,AB_BB:BB,AA_AB:AA,AA_AB:AB,BB_AB:AB,BB_AB:BB,AB_AB:AA,AB_AB:AB,AB_AB:BB,AA_AA:AA,AA_BB:AB,BB_AA:AB,BB_BB:BB,haplotype,haplotypeFreq,numSires,numDams,hSires,hDams,numProg
1,1,SNP1,3,100,125,0,0,0,1,0,0,0,0,0,0,0,0,0,0,1,222,.125,2,1,2,0,0
1,1,SNP1,3,100,125,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,122,.250,2,1,3,0,1
1,1,SNP1,3,100,125,0,0,0,0,0,0,0,2,0,0,0,0,0,0,0,121,.125,2,1,0,2,0
1,1,SNP1,3,100,125,0,0,0,0,0,0,0,2,0,0,0,0,0,0,0,112,.125,2,1,0,2,0
1,1,SNP1,3,100,125,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,211,.250,2,1,1,0,2
1,1,SNP1,3,100,125,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,212,.125,2,1,0,0,1
2,4,SNP1,3,135,165,0,0,0,1,0,0,0,0,0,0,0,0,1,0,0,221,.250,2,1,3,0,1
2,4,SNP1,3,135,165,0,0,0,0,0,0,0,2,0,0,0,0,0,0,0,211,.125,2,1,0,2,0
2,4,SNP1,3,135,165,0,0,0,0,0,0,1,1,0,0,0,0,0,0,0,122,.250,2,1,0,2,1
2,4,SNP1,3,135,165,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,112,.250,2,1,1,0,2
2,5,SNP2,3,140,170,0,0,0,1,0,0,0,0,0,0,0,0,0,0,1,212,.125,2,1,2,0,0
2,5,SNP2,3,140,170,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,211,.250,2,1,3,0,1
2,5,SNP2,3,140,170,0,0,0,0,0,0,0,2,0,0,0,0,0,0,0,112,.125,2,1,0,2,0
2,5,SNP2,3,140,170,0,0,0,0,0,0,0,2,0,0,0,0,0,0,0,221,.125,2,1,0,2,0
2,5,SNP2,3,140,170,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,121,.125,2,1,1,0,1
2,5,SNP2,3,140,170,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,222,.125,2,1,0,0,1
2,5,SNP2,3,140,170,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,122,.125,2,1,0,0,1
3,8,SNP1,3,280,300,0,0,0,0,0,0,0,1,0,0,1,0,0,0,0,121,.250,2,1,2,2,0
3,8,SNP1,3,280,300,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,111,.250,2,1,3,0,1
3,8,SNP1,3,280,300,0,0,0,0,0,0,0,2,0,0,0,0,0,0,0,212,.125,2,1,0,2,0
3,8,SNP1,3,280,300,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,211,.125,2,1,1,0,1
3,8,SNP1,3,280,300,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,222,.125,2,1,0,0,1
3,8,SNP1,3,280,300,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,221,.125,2,1,0,0,1

```
```
Usage: ./devHap
```

Interpreting DevHap Results:
The output identifies deviations from expected Mendelian inheritance patterns, which may signal reproductive failure or lethal haplotypes. Validation of these results is critical and potential findings should be cross-checked with:

Biological evidence (e.g., known lethal variants in the species/population).
Statistical thresholds (e.g., significance levels for inheritance deviations).
Independent datasets (to rule out technical artifacts like genotyping phasing errors).
Effect of selection.




References:

Abdalla, E.A.; Id-Lahoucine, S.; Cánovas, A.; Casellas, J.; Schenkel, F.S.; Wood, B.J.; Baes, C.F. Discovering Lethal Alleles across the Turkey Genome Using a Transmission Ratio Distortion Approach. Anim. Genet. 2020, 51, 876–889 [https://doi.org/10.1111/age.13003]. 
