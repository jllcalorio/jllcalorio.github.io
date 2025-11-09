---
title: "Metabolomics Data Analysis Toolkit"
excerpt: "The Metabolomics Data Analysis Toolkit is an R-based analytical framework developed to streamline and standardize the statistical workflow for metabolomics research."
collection: portfolio
---

It automates common yet complex processes such as data preprocessing, normalization, scaling, dimensionality reduction, multivariate modeling, and feature selection, allowing researchers to focus more on biological interpretation rather than repetitive coding tasks.

This toolkit was designed for researchers working with LC–MS, GC–MS, or NMR-based metabolomics datasets formatted as Samples × Features (rows × columns) and provides a comprehensive suite of statistical and visualization tools consistent with best practices in metabolomics data analysis.

🧩 Key Features
------

The toolkit, implemented as the R package MetaboStatR, integrates widely used metabolomics data processing and statistical workflows in a reproducible, modular way.

1. Data Preprocessing

- Handles feature removal according to rule-of-thumb: >20% missing in all groups.
- Handles missing values with minimum value replacement.
- Performs normalization (sum, quantile, log, vsn, glog, etc.) and scaling (auto, pareto).
- Supports batch correction and QC-based normalization.

2. Principal Component Analysis (PCA)

- PCA on QC samples or biological samples or both.
- Generates publication-ready scree plots and scores plots with ellipses.
- Automatically annotates outliers and computes total explained variance.

3. Hierarchical Clustering

- Clustering using Euclidean distance and Ward’s linkage.
- Outputs dendrograms with optional grouping rectangles to highlight cluster boundaries.

4. Multivariate Discriminant Analysis

- Implements Partial Least Squares–Discriminant Analysis (PLS-DA) and Orthogonal PLS-DA (OPLS-DA).
- Provides VIP plots, S-plots, and abundance plots for biomarker discovery.
- Visualizes group separations with confidence ellipses and cross-validation summaries.

5. Univariate and Fold-Change Analysis

- Computes fold change (FC) and log₂(FC) values for group comparisons.
- Performs t-tests, Mann–Whitney, ANOVA, or Kruskal–Wallis tests as appropriate after assumption testing.
- Adjusts p-values using Benjamini–Hochberg correction as default with many other methods available.
- Generates volcano plots highlighting up- and downregulated metabolites.

6. AUROC and Predictive Modeling

- Filters features based on VIP score, FC, and adjusted p-values.
- Computes AUROC for top discriminant metabolites and visualizes their classification performance.
- Integrates LASSO and Elastic Net Regression for predictive model building with cross-validation and confusion matrices.

⚙️ Core Functions

------
Function	| Purpose
performDataQualityCheck | Checks readiness of data for preprocessing
performDataPreprocessing() | Performs comprehensive data preprocessing from feature filtering, normalization, scaling
performPCA(), performPLS()	| Conducts PCA, PLS-DA, and OPLS-DA with comprehensive plotting outputs.
performFoldChange()	| Calculates fold change, log₂ fold change, and volcano plots.
performComparativeAnalysis() | Performs t-test/ANOVA or nonparametric alternatives based on the results of assumption testing.
performAUROC()	| Computes AUROC and plots discriminant features.
performRegression()	| Runs LASSO and Elastic Net regression, including coefficients and odds ratios.

All functions are designed with consistent syntax, automated figure saving, and reproducible outputs, making the package both beginner-friendly and powerful for experienced bioinformaticians.

🧠 Methodological Highlights
------

- Built upon sound statistical foundations in metabolomics (van den Berg et al., 2006; Worley & Powers, 2013).
- Employs Pareto scaling for intermediate variance stabilization.
- Integrates cross-validation and feature ranking for biomarker discovery.
- Outputs plots using ggplot2, ensuring publication-ready visualizations.

📊 Example Workflow
------

```r
library(MetaboStatR)

# Load example dataset (Samples × Features)
data <- performDataQualityCheck("metabolomics_data.csv")

# 1. PCA and visualization
pca_results <- performPCA(data, method = "PCA")

# 2. OPLS-DA modeling
opls_results <- performPLS(data, method = "OPLS-DA")

# 3. Fold change analysis
fc_results <- performFoldChange(data, group_col = "Group")

# 4. AUROC for top features
auroc_results <- performAUROC(data, group_col = "Group", fc_data = fc_results)
```

Each step produces both numerical results and high-quality figures saved in the working directory which can be exported later.

💡 Applications
------

- Biomarker discovery in clinical metabolomics
- Batch effect and QC assessment in multi-batch studies
- Metabolic profiling of disease vs. control groups
- Exploratory and confirmatory analysis for nutritional, environmental, and pharmacological studies

📈 Impact and Advantages
------

- Reduces the time required to process and interpret metabolomics data.
- Standardizes analysis workflows across projects and collaborators.
- Enhances reproducibility and transparency in biomedical research.
- Bridges statistical rigor and biological interpretation.

🧰 Tools and Technologies
------

- R Language (core implementation)
- mixOmics, ggplot2, gtsummary, ropls, pROC, glmnet
- Tested in RStudio environment
- Future compatibility with Shiny Web Apps for interactive data exploration

📦 Repository
------

🔗 GitHub: [github.com/jllcalorio/MetaboStatR](https://github.com/jllcalorio/MetaboStatR)
📘 Documentation: Available in the repository README and function manuals
