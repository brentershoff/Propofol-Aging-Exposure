# Propofol-Aging-Exposure
Retrospective PK/PD reconstruction of propofol effect-site concentration during anesthetic induction


# Propofol Age-Exposure Reconstruction

Code for retrospective reconstruction of propofol effect-site exposure during anesthetic induction across the adult lifespan.

## Overview

This repository contains the analytic workflow used to assemble a retrospective propofol induction dataset, reconstruct modeled effect-site concentration trajectories, perform age-stratified statistical analyses, and generate manuscript figures and tables.

The workflow was developed for a study evaluating the relationship between clinician-administered propofol dose, modeled peak brain exposure, and age-adjusted pharmacodynamic requirement.

## Repository structure

This repository is organized to mirror the major stages of the analysis:

1. dataset extraction and assembly from the perioperative SQL warehouse
2. pharmacokinetic simulation of propofol effect-site concentration trajectories
3. statistical modeling of age-associated dose and exposure patterns
4. generation of main and supplementary manuscript figures and tables

## Notebook descriptions

### 01_extract_propofol_induction_dataset.ipynb

Creates the analysis-ready propofol induction dataset from the perioperative SQL warehouse. This notebook:

- identifies eligible adult general anesthesia cases receiving propofol
- identifies first documented induction and intubation timestamps
- extracts propofol medication administrations occurring within 10 minutes after induction
- retains both bolus and infusion events
- combines age-batched extraction files into a master dataset
- cleans timestamps, units, and dose fields
- computes patient-level dose summary variables, including total bolus dose, total infusion dose, total propofol dose, and dose normalized to total body weight
- applies the primary total-bolus filtering rule
- merges patient-level summary variables back into the long medication-event dataset
- exports the analysis-ready CSV used in downstream modeling

  ### 02_generate_table1_age_stratified.ipynb

Generates the manuscript Table 1 age-stratified baseline summary table. This notebook:

- loads the cleaned analysis-ready propofol induction dataset
- collapses the long-format medication-event data to a patient-level analytic table
- retains demographic and induction variables used in Table 1
- assigns patients to prespecified age strata
- computes descriptive summary statistics within each stratum
- formats manuscript-ready summary values
- exports LaTeX output for direct inclusion in Overleaf

## Planned workflow

Additional notebooks in this repository will include:

- primary pharmacokinetic reconstruction using the Eleveld model
- sensitivity analyses, including alternate PK models and medication-adjusted models
- generation of main manuscript figures
- generation of main manuscript tables
- generation of supplementary figures and tables

## Main output files

The extraction notebook produces a cleaned long-format dataset containing medication-event rows enriched with patient-level summary dose metrics for downstream PK/PD simulation and statistical analysis.

## Reproducibility note

This public repository contains cleaned analytic code corresponding to the manuscript workflow. Institution-specific database connection details have been removed. Table and schema names have been generalized in the public version. Protected source data are not distributed with this repository.

## Important implementation notes

- The primary extraction workflow excludes cases with implausible total bolus propofol doses using predefined thresholds.
- Sensitivity analyses later repeat the workflow using broader inclusion criteria.
- Final manuscript analyses using adjusted body weight (ABW) are implemented in a later preprocessing/modeling notebook rather than in the extraction notebook.

## Citation and archived release

A versioned archived release corresponding to the manuscript submission will be added here.

- GitHub repository: [insert link]
- Archived release / DOI: [insert DOI]
