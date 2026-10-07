# Correlated Monte Carlo Portfolio Simulation

## 📌 Project Overview
This repository features a quantitative finance model that applies Monte Carlo simulations to evaluate portfolio risk. Specifically, it uses **Cholesky Decomposition** to generate simulated asset returns that mathematically preserve the historical correlation matrix of the real-world assets.

*(Please refer to the attached PDF presentation in this repository for the business case and a visual breakdown of the scenarios).*

## 📊 Dataset & Asset Allocation
Market data is automatically retrieved via the `yfinance` API (2020–2024). The simulated portfolio consists of equities and commodities:
* **Apple (AAPL):** 20%
* **Coca-Cola (KO):** 20%
* **Tesla (TSLA):** 30%
* **Gold Futures (GC=F):** 30%

## ⚙️ Methodology & Technical Highlights
* **Data Engineering:** Automated fetching and preprocessing of time-series financial data using `pandas`.
* **Cholesky Decomposition:** Applied `numpy.linalg.cholesky` to the historical correlation matrix. This ensures the random variables generated for the Monte Carlo simulation respect the real-world co-movements of the assets, rather than assuming independent returns.
* **Statistical Distribution Fitting:** Utilized `scipy.stats` to fit and overlay a theoretical Normal Distribution curve onto the empirical histograms of both actual and simulated portfolio returns.

## 🚀 How to Run
The model is self-contained in a single Python script and requires no local CSV files.

1. Install the required dependencies:
   ```bash
   pip install yfinance pandas numpy matplotlib scipy
   ```
2. Run the simulation:
   ```bash
   python monte_carlo_portfolio.py
   ```
3. The script will output the historical vs. simulated correlation matrices to the console and generate a comparative histogram (`monte_carlo_distribution.png`).
