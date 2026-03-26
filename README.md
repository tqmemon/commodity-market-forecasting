# Metal Price Dynamics: Testing the "Broken Haven" & Silver Catch-up Theories
This project investigates the evolving relationship between precious metals and macroeconomic indicators. We are testing two specific theories: whether gold has lost its "safe-haven" status post-2022, and whether silver prices are primarily driven by gold price parity (the "catch-up" theory).

Developed for ECON 323 at the University of British Columbia.

## 1. The "Broken Haven" Investigation (Gold)

Historically, gold prices rise during geopolitical tension and high inflation. However, recent trends suggest this relationship may be decoupling.

Methodology: Multivariate LASSO Regression.

The Experiment: Build and cross-validate a model using pre-2022 data. We will then use this model to predict post-2022 prices; significant variance will serve as evidence that the "safe-haven" mechanics have fundamentally changed.

Key Variables: Real Rates (Bond Yields - CPI), USD Exchange Rate (DEXUSEU), Geopolitical Risk Index, and Market Volatility (VIX).

## 2. The Silver "Catch-up" Theory

This theory suggests that when the Gold/Silver ratio becomes overextended, silver prices spike to bridge the gap.

Methodology: Random Forest.

The Experiment: We are using a Random Forest ensemble to determine the "Feature Importance" of silver price predictors. If Gold price is identified as the strongest predictor over industrial demand indicators, it provides quantitative support for the catch-up theory.

Key Variables: Gold prices, Industrial Demand controls (Renewables/Battery data), and Investment Demand (ETF flows).

### Data Sources

We are integrating disparate datasets to ensure a robust analysis:

Financial Data: Federal Reserve Economic Data (FRED) for VIX, CPI, and Treasury yields.

Commodity Data: Kaggle/Bloomberg for historical Gold/Silver closing prices.

Geopolitical Data: Geopolitical Risk Index (GPR).

### Team Roadmap

Phase 1: Data cleaning and alignment of time-series frequencies (Daily vs. Monthly).

Phase 2: Running the LASSO model to isolate significant macroeconomic "Safe Haven" drivers.

Phase 3: Training the Random Forest to rank predictors for Silver price spikes.
