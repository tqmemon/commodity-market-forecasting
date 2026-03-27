## Overview
This project investigates whether the traditional "safe-haven" status of gold and 10-year US Treasury bonds broke down during and after the COVID-19 pandemic. By analyzing macro-financial indicators across three distinct periods (Pre-COVID, COVID, and Post-COVID), we aim to identify if changes in asset behavior represent a temporary shock or a structural shift in the market.

## Data Sources
* **Kaggle**: [Gold & Geopolitical Risk (1985-2025)](https://www.kaggle.com/datasets/shreyanshdangi/gold-silver-price-vs-geopolitical-risk-19852025/data)
* **FRED API**: 
    * `VIXCLS` (Market Volatility / VIX)
    * `DEXUSEU` (USD/EUR Exchange Rate)
    * `DFF` (Federal Funds Rate)
    * `SP500` (S&P 500 Index)
    * `DGS10` (10-Year Treasury Yield)

## Methodology
1.  **Data Preprocessing**: Calculate log-returns to ensure time-series stationarity and create interaction terms (e.g., `VIX_x_PostCovid`) to test for structural breaks.
2.  **Machine Learning (Feature Selection)**: Utilize a cross-validated Lasso Regression (`scikit-learn`) to handle multicollinearity and algorithmically select the most statistically relevant variables.
3.  **Econometric Inference**: Apply ordinary least squares (OLS) regression via `statsmodels` on the selected features, utilizing HC3 robust standard errors to correct for heteroskedasticity.

## Repository Structure & Workflow
To prevent Git merge conflicts with Jupyter notebooks, this repository uses a modular pipeline. **Please do not edit files outside of your assigned task without coordinating with the team.**

* `1_data_ingestion.py`: Pulls FRED API data, merges it with the local Kaggle CSV, and outputs `raw_data.csv`. *(Assigned to: Member 1)*
* `2_data_cleaning.py`: Handles missing values, calculates log-returns, generates dummy variables, and outputs `final_model_data.csv`. *(Assigned to: Member 2)*
* `3_lasso_model.ipynb`: Standardizes features, runs Lasso regression, and outputs the selected variables. *(Assigned to: Member 3)*
* `4_ols_inference.ipynb`: Runs statsmodels OLS on the selected features and generates summary tables. *(Assigned to: Member 4)*
* `5_visualizations.ipynb`: Contains all EDA plots and final charts for the presentation. *(Assigned to: Member 5)*

## Setup & Git Instructions (PyCharm)
1. **Clone the Repo:** Open PyCharm, select `Get from VCS` (or `Git -> Clone` from the top menu), and paste the GitHub repository URL.
2. **Install Packages:** Open the PyCharm terminal at the bottom and run:
   `pip install pandas pandas-datareader scikit-learn statsmodels matplotlib`
3. **Daily Workflow:** * **Pull:** Always click the blue "Update Project" arrow at the top right before starting work to get everyone's latest code.
   * **Branch:** Create a new branch for your task using the Git widget in the bottom right corner (e.g., `feature/data-cleaning`).
   * **Commit & Push:** Use the green checkmark at the top right to commit your work and push it to GitHub.
4. **Notebook Rule:** Always click **"Restart Kernel and Clear All Outputs"** in your Jupyter notebook before committing to prevent massive merge conflicts!
