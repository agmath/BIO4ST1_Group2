---
title: "Intro to R for Bioinformatics"
author: "Melanie Dube, Scientist"
format: html
execute:
  keep-md: true
---



# Intro to Bioinformatics

## Introduction

### Activity Objectives

Below are the listed objectives for this new notebook:

-   Use the arrow (`<-`) operator to store objects in variables.

-   Use R's `sample()` function to create a random "genome" for the purpose of testing functions.

-   Build functions to process and analyze genetic data.

-   Learn about `for` loops and implement them when necessary.

-   Read in a real bacterial genome from a text file.

-   Analyse the genome using the ideas and tools developed in the first part of the notebook.

### Loading Packages

First code chunk always loads needed packages (seen below).





## Challenge 1

The first challenge is to create a list with the four nucleotides. This is done with the `c()` function.


::: {.cell}

```{.r .cell-code}
nucleotides <- c("A", "C", "G", "T" )

nucleotides
```

::: {.cell-output .cell-output-stdout}
```
[1] "A" "C" "G" "T"
```
:::
:::


## Challenge 2

The second challenge is to adapt a code to create a random strand of 15 nucleotides. This should be called `randGenome`.


::: {.cell}

```{.r .cell-code}
numNucleotides <- 15

randGenome <- sample(nucleotides, size = numNucleotides, replace = TRUE)

randGenome
```

::: {.cell-output .cell-output-stdout}
```
 [1] "C" "T" "A" "T" "T" "G" "A" "T" "C" "G" "T" "T" "G" "C" "T"
```
:::
:::


The block above creates the list for the random genome, and the block below will collapse it and make it more readable.


::: {.cell}

```{.r .cell-code}
paste(randGenome, collapse = "")
```

::: {.cell-output .cell-output-stdout}
```
[1] "CTATTGATCGTTGCT"
```
:::
:::


Before comparing my block with a someone else, I predict that another classmate's will be a different random order. This is because we are instructing R to generate a random code, therefore it should be different every time we run it.

## Challenge 3

The third challenge is to generate a random genome that is 1500 nucleotides long and collapse it down to a single string.


::: {.cell}

```{.r .cell-code}
numNucleotidesChal3 <- 1500

randGenomeChal3 <- sample(nucleotides, size = numNucleotidesChal3, replace = TRUE)

randGenomeChal3
```

::: {.cell-output .cell-output-stdout}
```
   [1] "T" "C" "T" "T" "G" "G" "T" "A" "A" "C" "A" "A" "G" "A" "T" "T" "T" "G"
  [19] "C" "T" "C" "T" "T" "G" "A" "G" "G" "G" "T" "A" "A" "A" "C" "C" "T" "A"
  [37] "G" "T" "A" "A" "A" "A" "C" "T" "A" "A" "A" "T" "C" "T" "G" "T" "G" "A"
  [55] "T" "A" "A" "T" "G" "T" "C" "C" "A" "G" "T" "C" "A" "G" "C" "T" "A" "T"
  [73] "T" "T" "T" "G" "G" "A" "C" "T" "T" "T" "C" "A" "A" "A" "T" "G" "A" "T"
  [91] "A" "A" "G" "T" "T" "T" "T" "G" "G" "C" "C" "C" "C" "G" "A" "C" "A" "A"
 [109] "C" "C" "G" "G" "G" "T" "A" "A" "G" "A" "C" "G" "G" "C" "T" "C" "A" "C"
 [127] "G" "G" "A" "A" "T" "T" "G" "A" "C" "T" "G" "A" "T" "A" "C" "C" "C" "C"
 [145] "T" "C" "C" "G" "G" "A" "A" "G" "G" "C" "G" "T" "T" "A" "G" "T" "A" "C"
 [163] "G" "C" "T" "C" "G" "T" "A" "A" "G" "T" "T" "C" "T" "A" "G" "T" "A" "A"
 [181] "G" "A" "C" "A" "C" "A" "T" "T" "C" "C" "T" "G" "T" "T" "G" "A" "A" "G"
 [199] "C" "C" "C" "T" "T" "A" "A" "C" "G" "C" "T" "G" "C" "A" "A" "C" "T" "G"
 [217] "T" "C" "A" "A" "G" "T" "T" "T" "T" "T" "G" "A" "C" "G" "G" "T" "C" "G"
 [235] "G" "T" "C" "T" "C" "C" "G" "A" "T" "G" "G" "T" "T" "C" "A" "A" "C" "G"
 [253] "A" "A" "G" "T" "A" "A" "T" "G" "T" "A" "A" "T" "C" "A" "G" "T" "T" "T"
 [271] "C" "G" "C" "T" "G" "T" "C" "A" "G" "T" "T" "T" "C" "C" "T" "C" "G" "T"
 [289] "A" "G" "T" "T" "A" "C" "T" "A" "A" "T" "C" "T" "A" "C" "G" "G" "G" "A"
 [307] "G" "G" "C" "G" "A" "A" "C" "C" "A" "C" "C" "C" "C" "T" "T" "A" "T" "C"
 [325] "T" "T" "A" "G" "G" "G" "A" "C" "T" "A" "T" "T" "A" "G" "G" "G" "C" "A"
 [343] "T" "C" "G" "G" "G" "A" "A" "A" "G" "A" "G" "G" "G" "C" "T" "T" "C" "A"
 [361] "C" "C" "C" "G" "C" "C" "C" "A" "A" "A" "T" "T" "C" "G" "T" "G" "C" "C"
 [379] "C" "C" "C" "C" "C" "G" "T" "C" "G" "A" "G" "A" "A" "A" "C" "C" "T" "T"
 [397] "A" "A" "A" "C" "G" "G" "A" "C" "G" "G" "A" "C" "C" "T" "G" "A" "A" "A"
 [415] "T" "G" "A" "T" "T" "T" "A" "G" "C" "A" "G" "A" "T" "C" "G" "G" "T" "G"
 [433] "C" "T" "C" "C" "T" "A" "C" "C" "G" "C" "T" "A" "G" "T" "T" "C" "T" "A"
 [451] "C" "T" "T" "T" "T" "A" "A" "G" "G" "C" "A" "T" "G" "C" "G" "T" "C" "C"
 [469] "A" "C" "C" "C" "A" "A" "A" "C" "T" "C" "G" "T" "G" "C" "T" "T" "T" "A"
 [487] "G" "G" "C" "G" "C" "A" "G" "T" "G" "T" "T" "T" "C" "C" "G" "A" "T" "T"
 [505] "G" "T" "T" "A" "G" "T" "A" "G" "G" "T" "G" "T" "A" "T" "T" "A" "T" "A"
 [523] "C" "T" "T" "G" "T" "G" "A" "T" "G" "T" "T" "G" "G" "T" "C" "A" "T" "G"
 [541] "A" "T" "A" "G" "A" "T" "C" "C" "T" "C" "T" "C" "G" "G" "C" "C" "G" "G"
 [559] "A" "G" "A" "A" "A" "C" "G" "T" "A" "G" "T" "C" "C" "A" "G" "A" "G" "T"
 [577] "A" "A" "G" "A" "A" "A" "A" "A" "C" "C" "C" "A" "A" "T" "C" "C" "A" "G"
 [595] "G" "C" "C" "A" "A" "T" "A" "T" "T" "G" "A" "C" "A" "T" "A" "G" "C" "A"
 [613] "G" "C" "C" "C" "C" "G" "A" "T" "C" "T" "A" "G" "C" "G" "T" "A" "A" "A"
 [631] "A" "T" "C" "G" "A" "G" "C" "G" "T" "G" "G" "A" "C" "T" "T" "G" "G" "G"
 [649] "C" "T" "C" "A" "G" "T" "T" "T" "T" "G" "A" "C" "T" "C" "T" "C" "G" "G"
 [667] "T" "T" "T" "T" "A" "T" "G" "C" "A" "A" "G" "C" "A" "T" "G" "G" "C" "T"
 [685] "C" "T" "C" "T" "T" "C" "G" "T" "A" "C" "A" "T" "G" "A" "G" "T" "C" "C"
 [703] "G" "T" "G" "A" "C" "T" "A" "G" "A" "G" "G" "G" "G" "G" "G" "A" "A" "T"
 [721] "C" "G" "A" "G" "T" "T" "C" "C" "C" "C" "C" "C" "A" "T" "T" "G" "C" "C"
 [739] "A" "C" "G" "G" "C" "G" "T" "T" "C" "G" "A" "C" "A" "A" "A" "T" "G" "A"
 [757] "G" "C" "C" "C" "G" "A" "T" "G" "C" "T" "A" "A" "C" "T" "T" "A" "C" "G"
 [775] "T" "A" "A" "G" "A" "T" "A" "A" "C" "G" "C" "T" "A" "G" "A" "C" "C" "C"
 [793] "T" "C" "T" "C" "C" "C" "A" "T" "T" "A" "T" "C" "T" "T" "T" "T" "C" "T"
 [811] "G" "A" "G" "G" "C" "C" "T" "G" "T" "C" "C" "G" "T" "A" "C" "G" "A" "G"
 [829] "C" "A" "C" "G" "T" "C" "A" "T" "A" "C" "A" "C" "T" "C" "C" "C" "A" "G"
 [847] "C" "C" "T" "T" "A" "G" "C" "A" "T" "T" "G" "A" "T" "A" "A" "T" "A" "T"
 [865] "A" "G" "A" "G" "T" "T" "C" "G" "A" "G" "T" "T" "G" "T" "T" "T" "G" "A"
 [883] "C" "A" "C" "G" "A" "G" "G" "C" "G" "G" "C" "T" "T" "A" "C" "A" "T" "T"
 [901] "A" "G" "T" "A" "C" "C" "C" "C" "T" "C" "G" "A" "T" "T" "G" "C" "A" "C"
 [919] "A" "G" "T" "G" "A" "C" "G" "G" "G" "A" "A" "C" "C" "C" "C" "C" "T" "C"
 [937] "T" "C" "A" "C" "T" "G" "T" "A" "A" "C" "G" "C" "T" "T" "G" "A" "A" "G"
 [955] "C" "A" "A" "C" "G" "T" "G" "C" "T" "A" "C" "C" "T" "C" "C" "G" "T" "C"
 [973] "G" "C" "A" "T" "G" "G" "C" "T" "T" "T" "G" "C" "T" "A" "C" "A" "G" "G"
 [991] "G" "T" "A" "C" "T" "G" "A" "A" "T" "G" "T" "C" "A" "G" "T" "G" "T" "T"
[1009] "T" "T" "G" "C" "A" "G" "C" "T" "G" "T" "T" "T" "C" "A" "A" "G" "C" "T"
[1027] "A" "A" "G" "G" "T" "C" "T" "A" "A" "T" "G" "C" "G" "T" "G" "A" "C" "G"
[1045] "G" "T" "C" "G" "G" "A" "G" "T" "T" "G" "A" "C" "G" "A" "C" "G" "T" "G"
[1063] "T" "G" "A" "C" "C" "A" "A" "A" "A" "C" "T" "C" "G" "A" "T" "G" "T" "A"
[1081] "C" "C" "T" "T" "A" "A" "G" "T" "C" "G" "A" "T" "C" "T" "C" "A" "T" "C"
[1099] "T" "C" "A" "C" "C" "G" "G" "C" "G" "G" "T" "C" "A" "G" "T" "T" "T" "A"
[1117] "G" "C" "G" "T" "C" "A" "A" "G" "G" "G" "C" "T" "T" "C" "A" "A" "C" "C"
[1135] "A" "G" "C" "A" "A" "C" "G" "T" "C" "G" "A" "T" "A" "A" "T" "A" "C" "C"
[1153] "C" "C" "A" "T" "C" "G" "G" "T" "C" "A" "C" "C" "G" "T" "T" "A" "A" "A"
[1171] "C" "C" "C" "C" "C" "A" "G" "T" "T" "T" "T" "A" "C" "T" "T" "G" "C" "C"
[1189] "G" "T" "T" "C" "A" "G" "A" "T" "C" "A" "T" "A" "C" "T" "G" "G" "A" "C"
[1207] "G" "G" "A" "C" "G" "A" "A" "G" "T" "T" "C" "G" "T" "C" "C" "T" "T" "G"
[1225] "G" "C" "A" "C" "T" "C" "T" "C" "G" "T" "A" "G" "T" "A" "A" "C" "A" "T"
[1243] "G" "A" "A" "T" "G" "G" "A" "G" "G" "G" "G" "C" "A" "A" "G" "G" "T" "T"
[1261] "T" "C" "A" "C" "C" "C" "A" "G" "G" "T" "A" "T" "G" "C" "C" "T" "A" "A"
[1279] "C" "A" "T" "T" "C" "G" "C" "C" "C" "T" "C" "C" "C" "G" "T" "C" "A" "G"
[1297] "T" "C" "G" "G" "T" "G" "A" "T" "C" "C" "G" "G" "T" "C" "G" "G" "G" "A"
[1315] "T" "C" "T" "T" "A" "C" "C" "G" "C" "T" "G" "A" "G" "T" "C" "C" "G" "G"
[1333] "T" "G" "G" "G" "T" "G" "G" "T" "A" "T" "C" "C" "T" "G" "T" "A" "G" "G"
[1351] "G" "C" "G" "T" "G" "A" "A" "T" "T" "G" "C" "C" "C" "G" "G" "C" "G" "G"
[1369] "A" "T" "G" "T" "T" "C" "G" "C" "C" "T" "A" "T" "G" "T" "T" "A" "A" "T"
[1387] "T" "A" "A" "G" "G" "G" "T" "T" "T" "A" "G" "G" "G" "T" "T" "G" "G" "C"
[1405] "C" "G" "T" "T" "A" "C" "C" "A" "G" "A" "A" "A" "G" "T" "G" "A" "G" "G"
[1423] "C" "A" "A" "G" "T" "G" "T" "C" "T" "G" "T" "G" "T" "A" "G" "C" "T" "A"
[1441] "T" "C" "T" "G" "C" "A" "C" "T" "C" "C" "T" "C" "C" "A" "G" "G" "T" "T"
[1459] "G" "C" "G" "G" "T" "C" "G" "T" "C" "G" "T" "C" "T" "A" "T" "A" "C" "T"
[1477] "G" "C" "C" "C" "G" "C" "C" "T" "G" "G" "C" "C" "G" "A" "A" "A" "T" "T"
[1495] "C" "G" "G" "A" "T" "A"
```
:::

```{.r .cell-code}
paste(randGenomeChal3, collapse = "")
```

::: {.cell-output .cell-output-stdout}
```
[1] "TCTTGGTAACAAGATTTGCTCTTGAGGGTAAACCTAGTAAAACTAAATCTGTGATAATGTCCAGTCAGCTATTTTGGACTTTCAAATGATAAGTTTTGGCCCCGACAACCGGGTAAGACGGCTCACGGAATTGACTGATACCCCTCCGGAAGGCGTTAGTACGCTCGTAAGTTCTAGTAAGACACATTCCTGTTGAAGCCCTTAACGCTGCAACTGTCAAGTTTTTGACGGTCGGTCTCCGATGGTTCAACGAAGTAATGTAATCAGTTTCGCTGTCAGTTTCCTCGTAGTTACTAATCTACGGGAGGCGAACCACCCCTTATCTTAGGGACTATTAGGGCATCGGGAAAGAGGGCTTCACCCGCCCAAATTCGTGCCCCCCCGTCGAGAAACCTTAAACGGACGGACCTGAAATGATTTAGCAGATCGGTGCTCCTACCGCTAGTTCTACTTTTAAGGCATGCGTCCACCCAAACTCGTGCTTTAGGCGCAGTGTTTCCGATTGTTAGTAGGTGTATTATACTTGTGATGTTGGTCATGATAGATCCTCTCGGCCGGAGAAACGTAGTCCAGAGTAAGAAAAACCCAATCCAGGCCAATATTGACATAGCAGCCCCGATCTAGCGTAAAATCGAGCGTGGACTTGGGCTCAGTTTTGACTCTCGGTTTTATGCAAGCATGGCTCTCTTCGTACATGAGTCCGTGACTAGAGGGGGGAATCGAGTTCCCCCCATTGCCACGGCGTTCGACAAATGAGCCCGATGCTAACTTACGTAAGATAACGCTAGACCCTCTCCCATTATCTTTTCTGAGGCCTGTCCGTACGAGCACGTCATACACTCCCAGCCTTAGCATTGATAATATAGAGTTCGAGTTGTTTGACACGAGGCGGCTTACATTAGTACCCCTCGATTGCACAGTGACGGGAACCCCCTCTCACTGTAACGCTTGAAGCAACGTGCTACCTCCGTCGCATGGCTTTGCTACAGGGTACTGAATGTCAGTGTTTTGCAGCTGTTTCAAGCTAAGGTCTAATGCGTGACGGTCGGAGTTGACGACGTGTGACCAAAACTCGATGTACCTTAAGTCGATCTCATCTCACCGGCGGTCAGTTTAGCGTCAAGGGCTTCAACCAGCAACGTCGATAATACCCCATCGGTCACCGTTAAACCCCCAGTTTTACTTGCCGTTCAGATCATACTGGACGGACGAAGTTCGTCCTTGGCACTCTCGTAGTAACATGAATGGAGGGGCAAGGTTTCACCCAGGTATGCCTAACATTCGCCCTCCCGTCAGTCGGTGATCCGGTCGGGATCTTACCGCTGAGTCCGGTGGGTGGTATCCTGTAGGGCGTGAATTGCCCGGCGGATGTTCGCCTATGTTAATTAAGGGTTTAGGGTTGGCCGTTACCAGAAAGTGAGGCAAGTGTCTGTGTAGCTATCTGCACTCCTCCAGGTTGCGGTCGTCGTCTATACTGCCCGCCTGGCCGAAATTCGGATA"
```
:::
:::


The block above successfully creates the 1500 unit random genome.


::: {.cell}

```{.r .cell-code}
set.seed(215)
genomeLength <- 1500

randGenome4 <- sample(nucleotides, size = genomeLength, replace = TRUE)

randGenome4
```

::: {.cell-output .cell-output-stdout}
```
   [1] "T" "G" "G" "A" "A" "T" "C" "T" "T" "T" "A" "A" "T" "G" "T" "T" "C" "C"
  [19] "G" "A" "C" "C" "T" "T" "T" "G" "A" "G" "C" "C" "T" "C" "A" "A" "G" "T"
  [37] "T" "G" "G" "A" "C" "T" "A" "C" "C" "G" "C" "G" "G" "C" "C" "C" "C" "C"
  [55] "G" "A" "C" "C" "G" "A" "G" "A" "G" "C" "T" "A" "A" "C" "T" "C" "T" "A"
  [73] "A" "A" "T" "G" "A" "T" "G" "C" "A" "A" "G" "C" "A" "G" "C" "G" "C" "G"
  [91] "T" "G" "C" "C" "G" "A" "G" "T" "C" "T" "C" "T" "G" "T" "G" "G" "A" "C"
 [109] "A" "G" "G" "A" "T" "C" "A" "C" "A" "T" "T" "G" "G" "A" "T" "G" "T" "G"
 [127] "A" "G" "C" "C" "A" "A" "G" "A" "T" "C" "T" "C" "G" "A" "G" "A" "T" "G"
 [145] "A" "A" "A" "A" "A" "C" "A" "A" "G" "T" "A" "G" "G" "T" "T" "C" "T" "C"
 [163] "T" "A" "T" "C" "G" "C" "T" "G" "G" "C" "T" "C" "C" "A" "A" "T" "C" "A"
 [181] "T" "T" "T" "T" "T" "A" "T" "C" "C" "T" "T" "T" "G" "C" "T" "G" "C" "A"
 [199] "T" "A" "C" "T" "T" "A" "T" "G" "G" "C" "C" "C" "T" "C" "C" "A" "A" "C"
 [217] "C" "T" "T" "G" "C" "G" "A" "A" "T" "T" "G" "C" "G" "G" "C" "A" "T" "T"
 [235] "A" "C" "G" "T" "T" "C" "T" "A" "T" "G" "C" "A" "C" "G" "A" "A" "A" "G"
 [253] "A" "G" "G" "C" "A" "C" "G" "A" "G" "A" "T" "G" "T" "A" "T" "A" "T" "C"
 [271] "A" "C" "T" "C" "T" "T" "C" "A" "G" "C" "T" "A" "T" "C" "T" "G" "A" "C"
 [289] "A" "C" "A" "G" "G" "T" "A" "G" "G" "C" "A" "T" "T" "G" "G" "A" "T" "G"
 [307] "T" "C" "A" "G" "C" "G" "T" "A" "C" "G" "A" "C" "C" "G" "G" "G" "G" "T"
 [325] "A" "G" "G" "C" "A" "A" "C" "C" "C" "C" "T" "T" "C" "T" "G" "T" "T" "G"
 [343] "C" "C" "C" "C" "G" "C" "T" "G" "G" "C" "C" "G" "G" "A" "T" "G" "C" "C"
 [361] "A" "A" "G" "G" "T" "G" "T" "T" "T" "T" "A" "C" "A" "T" "C" "G" "G" "T"
 [379] "A" "T" "T" "T" "T" "A" "A" "A" "G" "A" "T" "G" "T" "G" "A" "A" "C" "T"
 [397] "T" "A" "A" "G" "T" "A" "A" "C" "C" "T" "A" "C" "T" "T" "A" "G" "C" "T"
 [415] "G" "A" "C" "G" "G" "G" "A" "A" "G" "G" "T" "G" "C" "A" "C" "A" "T" "G"
 [433] "T" "A" "T" "G" "T" "G" "T" "G" "A" "C" "T" "C" "T" "A" "C" "A" "C" "C"
 [451] "A" "A" "G" "A" "T" "G" "C" "A" "C" "T" "T" "A" "G" "G" "C" "A" "T" "C"
 [469] "A" "A" "T" "A" "A" "A" "A" "G" "T" "T" "G" "C" "C" "G" "G" "T" "T" "T"
 [487] "G" "T" "A" "A" "T" "C" "C" "T" "T" "G" "A" "C" "A" "G" "T" "A" "A" "T"
 [505] "C" "G" "A" "G" "A" "T" "A" "A" "T" "T" "A" "C" "T" "T" "G" "C" "G" "G"
 [523] "G" "C" "A" "C" "A" "T" "A" "A" "C" "C" "T" "A" "C" "T" "C" "G" "G" "T"
 [541] "T" "C" "G" "T" "C" "C" "C" "C" "C" "T" "T" "A" "G" "C" "G" "T" "A" "C"
 [559] "G" "G" "G" "G" "G" "G" "G" "T" "G" "G" "G" "G" "A" "A" "C" "C" "A" "T"
 [577] "C" "A" "G" "C" "G" "T" "T" "C" "G" "T" "A" "T" "G" "T" "T" "A" "G" "T"
 [595] "C" "C" "T" "C" "C" "G" "G" "C" "A" "T" "T" "T" "T" "T" "G" "G" "T" "C"
 [613] "A" "C" "G" "G" "C" "C" "C" "T" "C" "C" "A" "T" "G" "A" "A" "A" "T" "A"
 [631] "C" "A" "T" "A" "C" "T" "A" "G" "C" "G" "T" "G" "C" "C" "A" "T" "T" "C"
 [649] "C" "G" "G" "T" "C" "A" "A" "A" "T" "G" "G" "C" "C" "C" "T" "G" "C" "G"
 [667] "A" "A" "G" "G" "A" "T" "G" "C" "G" "G" "T" "G" "C" "G" "G" "T" "A" "A"
 [685] "G" "C" "G" "T" "G" "T" "G" "G" "G" "C" "C" "A" "T" "A" "C" "T" "T" "G"
 [703] "G" "G" "C" "A" "G" "A" "T" "T" "G" "A" "G" "T" "T" "A" "T" "A" "A" "G"
 [721] "A" "A" "A" "C" "A" "G" "G" "C" "A" "A" "A" "T" "T" "G" "G" "G" "A" "A"
 [739] "C" "T" "A" "G" "T" "G" "C" "G" "G" "C" "A" "C" "A" "T" "G" "T" "A" "C"
 [757] "A" "G" "C" "T" "C" "G" "C" "A" "C" "T" "T" "C" "C" "T" "G" "G" "G" "G"
 [775] "G" "G" "C" "G" "A" "C" "T" "A" "C" "C" "G" "A" "A" "T" "T" "C" "C" "T"
 [793] "A" "G" "T" "A" "T" "G" "T" "C" "T" "G" "A" "G" "T" "A" "G" "C" "G" "T"
 [811] "A" "C" "C" "G" "G" "G" "C" "C" "A" "G" "C" "T" "T" "T" "G" "G" "G" "T"
 [829] "C" "C" "T" "C" "T" "T" "A" "C" "C" "T" "T" "G" "T" "A" "A" "T" "G" "G"
 [847] "G" "A" "T" "C" "G" "G" "C" "C" "T" "T" "A" "T" "G" "G" "G" "A" "T" "G"
 [865] "C" "C" "A" "T" "G" "A" "C" "G" "A" "C" "A" "C" "T" "G" "C" "G" "G" "G"
 [883] "A" "G" "G" "T" "T" "A" "A" "T" "A" "A" "G" "T" "G" "T" "C" "C" "G" "C"
 [901] "G" "A" "T" "A" "A" "A" "G" "C" "C" "T" "C" "G" "T" "G" "G" "T" "C" "G"
 [919] "A" "A" "A" "T" "C" "T" "G" "T" "T" "A" "C" "G" "T" "G" "C" "T" "C" "T"
 [937] "T" "C" "T" "G" "T" "C" "A" "T" "T" "T" "G" "C" "C" "A" "T" "A" "T" "T"
 [955] "G" "G" "T" "A" "A" "A" "G" "T" "T" "C" "A" "A" "G" "A" "G" "C" "C" "A"
 [973] "C" "C" "C" "T" "A" "T" "C" "T" "A" "T" "T" "G" "A" "C" "T" "C" "C" "T"
 [991] "A" "G" "A" "T" "C" "T" "C" "C" "C" "A" "A" "A" "T" "G" "T" "A" "T" "C"
[1009] "C" "T" "C" "C" "A" "A" "C" "A" "G" "T" "A" "C" "T" "T" "C" "A" "C" "C"
[1027] "T" "G" "G" "A" "T" "G" "G" "T" "A" "A" "C" "C" "C" "C" "A" "C" "C" "T"
[1045] "C" "A" "A" "T" "C" "A" "C" "C" "A" "C" "T" "T" "A" "G" "G" "T" "C" "T"
[1063] "C" "C" "A" "G" "T" "A" "C" "T" "T" "T" "T" "G" "A" "G" "C" "C" "G" "C"
[1081] "C" "T" "A" "C" "G" "C" "G" "C" "T" "C" "T" "C" "G" "A" "A" "A" "T" "A"
[1099] "A" "G" "C" "T" "A" "A" "G" "C" "T" "A" "G" "C" "T" "A" "C" "G" "G" "T"
[1117] "C" "C" "G" "T" "G" "T" "T" "A" "G" "G" "C" "G" "A" "A" "A" "A" "A" "T"
[1135] "G" "A" "A" "T" "C" "C" "C" "T" "T" "T" "C" "C" "A" "G" "C" "G" "C" "T"
[1153] "A" "C" "C" "A" "A" "G" "T" "G" "T" "A" "G" "T" "C" "G" "G" "A" "T" "G"
[1171] "C" "G" "G" "T" "T" "G" "A" "C" "T" "T" "A" "T" "G" "C" "C" "T" "G" "C"
[1189] "C" "C" "G" "G" "T" "G" "A" "G" "C" "A" "G" "A" "A" "T" "T" "T" "A" "A"
[1207] "A" "T" "C" "G" "C" "T" "G" "T" "A" "C" "C" "A" "A" "T" "C" "A" "G" "C"
[1225] "A" "C" "T" "A" "C" "C" "A" "C" "A" "A" "G" "G" "C" "G" "A" "A" "C" "G"
[1243] "G" "G" "G" "C" "A" "G" "C" "C" "A" "C" "G" "A" "C" "T" "G" "G" "C" "G"
[1261] "C" "C" "A" "C" "A" "A" "G" "C" "A" "T" "G" "G" "A" "A" "G" "G" "A" "G"
[1279] "T" "G" "T" "C" "G" "G" "G" "C" "G" "A" "A" "A" "T" "C" "A" "G" "G" "G"
[1297] "C" "C" "G" "C" "A" "T" "T" "A" "A" "G" "C" "C" "G" "T" "T" "T" "T" "A"
[1315] "T" "C" "A" "C" "G" "G" "G" "T" "A" "A" "A" "G" "A" "G" "G" "T" "C" "A"
[1333] "C" "A" "T" "G" "T" "G" "C" "A" "C" "A" "G" "A" "G" "C" "C" "A" "G" "A"
[1351] "T" "A" "G" "T" "C" "G" "G" "C" "A" "G" "T" "G" "A" "A" "G" "G" "G" "C"
[1369] "A" "C" "A" "A" "C" "G" "C" "T" "T" "T" "T" "T" "C" "G" "G" "C" "A" "G"
[1387] "G" "A" "A" "G" "A" "C" "C" "C" "T" "T" "G" "C" "A" "C" "C" "T" "T" "T"
[1405] "A" "T" "C" "A" "C" "A" "C" "C" "G" "C" "G" "G" "G" "T" "C" "A" "T" "C"
[1423] "A" "C" "C" "G" "G" "C" "C" "A" "A" "A" "G" "C" "A" "G" "T" "C" "G" "G"
[1441] "C" "G" "G" "T" "C" "A" "A" "C" "G" "T" "T" "A" "A" "A" "A" "T" "T" "A"
[1459] "T" "T" "G" "C" "A" "T" "G" "T" "C" "T" "A" "G" "G" "T" "A" "A" "A" "G"
[1477] "C" "A" "G" "G" "A" "C" "C" "A" "G" "A" "G" "A" "G" "A" "C" "G" "T" "C"
[1495] "G" "A" "A" "A" "T" "C"
```
:::

```{.r .cell-code}
randGenome4 <- paste(randGenome, collapse = "")
```
:::


Will need to compare this to others when able to do so.

## Challenge 4

The fourth challenge is to use the `set.seed(215)` command to create a random genome of 100 nucleotides in a single string.


::: {.cell}

```{.r .cell-code}
set.seed(215)
genomeLength <- 100

randGenome <- sample(nucleotides, size = genomeLength, replace = TRUE)
randGenome
```

::: {.cell-output .cell-output-stdout}
```
  [1] "T" "G" "G" "A" "A" "T" "C" "T" "T" "T" "A" "A" "T" "G" "T" "T" "C" "C"
 [19] "G" "A" "C" "C" "T" "T" "T" "G" "A" "G" "C" "C" "T" "C" "A" "A" "G" "T"
 [37] "T" "G" "G" "A" "C" "T" "A" "C" "C" "G" "C" "G" "G" "C" "C" "C" "C" "C"
 [55] "G" "A" "C" "C" "G" "A" "G" "A" "G" "C" "T" "A" "A" "C" "T" "C" "T" "A"
 [73] "A" "A" "T" "G" "A" "T" "G" "C" "A" "A" "G" "C" "A" "G" "C" "G" "C" "G"
 [91] "T" "G" "C" "C" "G" "A" "G" "T" "C" "T"
```
:::

```{.r .cell-code}
paste(randGenome, collapse = "")
```

::: {.cell-output .cell-output-stdout}
```
[1] "TGGAATCTTTAATGTTCCGACCTTTGAGCCTCAAGTTGGACTACCGCGGCCCCCGACCGAGAGCTAACTCTAAATGATGCAAGCAGCGCGTGCCGAGTCT"
```
:::
:::


The number of Adenine (A) in this sequence: **23** (need to verify with others)

### Loops

Basic idea of using a `for` loop function:

1.  Set an iterator (this may just be a counter or it may be floating over elements in an existing list).

2.  Provide the instructions to be run each time through the loop.

Practicing loops:


::: {.cell}

```{.r .cell-code}
mySum <- 0

for(i in 1:10){
  mySum <- mySum + i
  print(mySum)
}
```

::: {.cell-output .cell-output-stdout}
```
[1] 1
[1] 3
[1] 6
[1] 10
[1] 15
[1] 21
[1] 28
[1] 36
[1] 45
[1] 55
```
:::
:::


## Challenge 5

The fifth challenge is to initialize a variable called `myProduct` (with the value 1) and write a loop using the iterator `j`.


::: {.cell}

```{.r .cell-code}
myProduct <- 1

for(j in 1:15){
  myProduct <- myProduct + j
  print(myProduct)
}
```

::: {.cell-output .cell-output-stdout}
```
[1] 2
[1] 4
[1] 7
[1] 11
[1] 16
[1] 22
[1] 29
[1] 37
[1] 46
[1] 56
[1] 67
[1] 79
[1] 92
[1] 106
[1] 121
```
:::
:::


This code block runs the `for` loop with the created variable. Need to verify this with others when get the chance.

## Challenge 6

The sixth challenge is to create a random genome sub string of 10 nucleotides and use the `paste` function to collapse to a single string. Then, we need to use a `for` loop to print out each nucleotide.


::: {.cell}

```{.r .cell-code}
numNucleotides <- 10

randGenome <- sample(nucleotides, size = numNucleotides, replace = TRUE)
randGenome
```

::: {.cell-output .cell-output-stdout}
```
 [1] "C" "T" "G" "T" "G" "G" "A" "C" "A" "G"
```
:::

```{.r .cell-code}
paste(randGenome, collapse = "")
```

::: {.cell-output .cell-output-stdout}
```
[1] "CTGTGGACAG"
```
:::

```{.r .cell-code}
randGenome <- paste(randGenome, collapse = "")

for(i in 1:10){
  print(str_sub(randGenome, start = i, end = i))
}
```

::: {.cell-output .cell-output-stdout}
```
[1] "C"
[1] "T"
[1] "G"
[1] "T"
[1] "G"
[1] "G"
[1] "A"
[1] "C"
[1] "A"
[1] "G"
```
:::
:::


The above code block combines multiple functions to get a simple result. First, the `randGenome` function is created for 10 random nucleotides. Next, the `for` loop function creates the nucleotides into a single string, utilizing the `str_sub` command. This creates the whole strand into a single character.

## Challenge 7

This challenge asks to count the number of occurrences of Adenine in the randGenome sequence. This is done using an adaptation of the loop function. By adding `Adenine_count + 1`, the code knows to update the adenine count every time an `A` is encountered in the `randGenome`.


::: {.cell}

```{.r .cell-code}
randGenome
```

::: {.cell-output .cell-output-stdout}
```
[1] "CTGTGGACAG"
```
:::

```{.r .cell-code}
randGenome<- paste(randGenome, collapse = "")
Adenine_count <- 0
for(i in 1:nchar(randGenome)){
  if(str_sub(randGenome, start = i, end = i) == "A"){
    Adenine_count <- Adenine_count + 1
  }
}
print(Adenine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 2
```
:::
:::


## Challenge 8

In this challenge we must count the frequencies for each of the four nucleotides.


::: {.cell}

```{.r .cell-code}
randGenome
```

::: {.cell-output .cell-output-stdout}
```
[1] "CTGTGGACAG"
```
:::

```{.r .cell-code}
randGenome<- paste(randGenome, collapse = "")
Guanine_count <- 0
for(i in 1:nchar(randGenome)){
  if(str_sub(randGenome, start = i, end = i) == "G"){
    Guanine_count <- Guanine_count + 1
  }
}
print(Guanine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 4
```
:::
:::


This counts the frequency for `G`.


::: {.cell}

```{.r .cell-code}
randGenome
```

::: {.cell-output .cell-output-stdout}
```
[1] "CTGTGGACAG"
```
:::

```{.r .cell-code}
randGenome<- paste(randGenome, collapse = "")
Cytosine_count <- 0
for(i in 1:nchar(randGenome)){
  if(str_sub(randGenome, start = i, end = i) == "C"){
    Cytosine_count <- Cytosine_count + 1
  }
}
print(Cytosine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 2
```
:::
:::


This counts the frequency for `C`.


::: {.cell}

```{.r .cell-code}
randGenome
```

::: {.cell-output .cell-output-stdout}
```
[1] "CTGTGGACAG"
```
:::

```{.r .cell-code}
randGenome<- paste(randGenome, collapse = "")
Thymine_count <- 0
for(i in 1:nchar(randGenome)){
  if(str_sub(randGenome, start = i, end = i) == "T"){
    Thymine_count <- Thymine_count + 1
  }
}
print(Thymine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 2
```
:::
:::


This counts the frequency for `T`.

## Challenge 9

Now we need to use the same concepts to count the frequencies on a real genome with over a million nucleotides.


::: {.cell}

```{.r .cell-code}
vib_c <- scan("~/Desktop/Bioinformatics/VibrioCholerae.txt", what = "character", sep = NULL)

#vib_c
```
:::


Above is the entire genome for Vibrio Cholerae. Below is the code to count each of the nucleotides individually.

Counts for:

-   A = **293,942**

-   G = **256,024**

-   C = **263,573**

-   T = **294,711**


::: {.cell}

```{.r .cell-code}
vib_c<- paste(vib_c, collapse = "")
Cytosine_count <- 0
for(i in 1:nchar(vib_c)){
  if(str_sub(vib_c, start = i, end = i) == "C"){
    Cytosine_count <- Cytosine_count + 1
  }
}
print(Cytosine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 263573
```
:::
:::

::: {.cell}

```{.r .cell-code}
vib_c<- paste(vib_c, collapse = "")
Adenine_count <- 0
for(i in 1:nchar(vib_c)){
  if(str_sub(vib_c, start = i, end = i) == "A"){
    Adenine_count <- Adenine_count + 1
  }
}
print(Adenine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 293942
```
:::
:::

::: {.cell}

```{.r .cell-code}
vib_c<- paste(vib_c, collapse = "")
Guanine_count <- 0
for(i in 1:nchar(vib_c)){
  if(str_sub(vib_c, start = i, end = i) == "G"){
    Guanine_count <- Guanine_count + 1
  }
}
print(Guanine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 256024
```
:::
:::

::: {.cell}

```{.r .cell-code}
vib_c<- paste(vib_c, collapse = "")
Thymine_count <- 0
for(i in 1:nchar(vib_c)){
  if(str_sub(vib_c, start = i, end = i) == "T"){
    Thymine_count <- Thymine_count + 1
  }
}
print(Thymine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 294711
```
:::
:::


This could also all be combined into one `for` loop, to avoid running the genome so many times. Each of the components would each be repeated three times (count, if statements, and print) for each of the individual nucleotides.

## Challenge 10

The tenth challenge is to navigate and verify the Rosalind challenge. The data is uploaded below and the number of individual nucleotides is calculated.


::: {.cell}

```{.r .cell-code}
rosalind_dna <- scan("~/Desktop/Bioinformatics/rosalind_dna.txt", what = "character", sep = NULL)

rosalind_dna
```

::: {.cell-output .cell-output-stdout}
```
[1] "ATGGGGGACAGACTTAATGCTAGGTAAGTAGGCGTTAGCGCCACGCACTAGGCGTGATTGTTAGACCAAAGCCCCTTCAGGCGGCCGATCGACACTAGAATCGCCAACTCCGCGGCCGTTTTGTTATGGGGGCTGTTACGCAGTGTCCCGCTAACGGTAGGTTGAACAGATCCACAAAACAGCTCAAAATTCTCCTGTCGATTTGGCCTGAATCCATTAATGTTGTGGAAAGTACGTTCATACCGATCACGTCATTCTTAGGCAGGAAGGGTCCAAAGTCAGGGAATTATTGAGTAAGTCACGTGGGCTGCGGAACATCAATTGGTGCCCCTAGGGCTTTGTTATTATTGGGAGTGTTCGAGTTCCAGATCGGAAATATCTAACCAAATAGAAGGGGTACTCAGAAGAATTGTTTCTGTACTTTAGTGAACAGTGTTTTGTTCCAGCACTCTCTTCAGGGACTCCGTAGCAAAAGCATGGTACAGTGGCTAGGCAGTATAGTACTATTTGCGTTGAAGCTTTACGGGGTTGTTTCTGCTATCGCATCCACTGAGCACAGCCCGTTTTCTAGGGATGGGGCGCTTAATACGACAATAGTCGGGAGATCCGAGAGCCCACGGGTTCGTTGACCTAAACGTAAGCAACGTGTTAGCACATCCCTTCATGAGGGTGTTCAGGTACGAGTATCACATACGAAACAAAGGGGCAATACTGCGATTGCGGATCCTGTCCCCGACACTGTTTTGACATACCTAGACACTGTGCCTCATATTCCGAAGGGCAATCATCCAGCAGTACTCCTACGACTTTAGTTCGCTAGTGTTCGCGCCACCACTCTAGAGAACCATTATGTTCGACGCGACAAGCGGTTCAGTCCCCTTGCCGTTCGCGGACTTTTCATAGCTAATCGGCCAGCGGGTTGGTCTATCTTTATGA"
```
:::
:::

::: {.cell}

```{.r .cell-code}
rosalind_dna<- paste(rosalind_dna, collapse = "")
Thymine_count <- 0
Cytosine_count <- 0
Guanine_count <- 0
Adenine_count <- 0

for(i in 1:nchar(rosalind_dna)){
  if(str_sub(rosalind_dna, start = i, end = i) == "T"){
    Thymine_count <- Thymine_count + 1
  }
  if(str_sub(rosalind_dna, start = i, end = i) == "C"){
    Cytosine_count <- Cytosine_count + 1
  }
  if(str_sub(rosalind_dna, start = i, end = i) == "G"){
    Guanine_count <- Guanine_count + 1
  }
  if(str_sub(rosalind_dna, start = i, end = i) == "A"){
    Adenine_count <- Adenine_count + 1
  }
}
print(Thymine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 247
```
:::

```{.r .cell-code}
print(Cytosine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 219
```
:::

```{.r .cell-code}
print(Guanine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 240
```
:::

```{.r .cell-code}
print(Adenine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 230
```
:::
:::


Final Counts:

-   T: 247

-   C: 219

-   G: 240

-   A: 230

The challenge timed out before I was able to submit and verify my answers for the first data set, a second attempt is shown below.


::: {.cell}

```{.r .cell-code}
rosalind_dna1 <- scan("~/Desktop/Bioinformatics/rosalind_dna1.txt", what = "character", sep = NULL)

rosalind_dna1<- paste(rosalind_dna1, collapse = "")
Thymine_count <- 0
Cytosine_count <- 0
Guanine_count <- 0
Adenine_count <- 0

for(i in 1:nchar(rosalind_dna1)){
  if(str_sub(rosalind_dna1, start = i, end = i) == "T"){
    Thymine_count <- Thymine_count + 1
  }
  if(str_sub(rosalind_dna1, start = i, end = i) == "C"){
    Cytosine_count <- Cytosine_count + 1
  }
  if(str_sub(rosalind_dna1, start = i, end = i) == "G"){
    Guanine_count <- Guanine_count + 1
  }
  if(str_sub(rosalind_dna1, start = i, end = i) == "A"){
    Adenine_count <- Adenine_count + 1
  }
}
print(Thymine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 211
```
:::

```{.r .cell-code}
print(Cytosine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 214
```
:::

```{.r .cell-code}
print(Guanine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 173
```
:::

```{.r .cell-code}
print(Adenine_count)
```

::: {.cell-output .cell-output-stdout}
```
[1] 215
```
:::
:::


After submitting the answer to Rosalind, I was able to verify that these were the correct totals for each nucleotide for this data set.

# Replication Origin: Part I

## Intro: Functions

This is a function which takes in two arguments, a string (`genomeString`) and a `nucleotide`. The result of the function is the frequency of the `nucleotide` within the `genomeString`.


::: {.cell}

```{.r .cell-code}
nucleotide_frequency <- function(genomeString, nucleotide = "A"){
  count <- 0
  for(i in 1:nchar(genomeString)){
    if(str_sub(genomeString, start = i, end = i) == nucleotide){
      count <- count + 1
    }
  }
  return(count)
}

nucleotide_frequency("ACTTGCGGGTATCGAG", "G")
```

::: {.cell-output .cell-output-stdout}
```
[1] 6
```
:::
:::


This shows that there are 6 `guanine` in this string of nucleotides.

## Challenge 1

The first challenge for this section is to use the `sample()` function to create a random genome at least 2000 in length. Then, we must count the frequency of Cytosine.


::: {.cell}

```{.r .cell-code}
nt_sample <- sample(nucleotides, size = 2000, replace = TRUE)
nt_sample <- paste(nt_sample, collapse = "")

nucleotide_frequency(nt_sample, "C")
```

::: {.cell-output .cell-output-stdout}
```
[1] 487
```
:::
:::


## Challenge 2

In this challenge we must build a new function, `rand_genome()`, which uses the parameter `k` to determine how many nucleotides we want to generate in the genome.


::: {.cell}

```{.r .cell-code}
rand_genome <- function(k){
  randGenome <- sample(nucleotides, size = k, replace = TRUE)
  
  randGenome <- paste(randGenome, collapse = "")
  return(randGenome)
}

rand_genome(10)
```

::: {.cell-output .cell-output-stdout}
```
[1] "AACAGTAAAT"
```
:::
:::


## Challenge 3

In this challenge we a building a new function called `generate_3_mers()` to generate all the substrings of 3 nucleotides. Next, we want to use the `rand-genome()` function to construct a random genome of 2000 nucleotides in length, then use the `generate_3_mers()` to compute all the 3-mers in the random genome.


::: {.cell}

```{.r .cell-code}
myString <- rand_genome(10)
generate_3_mers <- function(myString) {
  list_3_mers <- c()
  
  for(i in 1:(nchar(myString) - 2)){
  list_3_mers <- list_3_mers %>%
  append(str_sub(myString, start = i, end = i + 2))
    }
  return(list_3_mers)
}
myString
```

::: {.cell-output .cell-output-stdout}
```
[1] "GACATTAGAA"
```
:::

```{.r .cell-code}
generate_3_mers(myString)
```

::: {.cell-output .cell-output-stdout}
```
[1] "GAC" "ACA" "CAT" "ATT" "TTA" "TAG" "AGA" "GAA"
```
:::
:::


## Challenge 4

For this challenge, we will create a new, updated version of the `generate_3_mers()` function so that it can generate k-mers of any length (must be less than the size of the original `genomeString`).


::: {.cell}

```{.r .cell-code}
generate_k_mers <- function(string, k = 3) {
  list_codon <- c()
  
  for (i in seq(1, nchar(string) - k + 1, by = k)) {
    list_codon <- list_codon %>%
      append(str_sub(string, start = i, end = i + k - 1))
  }
  return(list_codon)
}

generate_k_mers(rand_genome(9))
```

::: {.cell-output .cell-output-stdout}
```
[1] "GAC" "AAG" "ATG"
```
:::
:::


## Challenge 5

The last challenge is to create a new function which will count the number of occurrences of a particular pattern within the larger genome string.


::: {.cell}

```{.r .cell-code}
nt_patterns <- function(string, pattern){
  nt_matches <- 0
  for(i in 1:nchar(string)){
    if(str_sub(string, i, i + str_length(pattern)-1) == pattern){
      nt_matches = nt_matches + 1
    }
  }
  return(nt_matches)
}
  
nt_patterns(rand_genome(2000), "CTG")
```

::: {.cell-output .cell-output-stdout}
```
[1] 29
```
:::
:::


This code successfully creates a random genome, and then counts the number of specified kmers which are identified in quotes.

### Part 2

This part of the challenge uses data from rosalind to count the number of identified kmers. The rosalind data is loaded below.


::: {.cell}

```{.r .cell-code}
rosalind_string <- "TTAGTCCCCAGTCCCCAGTCCCCTCCAGTCCCCGCAGTCCCCCAGTCCCCAGTCCCCCAGTCCCCAGTCCCCAGTCCCCAGCCAGTCCCCACCGGTGTGGTAGTCCCCCAAGTCCCCAAGTCCCCAGTGATAACAGTCCCCTTCTCTAAGTCCCCAGTCCCCGAGTCCCCAGTTGAGTCCCCCTAGTCCCCGCCTATAGTCCCCCCACGAGTCCCCTGAAGTCCCCTGAAAGTCCCCCTGACGCAAGTCCCCTAGTCCCCCAGTCCCCAGAAGTCCCCCAGTCCCCTAAGTCCCCTAGAGTCCCCAGTCCCCGAGAGTCCCCTGTAAGTCCCCCTCAGTCCCCGGCTCGAGTCCCCGATGAGTCCCCGAGTCCCCCCGAGTCCCCGGTTAGTCCCCAAGTCCCCGAGTCCCCGAGTCCCCTGAAGTCCCCGAGTCCCCTCGAGTCCCCAGTCCCCGCTAGTCCCCCTTAGTCCCCAGTCCCCGAGTCCCCAGTCCCCAGTCCCCAAGTCCCCCGTGGAGAAGTCCCCGCAGTCCCCAGTCCCCTCGATTAGTCCCCATGCGATAGTCCCCCAGTCCCCTGAGTCCCCAGTCCCCAAGTCCCCGTTAGTCCCCGAGTCCCCAAAATTAGTCCCCGAAGTCCCCCCGTAGTCCCCTGTGAGTCCCCGAGTCCCCAGTCCCCTTACGAGTCCCCGTCCAGTCCCCTGATTATATGAGAGTCCCCTTGGAGTCCCCTAGTCCCCTAAGTCCCCAGAGTGATTCTTAGTCCCCAAGTCCCCAGTCCCCGCTAGTCCCCATAGTCCCCAGTCCCCCGCAGTCCCCCTACCTCAGTCCCCAAGTCCCCCAGTCCCCCAGTCCCCGGTATTAGTCCCCGAAGTCCCCGAGTCCCCATACTCAAGTCCCCCAGTCCCCGGATGGTAGAGTCCCCAGTCCCCTAGTCCCCCCGAGTCCCCAGTCCCCCAGTCCCCACGGCGGCTAAAGTCCCCTAGTCCCCAGTCCCCGATGCAGTCCCCAAGTCCCCAGTCCCC"
```
:::


This section uses the command created above to count the number of `AGTCCCCAG` in the code, which is appears to be 25.


::: {.cell}

```{.r .cell-code}
nt_patterns(rosalind_string, "AGTCCCCAG")
```

::: {.cell-output .cell-output-stdout}
```
[1] 25
```
:::
:::


# Replication Origin: Part 2
