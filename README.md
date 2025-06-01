Glioblastoma Gene Expression and Network Analysis from TCGA Data
Overview
This repository contains a comprehensive bioinformatics analysis of gene expression data from Glioblastoma (GBM) cases, leveraging publicly available data from The Cancer Genome Atlas (TCGA). The primary goal of this project is to identify key genes and their co-expression patterns that may contribute to glioblastoma development and progression, including its invasive characteristics.

The analysis workflow, implemented in a Jupyter Notebook, covers data preprocessing, differential gene expression analysis, gene co-expression network construction (using WGCNA-like principles), and a comparative analysis of network properties between normal and tumor tissue samples. Additionally, the project includes an exploration of clinical demographics and survival outcomes associated with the GBM cohort and specific gene mutations.

Data Source
The core expression data for this project is sourced from The Cancer Genome Atlas (TCGA) Glioblastoma (GBM) cohort.

Expression Data: glio.tsv
This TSV file contains expression clustering analysis data for 100 genes across 287 glioblastoma cases.
It is assumed that this file also contains a 'Tissue type' column to distinguish between Normal and Tumor samples.
Clinical Data: Additional clinical and demographic data (e.g., age, gender, ethnicity, primary diagnosis, race, and survival information) were also utilized from the TCGA database to provide context and perform survival analyses.
Analysis Workflow
All analyses are performed within the gliomak4.ipynb Jupyter Notebook.

The notebook covers the following key steps:

Data Loading and Preprocessing:

Loads the glio.tsv file into a pandas DataFrame.
Separates the dataset into "Normal" and "Tumor" cases based on the 'Tissue type' column.
Performs initial data cleaning, including handling missing values and applying transformations (e.g., log2 transformation, quantile normalization).
Filters genes based on variance to focus on informative features.
Differential Gene Expression Analysis:

Identifies significantly up- and down-regulated genes between normal and tumor samples using statistical tests (e.g., t-tests) and multiple hypothesis correction (FDR).
Visualizes differential expression using a Volcano Plot.
Gene Co-expression Network Analysis (WGCNA-like):

Calculates Spearman correlation matrices for significant genes.
Performs hierarchical clustering to identify gene modules/groups.
Computes the Topological Overlap Matrix (TOM) to quantify shared neighborhood similarity between genes.
Calculates Connectivity (weighted degree) and Clustering Coefficient (local network density) for each gene within the network.
Comparative Network Analysis (Normal vs. Tumor):

The co-expression network analysis (including correlation heatmaps, dendrograms, TOM, connectivity, and clustering coefficients) is performed separately for Normal and Tumor cases.
A comparative table is generated to highlight differences in connectivity and clustering coefficients for each gene between the normal and tumor conditions.
Visualizations (bar plots) are created to show the differences in these network metrics.
Clinical and Survival Analysis:

Demographic Profiling: Visualizes the distribution of cases by:
Age at Diagnosis (Image 1)
Ethnicity (Image 2)
Gender (Image 3)
Primary Diagnosis (Image 4)
Race (Image 5)
Overall Survival Analysis: Presents a Kaplan-Meier survival curve for the entire glioblastoma cohort (Image 6).
Gene-Specific Survival Analysis: Investigates the impact of specific gene mutations (SSM/CNV) on patient survival using Kaplan-Meier curves for:
KIF1A (Image 7)
AZGP1 (Image 8)
Key Findings & Visualizations
The project provides insights into the molecular characteristics of glioblastoma and highlights genes with potential roles in its pathogenesis.

Patient Demographics: The initial analysis provides a clear overview of the patient cohort's demographic distribution, including age, ethnicity, gender, primary diagnosis, and race (Images 1-5). This contextualizes the biological findings within the patient population.
Glioblastoma Prognosis: The overall survival curve (Image 6) underscores the aggressive nature of glioblastoma, with a steep decline in survival rate over time.
Gene-Specific Prognostic Impact: Survival analysis for individual genes like KIF1A (Image 7) and AZGP1 (Image 8) reveals how their mutation status may correlate with patient outcomes, suggesting their potential as prognostic biomarkers.
Gene Co-expression Networks: The correlation heatmaps, dendrograms, and Topological Overlap Matrices (generated within the notebook for both normal and tumor cases) illustrate the complex relationships and co-expression patterns among significant genes.
Network Hubs and Differences: The calculated connectivity and clustering coefficients, along with their comparative analysis between normal and tumor tissues, help identify genes that become more or less central/interconnected in the disease state. This can point to critical regulatory genes or pathways altered in glioblastoma.
Technologies Used
Python: Programming language for data analysis.
Jupyter Notebook: Interactive computing environment.
Pandas: Data manipulation and analysis.
NumPy: Numerical computing.
Matplotlib: Static, interactive, and animated visualizations.
Seaborn: Statistical data visualization.
SciPy: Scientific computing (for hierarchical clustering and distance calculations).
NetworkX: Graph and network analysis (for accurate clustering coefficient calculation).
How to Use / Reproduce
To run this analysis and reproduce the results:

Clone the Repository:
Bash

git clone https://github.com/YourUsername/Glioblastoma_Gene_Analysis.git
cd Glioblastoma_Gene_Analysis
Install Dependencies: It is highly recommended to use a virtual environment.
Bash

pip install pandas numpy matplotlib seaborn scipy networkx
Obtain Data:
Place your glio.tsv file in the root directory of the cloned repository.
(Optional, if not already included in glio.tsv): Ensure you have access to the necessary clinical/demographic data from TCGA if you wish to reproduce the demographic and survival plots.
Run the Notebook:
Bash

jupyter notebook gliomak4.ipynb
Open the gliomak4.ipynb file in your browser and run all cells sequentially.
Future Work
Biological Validation: Conduct in-depth biological validation (e.g., in vitro cell line experiments, in vivo animal models) for the identified hub genes and altered network modules.
Multi-Omics Integration: Integrate gene expression data with other omics layers (e.g., proteomics, epigenomics, somatic mutations) from TCGA to gain a more holistic understanding of GBM pathogenesis.
Functional Pathway Analysis: Perform more detailed functional enrichment and pathway analysis on the identified gene modules and their changes between normal and tumor states.
Therapeutic Target Identification: Further investigate the potential of identified genes (e.g., KIF1A, TPPP, SMIM3) as therapeutic targets for glioblastoma, considering their roles in invasion and proliferation.
Machine Learning for Prognosis/Prediction: Develop and evaluate machine learning models using the identified network features to predict patient prognosis or response to specific therapies.
