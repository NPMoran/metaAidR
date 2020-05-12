[![Build Status](https://travis-ci.org/daniel1noble/metaAidR.svg?branch=master)](https://travis-ci.org/daniel1noble/metaAidR) [![codecov](https://codecov.io/gh/daniel1noble/metaAidR/branch/master/graph/badge.svg)](https://codecov.io/gh/daniel1noble/metaAidR)

#**metaAidR**

## **Description**

*metaAidR* contains a set of functions that allows users to make use of both simple (i.e. calculation of effect size statistics) along with more advanced (i.e. generate correlation/(co)variance matrices for non-independence, calculate I<sup>2</sup> & R<sup>2</sup> statistics) formal meta-analytic procedures. In addition, it contains a number of datasets that are used to demonstrate the use of functions and statistical concepts. This package will accompany a 'how-to' paper and is under active development. 

## **Datasets**

*metaAidR* comes with a suite of different datasets which accompany the examples in the 'how-to' paper. These example datasets are used to demonstrate the functionality of *metaAidR* along with more advanced meta-analytic topics that maybe of interest to practitioners. Datasets can be queried and loaded as with normal R packages. Currently, the datasets that exist are as follows:

| Dataset                         | Reference                 | Description                                      |
|---------------------------------|---------------------------|--------------------------------------------------|
| agg_epp_wpp & multi_epp_wpp     | Cleasby & Nakagawa (2012) | Extra-pair and within pair multiple paternity    |
| birdegg_ssd.5 & birdegg_ssd.8   | Rutkowski et al. (2014)   | Egg sexual size dimorphism                       |
| heatshock                       | Lagisz et al. (2013)      | Heatshock protein meta-analysis                  |
| matdiet                         | Besson et al. (2016)      | Maternal diet and soping styles meta-analysis    |
| moNumtradeoff & moSizetradeoff  | Lim et al. (2014)         | Mother offspring size and number tradeoff        |
| ooAdjtradeoff & ooUnAdjtradeoff | Lim et al. (2014)         | Offspring size and number tradeoff meta-analysis |
| mtor                            | Garratt et al. (2016)     | Meta-analysis of mtor                            |
| parasites                       | Poulin (2000)             | Parasites impacting behaviour meta-analysis      |
| plumage                         | Santos et al. (2011)      | Meta-analysis on dominance and plumage traits                                                 |
| sparrows                        | Nakagawa et al. (2007)    | Sparrow meta-analysis and bib size               |

For more details on each specific meta-analysis use `?` in combination with the specific dataset (e.g. `?heatshock`). This will provide meta-data details for each dataset along with its reference and a description.

## **Functions**

Currently, there are five main functions: `es_stat`, `es_ratio`, `coMatrix`, `I2`, `foldnorm`. While `es_stat` and `es_ratio` are functions that can be found in other meta-analytic packages (e.g. `metafor`), we have separated out two different families of effect size statistics and have expanded these functions to include more recently developed effect size statistics. For example, `es_stat` will implement commonly used effect size statistics (i.e. Cohen's / Hedges' *d*; Hedges' *g*, Fisher's z-transformed correlation coefficient and log odds ratio). While these are common effect size measures, they also have the important property that these measurements can be converted among each other. Hence, the plan is to provide arguments that the user can specify the type of data they would like so that calculations can be done with multiple data types to the relevant effect size statistic and then re-calculated into a common type for analysis.  `es_ratio` contains the ratio family effect size statistics (e.g. log response ratio), along with newly developed or less commonly applied effects sizes including those for comparing variances (i.e. log coefficient of variation ratio and log variance ratio) and log hazards ratios. 

In addition to functions for calculating effect size statistics, *metaAidR* also will calculate flexible heterogeneity statistics (I<sup>2</sup>), from common meta-analytic models from `metafor` and `MCMCglmm` model objects. These are not yet implemented but are forthcoming. 

Meta-analytic models also often exhibit unique (and common) forms of non-independence. To provide users with useful functions to calculate correlation / (co)variance matrices *metaAidR* also provides a `coMatrix` function that allows the user to generate covariance matrices based on shared control measurements, phylogenetic correlation matrices or within-study/shared trait measurements matrices that can be used as input matrices for common meta-analytic models implemented in both `metafor` and `MCMCglmm`. 

For many situations in ecology and evolution, the absolute or magnitude of effect size is of most interest, rather than effect size estimates containing directionality (see Morrissey 2016a & b). Absolute effect size estimates follow a folded normal distribution and need to be modeled correctly to avoid bias. As such, for users interested in effect magnitude we have developed a `foldnorm` function which can apply results from normal meta-analytic models (that assume Gaussain error distributions) to generate corrected effect magnitude and credible intervals using an 'anlayse then transform' approach suggested by Morrissey (2016a).

## **Installation**

*metaAidR* is not currently on CRAN. For **testing purposes only** it can be downloaded through `devtools` as follows:

```
install.packages("devtools")
library(devtools)
install_github("daniel1noble/metaAidR")
```
`devtools` will install all the relevant documentation and data associated with the package. 

**NOTE**: While functions exist, they are still not completely functional. Additionally, not all functions have been effectively tested and so should not be used or used with extreme caution!

## **References**

Besson, A. A., Lagisz, M., Senior, A.M., Hector, K.L. and Nakagawa, S. (2016). Effect of maternal diet on offspring coping styles in rodents: a systematic review and meta-analysis. Biological Reviews, 91:1065-1080

Cleasby, I.R. and Nakagawa, S. (2012) The influence of male age on within-pair and extra-pair paternity in passerines. Ibis, 154: 318-324.

Garratt, M., Nakagawa, S., Simons, M.J.P. (2016) Comparative idiosyncrasies in life extension by reduced mTOR signaling and its distinctiveness from dietary restriction. Aging Cell, 15: 737-743.

Lagisz, M., Hector, K.L. and Nakagawa, S. (2013) Life exstension after heat shock exposure: Assessing meta-analytic evidence for hormesis. Ageing Research Reviews, 12:653-660.

Lim, J. N., Senior, A. M. and Nakagawa, S. (2014) Heterogeneity in individual quality and reproductive trade-offs within species. Evolution, 68:2306-2318.

Morrisey, M.B. (2016)a. Meta-analysis of magnitudes, differences and variation in evolutionary parameters. Journal of Evolutionary Biology, 29:1882-1904

Morrisey, M.B. (2016)b. Rejoinder: Further considerations for meta-analysis of transformed quantities such as absolute values. Journal of Evolutionary Biology, 29:1922-1931.

Nakgawa, S., Ockendon, N., Gillespie, D.O.S., Hatchwell, B.J. and Burke, T. (2007) Assessing the function of house sparrows' bib size using a flexible meta-analysis method. Behavioural Ecology, 18:831-840.

Poulin, R. (2000) Manipulation of host behaviour by parasites: a weakening paradigm? Proceedings of the Royal Society B: Biological Sciences, 267: 1471-2954.

Rutkowska, J., Dubiec, A. and Nakgawa, S. (2014). All eggs are made equal: a meta-analysis of egg sexual size dimorphism. Journal of Evolutionary Biology, 27:153-160.

Santos, E.S.A., Scheck, D. and Nakagawa, S. (2011) Dominance and plumage traits: meta-analysis and meta-regression analysis. Animal Behaviour, 82: 3-19.
