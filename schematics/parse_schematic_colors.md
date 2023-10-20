# 1. Polyadnylated mRNA
[mRNA]AAA...AAA

# 2. Reverse transcription (poly-A or random hexamers). Moloney Murine Leukemia Virus RT adds terminal Cs (up to 3) & R1 ligation
oligo is [BC1][linkerA]
   [mRNA]AAA...AAA
     <---T(30)[BC1][linkerA]

   [mRNA]AAA...AAA
CCC[cDNA]T(30)[BC1][linkerA]

OR
   [mRNA]NNNNNN
    <----NNNNNN[BC1][linkerA]

   [mRNA]
CCC[cDNA][BC1][linkerA]


# 3. R2 ligation
ligate [BC2][linkerB]

   [mRNA]A(?)
CCC[cDNA]T(30)[BC1][linkerA][BC2][linkerB]

# 4. R3 ligation
ligate [BC3][UMI][R2][BIOTIN]

   [mRNA]A(?)
CCC[cDNA]T(30)[BC1][linkerA][BC2][linkerB][BC3][UMI][R2][BIOTIN]

# 5. Cell lysis

# 6. Biotin pulldown with streptavidin beads

# 7. Template switch PCR 
Template switch with NNNGGG 

[UNK]GGG--->
     CCC[cDNA]T(30)[BC1][linkerA][BC2][linkerB][BC3][UMI][R2][BIOTIN]

[UNK]GGG[cDNA']A(30)[BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2']
     CCC[cDNA]T(30) [BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2][BIOTIN]

[UNK] in paper = AAGCAGTGGTATCAACGCAGAGT

# 8. Amplification PCR
PCR with R2 and [UNK]GGG

[UNK]GGG[cDNA']A(30)[BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2']
                                                           <----[R2]
[UNK]GGG---->
     CCC[cDNA] T(30)[BC1] [linkerA][BC2]  [linkerB] [BC3] [UMI] [R2][BIOTIN]

Result:

[UNK] GGG[cDNA']A(30)[BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2']
[UNK']CCC[cDNA] T(30)[BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2]

# 9. Fragmentation
## post fragmentation, avg. size 400 bp, results in 5' and 3' overhangs (not strand specific)

5'         [cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2'] 3'
3' [ovrhng][cDNA] [BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2] 5'

OR

5' [ovrhng][cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2'] 3'
3'         [cDNA] [BC1] [linkerA ][BC2] [linkerB ][BC3] [UMI] [R2] 5'

# 10. end repair (templated polymerase) 
TODO: figure out how this is done for suer
- During the DNA end repair reaction, fragmented DNA is converted into blunt-end DNA containing a 5'-phosphate and 3'-hydroxyl groups. Using 3'-> 5' exonuclease activity
- The 5'→3' polymerase activity of the Klenow Fragment (DNA Pol I) fills-in 5' protruded DNA ends (lacks 3'5' exo)
- 3'→5' exonuclease activity of T4 polymerase removes 3'-overhangs. 
- T4 PNK adds 5'-phosphates to ends of unphosphorylated DNA fragments, such as PCR products. 

## 10a. 3' -> 5' exonuclease

5'         [cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2'] 3'
3'         [cDNA] [BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2] 5'

OR

5' [ovrhng][cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2'] 3'
3'         [cDNA] [BC1] [linkerA ][BC2] [linkerB ][BC3] [UMI] [R2] 5'

## 10b. add 5' phosphates to allow ligation

5'       P-[cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2']   3'
3'         [cDNA] [BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2] -P 5'

OR

5' [ovrhng][cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2'] 3'
3'         [cDNA] [BC1] [linkerA ][BC2] [linkerB ][BC3] [UMI] [R2] 5'

##  

5' P-[cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2'] 3'
3'OH-[cDNA] [BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2]-no-phospho 5'

OR

5' P-[overhng][cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2'] 3'
3'OH-[ovrhng'][cDNA] [BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2]-no-phospho 5'

# 11. A-tailing to 3' hydroxylated ends (prep for orientation-specific ligation)

 [cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2']
A[cDNA] [BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2]

# 12. Ligation (requires phospho 5' ends)

Ligated adapters are:
  [R1']
T [R1] 
 
[R1]T[cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2']
[R1'] A[cDNA] [BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2]

# 13. Index PCR
Primers: [P5][R1']
         [P7][i7][R2]

     [R1] T[cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2']
                                                        <----[R2 ][i7][P7]

 [P5][R1]---->
     [R1']A[cDNA] [BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2]
    

# 14. Final library

[P5] [R1]  T[cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2'][i7'][P7']
[P5'][R1'] A[cDNA] [BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2] [i7] [P7]

# 15. Sequencing - forward strand  workflow
## Read 1
5' [P5] [R1]T[cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2'][i7'][P7'] 3' 
     [R1'] ----->

## Index Read 1 (i7)
5' [P5] [R1]T[cDNA'][BC1'][linkerA'][BC2'][linkerB'][BC3'][UMI'][R2'][i7'][P7'] 3'
                                                                 [R2] ----->
## complementary sequence synthesis (bridge amplification
## Read 2
3' [P5'][R1'] A[cDNA] [BC1] [linkerA] [BC2] [linkerB] [BC3] [UMI] [R2] [i7] [P7] 5'
                                                             <----[R2']
Sequences:
[P5]      = AATGATACGGCGACCACCGAGATCTACAC
[R1]      = TCGTCGGCAGCGTCAGATGTGTATAAGAGACAG # Nextera, used in paper
[R1]      = ACACTCTTTCCCTACACGACGCTCTTCCGATCT # TruSeq, a mix of TruSeq and Nextera is used in sequencing
[BC1]     = [8bp BC]
[linkerA] = ATCCACGTGCTTGAGACTGTGG
[BC2]     = [8bp BC]
[linkerB] = GTGGCCGATGTTTCGCATCGGCGTACGACT
[BC3]     = [8bp BC]
[UMI]     = [10 bp UMI, NNNNNNNNNN]
[R2]  = GTCTCGTGGGCTCGGAGATGTGTATAAGAGACAG # Nextera, end of nextera primers are the same, can do PCR with single primer
[R2]  = GTGACTGGAGTTCAGACGTGTGCTCTTCCGATCT # TruSeq, a mix of TruSeq and Nextera is used in sequencing
[i7]      = [6bp i7 barcode]
[P7]      = CAAGCAGAAGACGGCATACGAGAT
