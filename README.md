# R Package Runtime Validation Analysis  
*(Econometrics | Runtime Prediction | Validation Testing)*

## Overview
When developers submit R packages to CRAN, they must pass a validation process that includes running the `R CMD check` command across multiple platforms. The execution time of this process varies depending on package characteristics such as dependencies, file sizes, and structure.

This project analyzes over 13,000 R packages to identify the factors that influence validation runtime and to evaluate whether execution time can be accurately predicted using these characteristics.

---

## Objectives
- Identify key package characteristics affecting runtime  
- Quantify the impact of dependencies and package size  
- Build predictive models for `R CMD check` execution time  
- Evaluate model performance and robustness  

---

## Dataset
- Source: CRAN validation dataset (`check_times`)  
- Observations: ~13,500 R packages  

### Key Variables
- `check_time`: Execution time (dependent variable)  
- `depends`, `imports`: Dependency metrics  
- `r_size`, `src_size`, `doc_size`, `data_size`: Size-related features  
- `Roxygen`, `gh`: Binary indicators  

---

## Methodology

### Variable Selection
- Boruta algorithm used to identify important predictors  
- Correlation analysis used to reduce redundancy  

### Data Preprocessing
- Outlier detection using:
  - Studentized residuals  
  - Leverage  
  - Cook’s distance  
- Removal of influential observations to improve model stability  

### Transformation
- Yeo-Johnson transformations applied to address skewness  
- Bootstrap confidence intervals used to select transformation parameters  

### Modeling Approach
- Ordinary Least Squares (OLS)  
- Feasible Generalized Least Squares (FGLS) to address heteroskedasticity  
- Model specification tested using Ramsey RESET  
- Multicollinearity evaluated using Variance Inflation Factor (VIF)  

### Model Enhancement
- Inclusion of quadratic and interaction terms  
- Iterative specification testing  

### Validation
- Bootstrapping for parameter stability and confidence intervals  
- 5-fold cross-validation for predictive performance  

---

## Key Findings
- Dependency-related variables (`imports`, `depends`) significantly impact runtime  
- Package size metrics (`r_size`, `doc_size`, `src_size`) are strong predictors  
- Nonlinear relationships (quadratic terms) improve model performance  
- Yeo-Johnson transformations substantially improve model fit and residual behavior  
- Final models achieve strong explanatory power with robust validation results  


---

## Tools and Libraries
- Python (Pandas, NumPy)  
- Statsmodels (econometric modeling)  
- SciPy (transformations)  
- Seaborn, Matplotlib (visualization)  

---

## Repository Structure
