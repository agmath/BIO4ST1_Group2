---
title: "Intro to R for Bioinformatics"
author: "Melanie Dube, Scientist"
format: html
execute:
  keep-md: true
---



## Introduction

### Activity Objectives

Below are the listed objectives for this new notebook:

-   Use the arrow (`<-`) operator to store objects in variables.

-   Use R\'s `sample()` function to create a random \"genome\" for the purpose of testing functions.

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
 [1] "G" "A" "A" "G" "T" "A" "A" "T" "A" "A" "C" "A" "G" "T" "G"
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
[1] "GAAGTAATAACAGTG"
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
   [1] "T" "A" "C" "A" "C" "T" "T" "T" "G" "A" "T" "C" "G" "A" "C" "A" "A" "A"
  [19] "T" "T" "T" "A" "T" "T" "G" "C" "G" "A" "G" "A" "A" "T" "C" "G" "C" "C"
  [37] "C" "G" "C" "G" "G" "C" "T" "G" "C" "G" "A" "T" "A" "C" "T" "G" "A" "C"
  [55] "G" "A" "T" "A" "G" "A" "T" "A" "A" "A" "G" "A" "T" "G" "C" "T" "T" "C"
  [73] "T" "T" "C" "G" "C" "T" "G" "A" "C" "G" "A" "G" "C" "G" "A" "A" "A" "T"
  [91] "T" "G" "G" "G" "A" "A" "C" "C" "T" "T" "C" "A" "G" "C" "A" "G" "G" "A"
 [109] "C" "C" "C" "T" "C" "T" "A" "G" "G" "A" "A" "A" "G" "G" "G" "T" "T" "C"
 [127] "A" "T" "C" "G" "C" "T" "T" "G" "G" "C" "G" "A" "T" "C" "T" "G" "C" "A"
 [145] "A" "T" "A" "T" "C" "A" "A" "A" "G" "T" "T" "A" "A" "C" "G" "A" "T" "G"
 [163] "G" "C" "A" "A" "G" "A" "A" "T" "C" "A" "G" "A" "C" "G" "A" "T" "C" "C"
 [181] "T" "G" "T" "T" "G" "C" "G" "G" "T" "G" "A" "G" "G" "C" "C" "G" "G" "G"
 [199] "C" "A" "A" "A" "T" "A" "A" "T" "A" "A" "G" "T" "A" "G" "A" "T" "T" "C"
 [217] "C" "A" "T" "C" "T" "G" "G" "G" "G" "T" "G" "A" "T" "G" "T" "C" "A" "G"
 [235] "T" "G" "C" "C" "T" "A" "A" "A" "C" "A" "C" "G" "T" "T" "C" "A" "A" "C"
 [253] "G" "C" "T" "C" "T" "G" "T" "C" "G" "A" "T" "G" "A" "C" "T" "G" "T" "A"
 [271] "C" "C" "A" "C" "T" "G" "A" "T" "C" "T" "C" "T" "A" "G" "C" "C" "G" "C"
 [289] "A" "C" "G" "A" "C" "C" "G" "T" "G" "A" "G" "T" "T" "G" "A" "A" "G" "C"
 [307] "A" "A" "C" "A" "T" "C" "C" "G" "C" "C" "G" "C" "T" "A" "C" "T" "A" "C"
 [325] "A" "T" "C" "C" "C" "A" "T" "C" "A" "C" "C" "G" "G" "A" "C" "A" "A" "T"
 [343] "G" "T" "T" "C" "A" "T" "G" "T" "G" "A" "T" "A" "G" "T" "G" "G" "G" "C"
 [361] "C" "T" "A" "G" "A" "G" "T" "T" "G" "G" "C" "T" "C" "T" "G" "C" "A" "C"
 [379] "T" "A" "G" "G" "A" "C" "C" "C" "A" "C" "G" "T" "C" "T" "T" "A" "T" "C"
 [397] "G" "C" "T" "T" "C" "A" "G" "A" "G" "T" "A" "C" "A" "C" "T" "T" "C" "T"
 [415] "C" "A" "A" "G" "G" "G" "A" "T" "T" "G" "C" "G" "A" "G" "G" "T" "C" "C"
 [433] "A" "C" "A" "G" "C" "T" "C" "G" "G" "C" "A" "C" "A" "G" "C" "C" "A" "A"
 [451] "G" "G" "T" "A" "G" "T" "A" "T" "T" "T" "C" "C" "A" "C" "T" "T" "C" "G"
 [469] "C" "C" "G" "G" "A" "G" "A" "C" "T" "C" "C" "C" "C" "A" "C" "T" "A" "C"
 [487] "C" "A" "G" "A" "G" "G" "T" "A" "T" "G" "G" "G" "G" "G" "C" "G" "C" "A"
 [505] "A" "G" "G" "G" "G" "C" "C" "T" "A" "C" "A" "A" "G" "A" "C" "A" "C" "G"
 [523] "T" "C" "A" "G" "C" "C" "G" "T" "A" "A" "G" "T" "A" "A" "G" "T" "A" "C"
 [541] "T" "A" "G" "T" "T" "G" "A" "A" "T" "C" "T" "T" "G" "A" "G" "G" "G" "A"
 [559] "G" "G" "A" "T" "T" "G" "G" "A" "C" "G" "T" "C" "T" "T" "A" "C" "A" "T"
 [577] "A" "G" "T" "A" "G" "C" "T" "A" "T" "T" "G" "T" "T" "T" "T" "T" "C" "C"
 [595] "A" "A" "T" "T" "T" "A" "T" "T" "C" "A" "T" "A" "G" "G" "A" "T" "T" "T"
 [613] "A" "A" "T" "A" "T" "A" "T" "C" "G" "A" "A" "A" "A" "A" "G" "G" "C" "C"
 [631] "T" "G" "A" "T" "T" "G" "C" "T" "T" "T" "C" "T" "A" "G" "G" "C" "A" "T"
 [649] "C" "G" "C" "C" "T" "C" "A" "G" "A" "A" "A" "G" "T" "T" "G" "C" "C" "T"
 [667] "A" "T" "C" "A" "A" "G" "A" "A" "C" "G" "G" "G" "C" "C" "T" "T" "C" "G"
 [685] "G" "C" "T" "T" "C" "C" "T" "G" "C" "G" "C" "C" "C" "A" "G" "A" "A" "G"
 [703] "C" "T" "A" "C" "A" "A" "T" "G" "T" "C" "A" "T" "A" "T" "T" "G" "C" "A"
 [721] "G" "T" "A" "T" "G" "C" "C" "T" "C" "G" "C" "C" "C" "C" "T" "T" "C" "A"
 [739] "C" "T" "G" "T" "G" "C" "G" "C" "A" "G" "T" "C" "G" "G" "C" "C" "C" "G"
 [757] "C" "T" "G" "A" "C" "T" "G" "G" "T" "T" "G" "G" "G" "A" "G" "T" "C" "G"
 [775] "C" "T" "A" "G" "A" "A" "G" "T" "A" "T" "C" "T" "G" "T" "A" "T" "T" "T"
 [793] "T" "G" "G" "C" "A" "C" "C" "T" "G" "A" "G" "G" "T" "T" "C" "A" "A" "G"
 [811] "G" "C" "T" "A" "A" "A" "G" "C" "T" "A" "C" "G" "A" "A" "T" "T" "G" "G"
 [829] "A" "G" "C" "G" "C" "T" "T" "C" "G" "T" "C" "T" "C" "T" "C" "T" "C" "T"
 [847] "T" "A" "A" "G" "G" "C" "G" "C" "C" "A" "C" "A" "T" "C" "C" "G" "T" "G"
 [865] "T" "G" "G" "T" "T" "A" "G" "C" "C" "C" "C" "A" "A" "T" "A" "T" "T" "G"
 [883] "C" "G" "G" "C" "G" "C" "A" "G" "C" "A" "T" "C" "A" "C" "T" "G" "A" "A"
 [901] "C" "C" "C" "T" "G" "C" "C" "T" "A" "C" "G" "C" "G" "G" "G" "A" "A" "T"
 [919] "G" "A" "A" "T" "A" "G" "G" "T" "C" "T" "G" "C" "A" "G" "T" "G" "G" "C"
 [937] "T" "C" "T" "T" "A" "G" "C" "T" "A" "T" "T" "C" "C" "A" "T" "C" "G" "T"
 [955] "T" "A" "A" "T" "A" "T" "C" "G" "G" "A" "C" "A" "C" "G" "G" "C" "A" "T"
 [973] "G" "A" "C" "G" "G" "A" "C" "T" "T" "T" "G" "A" "C" "T" "T" "T" "C" "A"
 [991] "G" "A" "C" "T" "A" "G" "A" "A" "G" "C" "A" "A" "T" "G" "A" "G" "T" "A"
[1009] "T" "A" "G" "G" "T" "T" "A" "C" "A" "A" "A" "A" "C" "C" "A" "C" "G" "A"
[1027] "G" "A" "G" "A" "C" "T" "T" "T" "G" "A" "T" "G" "A" "T" "G" "C" "G" "A"
[1045] "G" "T" "C" "G" "G" "A" "T" "G" "G" "T" "A" "C" "C" "T" "G" "C" "G" "T"
[1063] "T" "T" "T" "G" "A" "T" "A" "T" "C" "C" "T" "A" "T" "G" "T" "T" "T" "T"
[1081] "T" "T" "G" "G" "C" "C" "A" "C" "A" "A" "C" "T" "G" "T" "A" "C" "T" "C"
[1099] "G" "C" "C" "T" "C" "G" "T" "T" "A" "A" "T" "A" "G" "T" "T" "C" "G" "C"
[1117] "A" "C" "G" "G" "G" "C" "G" "T" "T" "T" "A" "G" "G" "G" "T" "G" "T" "T"
[1135] "A" "C" "C" "T" "T" "C" "A" "T" "A" "T" "G" "C" "T" "T" "A" "A" "A" "A"
[1153] "T" "C" "G" "A" "T" "G" "G" "T" "A" "T" "C" "T" "C" "G" "G" "G" "G" "T"
[1171] "T" "C" "T" "A" "A" "C" "T" "T" "T" "A" "C" "G" "C" "T" "T" "C" "T" "T"
[1189] "G" "G" "A" "T" "C" "T" "T" "T" "C" "T" "G" "A" "A" "C" "T" "T" "C" "A"
[1207] "C" "T" "C" "A" "T" "T" "C" "A" "T" "C" "A" "C" "G" "C" "T" "T" "G" "G"
[1225] "G" "T" "C" "G" "A" "G" "G" "A" "G" "T" "G" "T" "T" "C" "C" "C" "A" "T"
[1243] "G" "T" "G" "A" "T" "G" "G" "T" "A" "C" "A" "T" "C" "C" "T" "A" "T" "C"
[1261] "T" "T" "G" "G" "T" "C" "A" "T" "A" "T" "A" "T" "G" "A" "G" "C" "C" "T"
[1279] "T" "G" "C" "A" "C" "C" "T" "T" "T" "A" "T" "G" "T" "C" "C" "T" "G" "A"
[1297] "G" "G" "C" "T" "G" "C" "G" "A" "C" "A" "A" "C" "A" "G" "G" "T" "T" "T"
[1315] "C" "A" "C" "T" "A" "T" "T" "C" "A" "T" "T" "A" "A" "G" "A" "C" "T" "G"
[1333] "C" "T" "A" "G" "G" "G" "G" "G" "G" "T" "A" "C" "G" "G" "A" "C" "T" "G"
[1351] "G" "T" "G" "G" "T" "G" "C" "G" "C" "C" "A" "A" "G" "C" "T" "C" "A" "A"
[1369] "G" "T" "G" "G" "G" "C" "A" "A" "T" "C" "T" "T" "A" "T" "T" "T" "A" "C"
[1387] "G" "C" "G" "T" "T" "A" "C" "G" "G" "G" "C" "A" "A" "T" "T" "G" "G" "T"
[1405] "G" "G" "T" "T" "T" "T" "G" "T" "A" "G" "G" "G" "T" "T" "A" "G" "G" "C"
[1423] "A" "C" "C" "C" "T" "A" "T" "A" "C" "A" "G" "C" "T" "G" "C" "C" "A" "G"
[1441] "T" "A" "T" "A" "T" "A" "T" "C" "C" "T" "G" "G" "T" "G" "T" "T" "C" "C"
[1459] "G" "C" "A" "G" "T" "C" "C" "T" "T" "A" "C" "G" "C" "G" "G" "G" "A" "C"
[1477] "A" "A" "A" "A" "T" "C" "T" "A" "T" "G" "A" "G" "A" "G" "C" "C" "A" "T"
[1495] "C" "C" "G" "A" "G" "C"
```
:::

```{.r .cell-code}
paste(randGenomeChal3, collapse = "")
```

::: {.cell-output .cell-output-stdout}
```
[1] "TACACTTTGATCGACAAATTTATTGCGAGAATCGCCCGCGGCTGCGATACTGACGATAGATAAAGATGCTTCTTCGCTGACGAGCGAAATTGGGAACCTTCAGCAGGACCCTCTAGGAAAGGGTTCATCGCTTGGCGATCTGCAATATCAAAGTTAACGATGGCAAGAATCAGACGATCCTGTTGCGGTGAGGCCGGGCAAATAATAAGTAGATTCCATCTGGGGTGATGTCAGTGCCTAAACACGTTCAACGCTCTGTCGATGACTGTACCACTGATCTCTAGCCGCACGACCGTGAGTTGAAGCAACATCCGCCGCTACTACATCCCATCACCGGACAATGTTCATGTGATAGTGGGCCTAGAGTTGGCTCTGCACTAGGACCCACGTCTTATCGCTTCAGAGTACACTTCTCAAGGGATTGCGAGGTCCACAGCTCGGCACAGCCAAGGTAGTATTTCCACTTCGCCGGAGACTCCCCACTACCAGAGGTATGGGGGCGCAAGGGGCCTACAAGACACGTCAGCCGTAAGTAAGTACTAGTTGAATCTTGAGGGAGGATTGGACGTCTTACATAGTAGCTATTGTTTTTCCAATTTATTCATAGGATTTAATATATCGAAAAAGGCCTGATTGCTTTCTAGGCATCGCCTCAGAAAGTTGCCTATCAAGAACGGGCCTTCGGCTTCCTGCGCCCAGAAGCTACAATGTCATATTGCAGTATGCCTCGCCCCTTCACTGTGCGCAGTCGGCCCGCTGACTGGTTGGGAGTCGCTAGAAGTATCTGTATTTTGGCACCTGAGGTTCAAGGCTAAAGCTACGAATTGGAGCGCTTCGTCTCTCTCTTAAGGCGCCACATCCGTGTGGTTAGCCCCAATATTGCGGCGCAGCATCACTGAACCCTGCCTACGCGGGAATGAATAGGTCTGCAGTGGCTCTTAGCTATTCCATCGTTAATATCGGACACGGCATGACGGACTTTGACTTTCAGACTAGAAGCAATGAGTATAGGTTACAAAACCACGAGAGACTTTGATGATGCGAGTCGGATGGTACCTGCGTTTTGATATCCTATGTTTTTTGGCCACAACTGTACTCGCCTCGTTAATAGTTCGCACGGGCGTTTAGGGTGTTACCTTCATATGCTTAAAATCGATGGTATCTCGGGGTTCTAACTTTACGCTTCTTGGATCTTTCTGAACTTCACTCATTCATCACGCTTGGGTCGAGGAGTGTTCCCATGTGATGGTACATCCTATCTTGGTCATATATGAGCCTTGCACCTTTATGTCCTGAGGCTGCGACAACAGGTTTCACTATTCATTAAGACTGCTAGGGGGGTACGGACTGGTGGTGCGCCAAGCTCAAGTGGGCAATCTTATTTACGCGTTACGGGCAATTGGTGGTTTTGTAGGGTTAGGCACCCTATACAGCTGCCAGTATATATCCTGGTGTTCCGCAGTCCTTACGCGGGACAAAATCTATGAGAGCCATCCGAGC"
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
  print(str_sub(randGenome, start = 1L, end = -1L))
}
```

::: {.cell-output .cell-output-stdout}
```
[1] "CTGTGGACAG"
[1] "CTGTGGACAG"
[1] "CTGTGGACAG"
[1] "CTGTGGACAG"
[1] "CTGTGGACAG"
[1] "CTGTGGACAG"
[1] "CTGTGGACAG"
[1] "CTGTGGACAG"
[1] "CTGTGGACAG"
[1] "CTGTGGACAG"
```
:::
:::


The above code block combines multiple functions to get a simple result. First, the `randGenome` function is created for 10 random nucleotides. Next, the `for` loop function creates the nucleotides into a single string, utilizing the `str_sub` command. This creates the whole strand into a single character.
