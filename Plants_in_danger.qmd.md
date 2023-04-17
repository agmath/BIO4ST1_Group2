---
title: "Plants in Danger"
author: "Adaobi Nwankwo"
format: html
editor: visual
execute:
  keep-md: true
---



## Plants in Danger Analysis

Installing tidyverse and other packages.


::: {.cell}

```{.r .cell-code}
#Load the tidyverse
library(tidyverse)
```

::: {.cell-output .cell-output-stderr}
```
── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
✔ ggplot2 3.4.0      ✔ purrr   1.0.0 
✔ tibble  3.1.8      ✔ dplyr   1.0.10
✔ tidyr   1.2.1      ✔ stringr 1.5.0 
✔ readr   2.1.3      ✔ forcats 0.5.2 
── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
```
:::

```{.r .cell-code}
library(kableExtra)
```

::: {.cell-output .cell-output-stderr}
```

Attaching package: 'kableExtra'

The following object is masked from 'package:dplyr':

    group_rows
```
:::

```{.r .cell-code}
#install.packages("tidymodels")
library(tidymodels)
```

::: {.cell-output .cell-output-stderr}
```
── Attaching packages ────────────────────────────────────── tidymodels 1.0.0 ──
✔ broom        1.0.2     ✔ rsample      1.1.1
✔ dials        1.1.0     ✔ tune         1.0.1
✔ infer        1.0.4     ✔ workflows    1.1.2
✔ modeldata    1.1.0     ✔ workflowsets 1.0.0
✔ parsnip      1.0.3     ✔ yardstick    1.1.0
✔ recipes      1.0.4     
── Conflicts ───────────────────────────────────────── tidymodels_conflicts() ──
✖ scales::discard()        masks purrr::discard()
✖ dplyr::filter()          masks stats::filter()
✖ recipes::fixed()         masks stringr::fixed()
✖ kableExtra::group_rows() masks dplyr::group_rows()
✖ dplyr::lag()             masks stats::lag()
✖ yardstick::spec()        masks readr::spec()
✖ recipes::step()          masks stats::step()
• Learn how to get started at https://www.tidymodels.org/start/
```
:::

```{.r .cell-code}
#install.packages("skimr")
library(skimr)
```
:::


Loading in "Plants in Danger" dataset.


::: {.cell}

```{.r .cell-code}
# Get the Data

# Read in with tidytuesdayR package 
# Install from CRAN via: install.packages("tidytuesdayR")
# This loads the readme and all the datasets for the week of interest

# Either ISO-8601 date or year/week works!

tuesdata <- tidytuesdayR::tt_load('2020-08-18')
```

::: {.cell-output .cell-output-stderr}
```
--- Compiling #TidyTuesday Information for 2020-08-18 ----
```
:::

::: {.cell-output .cell-output-stderr}
```
--- There are 3 files available ---
```
:::

::: {.cell-output .cell-output-stderr}
```
--- Starting Download ---
```
:::

::: {.cell-output .cell-output-stdout}
```

	Downloading file 1 of 3: `plants.csv`
	Downloading file 2 of 3: `threats.csv`
	Downloading file 3 of 3: `actions.csv`
```
:::

::: {.cell-output .cell-output-stderr}
```
--- Download complete ---
```
:::

```{.r .cell-code}
tuesdata <- tidytuesdayR::tt_load(2020, week = 34)
```

::: {.cell-output .cell-output-stderr}
```
--- Compiling #TidyTuesday Information for 2020-08-18 ----
```
:::

::: {.cell-output .cell-output-stderr}
```
--- There are 3 files available ---
```
:::

::: {.cell-output .cell-output-stderr}
```
--- Starting Download ---
```
:::

::: {.cell-output .cell-output-stdout}
```

	Downloading file 1 of 3: `plants.csv`
	Downloading file 2 of 3: `threats.csv`
	Downloading file 3 of 3: `actions.csv`
```
:::

::: {.cell-output .cell-output-stderr}
```
--- Download complete ---
```
:::

```{.r .cell-code}
plants <- tuesdata$plants

# Or read in the data manually

plants <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-08-18/plants.csv')
```

::: {.cell-output .cell-output-stderr}
```
Rows: 500 Columns: 24
```
:::

::: {.cell-output .cell-output-stderr}
```
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr  (6): binomial_name, country, continent, group, year_last_seen, red_list...
dbl (18): threat_AA, threat_BRU, threat_RCD, threat_ISGD, threat_EPM, threat...

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```
:::

```{.r .cell-code}
actions <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-08-18/actions.csv')
```

::: {.cell-output .cell-output-stderr}
```
Rows: 3000 Columns: 8
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr (7): binomial_name, country, continent, group, year_last_seen, red_list_...
dbl (1): action_taken

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```
:::

```{.r .cell-code}
threats <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-08-18/threats.csv')
```

::: {.cell-output .cell-output-stderr}
```
Rows: 6000 Columns: 8
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr (7): binomial_name, country, continent, group, year_last_seen, red_list_...
dbl (1): threatened

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```
:::
:::


## Introduction

This data takes in 500 extinct species as of 2020. 19.6% were endemic to Madagascar, 12.8% to Hawaiian islands. This dataset takes in several variables such as name, country, continent, threat, and action. Here, I loaded in a data set for the exploratory data of the Plants data set.


::: {.cell}

```{.r .cell-code}
library(skimr)
plants %>%
  skim()
```

::: {.cell-output-display}
<table style='width: auto;'
      class='table table-condensed'>
<caption>Data summary</caption>
<tbody>
  <tr>
   <td style="text-align:left;"> Name </td>
   <td style="text-align:left;"> Piped data </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Number of rows </td>
   <td style="text-align:left;"> 500 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Number of columns </td>
   <td style="text-align:left;"> 24 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> _______________________ </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Column type frequency: </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> character </td>
   <td style="text-align:left;"> 6 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> 18 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ________________________ </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Group variables </td>
   <td style="text-align:left;"> None </td>
  </tr>
</tbody>
</table>


**Variable type: character**

<table>
 <thead>
  <tr>
   <th style="text-align:left;"> skim_variable </th>
   <th style="text-align:right;"> n_missing </th>
   <th style="text-align:right;"> complete_rate </th>
   <th style="text-align:right;"> min </th>
   <th style="text-align:right;"> max </th>
   <th style="text-align:right;"> empty </th>
   <th style="text-align:right;"> n_unique </th>
   <th style="text-align:right;"> whitespace </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> binomial_name </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1.00 </td>
   <td style="text-align:right;"> 11 </td>
   <td style="text-align:right;"> 35 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 500 </td>
   <td style="text-align:right;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> country </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1.00 </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:right;"> 44 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 72 </td>
   <td style="text-align:right;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> continent </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1.00 </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:right;"> 13 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 6 </td>
   <td style="text-align:right;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> group </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1.00 </td>
   <td style="text-align:right;"> 5 </td>
   <td style="text-align:right;"> 16 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 6 </td>
   <td style="text-align:right;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> year_last_seen </td>
   <td style="text-align:right;"> 15 </td>
   <td style="text-align:right;"> 0.97 </td>
   <td style="text-align:right;"> 9 </td>
   <td style="text-align:right;"> 11 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 7 </td>
   <td style="text-align:right;"> 0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> red_list_category </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1.00 </td>
   <td style="text-align:right;"> 7 </td>
   <td style="text-align:right;"> 19 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:right;"> 0 </td>
  </tr>
</tbody>
</table>


**Variable type: numeric**

<table>
 <thead>
  <tr>
   <th style="text-align:left;"> skim_variable </th>
   <th style="text-align:right;"> n_missing </th>
   <th style="text-align:right;"> complete_rate </th>
   <th style="text-align:right;"> mean </th>
   <th style="text-align:right;"> sd </th>
   <th style="text-align:right;"> p0 </th>
   <th style="text-align:right;"> p25 </th>
   <th style="text-align:right;"> p50 </th>
   <th style="text-align:right;"> p75 </th>
   <th style="text-align:right;"> p100 </th>
   <th style="text-align:left;"> hist </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> threat_AA </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.45 </td>
   <td style="text-align:right;"> 0.50 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▆ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> threat_BRU </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.31 </td>
   <td style="text-align:right;"> 0.46 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▃ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> threat_RCD </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.17 </td>
   <td style="text-align:right;"> 0.38 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▂ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> threat_ISGD </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.16 </td>
   <td style="text-align:right;"> 0.37 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▂ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> threat_EPM </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.09 </td>
   <td style="text-align:right;"> 0.29 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▁ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> threat_CC </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.07 </td>
   <td style="text-align:right;"> 0.25 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▁ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> threat_HID </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.04 </td>
   <td style="text-align:right;"> 0.20 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▁ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> threat_P </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.03 </td>
   <td style="text-align:right;"> 0.17 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▁ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> threat_TS </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.02 </td>
   <td style="text-align:right;"> 0.15 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▁ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> threat_NSM </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.21 </td>
   <td style="text-align:right;"> 0.40 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▂ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> threat_GE </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.04 </td>
   <td style="text-align:right;"> 0.19 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▁ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> threat_NA </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.21 </td>
   <td style="text-align:right;"> 0.41 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▂ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> action_LWP </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.13 </td>
   <td style="text-align:right;"> 0.34 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▁ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> action_SM </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.12 </td>
   <td style="text-align:right;"> 0.32 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▁ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> action_LP </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.06 </td>
   <td style="text-align:right;"> 0.23 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▁ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> action_RM </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.05 </td>
   <td style="text-align:right;"> 0.23 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▁ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> action_EA </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.00 </td>
   <td style="text-align:right;"> 0.04 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▇▁▁▁▁ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> action_NA </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.76 </td>
   <td style="text-align:right;"> 0.43 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> ▂▁▁▁▇ </td>
  </tr>
</tbody>
</table>
:::
:::

::: {.cell}

```{.r .cell-code}
plants %>%
  head() %>%
  kable() %>%
  kable_styling(c("hover", "striped"))
```

::: {.cell-output-display}

`````{=html}
<table class="table table-hover table-striped" style="margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> binomial_name </th>
   <th style="text-align:left;"> country </th>
   <th style="text-align:left;"> continent </th>
   <th style="text-align:left;"> group </th>
   <th style="text-align:left;"> year_last_seen </th>
   <th style="text-align:right;"> threat_AA </th>
   <th style="text-align:right;"> threat_BRU </th>
   <th style="text-align:right;"> threat_RCD </th>
   <th style="text-align:right;"> threat_ISGD </th>
   <th style="text-align:right;"> threat_EPM </th>
   <th style="text-align:right;"> threat_CC </th>
   <th style="text-align:right;"> threat_HID </th>
   <th style="text-align:right;"> threat_P </th>
   <th style="text-align:right;"> threat_TS </th>
   <th style="text-align:right;"> threat_NSM </th>
   <th style="text-align:right;"> threat_GE </th>
   <th style="text-align:right;"> threat_NA </th>
   <th style="text-align:right;"> action_LWP </th>
   <th style="text-align:right;"> action_SM </th>
   <th style="text-align:right;"> action_LP </th>
   <th style="text-align:right;"> action_RM </th>
   <th style="text-align:right;"> action_EA </th>
   <th style="text-align:right;"> action_NA </th>
   <th style="text-align:left;"> red_list_category </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Abutilon pitcairnense </td>
   <td style="text-align:left;"> Pitcairn </td>
   <td style="text-align:left;"> Oceania </td>
   <td style="text-align:left;"> Flowering Plant </td>
   <td style="text-align:left;"> 2000-2020 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> Extinct in the Wild </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Acaena exigua </td>
   <td style="text-align:left;"> United States </td>
   <td style="text-align:left;"> North America </td>
   <td style="text-align:left;"> Flowering Plant </td>
   <td style="text-align:left;"> 1980-1999 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> Extinct </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Acalypha dikuluwensis </td>
   <td style="text-align:left;"> Congo </td>
   <td style="text-align:left;"> Africa </td>
   <td style="text-align:left;"> Flowering Plant </td>
   <td style="text-align:left;"> 1940-1959 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> Extinct </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Acalypha rubrinervis </td>
   <td style="text-align:left;"> Saint Helena, Ascension and Tristan da Cunha </td>
   <td style="text-align:left;"> Africa </td>
   <td style="text-align:left;"> Flowering Plant </td>
   <td style="text-align:left;"> Before 1900 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> Extinct </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Acalypha wilderi </td>
   <td style="text-align:left;"> Cook Islands </td>
   <td style="text-align:left;"> Oceania </td>
   <td style="text-align:left;"> Flowering Plant </td>
   <td style="text-align:left;"> 1920-1939 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> Extinct </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Acer hilaense </td>
   <td style="text-align:left;"> China </td>
   <td style="text-align:left;"> Asia </td>
   <td style="text-align:left;"> Flowering Plant </td>
   <td style="text-align:left;"> 1920-1939 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:right;"> 0 </td>
   <td style="text-align:left;"> Extinct in the Wild </td>
  </tr>
</tbody>
</table>

`````

:::
:::


## Abstract

Exploring the data will make it easier to create hypotheses. Here are some interesting questions I asked.

-   What region country has the most extinct plants?

-   By taxonomic group, when was the period the species was last seen?

-   Which threat has the biggest impact on plants becoming extinct.

-   After finding the biggest threat, what taxonomic group is effected by it the most?

## Hypothesis

The biggest threat to plant extinction is pollution. Pollution is one of the biggest effects on our planet today.

## Answering Our Questions


::: {.cell}

```{.r .cell-code}
plants %>%
  count(country)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 72 × 2
   country        n
   <chr>      <int>
 1 Angola         1
 2 Argentina      1
 3 Australia      2
 4 Belgium        1
 5 Bermuda        1
 6 Bhutan         2
 7 Bolivia        1
 8 Brazil        10
 9 Burundi       17
10 Cabo Verde     2
# … with 62 more rows
```
:::

```{.r .cell-code}
plants %>%
  ggplot() +
  geom_bar(mapping = aes(x = country), color = "hotpink", fill = "forestgreen") +
  labs(title ="Country vs. Count", x = "Country", y = "Count") +
  coord_flip()
```

::: {.cell-output-display}
![](Plants_in_danger.qmd_files/figure-html/unnamed-chunk-5-1.png){width=672}
:::
:::


By using this count function, it is evident that Madagascar has the highest number of extinct plants with a count of 98. The second highest is United States with a count of 66. The third highest is Ecuador with a count of 52.


::: {.cell}

```{.r .cell-code}
plants %>%
  group_by(group) %>%
  count(year_last_seen)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 23 × 3
# Groups:   group [6]
   group            year_last_seen     n
   <chr>            <chr>          <int>
 1 Algae            1960-1979          2
 2 Algae            Before 1900        1
 3 Conifer          1940-1959          1
 4 Cycad            1900-1919          1
 5 Cycad            1960-1979          1
 6 Cycad            1980-1999          1
 7 Cycad            2000-2020          5
 8 Ferns and Allies 1900-1919          1
 9 Ferns and Allies 1960-1979          4
10 Ferns and Allies 2000-2020          3
# … with 13 more rows
```
:::
:::


Algae was last seen in 1979. Cycad was last seen in 2020. Conifer was last seen in 1959.Ferns and Allies were last seen in 2020. Flowering plants were last seen in 2020.


::: {.cell}

```{.r .cell-code}
plants %>%
  count(threat_AA)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_AA     n
      <dbl> <int>
1         0   273
2         1   227
```
:::

```{.r .cell-code}
plants %>%
  count(threat_BRU)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_BRU     n
       <dbl> <int>
1          0   347
2          1   153
```
:::

```{.r .cell-code}
plants %>%
  count(threat_RCD)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_RCD     n
       <dbl> <int>
1          0   414
2          1    86
```
:::

```{.r .cell-code}
plants %>%
  count(threat_ISGD)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_ISGD     n
        <dbl> <int>
1           0   419
2           1    81
```
:::

```{.r .cell-code}
plants %>%
  count(threat_EPM)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_EPM     n
       <dbl> <int>
1          0   455
2          1    45
```
:::

```{.r .cell-code}
plants %>%
  count(threat_CC)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_CC     n
      <dbl> <int>
1         0   466
2         1    34
```
:::

```{.r .cell-code}
plants %>%
  count(threat_HID)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_HID     n
       <dbl> <int>
1          0   480
2          1    20
```
:::

```{.r .cell-code}
plants %>%
  count(threat_P)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_P     n
     <dbl> <int>
1        0   486
2        1    14
```
:::

```{.r .cell-code}
plants %>%
  count(threat_TS)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_TS     n
      <dbl> <int>
1         0   489
2         1    11
```
:::

```{.r .cell-code}
plants %>%
  count(threat_NSM)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_NSM     n
       <dbl> <int>
1          0   397
2          1   103
```
:::

```{.r .cell-code}
plants %>%
  count(threat_GE)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_GE     n
      <dbl> <int>
1         0   482
2         1    18
```
:::

```{.r .cell-code}
plants %>%
  count(threat_NA)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 2 × 2
  threat_NA     n
      <dbl> <int>
1         0   393
2         1   107
```
:::
:::


The biggest threat on extinct plants is agriculture and aquaculture with a number of 227. This takes in two large groups so it makes sense that this has a big effect. The threat transportation corridor had the lowest threat number of 11. Pollution only has a number of 14 and I was expecting this to be the highest number.


::: {.cell}

```{.r .cell-code}
plants %>%
  group_by(group) %>%
  count(threat_AA)
```

::: {.cell-output .cell-output-stdout}
```
# A tibble: 10 × 3
# Groups:   group [6]
   group            threat_AA     n
   <chr>                <dbl> <int>
 1 Algae                    0     3
 2 Conifer                  1     1
 3 Cycad                    0     7
 4 Cycad                    1     1
 5 Ferns and Allies         0     5
 6 Ferns and Allies         1     8
 7 Flowering Plant          0   256
 8 Flowering Plant          1   215
 9 Mosses                   0     2
10 Mosses                   1     2
```
:::
:::


The agriculture and aquaculture threat poses a large threat to the taxonomic group, flowering plant.

## Conclusion

Using this data set, I was able to answer all of my questions. Learning about plants and the threats posed to them was very interesting. There are several threats, the highest being agriculture and aquaculture. The most recent plant to go extinct was the cycad. The data set also takes in current actions being taken to prevent plants from going extinct. Some of these actions include land and water protection, species management, law & policy, research and monitoring, and education and awareness. My hypothesis was not supported as it is not the biggest cause of plant extinction, it's actually one of the lowest.
