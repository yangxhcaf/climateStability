
<!-- README.md is generated from README.Rmd. Please edit that file -->

# climateStability

The goal of climateStability is to provide a simple set of `R`-based
tools to generate climate stability estimates based on time slices of
climate data.

## Installation

You can install climateStability from github with:

``` r
# install.packages("devtools")
devtools::install_github("hannahlowens/climateStability")
```

## Example

This is a basic example which shows you how to calculate climate
stability using time-slice datasets for two variables:

``` r
# First, calculate deviation through time using even time slices
precipDeviation <- deviationThroughTime(variableDirectory = "../ClimateStabilityManuscript/precipfiles/",
                                        timeSlicePeriod = 1000, fileExtension = "asc");
temperatureDeviation <- deviationThroughTime(variableDirectory = "../ClimateStabilityManuscript/tempfiles/",
                                             timeSlicePeriod = 1000, fileExtension = "asc");

# Next, calculate stability for each variable (the inverse of deviation, scaled to between 0 and 1)
precipInvDev <- stabilityCalc(precipDeviation);
tempInvDev <- stabilityCalc(temperatureDeviation);

# Finally, multiply them together and rescale to estimate relative climate stability
climateStability <- rescale0to1(precipStability * tempStability)
```

For more information, refer to the vignette.

``` r
browseVignettes("climateStability")
```

## Citation

If you use the package you can cite the article that describes the
package:

> Owens, H.L., Guralnick, R., 2019. climateStability: An R package to
> estimate climate stability from time-slice climatologies. Biodiversity
> Informatics 14, 8–13. <https://doi.org/10.17161/bi.v14i0.9786>

You can also access the citation information through R using the
following command:

``` r
citation(package = "climateStability")
#> 
#> To cite climateStability in publications use:
#> 
#>   Owens, H.L., Guralnick, R., 2019. climateStability: An R package to
#>   estimate climate stability from time-slice climatologies.
#>   Biodiversity Informatics 14, 8–13.
#>   https://doi.org/10.17161/bi.v14i0.9786
#> 
#> A BibTeX entry for LaTeX users is
#> 
#>   @Article{,
#>     title = {climateStability: An R package to estimate climate stability from time-slice climatologies},
#>     author = {{Hannah L. Owens} and {Robert Guralnick}},
#>     journal = {Biodiversity Informatics},
#>     year = {2019},
#>     volume = {14},
#>     pages = {8-13},
#>     doi = {10.17161/bi.v14i0.9786},
#>   }
```
