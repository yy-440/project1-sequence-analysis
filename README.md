DNA Mismatch Analysis:

Title and Purpose:

This program analyses DNA sequencing reads to investigate whether exposure to a genotoxic agent is associated with increased mismatch frequencies and whether mismatches occur more frequently at specific nucleotide positions.


How to Run the Program:

Open the project notebook in Google Colab. Select Runtime → Run all to load the provided dataset, execute the functions, perform validation tests and generate the final analysis.


Inputs and Outputs:

The program accepts a reference DNA sequence and a list of dictionaries containing read identifiers, sample names, treatment groups and DNA sequences. It returns annotated reads, sample-level summary dictionaries and statistical comparison results. Printed outputs include valid and invalid read counts, mismatch percentages, substitution frequencies, the three most frequently mismatched positions and results from two-sided Welch's t-tests.


Code Design:

I divided the analysis into separate functions so that validation, mutation detection, sample summarisation and statistical comparison could be performed and tested independently.

I created the find_top_positions() helper function to avoid repeating the ranking procedure in Steps 4 and 5. Rather than using advanced sorting methods, I used loops and conditional statements to identify the highest mismatch counts while prioritising earlier positions when counts were equal.

I used nested dictionaries to organise sample-level results because they allow counts to be accessed and updated using sample names, substitution types and nucleotide positions. Although dictionaries were initially used for combined position counts in Step 5, I changed this to a full-length list to represent positions with zero mismatches as well.


Testing:

I used assert statements to test correctness and robustness. Three informative tests were:

Validating "ATN" against "ATGC" to confirm that both length and character errors were reported.

Testing equal mismatch counts at positions 1–4 to confirm that the earlier positions were prioritised.

Testing samples with no valid reads to ensure unavailable percentages returned None, preventing division by zero.
