
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Cell type-specific differential expression for spatial transcriptomics

<!-- badges: start -->
<!-- badges: end -->

Here, we will explain how the analysis occurred for our paper ‘Cell
type-specific differential expression in spatial transcriptomics’, which
introduces and validates the Generalized Linear Admixture Models for
Differential Expression (GLAMDE) method for detecting cell type-specific
differential expression in spatial transcriptomics. You may access
GLAMDE within our open-source R package
[here](https://github.com/dmcable/spacexr).

### Obtaining Data

The data generated and/or used in this study may be accessed at the
[Broad Institute’s Single Cell
Portal](https://singlecell.broadinstitute.org/single_cell/study/SCP1663).
This repository contains both the Slide-seq datasets used in this study,
and the single-cell RNA-sequencing references.

### DE Simulation

Using the helper functions in
[de_simulation_helper.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/helper_functions/de_simulation_helper.R),
code and results of GLAMDE on simulated data is shown in Figure 2 below.

### Cerebellum Slide-seq

The script
[cer_reps.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/Preprocessing_and_RCTD/cer_reps.R)
pre-processes the cerebellum Slide-seq data including cropping ROIs and
creating `SpatialRNA` objects. This script also runs RCTD on our three
cerebellum replicates.

The scripts
[run_de_cer_08.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/run_GLAMDE/run_de_cer_08.R),
[run_de_cer_09.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/run_GLAMDE/run_de_cer_09.R),
and
[run_de_cer_11.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/run_GLAMDE/run_de_cer_11.R)
run GLAMDE on the three Slide-seq replicates. Merging multiple
replicates uses functions from
[merge_de_helper.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/helper_functions/merge_de_helper.R).
The script
[hcr.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/image_analysis/hcr.R)
quantitatively processes the HCR data. Results are shown in Figure 3
below.

### Testes Slide-seq

The script
[run_RCTD_testes.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/Preprocessing_and_RCTD/run_RCTD_testes.R)
loads in the testes data and runs RCTD. Next, GLAMDE is run using the
script
[run_de_testes.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/run_GLAMDE/run_de_testes.R).
For downstream testes analysis (results in Figure 4 - Testes below),
helper functions are used from
[testes_helper.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/helper_functions/testes_helper.R).

### J20 Hippocampus Slide-seq

The file
[preprocess_j20.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/preprocess_j20.R)
preprocesses the Slide-seq data including cropping ROI. Next, RCTD is
run using the scripts
[run_RCTD_j20_21.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/run_RCTD_j20_21.R),
[run_RCTD_j20_22.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/run_RCTD_j20_22.R),
[run_RCTD_j20_23.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/run_RCTD_j20_23.R),
and
[run_RCTD_j20_24.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/run_RCTD_j20_24.R).

In the following analysis, helper functions from
[alzheimers_helper.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/helper_functions/alzheimers_helper.R)
are used.

In order to create the GLAMDE predictive variable, we must next align
the amyloid plaque antibody stains to the Slide-seq data. To do this,
[align_plaque_density.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/align_plaque_density.R)
aligns the images (manually) using the DAPI channel to the Slide-seq
data. Next, the script
[created_pd.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/create_pd.R)
creates and saves smoothed versions of the plaque images. Finally,
[pd_to_exvar.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/pd_to_exvar.R)
calculates the plaque density predictive variable at each Slide-seq
pixel.

After generating the predictive variable, we run GLAMDE on the four
samples using the scripts
[run_GLAMDE_j20_21.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/run_GLAMDE_j20_21.R),
[run_GLAMDE_j20_22.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/run_GLAMDE_j20_22.R),
[run_GLAMDE_j20_23.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/run_GLAMDE_j20_23.R),
and
[run_GLAMDE_j20_24.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/j20/run_GLAMDE_j20_24.R).
Overall results are shown in Figure 4 - J20 below, which uses helper
functinos from
[merge_de_helper.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/helper_functions/merge_de_helper.R).

### MERFISH Hypothalamus Slide-seq

The script
[run_de_merfish.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/run_GLAMDE/run_de_merfish.R)
runs GLAMDE (including RCTD) on the MERFISH hypothalamus data for both
linear and quadratic models. Results and other analysis are shown in
Figure 4 - MERFISH below.

### KP Tumor Slide-seq

The script
[overlay.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/image_analysis/overlay.R)
generates a plot of the KP tumor H&E annotations.

The script
[run_de_tumor.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/run_GLAMDE/run_de_tumor.R)
runs GLAMDE (including RCTD) on the Slide-seq KP tumor data for the
parametric case (DE as a function of immune cell density). Results and
other analysis are shown in Figure 5 - parametric below.

The script
[run_de_nonparametric.R](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/run_GLAMDE/run_de_nonparametric.R)
runs GLAMDE nonparametrically on the tumor data. Results and other
analysis are shown in Figure 5 - nonparametric below.

### Running GLAMDE

For each dataset, RCTD and GLAMDE were run according to the instructions
for the [spacexr package](https://github.com/dmcable/spacexr).

### Generating Main Figures

We provide R Markdown files that were used to create the main figures:

-   [Validating GLAMDE on simulated
    data](https://raw.githack.com/dmcable/spacexr/master/AnalysisGLAMDE/Figures/figure2.html)
    (Figure 2)
-   [GLAMDE on Slide-seq
    cerebellum](https://raw.githack.com/dmcable/spacexr/master/AnalysisGLAMDE/Figures/figure3.html)
    (Figure 3)
-   [GLAMDE on Slide-seq J20
    hippocampus](https://raw.githack.com/dmcable/spacexr/master/AnalysisGLAMDE/Figures/figure4_j20.html)
    (Figure 4)
-   [GLAMDE on Slide-seq
    testes](https://raw.githack.com/dmcable/spacexr/master/AnalysisGLAMDE/Figures/figure4_testes.html)
    (Figure 4)
-   [GLAMDE on MERFISH
    hypothalamus](https://raw.githack.com/dmcable/spacexr/master/AnalysisGLAMDE/Figures/figure4_merfish.html)
    (Figure 4)
-   [Parametric GLAMDE on Slide-seq KP
    tumor](https://raw.githack.com/dmcable/spacexr/master/AnalysisGLAMDE/Figures/figure5_parametric.html)
    (Figure 5)
-   [Nonparametric GLAMDE on Slide-seq KP
    tumor](https://raw.githack.com/dmcable/spacexr/master/AnalysisGLAMDE/Figures/figure5_nonparametric.html)
    (Figure 5)

### Supplementary Figures

R Markdown code for generating supplemental figures can be found at:

-   [Supplementary figures part
    1](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/Figures/supp1.Rmd)
-   [Supplementary figures part
    2](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/Figures/supp2.Rmd)
-   [Supplementary figures part
    3](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/Figures/supp3.Rmd)
-   [Supplementary figures part
    4](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/Figures/supp4.Rmd)
-   [Supplementary figures part
    5](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/Figures/supp5.Rmd)
-   [Supplementary figures part
    6](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/Figures/supp6.Rmd)
-   [Supplementary figures part
    7](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/Figures/supp7.Rmd)

### GLAMDE Results

A list of significant genes found by GLAMDE on all datasets (for each
cell type) can be found at [GLAMDE
results](https://github.com/dmcable/spacexr/tree/master/AnalysisGLAMDE/paper_results)