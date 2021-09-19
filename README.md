# `linconGaussR`: partial R implementation of `LinConGauss`
###  _samples of Gaussians under linear domain constraints_


The original Python implementation can be found [here](https://github.com/alpiges/LinConGauss). The reference of `LinConGauss` is this [paper](https://arxiv.org/abs/1910.09328). It's very likely this repo will only implement the sampling methods in the near future.

It is not on CRAN and likely won't, to install, use

```r
devtools::install_github("YunyiShen/linconGaussR")
```

An example would be:

```r
my_sample <- linconGauss(100, diag(2),c(0,0),diag(2),c(0,0))
MASS_sample <- MASS::mvrnorm(1000,c(0,0),diag(2))
plot(MASS_sample)
points(my_sample,col = "red")
abline(h=0)
abline(v=0)
```

For developers: Files in `src` is quite a stand-alone C++ implementation of the algorithm, just relies on `RcppArmadillo` to call `armadillo` from R. To use it in pure C++ or to continue develope in R, you can copy it out and include `armadillo.h` if necessary. Utilities are in those headers, classes are very similar to the original Python implementation, main function is in `src/linconGaussCpp.cpp`.