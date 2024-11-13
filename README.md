# classif

![cropped_logo](https://github.com/user-attachments/assets/38ea7e0c-3af3-4026-af55-b87d5bc6c78a)

This is a statiscal method to infer a spectral type for a ultracool dwarfs based only on their photometry. The procedure is described in detail Carnero Rosell et al. (2019), based on Skrzypek et al. (2015). 

The spectral type is assigned by the minimization of the $\chi^2$ relative to empirical templates. The $\chi^2$ for the $k$-th source and the $j$-th spectral type is

```math
\chi^2(\{m_{b}\},\{\sigma_{b}\},\hat{{m}}_{z,k,j},\{c_b\}) = \sum_{b=1}^{N_{bands}}{\left(\frac{m_{b,k}-\hat{{m}}_{z,k,j}-c_{b,j}}{\sigma_{b,k}}\right)}^2
```

where $m_{b,k}$ are the measured magnitudes for the source in all available filters, and $c_{b,j}$ are the template colors for the $j$-th spectral type and for the same bands. These latter are measured for all templates with respect to a reference band. The $\sigma_{b,k}$ are the $k$-th source's photometric errors added in quadrature to the intrinsic scatter. As for $\hat{{m}}_{z,k,j}$, it is the inverse variance weighted estimate of the reference magnitude, computed using all the source's magnitudes, their associated uncertainties and the given template colours for the $j$-th type, as follows

```math
\hat{m}_{z,k,j}=\frac{\sum_{b=1}^{N_{bands}} {\frac{m_{b,k}-c_{b,j}}{\sigma_{b,k}^{2}}}} {\sum_{b=1}^{N_{bands}} {\frac{1}{\sigma_{b,k}^{2}}}}
```
