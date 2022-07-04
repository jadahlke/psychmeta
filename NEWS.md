# psychmeta 2.6.4 (2022-07-03)

- Minor maintenance update. Per feedback from CRAN, we updated the notation for the univariate indirect range restriction attenuation formula in the `estimate_var_rho_tsa` documentation to include a plaintext version of the formula.


# psychmeta 2.6.3 (2022-04-13)

- Bug fix in SE for tau for models with `var_biased = TRUE`.

- Bug fix for forest plots generated from the results of ma_generic().


# psychmeta 2.6.2 (2022-01-17)

- Made a superficial update to the overview vignette to satisfy CRAN's requirements.


# psychmeta 2.6.1 (2022-01-01)

- Bug fix in `limits_tau2()` when `method == "normal_logQ"`.

- Update `generate_bib()` and `metabulate()` to permit direct rendering of bibliographies in RMarkdown documents ([rmarkdown #1364](https://github.com/rstudio/rmarkdown/issues/1364))
  
- Changed the *psychmeta* NEWS file to NEWS.md for easier viewing.

- In `plot_forest()`, by default, use the same `conf_method` and `conf_level` values as used when the meta-analysis model was fit.

- Fix bug in `wt_cor()` where it always returned 1 when correlating only 2 variables.

- Added a local copy of "apa.csl" to the vignette resources to avoid build issues if zotero.org's style templates are unavailable due to AWS downtime.


# psychmeta 2.6.0 (2021-05-31)

- Improved handling of effect sizes with observed magnitudes of exactly zero in individual-correction meta-analyses. To accurately account for the estimation of error variances after correcting for artifacts, effect sizes of exactly zero are substituted with functionally equivalent but computationally non-zero values via the `zero_substitute` argument of the `control_psychmeta()` function. The default `zero_substitute` value is `.Machine$double.eps`---this permits the effect size to be treated as functionally zero while still allowing an attenuation factor to be computed, which is used to estimate a more accurate corrected error variance value.

- Reduced number of dependencies. 

- Updated documentation.


# psychmeta 2.5.1 (2021-05-07)

- Bug fix in consolidating dependent correlations when the dataset contains same-construct intercorrelations.


# psychmeta 2.5.0 (2021-05-02)

- Added `var_error_spearman()`, `var_error_mult_R()`, and `var_error_mult_Rsq()` functions.

- Made internal code updates to improve performance.


# psychmeta 2.4.2 (2020-08-18)

- Fixed a bug in which missing artifacts were sometimes not imputed when resolving dependency among observations.

- Improved standard error for `SD_res` when `var_unbiased == TRUE`.


# psychmeta 2.4.1 (2020-07-16)

- Restore 'overview' vignette.


# psychmeta 2.4.0 (2020-07-11)

- Bug fix in `convert_es()`.

- `convert_es()` now returns a simple frame with converted effect sizes, variances, and (effective) sample sizes.

- Bug fix in moderator reconciliation.

- Added robustness to variable selection and second-order meta-analysis functions.


# psychmeta 2.3.10 (2020-06-07)

- Bug fix when compositing facets into overall construct variables.

- Bug fix in `ma_r_ic()`.

- Moved packages *MASS*, *tmvtnorm*, and *nor1mix* to "Suggests" to avoid errors some users have encountered when loading *psychmeta* in *R* 4.0.0.


# psychmeta 2.3.9 (2020-06-04)

- Bug fix when compositing facets into overall construct variables.

- Remove unnecessary S4 class exports.

- Bug fix in `get_matrix()`.

- Fix extraneous warnings in `ma_r()` when `ma_method="ic"` since *dplyr* 1.0.0.

- Print all columns of meta-analysis results tables.


# psychmeta 2.3.8 (2020-04-21)

- Bug fix to correct an issue that arose in *psychmeta* 2.3.7 in which factor-type variables passed to `ma_r()` and `ma_d()` as construct/facet/measure arguments were coerced to numeric variables.


# psychmeta 2.3.7 (2020-04-09)

- Updates to ensure consistency with upcoming *R* 4.0.0.

- Bug fixes in `ma_r()` moderated meta-analyses that involve dependency consolidation.


# psychmeta 2.3.6 (2020-02-19)

- Bug fix in dependent sample consolidation.

- A vector of moderator variable names can now be specified quoted or unquoted, like other arguments.


# psychmeta 2.3.5 (2020-02-13)

- Improved print methods for tibble-like output.

- Improved small-sample bias correction for d values; new correction uses the gamma function, consistent with *metafor*.

- Replaced deprecated functions from *dplyr*.

- Made stability improvements to `compute_dmod()`.

- Added moderator information to the output from `get_escalc()`.

- Added `var_error_R()` and `var_error_Rsq()` functions for the error variance of multiple correlations from multiple regression.

- Updated the URL used for version checking to avoid error messages experienced by a subset of users.

- Additional bug fixes in `convert_es()`, `create_ad_int()`, `anova.ma_psychmeta()`, `metabulate()`, `generate_bib()`

- Typo corrections in documentation.


# psychmeta 2.3.4 (2019-12-18)

- Support for contour-enhanced funnel plots added to `plot_funnel()` and added a new `plot_cefp()` function.

- Bug fixes for uncertainty intervals in second-order meta-analyses.

- New `anova()` method for comparing subgroup moderator levels.

- Abbreviation for credibility interval changed to "CR" instead of "CV".

- Support for construct_order argument added to `ma_r_order2()`.

- Added an error message for impossible composites. An error message is now displayed when a sample's composite effect size is statistically impossible. Prior to this update, impossible effect sizes produced generic errors that did not provide users with useful feedback on the source of the problem.

- Updated the URL used version checking to avoid error messages experienced by a subset of users.

- Additional bug fixes in `get_matrix()`, `reshape_wide2long()`, and `ma_r_order2()`.


# psychmeta 2.3.3 (2019-04-11)

- Bug fix for the `metabulate()` function's use of RMarkdown.

- Bug fix for retrieving artifact distributions with the `get_ad()` function.

- Bug fix to accommodate truly missing artifacts in the artifact-imputation procedure.

- Bug fix for leave-one-out and cumulative meta-analyses for *d* values.

- Update to sample from beta distributions with `SD = 0` in `simulate_r_database()` and `simulate_d_database()`.


# psychmeta 2.3.2 (2019-02-26)

- Bug fix for using categorical moderators in meta-regressions.

- Bug fix for using moderators in `ma_generic()` when there are no construct or group-identification variables in the analysis.

- Added an optional `weights` argument to `ma_generic()`, which allows users to supply their own custom weights for effect sizes.

- Added alternative methods for calculating confidence limits for tau-squared.


# psychmeta 2.3.1 (2019-02-15)

- Increased support for heterogeneity analyses conducted using weights imported from the *metafor* package.

- Updated estimates for small-sample-bias corrected error variances to be computed from the bias-corrected effect size rather than applying a post-hoc linear variance adjustment.

- Changed default weighting method for *d* values to `"n_effective"`. This method is superior to sample-size weights because it accounts for both total sample size and deviations from equal subgroup representation.

- Updated compatibility with *dplyr* 0.8.0.

- Updated the labeling of output from the `mix_dist()` function.

- Assorted bug fixes affecting mean *d* value estimates (from the `ma_d()` and `ma_d_ic()` functions), artifact distributions, and weighted correlations and covariances.


# psychmeta 2.3.0 (2019-01-08)

- Individual-correction validity generalization meta-analyses have been corrected to remove variation due to between-sample reliability differences prior to adding back measurement error.

- Improved compatibility with *dplyr* and *tibble* packages.

- Bug fixes for `var_error_d()` and `var_error_g()` to accommodate inputs of differing lengths.

- Bug fix for cumulative meta-analyses.

- Bug fix for handling null interactive artifact distributions

- Bug fix for meta-analyzing correlations between global constructs and facets.

- Bug fix for estimating correction-implied subgroup proportions in `correct_d()`.

- Bug fix for using `correct_d()` when `n2` is left unspecified.


# psychmeta 2.2.1 (2018-10-12)

- Added option to suppress progress indicators in the console. Use `options(psychmeta.show_progress = FALSE)` to suppress progress indicators.

- Increased support for common wide database formats in the `reshape_wide2long()` function.

- Bug fixes for managing dependent observations in artifact distributions created within `ma_r()` and `ma_d()`.

- Bug fixes for resolving dependency in effect sizes in meta-analyses with moderators.

- Added error-variance estimates to the output of `convert_es()` for increased compatibility with the `ma_generic()` function.


# psychmeta 2.2.0 (2018-09-18)

- Added support for separately compositing measures of constructs and the constructs' facets. Arguments for `facet_x` and `facet_y` have been added to `ma_r()` and `ma_d()` so that more comprehensive output tables can be generated.

- Stability fixes for data management within the `ma_r()` function.

- Added checks for missing and infinite values to the `ma_generic()` function.


# psychmeta 2.1.12 (2018-09-07)

- Bug fix for managing reliability types that have been incidentally converted from characters into factors.


# psychmeta 2.1.11 (2018-08-30)

- Bug fix for `create_ad()` with interactive method when all sample sizes are `NA`.

- Bug fix for `ma_r_ad()` with individual artifact distributions supplied.


# psychmeta 2.1.10 (2018-08-24)

- Bug fix for using output of `metabulate()` in RMarkdown documents.

- Bug fix for meta-analyses of effect sizes that have been averaged or composited.


# psychmeta 2.1.9 (2018-08-22)

- Increased the stability of artifact-distribution meta-analyses with moderators computed using the `ma_r()` function.

- Bug fix for the `get_ad()` function to appropriately handle artifact-distribution objects that contain no artifact information.


# psychmeta 2.1.8 (2018-08-21)

- Updated and corrected the text displayed in table notes produced by the `metabulate()` function.

- Bug fix for handling meta-analyses with only one effect size.


# psychmeta 2.1.7 (2018-07-16)

- Removed package *fungible* as a dependency, as *fungible* was archived and removed from CRAN on 2018-07-15.

- Bug fixes and improvements to `format_num()` and `metabulate()` for handling leading zeros.


# psychmeta 2.1.6 (2018-07-12)

- Bug fix for `ma_generic()` analyses that include construct names and/or group names, but no moderators.


# psychmeta 2.1.5 (2018-07-09)

- Bug fix for printing the residual summary from `lm_mat()` so that console output will show a properly scaled vector of theoretical residual quantiles.


# psychmeta 2.1.4 (2018-06-28)

- Bug fix for defining the *p* values of negative coefficients in `lm_mat()`.


# psychmeta 2.1.3 (2018-06-27)

- Changed Unicode entities to HTML entities in `metabulate()` for increased support across locales.

- Bug fix for artifact imputation without a moderator.


# psychmeta 2.1.2 (2018-06-26)

- Added grouping variables and construct variables to `ma_generic()`. This helps to streamline meta-analyses of generic effect sizes that involve multiple group-wise contrasts and/or multiple constructs.

- Bug fixes for `format_num()` and `metabulate()` to allow missing values in formatted numeric strings.

- Updated `lm_mat()` to use `fungible::seBetaCor()` to estimate standard errors when `se_beta_method = "normal"` and `cov_mat` is a correlation matrix.


# psychmeta 2.1.1 (2018-06-10)

- Updates and bug fixes for the `metabulate()` function. Fixed issues with file-writing protocols. Increased support for Unicode characters on Windows systems. Added arguments to control whether table headers are rendered in bold font (`bold_headers`) and whether redundant construct-pair labels are collapsed in meta-analysis tables (`collapse_construct_labels`).

- Updated the `"summary"` attributes of artifact-distribution objects for greater consistency between interactive and Taylor-series objects.

- Added third-order sample sizes (i.e., the number of meta-analyses meta-analyzed; denoted as `"L"`) to the output from second-order meta-analyses.

- Added `get_stuff()` function that serves as a wrapper for other functions in the `get_stuff` family of functions.


# psychmeta 2.1.0 (2018-06-01)

- Updated `metabulate()` function based on RMarkdown. The `metabulate()` function can now output to Word, PDF, HTML, Markdown, ODT, and plain text and accepts arguments to include a bibliography in the same output as results tables. Output can be rendered directly into the selected format or placed into a larger RMarkdown document. The function also includes improvements to the typesetting of numeric results and column headings (e.g., ρ̅ instead of Mean<sub>ρ</sub>).

- New `num_format()` function to format numbers to a specified number of digits and allowing control of the characters used for decimal points, thousands and decimal digit group separators, leading zeros, and positive and negative signs. It's useful to avoid unpleasant surprises during publisher typesetting of tables.


# psychmeta 2.0.2 (2018-05-30)

Hotfix for handling `NULL` moderator objects in dependency resolution procedure.


# psychmeta 2.0.1 (2018-05-29)

Hotfix for missing object in the dependency resolution procedure when no moderators are present.


# psychmeta 2.0.0 (2018-05-28)

- Major overhauls to the format of meta-analysis objects to improve the user experience. The outputs of meta-analysis functions are now nested tibbles rather than nested lists. This provides users with a clearer overview of the structure of the object, streamlines the manipulation of results objects (e.g., selecting/subsetting columns, filtering, and arranging), and makes the objects more flexible in terms of performing follow up analyses and performing artifact-distribution corrections (because AD corrections can now by done separately by moderator level). As the print methods for meta-analyses no longer report grand tables of results, we recommend using `summary()` or `get_metatab()` to obtain this information.

- Arguments for specifying methodological parameters (e.g., `conf_method`, `conf_level`, `var_unbiased`) in meta-analyses have been migrated to a new `control_psychmeta()` function---the output of this function can be passed to the `control` argument of meta-analysis functions to select the methodological parameters. This is meant to reduce the number of arguments native to meta-analysis functions and simplify the documentation of *psychmeta*’s core functions. All of the arguments to `control_psychmeta()` can still be passed directly to meta-analysis functions and all function calls accepted by previous versions of *psychmeta* should continue to work in this version of the package.

- The dependency resolution process in `ma_r()` and `ma_d()` in which dependent effect sizes are automatically combined into composites has been enhanced. The `intercor` argument now accepts a variety of types of information. The user can now set a default scalar value to use as well as supply a named vector of values (the names can refer to construct names and/or `sample_id` and construct pairings) and/or a database from which to harvest intercorrelation information. This allows the compositing procedure to use sample-specific information to compute composites when that information is available.

- `summary()` methods have been added for classes exported from *psychmeta*.

- The overview vignette has been updated to provide instructions on how to navigate the output objects from meta-analyses.

- The class structure of meta-analysis objects has been simplified. There is now only one class for meta-analyses (`"ma_psychmeta"`).

- Data management has been streamlined within the `ma_r()` and `ma_d()` functions to permit more efficient cleaning and imputation of artifact information.

- To complement the new structure of meta-analysis objects, the `create_ad_list()` function now produces tibbles of artifact distributions and the function is now an alias of `create_ad_tibble()`. This function can now create artifact distributions for construct pairs and/or specific moderator combinations.

- The behavior of the `supplemental_ads` argument to meta-analysis functions has been expanded to allow artifact information to be supplied as individual artifact distributions, lists of artifact distributions, or tibbles of artifact distributions.

- `print()` methods have been updated for a variety of object classes.

- Bug fixes and stability improvements have been made to follow-up analyses, plotting functions, dependency resolution, `convert_ma()`, and `compute_dmod()`.


# psychmeta 1.0.3 (2018-05-08)

- The performance of the `hs_override` argument has been improved in `ma_r()` and `ma_d()` by correcting a bug that caused the argument to not be evaluated when running an artifact-distribution meta-analysis or only a bare-bones meta-analysis.

- The default value for the `use_all_arts` argument in `ma_r()` and `ma_d()` has been changed from `FALSE` to `TRUE`. This is meant to improve the ease with which the most robust artifact-distribution corrections can be applied.


# psychmeta 1.0.2 (2018-05-01)

- Bug fixes have been made for defining confidence-interval method in bare-bones and artifact-distribution meta-analyses computed with the `ma_r()` function.

- A new `seed` argument has been added to `ma_r()` and `ma_d()` to set the seed value when imputing artifacts for greater reproducibility.

- New console messages have been introduced for when follow-up results are added to a meta-analysis object.


# psychmeta 1.0.1 (2018-04-25)

- Bug fixes for using true-score u ratios in individual-correction meta-analyses.

- Bug fix for appropriately returning results from the `compute_dmod()` function.


# psychmeta 1.0.0 (2018-04-17)

- New `citekey` arguments have been added to meta-analysis function that allow users to supply citation keys for use in reference-management programs. The new `generate_bib()` function can harvest the citation keys from studies that are included in meta-analysis objects and create formatted reference lists for use in publications.

- Plotting functions have been added. The `plot_forest()` and `plot_funnel()` functions use *ggplot2* to create forest and funnel plots, respectively. These functions take a meta-analysis object as an input and add a list of plots to the object.

- New functions to retrieve results from within meta-analysis objects have been added. The `get_stuff` family of functions provide easy ways to extract meta-analysis tables, follow-up analyses (e.g., cumulative meta-analyses, leave-one-out meta-analyses, bootstrap results), plots, and more.

- Assorted bug fixes have been implemented to improve the stability of the dependency resolution process, the handling of artifact distributions, and the accommodation of continuous moderators.


# psychmeta 0.2.5 (2018-03-21)

- Hot fix for consolidating dependent effect sizes.


# psychmeta 0.2.4 (2018-03-20)

- A new method to account for sampling error in interactive artifact distributions has been added (NOTE: this is now the default methods used in interactive AD meta-analyses).

- Stability improvements for dMod functions.

- Artifacts harvested from rows of a database that do not contain effects sizes in the `ma_r()` and `ma_d()` functions are now organized to avoid redundancy with observations from the same sample that are included in the meta-analytic computations.

- Bug fixes to `metabulate()`.


# psychmeta 0.2.3 (2018-02-09)

- Bug fix to the interactive artifact-distribution method for bivariate indirect range restriction (`"bvirr"`) to properly compute SDrho.

- Bug fix to allow interactive artifact distributions to be rounded to the desired number of decimal places.

- Bug fix for computing the mean reliability indices in the Taylor-series estimate of the corrected error variance for correlations corrected with the bivariate indirect range restriction (`"bvirr"`) correction.


# psychmeta 0.2.2 (2018-01-24)

- A new function (called `matreg()`, with aliases of `matrixreg()`, `lm_mat()`, and `lm_matrix()`) has been added that computes regression models from covariance matrices and vectors of means and generates output that resembles that of the `"lm"` function. Output from `matreg()` can be used with the `summary()`, `predict()`, and `confint()` functions.

- The `ma_r()` and `mad_d()` functions have been modified to allow for more flexibility in computing multiple meta-analyses in a single function call, especially when those meta-analyses use artifact-distribution corrections. Several new arguments have been added to allow users to name the types artifact corrections they would like to apply to each construct---see function documentation for argument details.

- The `correct_rxx` and `correct_ryy` arguments across meta-analysis routines (excluding `ma_r_ad()` and `ma_d_ad()`) can now support both scalar and vector arguments.

- Efficiency improvements and improvements to the accuracy of progress-bar feedback have been made to the `simulate_r_database()` and `simulate_d_database()` functions.


# psychmeta 0.2.1 (2018-01-07)

- Hotfixes for bugs in `simulate_d_sample()` function affecting composite variables.

- A `k_items_vec` argument is now included in the `simulate_psych()` function.

- The `simulate_d_database()` function has been improved for faster computations.


# psychmeta 0.2.0 (2018-01-05)

- Bug fixes for identifying independent artifacts in artifact-distribution meta-analyses using `ma_r()` and `ma_d()`.

- The simulation functions (`simulate_r_sample()`, `simulate_r_database()`, `simulate_d_sample()`, `simulate_d_database()`) can now simulate coefficient &alpha; (alpha) reliabilities for variables when the number of items in a scale is indicated with the `k_items_vec` or `k_items_params` arguments.

- A new function called `metabulate()` has been added that writes meta-analytic tables as rich text files with near publication-quality formatting.


# psychmeta 0.1.3 (2017-12-13)

- Bug fixes and stability improvements for moderator analyses, the creation of artifact distributions, and computation of follow-up analyses.

- Added reliability types arguments (e.g., `rxx_type`, `ryy_type`) to functions requiring reliability estimates to be corrected for range restriction. String vectors of reliability labels (e.g., `"alpha"`, `"retest"`, `"parallel"`; see documentation for the `ma_r()` function for a complete list of supported labels) can now be supplied to many functions. When direct range restriction occurs, different corrections for range restriction are applied to internal-consistency reliability estimates and reliability estimates computed by correlating data from different testing occasions.

- The `ma_r()` and `ma_d()` functions now allow users to supply lists of external artifact information using the `supplemental_ads` argument (the `ma_r_ic()` and `ma_d_ic()` functions also allow this with the `supplemental_ads_x` and `supplemental_ads_y` arguments). These functions can also now harvest artifact information from studies in a database with invalid or missing effect sizes by setting the `use_all_arts` argument to `TRUE`.

- `rho_params` arguments to the `simulate_r_database()` function can now be supplied as a correlation matrix rather than a list (for situations in which samples are drawn from a single population). Similarly, elements in the `rho_params` list argument for the `simulate_d_database()` can include matrices.

- Progress bars have been added to potentially time-consuming functions to provide feedback about the percentage of progress and the estimated time remaining.


# psychmeta 0.1.2 (2017-11-16)

- Bug fixes for moderator analyses.

- Bug fixes for specifying the order of constructs and selecting a subset of constructs in a database.

- New function `correct_r_coarseness()` to correct for scale coarseness.

- Improved vectorization support.


# psychmeta 0.1.1 (2017-09-21)

- We have added a suite of simulation function for *d* values (see the `simulate_d_sample()` and `simulate_d_database()` functions).

- Methods for meta-analyzing d values have been updated to better account for subgroup proportions when converting between the *r* and *d* metrics. The `escalc` objects that accompany a meta-analysis of *d* values now include more detailed information about incumbent and applicant subgroup proportions and the default for the `"pa"` argument (i.e., applicant proportions) is now `NULL` rather than `.5` to prevent unintended corrections for range restriction.

- A new `ma_generic()` function has been added that allow users to do a *psychmeta*-style meta-analysis for any effect size for which the user has error-variance estimates. This function is supported by *psychmeta*'s `sensitivity()` and `heterogeneity()` functions.

- Taylor series methods for estimating the variance of converted artifact values (e.g., a *r<sub>xxi</sub>* distribution converted to a *r<sub>xxa</sub>* distribution) have been expanded to account for the correlation between artifact distributions when such information is available. Correlations among artifacts' sampling distributions can also be passed to the `var_error_r_bvirr()` function when it is called outside of a meta-analysis routine.

- The implementation of corrections of bivariate range restriction in individual-correction meta-analyses have been updated. Corrections for bivariate direct range restriction now use conventional compound attenuation factors, while the attenuation factors for bivariate indirect range restriction are now computed using mean effect sizes and artifacts to estimate sampling variances.

- Assorted bugs have been fixed (e.g., an error that occurred when running multi-construct meta-analyses without specifying moderators; filters to retain valid correlations did not screen construct names, sample ids, or measure names; subgroup proportions were not being retained when *d* values were meta-analyzed as correlations).


# psychmeta 0.1.0 (2017-08-15)

- *psychmeta* has officially launched for public beta!

- Please see the `"psychmeta-package"` entry in the *psychmeta* manual for an overview of the package and its applications.
