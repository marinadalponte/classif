# classif

<img src="https://github.com/marinadalponte/classif/blob/main/logo/cropped_logo.png" width="100">

Based on [Skrzypek et al. (2015)](https://ui.adsabs.harvard.edu/abs/2015A%26A...574A..78S/abstract), this is a statiscal method to infer a spectral type for ultracool dwarfs based only on their photometry. The procedure is described in detail in [Carnero Rosell et al. (2019)](https://ui.adsabs.harvard.edu/abs/2019MNRAS.489.5301C/abstract) and [dal Ponte et al. (2023)](https://ui.adsabs.harvard.edu/abs/2023MNRAS.522.1951D/abstract). 

## How it works

The spectral type is assigned by the minimization of the $\chi^2$ relative to empirical templates. The $\chi^2$ for the $k$-th source and the $j$-th spectral type is

```math
\chi^2(\{m_{b}\},\{\sigma_{b}\},\hat{{m}}_{z,k,j},\{c_b\}) = \sum_{b=1}^{N_{bands}}{\left(\frac{m_{b,k}-\hat{{m}}_{z,k,j}-c_{b,j}}{\sigma_{b,k}}\right)}^2
```

where $m_{b,k}$ are the measured magnitudes for the source in all available filters, and $c_{b,j}$ are the template colors for the $j$-th spectral type and for the same photometric bands. These latter are measured for all templates with respect to a reference band. The $\sigma_{b,k}$ are the $k$-th source's photometric errors added in quadrature to the intrinsic scatter. As for $\hat{{m}}_{z,k,j}$, it is the inverse variance weighted estimate of the reference magnitude, computed using all the source's magnitudes, their associated uncertainties and the given template colours for the $j$-th type, as follows

```math
\hat{m}_{z,k,j}=\frac{\sum_{b=1}^{N_{bands}} {\frac{m_{b,k}-c_{b,j}}{\sigma_{b,k}^{2}}}} {\sum_{b=1}^{N_{bands}} {\frac{1}{\sigma_{b,k}^{2}}}}
```

## Important notes

- The code is set to run with the following photometry bands: i, Y, z (from Dark Energy Survey), J, H, Ks (from VHS), W1 and W2 (from WISE).
- M, L, and T dwarf templates and intrinsic scatter used in the code are those described in [dal Ponte et al. (2023)](https://ui.adsabs.harvard.edu/abs/2023MNRAS.522.1951D/abstract).
