---
title: "MetabolomicStatR: Perform Data Preprocessing, Bioinformatics and Statistical Data Analysis, and Data Visualization on Peak Intensities"
collection: rpackages
type: "R Package"
layout: talk
permalink: /talks/metabostatr
venue: "Online"
date: 2024-10-10
location: "GitHub"
---

This repository contains a set of R scripts designed to analyze metabolomics data, specifically, on data from direct-injection. This package accepts various types including csv files. See the documentation [here](https://jllcalorio.github.io/MetaboStatR/reference/index.html).

Here are the functions:

perform_DataQualityCheck: Perform Comprehensive Data Quality Check for Metabolomics Data
-----

This function imports and validates metabolomics data from Excel, CSV, TSV, or text files, performing comprehensive quality controls to ensure data integrity and compatibility with downstream analysis functions. The function validates data structure, checks for required metadata rows, ensures uniqueness constraints, cleans special characters from identifiers, and prepares data for preprocessing pipelines.

perform_PreprocessingPeakData: Comprehensive Data Preprocessing Pipeline
-----

Performs a complete data preprocessing workflow to prepare raw data for downstream analysis. This function applies preprocessing steps sequentially in the order specified by the parameters to ensure optimal data quality and analytical readiness.

perform_PCA: Perform Principal Component Analysis (PCA)
-----

This function performs PCA and generates multiple scores plots at once based on a list of principal component combinations, plus an optional scree plot. Each combination in the list will produce a separate scores plot.

perform_PLS: Perform Orthogonal Partial Least Squares Discriminant Analysis (OPLS-DA) and Related Methods
-----

This function performs various Partial Least Squares (PLS) methods including PLS, PLS-DA, OPLS-DA, and sparse PLS-DA (sPLS-DA) on metabolomics or other omics data. It provides comprehensive analysis with visualization and feature importance assessment.

perform_FoldChange: Perform Fold Change Analysis on Preprocessed Peak Data
-----

Performs pairwise fold change analysis on preprocessed metabolomics or proteomics peak data. The function calculates fold changes and log2 fold changes between all possible group pairs while excluding quality control (QC) samples. The analysis uses group means for comparison and includes options for custom group ordering and result sorting.

perform_ComparativeAnalysis: Perform Comparative Statistical Analysis on Preprocessed Metabolomics Data
-----

Conducts comprehensive comparative statistical analysis on preprocessed metabolomics data. The function automatically selects appropriate statistical tests based on data characteristics including normality, variance homogeneity, and sample independence. Supports both two-group and multi-group comparisons with parametric and non-parametric alternatives.

perform_AUROC: Perform Area Under the Receiver Operating Characteristic Curve Analysis
-----

Performs comprehensive Area Under the Receiver Operating Characteristic (AUROC) analysis for metabolomics data. This function integrates results from data preprocessing, dimension reduction (OPLS-DA), fold change analysis, and comparative analysis to identify and visualize discriminative metabolic features between different groups. The function automatically filters features based on Variable Importance in Projection (VIP) scores, fold change thresholds, and statistical significance, then generates ROC curves for the most discriminative features.

perform_Regression: Perform LASSO and Elastic Net Regression with Cross-Validation
-----

This function performs regularized regression analysis using LASSO (Least Absolute Shrinkage and Selection Operator) and/or Elastic Net regression methods. Both methods are regularization techniques that prevent overfitting by adding penalty terms to the loss function. LASSO uses L1 regularization for feature selection by shrinking coefficients to zero, while Elastic Net combines L1 and L2 penalties to handle multicollinearity and perform simultaneous feature selection. The function supports both binary and multinomial classification tasks with comprehensive model evaluation and result reporting.

plot_BeforeAfter: Visualize Data Before and After Preprocessing
-----

Creates comprehensive visualizations comparing data distributions and patterns before and after preprocessing steps. Generates density plots and box plots from either sample or feature perspectives to assess preprocessing effectiveness. Supports both PCA and PLS scaled data visualization with intelligent random sampling for large datasets.

plot_CorrelationHeatmap: Plot Correlation and Hierarchical Clustering Heatmaps
-----

Generates correlation or hierarchical clustering heatmaps with advanced filtering capabilities. The function creates publication-ready visualizations by selecting the most variable features/samples based on interquartile range (IQR) and applies statistical significance masking for correlation plots.

plot_Volcano: Create Volcano Plots for Differential Expression Analysis
-----

Generates volcano plots to visualize the results of differential expression analysis by plotting log2 fold changes against negative log10 adjusted p-values. The function creates plots for all pairwise group comparisons and applies significance thresholds to highlight upregulated, downregulated, and non-significant features.

perform_Export2Excel: Export Data Frames to Excel Workbook
-----

Exports data frames from named lists or multiple lists to multi-sheet Excel workbooks. The function automatically detects data frames and tibbles within the input, creates appropriately named worksheets, and handles various edge cases including sheet name length restrictions, duplicate names, and invalid characters. Each data frame becomes a separate worksheet in the output Excel file. The function can accept either a single named list or multiple lists, and will create separate Excel files for each list when multiple file names are provided.

perform_ExportPlots2Image: Export Plot Objects to Image Files
-----

Exports plot objects (ggplot2, base plots, lattice, plotly, etc.) from named lists or multiple lists to individual image files. The function automatically detects various plot objects within the input, creates appropriately named image files, and handles various edge cases including file name length restrictions, duplicate plots, invalid characters, and different plot formats. Each plot object becomes a separate image file in the specified format. The function can accept either a single named list or multiple lists, and will create separate folders or file naming schemes for each list when multiple folder names are provided.
