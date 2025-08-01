# Media Spend Cost Optimization  
**Marketing Mix Modeling with Bayesian and SHAP Approaches**

## Overview  
This project builds a marketing mix model to evaluate and optimize media spending for a shampoo product advertiser using Bayesian regression and SHAP (Shapley Additive Explanations). The model quantifies the impact of multiple media channels on sales, incorporating adstock and saturation effects. We aim to identify diminishing returns, optimize future budget allocation, and improve ROI through modern statistical and machine learning techniques.

## Table of Contents  
- Introduction  
- Dataset Description  
- Architecture  
- Methods  
  - Workflow 1: LightweightMMM  
  - Workflow 2: SHAP + XGBoost  
- Results and Evaluation  
- Conclusion  

## Introduction  
Marketing Mix Modeling (MMM) helps marketers attribute sales to multiple media channels like TV, newspapers, SEM, etc. The project explores traditional Bayesian approaches as well as modern SHAP-based explanations to:  
- Understand media channel effectiveness  
- Quantify adstock lag effects  
- Capture saturation/diminishing returns  
- Optimize spend for maximum ROI  

This allows stakeholders to make data-driven budget decisions across campaigns.

## Dataset Description  
- **Source**: Neustar MarketShare, used by Google for MMM case studies  
- **Granularity**: Weekly data over 4 years  
- **Variables**:  
  - **Media Spend** (`mdsp_*`): across 13 channels  
  - **Media Impressions** (`mdip_*`)  
  - **Control Features**: macroeconomic indicators, markdowns, store count, seasonal holidays  
  - **Target**: Weekly sales volume in dollars  

## Architecture  
The modeling pipeline follows two parallel workflows:  
- **Workflow 1**: Bayesian MMM using LightweightMMM  
- **Workflow 2**: Tree-based SHAP interpretation using XGBoost  

Both workflows process the same feature set but offer different insights into media effectiveness.

## Methods  

### Workflow 1: LightweightMMM (Bayesian MMM)  
1. Standard preprocessing: nulls, encoding, scaling  
2. Transformations:  
   - Adstock (carryover)  
   - Saturation (Hill function)  
3. Define priors for Bayesian inference  
4. Run model and evaluate posteriors  
5. Analyze:  
   - Baseline spend impact  
   - Response curves (diminishing returns)  
   - Optimized media budget  
6. Calculate ROI per media channel

### Workflow 2: SHAP-based XGBoost Model  
1. Preprocessing + Optuna for Adstock decay tuning  
2. Train XGBoost model with media + control features  
3. Generate:  
   - SHAP summary plots (feature importance)  
   - SHAP dependence plots (diminishing returns)  
   - SHAP interaction values  
4. Optimize spend using SciPy with constraints  
5. Evaluate predicted vs actual sales (adjusted R²)

## Results and Evaluation  

### LightweightMMM Findings  
- **R² = 0.672**  
- **Top Media Contributors**:  
  - Direct Mail, TV, and Online Display  
- **Optimized Budget**:  
  - Increased SEM allocation from ~10% to 36%  
  - Sales prediction improved from $713.9M to $728.2M  

### SHAP + XGBoost Findings  
- **Adjusted R² = 0.535**  
- **Top Positive Features**:  
  - SEM media spend, SEM impressions  
- **Negative but significant features**:  
  - Impressions from newspaper, radio, and digital audio  
- **Budget Optimization**:  
  - SEM and Insert received increased allocations  
  - Added 20% deviation constraint to reflect business limits  

## Conclusion  
- **Bayesian MMM** explained majority of sales variance and quantified ROI under uncertainty.  
- **SHAP + XGBoost** provided transparent interpretation and feature-wise insights into diminishing returns.  
- **Optimized Budget** allocation improved predicted sales and media efficiency.  
- **Adstock & Saturation effects** were successfully modeled, offering realistic advertising impact timelines.

## Lessons Learned  
- Successfully combined statistical modeling with machine learning interpretability.  
- Demonstrated that SHAP explanations offer actionable transparency for marketing decisions.  
- Learned to align ROI-driven marketing strategy with budget constraints and diminishing returns.  
- Highlighted importance of model validation with real-world budget scenarios.
