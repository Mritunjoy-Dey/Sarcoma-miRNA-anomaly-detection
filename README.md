# Sarcoma miRNA Anomaly Detection
### Description
>#### One-class anomaly detection framework using miRNA expression data to distinguish sarcoma from other cancer lineages, identify lineage vs oncogenic signals, and uncover prognostic biomarkers.
>
><img width="3000" height="2100" alt="Isolation forest pipeline for Bioinformatics research paper" src="https://github.com/user-attachments/assets/b79a5787-6c7b-4b7c-a828-7c97ba600e0f" />

> ----------------------------------------------------------------
### Code accompanying the manuscript:
>#### "miRNA expression differences between sarcoma and other cancer lineages encode distinct biological and clinical signals"
>#### Dey M, Remiszewski P, Perdas E, Golik P, Piątkowski J & Czarnecka AM
> -----------------------------------------------------------------
### What this study does
>#### Sarcomas are mesenchymal malignancies that are molecularly under-characterised. This study asks whether miRNA expression differences between sarcoma and other cancer types reflect biologically meaningful programmes or just descriptive variation.
>#### Three independent Isolation Forest models were trained on epithelial, haematological, and neurological TCGA cancer cohorts — with sarcoma treated as a strictly held-out anomaly class throughout. SHAP-based feature attribution identified eight consensus miRNAs driving the sarcoma anomaly signal. These were then evaluated against normal mesenchymal tissue to separate retained lineage identity from true oncogenic dysregulation, and assessed for prognostic relevance through survival analysis.
> -----------------------------------------------------------------
### Scripts
>### Isolation_forest
>#### Trains three cohort-specific Isolation Forest models (epithelial, haematological, neurological) using 5-fold cross-validation. Computes AUC-ROC, AUC-PR, sensitivity, and specificity with a constrained threshold strategy (maximise specificity subject to sensitivity ≥ 0.80). Runs TreeSHAP fold-by-fold on sarcoma samples and identifies consensus miRNAs appearing in the top-20 feature lists of two or more lineage comparisons.
> -----------------------------------------------------------------
>### Sarc_Vs_Normal_comparison
>#### Performs differential expression analysis of the consensus miRNAs between TCGA sarcoma (n = 262) and normal mesenchymal muscle tissue (GEO: GSE163534; n = 4). Uses Mann-Whitney U test with Benjamini-Hochberg FDR correction and rank-biserial correlation as effect size. Outputs a volcano plot, expression heatmap, violin plots, and MA plot.
> -----------------------------------------------------------------
>### KM survival analysis
>#### Runs Kaplan-Meier overall survival analysis for each consensus miRNA in TCGA-SARC. Patients are dichotomised by median expression; survival curves are compared using the log-rank test. Produces individual and combined KM plots with 95% confidence bands and a summary CSV.
> -----------------------------------------------------------------
