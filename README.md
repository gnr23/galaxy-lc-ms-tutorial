# LC-MS Metabolomics Workflow: Entry into Bioinformatics

This repository contains my step-by-step documentation following the **Galaxy Training Network** tutorial on **untargeted LC-MS metabolomics analysis** using the **XCMS** tools in Galaxy.

##  This Repo Structure

My study is located in the folder tutorial.md in /notebook

##  Tutorial Overview

**Title:** Mass Spectrometry: LC-MS Analysis  
**Platform:** Galaxy (GTN)  
**Link:** [Galaxy Metabolomics Tutorial](https://training.galaxyproject.org/training-material/topics/metabolomics/tutorials/lcms/tutorial.html)

**Tutorial Objectives:**
- Learn the full untargeted LC-MS data processing workflow—from raw data to annotated results.
- Gain familiarity with each stage: preprocessing, data processing, statistical analysis, and annotation.
- Understand how Galaxy tools package R-based functions like **XCMS** and **CAMERA** into reusable workflows.

**Workflow Steps Covered:**
1. **Preprocessing (XCMS)**  
   - Import raw LC-MS files and sample metadata  
   - Perform chromatogram overview and first peak picking (centWave algorithm)  
   - Group peaks across samples, optionally correct retention time and fill missing peaks  
   - Optionally run CAMERA for isotope/adduct annotation

2. **Data Processing**  
   - Quality control: global variability checks, signal drift correction, and coefficient-of-variation filtering

3. **Statistical Analysis**  
   - Use PCA and Quality Metrics to explore data structure  
   - Example univariate analysis (e.g., correlation with BMI)

4. **Annotation (Optional)**  
   - Use CAMERA to assign putative identities to detected features via isotope/adduct recognition