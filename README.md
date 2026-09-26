# Virtual R Data Analyst Internship

**Week 2 of 4 – Data Visualization and Insight Communication Using R**

This repository contains the code, data and outputs of the Week 2 submission: the R code (including the Week 1 import and cleaning steps needed to recreate the cleaned data), the dataset, all charts and the data behind them, console transcripts, rendered screenshots and an interactive chart. The written report (Word document) is submitted separately through the internship portal.

## Project Overview

The internship project analyses customer churn for a telecommunications company using the IBM Telco Customer Churn dataset. The work is split into four weekly submissions, each in its own repository:

| Week | Topic | Repository |
|---|---|---|
| 1 | Data cleaning and preliminary analysis | [Virtual-R-Data-Analyst-Week1](https://github.com/Pharos-0/Virtual-R-Data-Analyst-Week1) |
| **2 (this repository)** | Data visualisation and insight communication | [Virtual-R-Data-Analyst-Week2](https://github.com/Pharos-0/Virtual-R-Data-Analyst-Week2) |
| 3 | Statistical analysis and predictive modelling | [Virtual-R-Data-Analyst-Week3](https://github.com/Pharos-0/Virtual-R-Data-Analyst-Week3) |
| 4 | Comprehensive final report | [Virtual-R-Data-Analyst-Week4](https://github.com/Pharos-0/Virtual-R-Data-Analyst-Week4) |

## Dataset

- **Name:** Telco Customer Churn (IBM sample data describing a fictional telecommunications company)
- **Source:** [IBM/telco-customer-churn-on-icp4d](https://github.com/IBM/telco-customer-churn-on-icp4d/blob/master/data/Telco-Customer-Churn.csv) – Apache License 2.0
- **Size:** 7,043 rows × 21 columns; target `Churn` (26.5% churned)
- **Input to Week 2:** the cleaned data from Week 1, recreated here by `R/01_data_import.R` and `R/02_data_cleaning.R`

## Objectives

Create informative visualisations with `ggplot2` that answer six questions about the customers – who they are, which variables separate churners, which numeric variables are related, what patterns appear across tenure, which groups have very different outcomes, and which observations are unusual – and communicate the findings to a non-technical audience.

## Week 1 – Data Cleaning and Preliminary Analysis

Import, inspection, missing values (11 blank `TotalCharges` set to 0 for zero-tenure customers), duplicates, type conversion, outliers, scaling, encoding, descriptive statistics and correlation. See the [Week 1 repository](https://github.com/Pharos-0/Virtual-R-Data-Analyst-Week1).

## Week 2 – Data Visualization (this repository)

- **Report:** `Week_2_Report.docx`, submitted through the internship portal (not stored in this repository)
- **Code:** [`R/04_visualization.R`](R/04_visualization.R) (after `R/01_data_import.R` and `R/02_data_cleaning.R`), run by [`run_all.R`](run_all.R)
- **Outputs:** eleven charts in `figures/w2_*.png`, the data behind them in `outputs/tables/w2_*.csv`, an interactive chart in `outputs/interactive/w2_interactive_scatter.html`, console transcripts in `outputs/logs/`, screenshots in `screenshots/`

| Chart | Type | Question |
|---|---|---|
| V1 | Bar chart | How does churn differ by contract type? |
| V2 | Scatter plot | How are tenure and monthly charges related, and where are churners? |
| V3 | Histogram | How is tenure distributed for churned and retained customers? |
| V4 | Line chart | How does churn change across tenure for each contract type? |
| A1 | Faceted bar chart | Who are the customers? |
| A2 | Stacked bar chart | Does churn differ by payment method? |
| A3 | Density plot | Do churned customers pay more? |
| A4 | Box + violin plot | Is the higher bill a price or a service-mix effect? Unusual charges? |
| A5 | Heatmap | Which contract × internet combinations churn most? |
| A6 | Faceted bar chart | Are add-on services linked to lower churn? |
| A7 | Boxplot | Which customers have unusual tenure for their group? |

## Week 3 – Statistical Analysis and Predictive Modeling

Hypothesis tests with assumption checks, and logistic regression / random forest models with cross-validation. See the [Week 3 repository](https://github.com/Pharos-0/Virtual-R-Data-Analyst-Week3).

## Week 4 – Comprehensive Final Report

Integrated final report. See the [Week 4 repository](https://github.com/Pharos-0/Virtual-R-Data-Analyst-Week4).

## Technologies

R 4.3.3 · `ggplot2` · `dplyr` · `tidyr` · `forcats` · `scales` · `ragg` (300 dpi PNG output) · `plotly` + `htmlwidgets` (interactive chart) · `readr` · `stringr` · `purrr` · `janitor` · `highr` (screenshots). The analysis was run with `Rscript`; RStudio was not available, so screenshots are renderings of the saved R console transcripts and script files.

## Repository Structure

```text
Virtual-R-Data-Analyst-Week2/
├── README.md
├── run_all.R                    # runs every script in R/ and saves console transcripts
├── R/                           # analysis scripts
│   ├── 00_setup.R
│   ├── 01_data_import.R
│   ├── 02_data_cleaning.R
│   ├── 04_visualization.R
│   ├── render_screenshots.R
│   └── screenshot_specs.R
├── data/
│   ├── README.md
│   ├── raw/                     # Telco-Customer-Churn.csv + Apache-2.0 licence
│   └── processed/               # telco_clean.csv (cleaned data)
├── outputs/
│   ├── tables/                  # 13 CSV tables
│   ├── metrics/                 # 3 JSON files with the key results
│   ├── logs/                    # console transcripts, run summary, session info, package versions
│   └── interactive/             # interactive plotly chart (open the HTML file in a browser)
├── figures/                     # 11 charts (PNG, 300 dpi)
├── screenshots/                 # 21 renderings of R console output + index
└── requirements/
    └── R_packages.txt           # packages and versions used
```

## Methodology

All charts share one restrained style: churned customers are always navy and retained customers grey, titles state the finding (numbers in titles are computed from the data), rates are used instead of counts when groups differ in size, and every chart has labelled axes and a legend or direct labels. The navy/grey palette was checked for colour-vision-deficiency separation. The data behind every chart is printed to the console transcript before the chart is saved. The full method is described in the Week 2 report.

## Key Findings

- Month-to-month customers churn at **42.7%**, two-year customers at **2.8%**.
- **55%** of churned customers left within their first 12 months.
- Fibre customers on month-to-month contracts churn at **54.6%**; they are 30% of customers but 62% of churners.
- Churned customers pay more overall (median 79.65 vs 64.43), but **within** DSL and fibre they pay less – the difference reflects the service mix.
- Electronic-check payers churn at 45.3%; internet customers with online security churn at 15% vs 42% without.

These are descriptive patterns in a cross-sectional sample, not causal effects.

## Reproducibility

```bash
Rscript run_all.R
```

Runs the import, cleaning and visualisation scripts in order (seed 42), writes console transcripts to `outputs/logs/` and re-renders the screenshots (requires Google Chrome or Chromium). Packages and versions: [`requirements/R_packages.txt`](requirements/R_packages.txt). Install them with the command at the top of that file. A single script can be re-run with, for example, `Rscript run_all.R 02`; the R session information and package versions of the last run are saved in `outputs/logs/`.

**About the screenshots:** RStudio was not available, so the images in `screenshots/` are renderings of genuine R console transcripts and script excerpts, not RStudio window captures. The interactive-chart screenshot is a headless-browser capture of the HTML file produced by `plotly`.

## Dataset Source

IBM, *Telco Customer Churn* sample data, repository [IBM/telco-customer-churn-on-icp4d](https://github.com/IBM/telco-customer-churn-on-icp4d), file `data/Telco-Customer-Churn.csv`. Apache License 2.0; see [`data/raw/LICENSE-Apache-2.0_IBM.txt`](data/raw/LICENSE-Apache-2.0_IBM.txt).

## Author

Pharos Sophy Samuel T J – Virtual R Data Analyst Internship, Week 2 submission.
