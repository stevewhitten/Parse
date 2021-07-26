Given an input primary sequence, Parse calculates nu_model, β-turn propensity, and r_model, both for the whole sequence and at the residue level. From these calculations, each position in the primary sequence is relabeled as either P, D, or F, which is then used to predict domain level structure, as explained in Paiz et al 2020 bioRxiv.

nu_model is determined by log(Rh/2.16)/log(N), where N is amino acid length and Rh is calculated as decribed by eq 2 in English et al (JPCB 2019, vol 123, 10014-10024).

β-turn propensity is determined using the scale from Levitt (Biochemistry 1978, vol 17, pgs 4277-4285).

r_model is the ratio β-turn propensity / nu_model.

Residue level values for r_model (calculated by a sliding-window scheme) are output into the text file, "residue_level_rmodel.csv". This file contains 4 columns, the first is residue number, the second is 1-letter code for the amino acid type, the third is the position label (P, D, or F), and the fourth is the value in r_model for the window centered on the residue position.


To use Parse:
1. Compile Parse.f using a fortran compiler. The program was tested using GNU Fortran (Homebrew GCC 11.1.0_1) 11.1.0.
2. Run the program using the obtained executable followed by the protein primary sequence, for example "./a.out SEQUENCESEQUENCESEQUENCESEQUENCE" without the quotes.

The Parse.f program limits primary sequence lengths to at least 25 residues, which is required for the sliding-window scheme, and no longer than 10000. 