
<!-- README.md is generated from README.Rmd. Please edit that file -->

# MQmetrics

<!-- badges: start -->

<!-- badges: end -->

The goal of MQmetrics is to analyze Proteomics data from LC-MS/MS. It
takes the output tables from MaxQuant and plots multiple parameters.

## Installation

You can install the development version from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("BioAlvaro/MQmetrics")
```

## Example

MQmetrics it’s easy to use, and will provide you information about your
Proteomics MaxQuant analysis.

Start by loading the library. By default, the MaxQuant results will be
stored in a folder named *Combined*. The directory to that folder is all
you need to use MQmetrics.

``` r
library(MQmetrics)

MQPathCombined <- '/home/alvaro/Documents/MaxQuant/example5/combined/'
```

The main function of the package is **generateReport()**. It will
generate a PDF report containing several visualizations and tables from
different MaxQuant output tables. As input it is only necessary to
provide the Path to the *Combined* folder of MaxQuant output.

``` r
generateReport(MQPathCombined, long_names = TRUE, sep_names = '_')
```

Two useful parameters of every function including **generateReport()**
are: *long\_names* and *sep\_names*. They will allow a clear
visualization of those samples that have long names separated by a
character. In this example, the Experiment names are one full string
separated by underscores (\_):
*PLK010\_QC02\_210121\_HeLa\_125ng\_150meth*.

``` r
# ReadDataFromDir reads all the files needed from the MaxQuant output and remove
# Potential contaminants, reverse, and proteins identified by site only.
files <- ReadDataFromDir(MQPathCombined, remove_contaminants = TRUE) 

PlotIntensity(files[["proteinGroups.txt"]], long_names = TRUE, sep_names = '_')
```

<img src="man/figures/README-example long names-1.png" width="100%" />

Check the vignettes for more information.
