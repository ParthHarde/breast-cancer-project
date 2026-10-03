# Dataset Notes: METABRIC

## Source
- Name: Breast Cancer Gene Expression Profiles (METABRIC)
- Kaggle: https://www.kaggle.com/datasets/raghadalharbi/breast-cancer-gene-expression-profiles-metabric
- File used: METABRIC_RNA_Mutation.csv
- Downloaded on: 3 October 2026

## Original research sources (cite these in the report)
- Curtis et al., 2012, Nature
- Pereira et al., 2016, Nature Communications

## Dataset summary
- Shape (df.shape): 1904 x 693
- Each row = one patient (1,904 patients)
- Column groups:
  - 31 clinical columns (first 31 columns)
  - Gene expression columns (float): about 489 (to be confirmed in preprocessing)
  - Mutation columns (text): about 173 (to be confirmed in preprocessing)
- Data types: 498 float64, 190 object, 5 int64
- Duplicate rows: 0
- Duplicate patient IDs: 0

## Target
- Main target: overall_survival
- Meaning (verified with crosstab against death_from_cancer): 1 = living, 0 = deceased
- Class balance: 0 (deceased) = 1103 (57.9%), 1 (living) = 801 (42.1%)
- Majority-class baseline accuracy: 57.9%
- Limitation: the deceased class includes 622 deaths from disease and 480 deaths from other causes, so the target is not cancer-specific

## Columns excluded from features
- death_from_cancer: reveals the outcome (data leakage)
- overall_survival_months: describes the outcome itself (data leakage)
- patient_id: identifier
- cohort: study group, not available to an app user

## Columns with most missing values
1. tumor_stage: 501 (26.3%)
2. 3-gene_classifier_subtype: 204 (10.7%)
3. primary_tumor_laterality: 106 (5.6%)
4. neoplasm_histologic_grade: 72 (3.8%)
5. cellularity: 54 (2.8%)
6. mutation_count: 45 (2.4%)
- Gene expression columns have no missing values in the columns inspected.

## Notes
- Raw data is stored in data/raw and is never edited.
- This Kaggle file is a pre-processed copy; the original studies are the primary sources.
- 3-gene_classifier_subtype, pam50_+_claudin-low_subtype and integrative_cluster are derived from gene expression. They are acceptable for the survival target but must be excluded from the subtype extension.
