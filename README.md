
<!-- README.md is generated from README.Rmd. Please edit that file -->
<!-- badges: start -->
<!-- badges: end -->

# {theme.aagi}: Apply AAGI Brand Guidelines to R Graphic Output and Create AAGI Themed Documents <img align="right" src="man/figures/logo.png">

This repository contains the code for the R package {theme.aagi}, which
once installed in your R session (local or RStudio Server), provides
helper functions for creating and exporting graphics created in R with a
unified style that follows the AAGI brand guidelines.

The goal of {theme.aagi} is to provide easy to use theming of R graphics
for AAGI team members. Following AAGI’s brand guidelines, AAGI colours
are used where applicable and the font defaults to Proxima Nova. The
resulting graphs, plots and charts feature a x and y axis that meet at 0
with no gridlines, but these can optionally be set to appear. The
resulting maps from `theme_aagi_map()` feature a white canvas with the
legend on the right.

## Installation instructions

You can install {theme.aagi} like so:

``` r
if (!requireNamespace("remotes", quietly = TRUE)) {
  install.packages("remotes")
}
remotes::install_github("CCDM-AAGI/theme.aagi",
                        build_vignettes = TRUE,
                        dependencies = TRUE
)
```

## Quick start

Following are some quick examples of {theme.aagi} functionality.
However, you may wish to browse the vignette for a more detailed look at
what the package offers using:

``` r
vignette("Cookbook", package = "theme.aagi")
```

### Plots and graphs

{theme.aagi} provides several functions to assist users in creating
plots, charts and graphs with a more unified AAGI style.

For creating standalone graphs using R’s base library there are:

- `barplot_aagi()`,

- `boxplot_aagi()`,

- `hist_aagi()`, and

- `plot_aagi()`.

#### Using the basic plot functions

Example of how the base graphics functionality with AAGI style
pre-applied is used:

``` r
library(theme.aagi)
boxplot_aagi(decrease ~ treatment,
              data = OrchardSprays,
              xlab = "treatment",
              ylab = "decrease")
```

<img src="man/figures/README-boxplot_aagi-1.png" width="100%" />

See the respective function’s help files and the {theme.aagi} cookbook
for more examples and documentation.

#### Using With {ggplot2}

The function `theme_aagi()` is provided to apply a unified style for
creating AAGI themed plots, charts and graphs using {ggplot2}. The
function is very basic and provides only one parameter, `base_size`,
which is used to set the font size (in points) used in the resulting
figure. No adjustments are made by the type of graph being produced, so
you may wish to add gridlines or change the colour palette that is used
to alter point or line colours in your graph.

Example of how `theme_aagi()` is used in a standard {ggplot2} workflow:

``` r
library(theme.aagi)
library(ggplot2)

ggplot(data = OrchardSprays, aes(x = treatment, y = decrease)) +
  geom_boxplot() +
  scale_y_continuous(breaks = seq(0, 120, by = 20)) +
  theme_aagi()
```

<img src="man/figures/README-theme_aagi-1.png" width="100%" />

## Using {theme.aagi} Word Templates

{theme.aagi} provides RMarkdown Word document templates for you to
quickly and easily create RMarkdown documents that use the AAGI colours
in the template. The templates are available through RStudio,
`File > New File > R Markdown`, then select “From Template” and then
select the template you’d like to use.
