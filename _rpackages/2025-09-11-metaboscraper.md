---
title: "MetaboScrapeR: HMDB MS Spectra Query App"
collection: rpackages
type: "R Package"
layout: talk
permalink: /r-packages/metaboscraper
venue: "Online"
date: 2024-09-11
location: "GitHub/ShinyApps"
---

A Shiny Web app stored in GitHub. This [repository](https://github.com/jllcalorio/MetaboScrapeR) contains a set of R scripts designed to perform web scraping on the Human Metabolome Database (HMDB) to assist in the metabolomics data annotation/identification process. Access the Shiny Web App [here](https://jllcalorio.shinyapps.io/metaboscraper/).

Here are more details:

Overview
-----

This app queries the [HMDB (Human Metabolome Database)](https://www.hmdb.ca/)'s [LC-MS Search](https://www.hmdb.ca/spectra/ms/search) interface to retrieve compound information based on mass spectrometry features. It uses web scraping for reliable data retrieval.

Input Format
-----

Features (m/z@RT)
Enter your features in the format: MZ@RT where:
- MZ is the mass-to-charge ratio (e.g., 626.3547)
- RT is the retention time (e.g., 95.2)

Use @ (single at sign) as the separator
Separate multiple features with newlines, commas, or both
Maximum 700 features allowed per query

Examples:

- 626.3547@95.2
- 615.3753@120.5
- 450.2315@80.0

OR:

626.3547@95.2, 615.3753@120.5, 450.2315@80.0

OR:

- 626.3547@95.2, 615.3753@120.5
- 450.2315@80.0

Ion Mode
-----

Select the ionization mode used in your experiment. This will automatically update the default 'Adducts to Keep' list.

Adducts to Keep
-----

If left blank, all results will be returned in the 'Compound Metadata' tab.

Here are the adducts available in HMDB:

Negative Mode:
- M-H, M-H20-H, M+Na-2H, M+Cl, M+K-2H, M+FA-H, M-H+HCOONa, 2M-H, 2M+FA-H, 3M-H, M-2H, M-3H
Positive Mode:
- M+H, M+H-2H2O, M+H-H2O, M+Na, M+CH3OH+H, M+K, M+ACN+H, M+2Na-H, M+ACN+Na, M+2K-H, M+2ACN+H, M+H+HCOONa, 2M+H, 2M+Na, 2M+2H+3H2O, 2M+K, 2M+ACN+H, 2M+ACN+Na, 2M+H-H2O, M+2H, M+H+Na, M+H+K, M+ACN+2H, M+2Na, M+2ACN+2H, M+3ACN+2H, M+3H, M+2H+Na, M+H+2Na, M+3Na, M+H+2K
Neutral Mode:
- Unknown, M

The default adducts selected by this app when you change Ion Mode are a curated list of the most common adducts from the lists above.

R Packages Used
-----

This application uses the following R packages:
- shiny - Web application framework
- shinyjs - JavaScript operations in Shiny
- DT - Interactive DataTables
- writexl - Excel file export
- rvest - Web scraping
- stringr - String manipulation
- dplyr - Data manipulation
- purrr - Functional programming tools
- httr - HTTP requests
- jsonlite - JSON parsing
- future - Parallel processing framework
- furrr - Parallel mapping with purrr
- later - Deferred execution

Output Tabs
-----

**Compound Metadata**: Shows compounds that matched your search criteria AND your selected adducts. Includes detailed metadata from HMDB.

**Excluded Results**: Shows compounds that matched your search criteria but were filtered out because their adducts did not match your 'Adducts to Keep' list.

**Logs**: Shows a detailed, timestamped log of the entire query process, updated in real-time.
