# Harmonic Sensitivity

GCS_config_setup.ipynb: We need to set up a bucket to work with, reference it, associate it with our NCA project (bop_nca_data_space) and make sure that our credentials pass + the directory we write to (harmonic_sensitivity) exists
2016_2025_K2K3_Writer.ipynb: GEE interface to get second and third order harmonics at vegetation plot points.
2018_FuncGroup_K2-K3-K3_24MonthSupport.ipynb: Looks at PCAs of FGs explained by harmonic information - initial attempt to trim dimensionality of harmonic features/order selection. Effective, but black boxy - proceed to regression instead. 
2018_PointSampling.ipynb: Just 2018 vegetation data, evaluates harmonics for K1-K4 and looks at indices at all plots in 2018. we subset for major PFT distributions (max eag; max bareground; max shrub, etc.) - lots of good visualizations about how harmonic     orders affect fit/complexity.
2018HarmonicSensitivity_K3_24MonthSupport.ipynb: visualize random pixel of 24month fit, retaining that 2018 year is t0 to t1 and 2017<0 and 2019 >1
2018harmonicSensitivity.ipynb:
*First, downloads and localizes the shards from the google cloud bucket harmonic_sensitivity/harmonic_sensitivity
*Second, produces VRT files after stitching together all shards
*Third, validates footprints of each VRT 
*Fourth, writes the output rasters as intercept, amplitude, phase, RMSE, nobs tifs.
Harmonic_information_partitioning_framework.ipynb: 2018 only, not enough sample size; proceed to updated notebook.
Harmonic_information_partitioning_framework_2016_2018_2025_updated.ipynb: this is where the magic happens.
Evaluates plant FG response as predicted by harmonic coefficients in ablation experiment: I vs A vs P vs IA vs IP vs AP vs IAP
starts with frequentist model of k2 vs k3 improvements in R-squared for a beta distributed model - identifies primary domain but is faulty; 0s become small non-zeroes but we now have a legitimate detection problem! 2nd order IA is best predictor set across the board
proceeds to model with a hurdle model - 0s (presence/absence) is a different mechanism relative to abundance (0.0001 to 0.9999); confirms that 2nd order IA is significantly better than 3rd order (dimensionality reduction AND performance)
prompts bayesian zero inflated beta model in R - same concept but final implementation: just K2 IA, explain how each predictor affects the response. see R code for details [K2_IA_bayes.r]