
## Additional Data for `NetOrigin` R package

The `NetOrigin` R package performs network-based source estimation.
Different approaches are available: effective distance median, recursive
backtracking, and centrality-based source estimation. Additionally, we
provide public transportation network data as well as methods for data
preparation, source estimation performance analysis and visualization.

The repository contains additional data exemplifying the Gaussian origin
detection algorithm.

## Data Description

### Environment parameters List for KwaZulu-Natal

List “envirparaList”, including

  - `beta_max` maximum contact rate (day^-1)
  - `beta` contact rate (day^-1) for each node, length 851
  - `theta_max` maximum contamination rate
  - `theta` contamination rate for each node, length 851
  - `humanmob.mass` An 851-by-851 matrix, where each row contains the
    probabilities a person travels from the given city (by Row Index) to
    another city (by Column Index). For example, the first row
    represents the probabilities that a person travels from City 1 to
    the other 850 cities
  - `lati.long.851` a 851-by-2 matrix, of which the 1st column is
    longitude and the 2nd column is latitude, for each city
  - `newcases.per.day` new cases per day per node, 851(number of
    nodes)-by-1312(number of days)
  - `no_toilet_access` probability of no toilet access for each node
    (length 851 vector)
  - `no_water_access` probability of no water access for each node
    (length 851 vector)
  - `popu` population for each node (length 851 vector)
  - `R0_max` maximum reproduction number
  - `R0` maximum reproduction number for each node (length 851 vector)
  - `alpha` cholera induced mortality rate (day^-1)
  - `gamma` rate at which people recover from cholera (day^-1)
  - `incidence.threshold` The threshold value applied to the percent of
    infected individuals in a city population, used to declare whether
    or not the city is infected.
  - `mu` population natality and mortality rate (day^-1)
  - `mu_B` death rate of V.cholerae in the aquatic environment (day^-1)
  - `rho` immunity loss rate (day^-1)
  - `sigma` symptomatic ratio, i.e., fraction of infected people that
    develop symptoms and are infective. (The remaining fraction enters
    directly the recovered compartment.)

## Examples

``` r
require(NetOrigin)
```

    ## Loading required package: NetOrigin

``` r
# read data from github repo
load("envirparaList.rda")
# example for Gaussian origin detection
y0 <- initial_condition_sib_model(envirparaList$popu, envirparaList$sigma, 
  envirparaList$mu_B, envirparaList$theta, c(428))
```

## References

Jun Li, Juliane Manitz, Enrico Bertuzzo, Eric D. Kolaczyk, Sensor-based
localization of epidemic sources on human mobility networks (arXiv link
pending)
