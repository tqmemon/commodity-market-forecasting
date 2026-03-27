# The "Broken Haven" Hypothesis

## 1. Core Research Question
Did gold prices behave differently during or after crisis periods?
Normally, when market stress is high, investors flock to safe-haven assets like gold. We are testing the "Broken Haven" hypothesis to see if this relationship broke down during and after the COVID-19 pandemic, and whether that change was temporary or a structural shift.

To make the economic analysis stronger, we are also going to run the exact same model using the 10-year US Treasury note yield as the dependent variable to see if all safe havens broke down, or just gold.

## 2. Variables & Data Sources
We need to merge a local Kaggle dataset with macroeconomic data pulled directly from the FRED API.

### Dependent Variables:

Gold Price (Closing Price) -> Will convert to Log-Returns for stationarity.

US 10-Year Treasury Note Yield (Benchmark safe-haven)

###  Independent Variables:

VIX: Measures overall market volatility/stress. (High VIX usually = High Gold).

Geopolitical Risk Index: Shapes investor expectations.

USD/EUR Exchange Rate: Demand for gold depends on USD.

Federal Funds Rate (Interest Rates): Determines money supply.

S&P 500 Prices: Baseline market performance.

Data Links: * Gold & Geopolitical Risk (Kaggle)

FRED Series: VIXCLS (VIX), DEXUSEU (USD), DFF (Rates), SP500 (Market), DGS10 (Treasuries).

## 3. Methodology
We are splitting the data into three periods: Pre-COVID (Training), COVID, and Post-COVID (Testing).
To prove a structural break, we are using interaction terms (e.g., VIX × Post-COVID dummy).

Machine Learning (sklearn): Run a Lasso Regression to handle feature selection and weed out multicollinearity (e.g., if USD and Interest Rates are too highly correlated).

Econometrics (statsmodels): Take the variables that survive the Lasso penalty and run an OLS regression using robust standard errors (HC3) to fix any heteroskedasticity. This gives us the p-values and coefficients needed for the economic interpretation.

## 4. GitHub Workflow & File Structure
To avoid GitHub merge conflicts (which happen constantly if multiple people edit the same Jupyter notebook), we are strictly separating the pipeline into 5 different files. Do not edit someone else's file without checking with them first.

1_data_ingestion.py: Connects to FRED, loads Kaggle, and saves raw_data.csv.

2_data_cleaning.py: Calculates log-returns, creates dummy variables, drops NaNs, and saves final_model_data.csv.

3_lasso_model.ipynb: Loads the final CSV, standardizes variables, runs LassoCV, and outputs the selected features.

4_ols_inference.ipynb: Runs the statsmodels OLS on the selected features and generates the summary tables.

5_visualizations.ipynb: Holds all EDA plots, scatter plots, and time-series charts for the presentation.

## 5. Task Assignments
Member 1 (Data Gatherer): Write 1_data_ingestion.py. Get the API pulls working and merge the dates perfectly.

Member 2 (Data Cleaner): Write 2_data_cleaning.py. Handle the stationarity (log-returns) and build the COVID/Post-COVID interaction terms.

Member 3 (ML Modeler): Own 3_lasso_model.ipynb. Standardize the data, find the optimal alpha, and determine which variables matter.

Member 4 (Econometrician): Own 4_ols_inference.ipynb. Run the statsmodels regressions, apply HC3 standard errors, and interpret the economic meaning of the coefficients.

Member 5 (Visualizer / PM): Own 5_visualizations.ipynb. Create the EDA (boxplots, heatmaps) and compile the final findings into the slide deck.
