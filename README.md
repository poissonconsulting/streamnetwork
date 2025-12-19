
<!-- README.md is generated from README.Rmd. Please edit that file -->

# streamnetwork

<!-- badges: start -->

<!-- badges: end -->

`streamnetwork` will be an R package to create, manipulate, query and
plot stream networks.

## Design

- A streamnetwork is an object of S3 class `streamnetwork` which
  inherits from class `dm`.
- Functions have the prefix `sn_`

### Dependencies

- `dm`
- `tibble`
- `sf`

### Related Packages

- [`sfnetworks`](https://github.com/luukvdmeer/sfnetworks)
- `fwatlasbc`
- `tidygraph`

## Installation

You can install the development version of streamnetwork from
[GitHub](https://github.com/) with:

``` r
# install.packages("pak")
pak::pak("poissonconsulting/streamnetwork")
```
