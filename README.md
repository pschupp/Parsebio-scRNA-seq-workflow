# README for the development process of the Parsebiosciences snRNA-seq workflow

## Overview of the wetlab portion of the procedure

| Step  | Action                                                             | Kit        | Location of nucleotide |
| ---   | ---                                                                | ---        | ---                    |
| 1 & 2 | reverse transcription with poly-A or random hexamer along with BC1 | parse      | *in cyto*            |
| 3 & 4 | ligation of barcode 2 and 3 (BC2 and BC3)                          | parse      | *in cyto*            |
| 5 & 6 | cell lysis and biotin pulldown with streptavidin beads             | parse      | *in vitro*           |
| 7     | template switch pcr                                                | parse      | *in vitro*           |
| 8     | amplification pcr                                                  | parse      | *in vitro*           |
| 9     | enzymatric fragmentation                                           | watchmaker | *in vitro*           |
| 10    | end repair                                                         | watchmaker | *in vitro*           |
| 11    | A-tailing                                                          | watchmaker | *in vitro*           |
| 12    | ligation of illumina adapters                                      | watchmaker | *in vitro*           |
| 13    | index pcr                                                          | watchmaker | *in vitro*           |
| 14    | sequencing                                                         | illumina   | *in sequenenco*      |

- *n.b.* with  Watchmaker kit, steps 9-11 occur in one reaction

## Terminology
Stubby adapter - adapters used in ligation during TruSeq that only include partial **read 1** and **read 2** sequences and not any **i5**/**i7** sequences nor the **P5** or **P7** cluster generation sequences.

    - see the folder `documentation/adapterama` for the papers that introduce this idea
    - TODO: why is there a spacer between the **read 1**/**read 2** sequence...perhaps it was found to yield in better lack of associatin of stubby-yoke adapter
    - *n.b.* in our case ethere there is only ligation on one side, it is unneccsarry to have y-yoke as we cannot generate the top strand twice as one end (with **R2**, ligation with the same adapter on each end) is already fixed. This also means that our library prep is **stranded**.

## Watchmaker notes

- Illumina adapters are not included. This is for the PCR or ligation step? Is it true that watchmaker expects no pcr, ligation only? TODO

- Equinox MM for PCr workflows, but default does not include any MM
    - Equinox MM has high GC tolerance and allows amplification in the presence of paramagnetic beads.
- Watchmaker also uses ampure beads
- buffer for input DNA 10mM Tris-HCl, pH 8, 0.1 mM EDTA is recommended for best results
- compatible with overhanging T to facilitate adapter orientation
    - must be sure adapters are duplexed and correct concentration
    - will need primers with barcodes during final amplification
    - stubby adapters must be added at higher concentration compared to regular adapters to increase conversion efficiency of unique library molecules with minimal adapter dimer formation.
- for the index PCR, use primer concentration of 20uM of each primer for final reaction concentration of 2uM. These primers might include 3' P mod for specificity. 
- TODO: look up 3'-phosphorothioate bond modification. This helps with specificity?
- during index pcr temperature can range from 55 to 70C. TODO: compare the length of sequence we ordered with Adapterama I paper!
- extension time of 30s for up to 500bp, 45s for fragments larger than 500bp

## Decision made during wet lab procedure
- TODO: what was the DNA input
- TODO: get incubation time & length
- TODO: what adapter concentration was used (dependent on DNA input), with stuby adapter should use more.
- TODO: what is the distribution of fragment lengths from Watchmaker output
- TODO: how many pcr cycles were done during the PCR?
- TODO: Was the Watchmaker Equinox PCR MM used? If not, which MM?
    - Don't really need Equinox kit as we are no performing PCR in the presence of beads?
