---
title: "Starter Notebook"
author: "Adaobi Nwankwo, Scientist"
format: html
execute:
  keep-md: true
---




::: {.cell}

```{.r .cell-code}
nucleotides <- c("Adenine (A)", "Cytosine (C), ", "Guanine (G)", "Thymine (T)")

nucleotides
```

::: {.cell-output .cell-output-stdout}
```
[1] "Adenine (A)"    "Cytosine (C), " "Guanine (G)"    "Thymine (T)"   
```
:::
:::

::: {.cell}

```{.r .cell-code}
genomeLength <- 15

randGenome <- sample(nucleotides, size = genomeLength, replace = TRUE)

paste(randGenome, collapse = "")
```

::: {.cell-output .cell-output-stdout}
```
[1] "Guanine (G)Adenine (A)Cytosine (C), Guanine (G)Thymine (T)Guanine (G)Adenine (A)Thymine (T)Cytosine (C), Adenine (A)Thymine (T)Thymine (T)Guanine (G)Adenine (A)Cytosine (C), "
```
:::
:::

::: {.cell}

```{.r .cell-code}
genomeLength <- 1500

randGenome <- sample(nucleotides, size = genomeLength, replace = TRUE)

paste(randGenome, collapse = "")
```

::: {.cell-output .cell-output-stdout}
```
[1] "Adenine (A)Thymine (T)Adenine (A)Thymine (T)Thymine (T)Thymine (T)Adenine (A)Thymine (T)Thymine (T)Thymine (T)Adenine (A)Thymine (T)Guanine (G)Cytosine (C), Thymine (T)Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Adenine (A)Thymine (T)Cytosine (C), Adenine (A)Thymine (T)Guanine (G)Adenine (A)Adenine (A)Adenine (A)Adenine (A)Adenine (A)Guanine (G)Adenine (A)Cytosine (C), Guanine (G)Guanine (G)Guanine (G)Adenine (A)Thymine (T)Adenine (A)Cytosine (C), Thymine (T)Cytosine (C), Cytosine (C), Cytosine (C), Cytosine (C), Guanine (G)Guanine (G)Thymine (T)Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Adenine (A)Adenine (A)Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Adenine (A)Guanine (G)Thymine (T)Cytosine (C), Adenine (A)Cytosine (C), Adenine (A)Cytosine (C), Thymine (T)Thymine (T)Thymine (T)Thymine (T)Guanine (G)Adenine (A)Adenine (A)Guanine (G)Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Thymine (T)Cytosine (C), Cytosine (C), Adenine (A)Cytosine (C), Guanine (G)Adenine (A)Guanine (G)Guanine (G)Thymine (T)Guanine (G)Thymine (T)Adenine (A)Adenine (A)Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Adenine (A)Cytosine (C), Adenine (A)Cytosine (C), Thymine (T)Thymine (T)Thymine (T)Thymine (T)Adenine (A)Thymine (T)Cytosine (C), Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Thymine (T)Thymine (T)Cytosine (C), Thymine (T)Cytosine (C), Cytosine (C), Cytosine (C), Thymine (T)Thymine (T)Guanine (G)Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Adenine (A)Guanine (G)Guanine (G)Adenine (A)Thymine (T)Thymine (T)Thymine (T)Cytosine (C), Guanine (G)Cytosine (C), Thymine (T)Thymine (T)Thymine (T)Cytosine (C), Adenine (A)Cytosine (C), Thymine (T)Cytosine (C), Thymine (T)Cytosine (C), Guanine (G)Cytosine (C), Thymine (T)Adenine (A)Adenine (A)Guanine (G)Thymine (T)Guanine (G)Cytosine (C), Thymine (T)Thymine (T)Cytosine (C), Adenine (A)Adenine (A)Cytosine (C), Guanine (G)Guanine (G)Thymine (T)Adenine (A)Guanine (G)Guanine (G)Cytosine (C), Thymine (T)Adenine (A)Adenine (A)Guanine (G)Thymine (T)Cytosine (C), Thymine (T)Thymine (T)Guanine (G)Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Cytosine (C), Thymine (T)Guanine (G)Adenine (A)Thymine (T)Thymine (T)Cytosine (C), Guanine (G)Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Guanine (G)Thymine (T)Thymine (T)Cytosine (C), Thymine (T)Cytosine (C), Cytosine (C), Thymine (T)Thymine (T)Cytosine (C), Guanine (G)Thymine (T)Thymine (T)Thymine (T)Cytosine (C), Guanine (G)Thymine (T)Thymine (T)Adenine (A)Guanine (G)Cytosine (C), Cytosine (C), Adenine (A)Adenine (A)Adenine (A)Cytosine (C), Thymine (T)Adenine (A)Adenine (A)Guanine (G)Thymine (T)Adenine (A)Cytosine (C), Guanine (G)Adenine (A)Adenine (A)Cytosine (C), Adenine (A)Guanine (G)Guanine (G)Guanine (G)Thymine (T)Thymine (T)Thymine (T)Guanine (G)Adenine (A)Cytosine (C), Guanine (G)Cytosine (C), Adenine (A)Cytosine (C), Cytosine (C), Guanine (G)Thymine (T)Adenine (A)Thymine (T)Thymine (T)Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Cytosine (C), Thymine (T)Thymine (T)Adenine (A)Cytosine (C), Adenine (A)Adenine (A)Thymine (T)Adenine (A)Guanine (G)Cytosine (C), Guanine (G)Thymine (T)Thymine (T)Thymine (T)Cytosine (C), Adenine (A)Cytosine (C), Thymine (T)Thymine (T)Cytosine (C), Adenine (A)Thymine (T)Guanine (G)Guanine (G)Cytosine (C), Adenine (A)Thymine (T)Adenine (A)Guanine (G)Adenine (A)Guanine (G)Guanine (G)Cytosine (C), Thymine (T)Thymine (T)Thymine (T)Guanine (G)Cytosine (C), Adenine (A)Guanine (G)Adenine (A)Adenine (A)Cytosine (C), Thymine (T)Cytosine (C), Guanine (G)Guanine (G)Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Guanine (G)Guanine (G)Adenine (A)Thymine (T)Thymine (T)Cytosine (C), Thymine (T)Adenine (A)Thymine (T)Adenine (A)Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Thymine (T)Cytosine (C), Adenine (A)Adenine (A)Thymine (T)Adenine (A)Cytosine (C), Guanine (G)Cytosine (C), Thymine (T)Guanine (G)Guanine (G)Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Cytosine (C), Guanine (G)Cytosine (C), Guanine (G)Adenine (A)Thymine (T)Guanine (G)Adenine (A)Cytosine (C), Cytosine (C), Thymine (T)Adenine (A)Thymine (T)Thymine (T)Guanine (G)Thymine (T)Guanine (G)Thymine (T)Guanine (G)Cytosine (C), Thymine (T)Adenine (A)Adenine (A)Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Guanine (G)Cytosine (C), Guanine (G)Adenine (A)Thymine (T)Thymine (T)Cytosine (C), Guanine (G)Guanine (G)Cytosine (C), Guanine (G)Thymine (T)Guanine (G)Guanine (G)Adenine (A)Guanine (G)Guanine (G)Thymine (T)Thymine (T)Thymine (T)Adenine (A)Adenine (A)Guanine (G)Adenine (A)Adenine (A)Thymine (T)Adenine (A)Adenine (A)Cytosine (C), Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Thymine (T)Thymine (T)Cytosine (C), Cytosine (C), Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Cytosine (C), Cytosine (C), Guanine (G)Cytosine (C), Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Thymine (T)Guanine (G)Cytosine (C), Adenine (A)Thymine (T)Adenine (A)Thymine (T)Cytosine (C), Cytosine (C), Cytosine (C), Cytosine (C), Adenine (A)Thymine (T)Adenine (A)Thymine (T)Thymine (T)Thymine (T)Thymine (T)Thymine (T)Adenine (A)Cytosine (C), Thymine (T)Guanine (G)Thymine (T)Adenine (A)Adenine (A)Cytosine (C), Thymine (T)Thymine (T)Thymine (T)Guanine (G)Thymine (T)Cytosine (C), Adenine (A)Cytosine (C), Guanine (G)Thymine (T)Guanine (G)Adenine (A)Cytosine (C), Adenine (A)Cytosine (C), Guanine (G)Adenine (A)Guanine (G)Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Adenine (A)Adenine (A)Cytosine (C), Guanine (G)Thymine (T)Cytosine (C), Guanine (G)Cytosine (C), Adenine (A)Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Adenine (A)Cytosine (C), Thymine (T)Guanine (G)Adenine (A)Adenine (A)Guanine (G)Guanine (G)Thymine (T)Adenine (A)Cytosine (C), Guanine (G)Thymine (T)Cytosine (C), Adenine (A)Guanine (G)Guanine (G)Guanine (G)Guanine (G)Adenine (A)Thymine (T)Guanine (G)Thymine (T)Thymine (T)Thymine (T)Guanine (G)Adenine (A)Thymine (T)Thymine (T)Adenine (A)Adenine (A)Cytosine (C), Adenine (A)Guanine (G)Cytosine (C), Thymine (T)Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Guanine (G)Adenine (A)Guanine (G)Thymine (T)Thymine (T)Adenine (A)Adenine (A)Adenine (A)Adenine (A)Cytosine (C), Guanine (G)Guanine (G)Cytosine (C), Thymine (T)Thymine (T)Thymine (T)Cytosine (C), Guanine (G)Guanine (G)Thymine (T)Adenine (A)Thymine (T)Adenine (A)Thymine (T)Adenine (A)Guanine (G)Guanine (G)Adenine (A)Guanine (G)Thymine (T)Guanine (G)Cytosine (C), Adenine (A)Guanine (G)Guanine (G)Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Adenine (A)Cytosine (C), Guanine (G)Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Cytosine (C), Guanine (G)Thymine (T)Guanine (G)Adenine (A)Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Adenine (A)Cytosine (C), Adenine (A)Guanine (G)Thymine (T)Guanine (G)Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Guanine (G)Thymine (T)Cytosine (C), Guanine (G)Guanine (G)Thymine (T)Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Cytosine (C), Adenine (A)Thymine (T)Guanine (G)Thymine (T)Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Adenine (A)Guanine (G)Adenine (A)Cytosine (C), Guanine (G)Guanine (G)Guanine (G)Cytosine (C), Adenine (A)Thymine (T)Guanine (G)Adenine (A)Cytosine (C), Adenine (A)Adenine (A)Guanine (G)Adenine (A)Thymine (T)Adenine (A)Adenine (A)Adenine (A)Guanine (G)Thymine (T)Adenine (A)Cytosine (C), Guanine (G)Thymine (T)Cytosine (C), Thymine (T)Guanine (G)Adenine (A)Thymine (T)Cytosine (C), Cytosine (C), Thymine (T)Cytosine (C), Thymine (T)Cytosine (C), Guanine (G)Guanine (G)Thymine (T)Thymine (T)Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Cytosine (C), Adenine (A)Adenine (A)Cytosine (C), Thymine (T)Cytosine (C), Cytosine (C), Cytosine (C), Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Cytosine (C), Cytosine (C), Thymine (T)Cytosine (C), Guanine (G)Thymine (T)Adenine (A)Adenine (A)Adenine (A)Thymine (T)Guanine (G)Guanine (G)Guanine (G)Thymine (T)Adenine (A)Thymine (T)Thymine (T)Guanine (G)Guanine (G)Guanine (G)Cytosine (C), Adenine (A)Adenine (A)Thymine (T)Guanine (G)Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Guanine (G)Cytosine (C), Thymine (T)Adenine (A)Guanine (G)Adenine (A)Thymine (T)Thymine (T)Guanine (G)Thymine (T)Thymine (T)Adenine (A)Thymine (T)Guanine (G)Guanine (G)Adenine (A)Cytosine (C), Thymine (T)Guanine (G)Thymine (T)Cytosine (C), Adenine (A)Thymine (T)Thymine (T)Cytosine (C), Guanine (G)Thymine (T)Cytosine (C), Thymine (T)Adenine (A)Thymine (T)Guanine (G)Thymine (T)Adenine (A)Cytosine (C), Guanine (G)Adenine (A)Adenine (A)Thymine (T)Guanine (G)Thymine (T)Cytosine (C), Cytosine (C), Adenine (A)Cytosine (C), Guanine (G)Thymine (T)Adenine (A)Adenine (A)Guanine (G)Adenine (A)Thymine (T)Thymine (T)Cytosine (C), Cytosine (C), Cytosine (C), Thymine (T)Guanine (G)Guanine (G)Cytosine (C), Thymine (T)Guanine (G)Thymine (T)Adenine (A)Thymine (T)Thymine (T)Thymine (T)Cytosine (C), Thymine (T)Thymine (T)Adenine (A)Cytosine (C), Cytosine (C), Adenine (A)Cytosine (C), Cytosine (C), Cytosine (C), Adenine (A)Thymine (T)Thymine (T)Cytosine (C), Cytosine (C), Adenine (A)Adenine (A)Guanine (G)Adenine (A)Thymine (T)Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Cytosine (C), Guanine (G)Thymine (T)Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Guanine (G)Cytosine (C), Thymine (T)Adenine (A)Guanine (G)Guanine (G)Cytosine (C), Thymine (T)Adenine (A)Adenine (A)Cytosine (C), Thymine (T)Thymine (T)Adenine (A)Guanine (G)Adenine (A)Guanine (G)Cytosine (C), Guanine (G)Thymine (T)Thymine (T)Adenine (A)Cytosine (C), Cytosine (C), Guanine (G)Thymine (T)Cytosine (C), Guanine (G)Guanine (G)Guanine (G)Cytosine (C), Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Guanine (G)Adenine (A)Cytosine (C), Guanine (G)Thymine (T)Cytosine (C), Cytosine (C), Thymine (T)Thymine (T)Thymine (T)Cytosine (C), Thymine (T)Thymine (T)Adenine (A)Guanine (G)Cytosine (C), Cytosine (C), Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Cytosine (C), Guanine (G)Guanine (G)Thymine (T)Guanine (G)Adenine (A)Cytosine (C), Adenine (A)Adenine (A)Thymine (T)Guanine (G)Cytosine (C), Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Adenine (A)Adenine (A)Adenine (A)Adenine (A)Thymine (T)Thymine (T)Guanine (G)Thymine (T)Cytosine (C), Thymine (T)Cytosine (C), Adenine (A)Thymine (T)Guanine (G)Thymine (T)Adenine (A)Adenine (A)Thymine (T)Guanine (G)Thymine (T)Adenine (A)Cytosine (C), Guanine (G)Guanine (G)Cytosine (C), Adenine (A)Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Thymine (T)Cytosine (C), Thymine (T)Thymine (T)Guanine (G)Thymine (T)Thymine (T)Adenine (A)Cytosine (C), Cytosine (C), Guanine (G)Thymine (T)Adenine (A)Cytosine (C), Thymine (T)Guanine (G)Adenine (A)Guanine (G)Adenine (A)Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Thymine (T)Adenine (A)Adenine (A)Cytosine (C), Adenine (A)Cytosine (C), Guanine (G)Thymine (T)Adenine (A)Adenine (A)Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Adenine (A)Adenine (A)Adenine (A)Adenine (A)Thymine (T)Guanine (G)Cytosine (C), Adenine (A)Guanine (G)Cytosine (C), Adenine (A)Cytosine (C), Thymine (T)Thymine (T)Adenine (A)Guanine (G)Guanine (G)Guanine (G)Thymine (T)Guanine (G)Adenine (A)Adenine (A)Cytosine (C), Guanine (G)Cytosine (C), Cytosine (C), Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Thymine (T)Cytosine (C), Thymine (T)Thymine (T)Cytosine (C), Thymine (T)Cytosine (C), Cytosine (C), Adenine (A)Adenine (A)Adenine (A)Thymine (T)Thymine (T)Cytosine (C), Cytosine (C), Thymine (T)Guanine (G)Guanine (G)Adenine (A)Adenine (A)Adenine (A)Guanine (G)Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Cytosine (C), Thymine (T)Adenine (A)Guanine (G)Cytosine (C), Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Thymine (T)Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Cytosine (C), Adenine (A)Adenine (A)Thymine (T)Guanine (G)Guanine (G)Guanine (G)Guanine (G)Thymine (T)Guanine (G)Cytosine (C), Thymine (T)Cytosine (C), Adenine (A)Cytosine (C), Cytosine (C), Guanine (G)Cytosine (C), Adenine (A)Thymine (T)Thymine (T)Cytosine (C), Thymine (T)Thymine (T)Guanine (G)Guanine (G)Thymine (T)Adenine (A)Adenine (A)Thymine (T)Guanine (G)Thymine (T)Guanine (G)Guanine (G)Adenine (A)Thymine (T)Thymine (T)Guanine (G)Adenine (A)Guanine (G)Adenine (A)Thymine (T)Thymine (T)Cytosine (C), Cytosine (C), Thymine (T)Adenine (A)Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Guanine (G)Thymine (T)Guanine (G)Guanine (G)Guanine (G)Cytosine (C), Adenine (A)Thymine (T)Thymine (T)Thymine (T)Thymine (T)Adenine (A)Cytosine (C), Thymine (T)Adenine (A)Cytosine (C), Thymine (T)Adenine (A)Guanine (G)Thymine (T)Adenine (A)Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Thymine (T)Guanine (G)Thymine (T)Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Thymine (T)Thymine (T)Thymine (T)Cytosine (C), Cytosine (C), Adenine (A)Guanine (G)Cytosine (C), Guanine (G)Guanine (G)Adenine (A)Guanine (G)Cytosine (C), Adenine (A)Guanine (G)Adenine (A)Thymine (T)Thymine (T)Adenine (A)Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Cytosine (C), Thymine (T)Adenine (A)Cytosine (C), Thymine (T)Thymine (T)Cytosine (C), Thymine (T)Adenine (A)Guanine (G)Adenine (A)Adenine (A)Thymine (T)Cytosine (C), Cytosine (C), Thymine (T)Thymine (T)Adenine (A)Adenine (A)Guanine (G)Thymine (T)Cytosine (C), Cytosine (C), Adenine (A)Guanine (G)Thymine (T)Cytosine (C), Thymine (T)Adenine (A)Guanine (G)Guanine (G)Thymine (T)Guanine (G)Thymine (T)Guanine (G)Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Thymine (T)Cytosine (C), Guanine (G)Thymine (T)Guanine (G)Thymine (T)Cytosine (C), Adenine (A)Guanine (G)Adenine (A)Cytosine (C), Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Thymine (T)Thymine (T)Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Thymine (T)Cytosine (C), Adenine (A)Adenine (A)Guanine (G)Guanine (G)Thymine (T)Guanine (G)Adenine (A)Guanine (G)Thymine (T)Guanine (G)Thymine (T)Adenine (A)Thymine (T)Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Cytosine (C), Guanine (G)Thymine (T)Cytosine (C), Cytosine (C), Cytosine (C), Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Thymine (T)Cytosine (C), Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Cytosine (C), Guanine (G)Thymine (T)Thymine (T)Adenine (A)Guanine (G)Adenine (A)Thymine (T)Guanine (G)Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Thymine (T)Adenine (A)Guanine (G)Cytosine (C), Thymine (T)Adenine (A)Guanine (G)Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Adenine (A)Cytosine (C), Adenine (A)Adenine (A)Guanine (G)Thymine (T)Guanine (G)Guanine (G)Guanine (G)Adenine (A)Cytosine (C), Cytosine (C), Cytosine (C), Adenine (A)Adenine (A)Thymine (T)Cytosine (C), Adenine (A)Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Guanine (G)Cytosine (C), Cytosine (C), Cytosine (C), Guanine (G)Cytosine (C), Guanine (G)Guanine (G)Cytosine (C), Cytosine (C), Adenine (A)Guanine (G)Thymine (T)Guanine (G)Adenine (A)Adenine (A)Thymine (T)Adenine (A)Thymine (T)Guanine (G)Guanine (G)Thymine (T)Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Thymine (T)Thymine (T)Adenine (A)Thymine (T)Adenine (A)Thymine (T)Cytosine (C), Thymine (T)Adenine (A)Guanine (G)Adenine (A)Adenine (A)Thymine (T)Adenine (A)Thymine (T)Cytosine (C), Guanine (G)Thymine (T)Guanine (G)Adenine (A)Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Thymine (T)Guanine (G)Adenine (A)Thymine (T)Thymine (T)Guanine (G)Guanine (G)Thymine (T)Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Guanine (G)Cytosine (C), Adenine (A)Cytosine (C), Guanine (G)Thymine (T)Guanine (G)Thymine (T)Cytosine (C), Guanine (G)Guanine (G)Guanine (G)Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Cytosine (C), Adenine (A)Cytosine (C), Adenine (A)Cytosine (C), Thymine (T)Adenine (A)Cytosine (C), Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Cytosine (C), Cytosine (C), Guanine (G)Guanine (G)Adenine (A)Adenine (A)Guanine (G)Guanine (G)Thymine (T)Guanine (G)Adenine (A)Adenine (A)Cytosine (C), Guanine (G)Thymine (T)Cytosine (C), Thymine (T)Cytosine (C), Guanine (G)Cytosine (C), Guanine (G)Cytosine (C), Guanine (G)Adenine (A)Cytosine (C), Thymine (T)Thymine (T)Adenine (A)Thymine (T)Adenine (A)Adenine (A)Guanine (G)Guanine (G)Adenine (A)Cytosine (C), Thymine (T)Thymine (T)Guanine (G)Cytosine (C), Adenine (A)Thymine (T)Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Cytosine (C), Guanine (G)Cytosine (C), Cytosine (C), Adenine (A)Thymine (T)Thymine (T)Adenine (A)Thymine (T)Thymine (T)Adenine (A)Cytosine (C), Thymine (T)Adenine (A)Adenine (A)Cytosine (C), Thymine (T)Thymine (T)Adenine (A)Guanine (G)Guanine (G)Cytosine (C), Thymine (T)Guanine (G)Adenine (A)Adenine (A)Thymine (T)Adenine (A)Adenine (A)Adenine (A)Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Adenine (A)Cytosine (C), Guanine (G)Cytosine (C), Guanine (G)Guanine (G)Adenine (A)Adenine (A)Adenine (A)Cytosine (C), Thymine (T)Guanine (G)Cytosine (C), Guanine (G)Guanine (G)Thymine (T)Adenine (A)Guanine (G)Guanine (G)Guanine (G)Guanine (G)Adenine (A)Cytosine (C), Adenine (A)Thymine (T)Adenine (A)Guanine (G)Adenine (A)Cytosine (C), Guanine (G)Adenine (A)Adenine (A)Cytosine (C), Guanine (G)Cytosine (C), Guanine (G)Thymine (T)Cytosine (C), Thymine (T)Guanine (G)Guanine (G)Adenine (A)Cytosine (C), Guanine (G)Adenine (A)Cytosine (C), "
```
:::
:::

::: {.cell}

```{.r .cell-code}
set.seed(215)
genomeLength <- 100

randGenome <- sample(nucleotides, size = genomeLength, replace = TRUE)

paste(randGenome, collapse = "")
```

::: {.cell-output .cell-output-stdout}
```
[1] "Thymine (T)Guanine (G)Guanine (G)Adenine (A)Adenine (A)Thymine (T)Cytosine (C), Thymine (T)Thymine (T)Thymine (T)Adenine (A)Adenine (A)Thymine (T)Guanine (G)Thymine (T)Thymine (T)Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Cytosine (C), Cytosine (C), Thymine (T)Thymine (T)Thymine (T)Guanine (G)Adenine (A)Guanine (G)Cytosine (C), Cytosine (C), Thymine (T)Cytosine (C), Adenine (A)Adenine (A)Guanine (G)Thymine (T)Thymine (T)Guanine (G)Guanine (G)Adenine (A)Cytosine (C), Thymine (T)Adenine (A)Cytosine (C), Cytosine (C), Guanine (G)Cytosine (C), Guanine (G)Guanine (G)Cytosine (C), Cytosine (C), Cytosine (C), Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Guanine (G)Adenine (A)Guanine (G)Cytosine (C), Thymine (T)Adenine (A)Adenine (A)Cytosine (C), Thymine (T)Cytosine (C), Thymine (T)Adenine (A)Adenine (A)Adenine (A)Thymine (T)Guanine (G)Adenine (A)Thymine (T)Guanine (G)Cytosine (C), Adenine (A)Adenine (A)Guanine (G)Cytosine (C), Adenine (A)Guanine (G)Cytosine (C), Guanine (G)Cytosine (C), Guanine (G)Thymine (T)Guanine (G)Cytosine (C), Cytosine (C), Guanine (G)Adenine (A)Guanine (G)Thymine (T)Cytosine (C), Thymine (T)"
```
:::
:::

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

::: {.cell}

```{.r .cell-code}
myProduct <- 1

for(j in 1:15){
  myProduct <- myProduct + i
  print(myProduct)
}
```

::: {.cell-output .cell-output-stdout}
```
[1] 11
[1] 21
[1] 31
[1] 41
[1] 51
[1] 61
[1] 71
[1] 81
[1] 91
[1] 101
[1] 111
[1] 121
[1] 131
[1] 141
[1] 151
```
:::
:::

::: {.cell}

```{.r .cell-code}
nucleotides <- c("A", "C", "G", "T")
genomeLength <- 10

randGenome <- paste(
  sample(nucleotides, size = genomeLength, replace = TRUE),
                   collapse = "")
print(randGenome)
```

::: {.cell-output .cell-output-stdout}
```
[1] "CTGTGGACAG"
```
:::
:::

::: {.cell}

```{.r .cell-code}
randGenome <- sample(nucleotides, size=genomeLength, replace = TRUE)
randGenome
```

::: {.cell-output .cell-output-stdout}
```
 [1] "G" "A" "T" "C" "A" "C" "A" "T" "T" "G"
```
:::

```{.r .cell-code}
randGenome <- paste(randGenome, collapse = "")
randGenome
```

::: {.cell-output .cell-output-stdout}
```
[1] "GATCACATTG"
```
:::

```{.r .cell-code}
for(j in 1:15){
  print(str_sub(randGenome, start = 1, end = 1))
}
```

::: {.cell-output .cell-output-stdout}
```
[1] "G"
[1] "G"
[1] "G"
[1] "G"
[1] "G"
[1] "G"
[1] "G"
[1] "G"
[1] "G"
[1] "G"
[1] "G"
[1] "G"
[1] "G"
[1] "G"
[1] "G"
```
:::
:::

::: {.cell}

```{.r .cell-code}
for(i in 1:nchar(randGenome)){
  if(str_sub(randGenome, start = i, end = i) == "A"){
    print(str_sub(randGenome, start = i, end = i))
  }
}
```

::: {.cell-output .cell-output-stdout}
```
[1] "A"
[1] "A"
[1] "A"
```
:::
:::

::: {.cell}

```{.r .cell-code}
for(i in 1:nchar(randGenome)){
  if(str_sub(randGenome, start = i, end = i) == "G"){
    print(str_sub(randGenome, start = i, end = i))
  }
}
```

::: {.cell-output .cell-output-stdout}
```
[1] "G"
[1] "G"
```
:::
:::

::: {.cell}

```{.r .cell-code}
for(i in 1:nchar(randGenome)){
  if(str_sub(randGenome, start = i, end = i) == "T"){
    print(str_sub(randGenome, start = i, end = i))
  }
}
```

::: {.cell-output .cell-output-stdout}
```
[1] "T"
[1] "T"
[1] "T"
```
:::
:::

::: {.cell}

```{.r .cell-code}
for(i in 1:nchar(randGenome)){
  if(str_sub(randGenome, start = i, end = i) == "C"){
    print(str_sub(randGenome, start = i, end = i))
  }
}
```

::: {.cell-output .cell-output-stdout}
```
[1] "C"
[1] "C"
```
:::
:::
