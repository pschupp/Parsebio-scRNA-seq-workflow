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


## Watchmaker notes

- Illumina adapters are not included. This is for the PCR or ligation step? Is it true that watchmaker expects no pcr, ligation only? TODO
- Equinox MM for PCr workflows, but default does not include any MM
    - Equinox MM has high GC tolerance and allows amplification in the presence of paramagnetic beads.


