# Automated Stochastic DCF Valuation Engine

## Overview
Traditional Discounted Cash Flow (DCF) models suffer from a fundamental vulnerability: extreme sensitivity to single-point estimates. A fractional adjustment in a terminal growth rate or discount rate can wildly skew intrinsic value, creating a false sense of precision. 

This project engineers a programmatic valuation engine in Python that replaces static assumptions with probability distributions. By automating fundamental data ingestion and running a 10,000-iteration Monte Carlo simulation, this model quantifies risk parameters and establishes probability-weighted intrinsic value confidence intervals.

## Core Architecture
1. **Automated Data Ingestion:** Hooks into the Yahoo Finance API to dynamically pull a target equity's historical SEC filings, calculating the exact historical mean and variance (standard deviation) of revenue growth and operating margins.
2. **Dynamic Cost of Capital:** Automatically calculates the Weighted Average Cost of Capital (WACC) by fetching the live 10-Year U.S. Treasury Yield and computing the Cost of Equity via the Capital Asset Pricing Model (CAPM).
3. **Monte Carlo Simulation:** Executes 10,000 randomized DCF pathways, adjusting growth, margins, and discount rates within their calculated probability distributions to simulate thousands of macroeconomic realities.

## Real-World Application & Value Investing
The model is built to strip away market sentiment and evaluate businesses strictly on expected future free cash flow. 
* **Growth/Tech Premiums:** When applied to equities like Microsoft, the model correctly isolates the massive forward-looking growth premiums currently priced in by the market.
* **Value Identification:** When applied to mature, cash-flowing infrastructure or healthcare equities (e.g., Cisco, Verizon), the engine maps a highly constrained risk distribution, effectively identifying true Margin of Safety entry points.

## Technologies Used
* **Language:** Python
* **Libraries:** `pandas` (Data manipulation), `numpy` (Vectorized probability distributions), `yfinance` (Fundamental data extraction), `seaborn` / `matplotlib` (Distribution visualizations).

---
*Disclaimer: All code and outputs are research-grade and for educational purposes only. This is not financial advice.*
