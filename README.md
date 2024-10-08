this repo is a fork of: [prosail](https://github.com/jbferet/prosail)

# __prosail__ <img src="man/figures/logo.png" align="right" alt="" width="200" />

# An R package for the simulation of canopy reflectance using the model PROSAIL (PROSPECT+SAIL).

[![licence](https://img.shields.io/badge/Licence-GPL--3-blue.svg)](https://www.r-project.org/Licenses/GPL-3)
[![Build Status](https://gitlab.com/jbferet/prosail/badges/master/pipeline.svg)](https://gitlab.com/jbferet/prosail/pipelines/latest)

# 1 Requirements

## Install `devtools`

Install the package `devtools` following the [instructions](https://www.r-project.org/nosvn/pandoc/devtools.html) depending on your operating system. 


## Install `prospect`

Install the package `prospect` with the following command line in R session:
```
devtools::install_github('jbferet/prospect')
```

## Install liquidSVM

`prosail` uses Support Vector Regression (SVR) for hybrid inversion. 

The default SVM implementation is currently based on the package 
[`liquidSVM`](http://pnp.mathematik.uni-stuttgart.de/isa/steinwart/software/R/documentation.html).
A SVM implementation based on the R package [`caret`](https://topepo.github.io/caret/) 
is also available.

[`liquidSVM`](https://arxiv.org/pdf/1702.06899v1.pdf) provides very efficient and 
fully-integrated hyper-parameter selection, multithreading and GPU support. 
However, this package is not maintained anymore and may cause difficulties during 
the installation. 

To install `liquidSVM`, please follow installation instructions provided in the 
[documentation webpage](http://pnp.mathematik.uni-stuttgart.de/isa/steinwart/software/R/documentation.html). 

### !!! WINDOWS USERS !!!

Once `liquidSVM` is installed, you may need to add the 32bit DLL into the R library. 
This `i386` directory should be downloaded [here](https://gitlab.com/jbferet/myshareddata/-/tree/master/LiquidSVM_32bits) 
and copied into the local directory on your computer, where the binary codes of liquidSVM are installed:

`Path_For_My_R_distribution/library/liquidSVM/libs/`.

### If liquidSVM installation fails

`liquidSVM` is a suggested package, so the installation of `prosail` should succeed 
even without `liquidSVM`. 
Two main functions using `liquidSVM` as default may be impacted: `train_prosail_inversion` 
and `PROSAIL_Hybrid_Train`. 

If the installation of `liquidSVM` does not succeed, please define `method = 'svmRadial'` 
or `method = 'svmLinear'` as optional input variable. 
This will use the caret implementation, but it will require longer training stage.


# 2 Install `prosail`

The package `prosail` can then be installed with the following command line in R session:
```
devtools::install_github('jbferet/prosail')
```

# 3 Tutorial

<!-- README.md is generated from README.Rmd. Please edit that file -->

<!-- ```{r include = FALSE} -->
<!-- knitr::opts_chunk$set( -->
<!--   collapse = TRUE, -->
<!--   comment = "#>", -->
<!--   fig.path = "man/figures/README-", -->
<!--   out.width = "100%" -->
<!-- ) -->
<!-- ``` -->

A tutorial vignette is available [here](https://jbferet.gitlab.io/prosail/articles/prosail1.html).


# 4 Acknowledgments / Fundings

This research was supported by the Agence Nationale de la Recherche ([ANR](https://anr.fr/en/open-calls-and-preannouncements/), France) through the young researchers project **BioCop** (ANR-17-CE32-0001)

We thank [Ingo Steinwart](ingo.steinwart@mathematik.uni-stuttgart.de) and [Philipp Thomann](philipp.thomann@mathematik.uni-stuttgart.de) (nstitute for Stochastics and Applications, University of Stuttgart, Germany) for the development of the package `liquidSVM`.


# 5 Citation

If you use **prosail**, please consider citing the following references when appropriate :

### PROSPECT

Féret, J.-B. & de Boissieu, F. (2024). `prospect`: an R package to link leaf optical properties with their chemical and structural properties with the leaf model PROSPECT. Journal of Open Source Software, 9(94), 6027, https://doi.org/10.21105/joss.06027

Féret J-B, Gitelson AA, Noble SD & Jacquemoud S, 2017. PROSPECT-D: Towards modeling leaf optical properties through a complete lifecycle. Remote Sensing of Environment, 193, 204–215. https://doi.org/10.1016/j.rse.2017.03.004

Féret J-B, Berger K, de Boissieu F & Malenovský Z, 2021. PROSPECT-PRO for estimating content of nitrogen-containing leaf proteins and other carbon-based constituents. Remote Sensing of Environment, 252, 112173. https://doi.org/10.1016/j.rse.2020.112173

### PROSAIL
Jacquemoud S, Verhoef W, Baret F, Bacour C, Zarco-Tejada PJ, Asner GP, François C & Ustin SL, 2009. PROSPECT+ SAIL models: A review of use for vegetation characterization. Remote Sensing of Environment, 113:S56–S66. https://doi.org/doi:10.1016/j.rse.2008.01.026

Berger K, Atzberger C, Danner M, D’Urso G, Mauser W, Vuolo F & Hank T 2018. Evaluation of the PROSAIL Model Capabilities for Future Hyperspectral Model Environments: A Review Study. Remote Sensing, 10:85. https://doi.org/10.3390/rs10010085

### 4SAIL & 4SAIL2
Verhoef W & Bach H, 2007. Coupled soil–leaf-canopy and atmosphere radiative transfer modeling to simulate hyperspectral multi-angular surface reflectance and TOA radiance data. Remote Sensing of Environment, 109:166-182. https://doi.org/10.1016/j.rse.2006.12.013

Verhoef W, Jia L, Xiao Q & Su Z, 2007. Unified optical-thermal four-stream radiative transfer theory for homogeneous vegetation canopies. IEEE Transactions in Geosciences and Remote Sensing, 45:1808–1822. https://doi.org/10.1109/TGRS.2007.895844

### liquidSVM
Steinwart I & Thomann P (2017). liquidSVM: A Fast and Versatile SVM package. [__ArXiv e-prints 1702.06899__](https://doi.org/10.48550/arXiv.1702.06899), http://www.isa.uni-stuttgart.de/software

### SOILSPECT
Jacquemoud S, Baret F, Hanocq J-F, 1992. Modeling spectral and bidirectional soil reflectance. Remote Sensing of Environment, 41, 123–132. https://doi.org/10.1016/0034-4257(92)90072-R

