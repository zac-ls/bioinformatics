# Polypyrimidine Tract Prediction Tools

The polypyrimidine tract (PPT) is a pyrimidine-rich region of pre-messenger RNA (pre-mRNA) that promotes spliceosome assembly and guides intron removal during RNA splicing. It is typically located near the 3' splice site and is usually 15–20 base pairs long.

The R functions in this repository are **predictive tools designed to identify and evaluate PPTs** within a given nucleotide sequence (A, C, G, T). The available tools here are:

- **`find_PPT`**: identifies potential PPTs in a sequence, such as those located upstream of the 3' splice site.
- **`calculate_ppt_score`**: calculates the strength of a PPT element based on its nucleotide composition. This tool can be applied to PPTs identified by find_PPT.
- **`percent_pyrimidines`**: determines the percentage of pyrimidine content (C and T) within a specified sequence.

**`find_PPT`** ― *PPT Identification Tool*

The function for finding PPTs is optimized to detect the longest PPT based on the heuristic described by Corvelo *et al.* (2010), which includes the following criteria:

1. Both 3′ and 5′ ends must be pyrimidines;
2. No more than two contiguous purines are allowed;
3. Each purine segment (length L < 3) must be flanked by at least 4L pyrimidines, ensuring a minimum pyrimidine content of over 2/3, with both upstream and downstream pyrimidine segments of length ≥ L;
4. T(GT)_n stretches are allowed;
5. Minimum PPT length of 9 nucleotides or a uridine content ≥ 5.

**`calculate_ppt_score`** ― *PPT Strength Score Tool*

The function for calculating the PPT strength score is based on the specific nucleotide composition of the sequence, using the following formula:

$\text{PPT}_{\text{score}} = f(A) \cdot (-2) + f(C) \cdot 2 + f(G) \cdot (-2) + f(T) \cdot 3$

Where: $f(A)$, $f(C)$, $f(G)$ and $f(T)$ represent the frequency of adenine ($A$), cytosine ($C$), guanine ($G$), and thymine ($T$), respectively.

**References:**

Corvelo, A., Hallegger, M., Smith, C. W., & Eyras, E. (2010). Genome-wide association between branch point properties and alternative splicing. *PLoS Computational Biology*, 6(11), e1001016. https://doi.org/10.1371/journal.pcbi.1001016
