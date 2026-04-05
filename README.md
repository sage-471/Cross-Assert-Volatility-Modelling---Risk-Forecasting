# Cross-Asset Volatility Modeling & Risk Forecasting

> **Quant Finance / Risk Modeling Project**  
> Python-based analysis of volatility clustering, conditional variance, tail risk, and crisis-period market behavior across major U.S. equities.

---

## Overview

This project investigates the behavior of **financial market volatility** across multiple sectors using **daily equity return data** from **2000 to 2024**. The analysis focuses on how risk evolves over time, how volatility behaves during market stress periods, and how conditional variance models can be used to better understand and forecast financial risk.

Rather than treating volatility as constant, this project models it as a **dynamic and persistent process**, reflecting one of the most important stylized facts in financial time series: **volatility clustering**.

The study combines **descriptive statistics**, **rolling risk metrics**, **GARCH-family models**, and **portfolio-level tail risk measures** to evaluate the behavior of returns and volatility across a diversified set of large-cap U.S. equities.

---

## Objective

The primary goal of this project is to answer the following question:

> **How does volatility behave across major equity sectors, and to what extent can time-series volatility models capture and forecast conditional market risk?**

This project was designed to bridge **data science**, **econometrics**, and **quantitative finance**, with practical relevance to:

- **Risk management**
- **Portfolio construction**
- **Volatility forecasting**
- **Stress testing**
- **Market regime analysis**

---

## Asset Universe

The analysis uses daily adjusted closing prices for the following U.S. equities:

| Ticker | Company | Sector |
|--------|---------|--------|
| JPM | JPMorgan Chase & Co. | Financials |
| XOM | Exxon Mobil Corp. | Energy |
| GE | General Electric Co. | Industrials |
| KO | Coca-Cola Co. | Consumer Staples |
| IBM | IBM | Technology |
| DIS | Walt Disney Co. | Consumer Discretionary |

This cross-sector structure allows for comparison of how volatility behaves across industries under both normal and stressed market conditions.

---

## Time Period

**Sample Period:** 2000 – 2024

This time horizon captures several major market regimes and stress events, including:

- **Dot-com aftermath**
- **2008 Global Financial Crisis**
- **COVID-19 market shock**
- **Post-pandemic tightening / inflation regime**

These periods provide a useful backdrop for examining how volatility reacts to systemic shocks and whether those effects persist differently across sectors.

---

## Methodology

### 1. Data Collection
Historical daily price data was retrieved using:

- `yfinance`

### 2. Return Construction
Daily **log returns** were calculated as:

```math
r_t = \ln\left(\frac{P_t}{P_{t-1}}\right)
```

Using log returns makes the series more appropriate for statistical modeling and aligns with standard practice in quantitative finance.

### 3. Exploratory Data Analysis
Each return series was evaluated using:

- Mean return
- Standard deviation
- Skewness
- Kurtosis
- Return distribution visualizations

This helps identify key stylized facts such as:

- **Fat tails**
- **Asymmetry**
- **Non-normality**
- **Extreme market moves**

### 4. Rolling Volatility Analysis
To visualize how risk evolves over time, the project computes **60-day rolling volatility** for each asset.

This allows us to observe:

- Volatility clustering
- Crisis-driven spikes
- Regime shifts
- Persistence in market uncertainty

### 5. Conditional Volatility Modeling
The project fits **Student-t GARCH(1,1)** models to estimate time-varying conditional variance:

```math
\sigma_t^2 = \omega + \alpha \varepsilon_{t-1}^2 + \beta \sigma_{t-1}^2
```

These models are used to evaluate whether volatility shocks are:

- **Persistent**
- **Mean-reverting**
- **Responsive to new information**

### 6. Portfolio Risk Layer
The project extends beyond single-asset volatility and includes:

- **1-day 99% Value at Risk (VaR)**
- **Expected Shortfall (ES)**
- **Dynamic optimized portfolio weights**
- **Cross-asset volatility spillover interpretation**

---

## Key Questions Explored

This project investigates the following:

- Do different sectors exhibit different volatility dynamics?
- Which equities experience the most persistent volatility shocks?
- How do crisis periods alter the structure of market risk?
- Can conditional volatility models capture the changing nature of financial uncertainty?
- What do rolling and model-based volatility estimates reveal about market regimes?
- How does sector composition affect portfolio-level tail risk?

---

## Tools & Libraries

This project was built in **Python** using the following libraries:

- `pandas`
- `numpy`
- `matplotlib`
- `scipy`
- `yfinance`
- `arch`
- `cvxpy`
- `jupyter`

---

## Project Structure

```bash
Cross-Assert-Volatility-Modelling---Risk-Forecasting/
│
├── figures/
├── notebooks/
├── README.md
└── requirements.txt
```

> You can expand this structure later by separating reusable logic into a `src/` folder.

---

## Selected Results

### Daily Log Returns
Daily return series fluctuate around zero, but volatility is clearly **time-varying**, with visible turbulence during the **2008 Global Financial Crisis** and the **2020 COVID-19 shock**.

<img width="993" height="441" alt="Daily Log Returns" src="https://github.com/user-attachments/assets/8cbe5668-9136-4c83-8bd9-d56964d3e1e2" />

### Descriptive Statistics
Higher-order moments reveal that the return distributions are **non-Gaussian**, with evidence of **negative skewness** and **excess kurtosis** across several names.

<img width="657" height="307" alt="Descriptive Statistics" src="https://github.com/user-attachments/assets/3f13009d-bbee-4d84-aef7-22012550332c" />

### Skewness of Log Returns
Negative skewness in names such as **JPM**, **GE**, and **DIS** suggests that downside shocks are more extreme than upside moves.

<img width="989" height="590" alt="Skewness of Log Returns" src="https://github.com/user-attachments/assets/3aa31fd8-24b3-44f0-a302-d58572a24b14" />

### Kurtosis of Log Returns
All assets exhibit **fat tails**, meaning extreme return events occur more frequently than predicted under a normal distribution.

<img width="989" height="590" alt="Kurtosis of Log Returns" src="https://github.com/user-attachments/assets/91cadeb4-0fa3-4900-8742-79fa3007f753" />

### 60-Day Rolling Volatility
Rolling volatility highlights clear **volatility clustering**, especially during major crisis periods.

<img width="990" height="441" alt="60 Day Rolling Volatility" src="https://github.com/user-attachments/assets/dc8ec9cc-452f-4738-a1f1-cf74ba1cb4a0" />

### GARCH Conditional Volatility
#### JPM Conditional Volatility
<img width="977" height="451" alt="JPM Conditional Volatility" src="https://github.com/user-attachments/assets/014b387a-f7a2-4d52-9972-a6d5095d2f60" />

#### GE Conditional Volatility
<img width="968" height="451" alt="GE Conditional Volatility" src="https://github.com/user-attachments/assets/8de8bbac-a6a3-45ba-a3e7-aeb28af3b4b7" />

#### KO Conditional Volatility
<img width="968" height="451" alt="KO Conditional Volatility" src="https://github.com/user-attachments/assets/dac831c5-08a8-4fde-a997-4e96da1a640d" />

### Cross-Asset Volatility Spillovers
The spillover matrix suggests that **financials** and **energy** are stronger transmitters of volatility than more defensive sectors.

<img width="567" height="146" alt="Volatility Spillovers" src="https://github.com/user-attachments/assets/062096e8-45ab-438d-8240-f908dbe429e4" />

---

## Key Findings

### 1. Volatility is clearly time-varying
Across all assets, volatility is **not constant**. Instead, it appears in bursts, with high-volatility periods followed by further high-volatility periods.

This confirms the presence of **volatility clustering**, one of the most important stylized facts in financial markets.

### 2. Crisis periods produce sharp and persistent volatility spikes
Periods such as **2008** and **2020** show pronounced increases in both rolling and model-implied volatility, indicating strong market-wide stress transmission.

### 3. Sector behavior differs meaningfully
Certain sectors appear more sensitive to macroeconomic and systemic shocks than others, suggesting that sector composition materially affects portfolio risk exposure.

### 4. GARCH models capture conditional risk more realistically than static measures
Compared with unconditional standard deviation, conditional variance models better reflect the changing nature of market risk over time.

### 5. Portfolio tail risk remains material even under diversification
The estimated **VaR** and **Expected Shortfall** indicate that diversification reduces idiosyncratic exposure, but systemic drawdown risk remains meaningful during crisis regimes.

---

## Portfolio Risk Snapshot

### 1-Day 99% Risk Measures

- **VaR:** `-1.53%`
- **Expected Shortfall:** `-1.76%`

### Dynamic Optimized Portfolio Weights

| Asset | Weight |
|--------|--------|
| JPM | 9.5% |
| XOM | 24.1% |
| GE | 6.7% |
| KO | 35.0% |
| IBM | 9.0% |
| DIS | 15.7% |

### Interpretation

- **KO** receives the largest allocation due to its relatively defensive volatility profile.
- More cyclical names receive lower weight, improving **risk-adjusted resilience**.
- Diversification helps, but does not fully remove exposure to **systemic shocks**.

---

## Financial Interpretation

From a quantitative finance perspective, the findings of this project reinforce several important ideas:

- **Market risk is regime-dependent**
- **Volatility is persistent**
- **Risk is not evenly distributed across time**
- **Sector diversification does not eliminate crisis sensitivity**
- **Tail-aware risk measures are more realistic than Gaussian assumptions**

These dynamics are highly relevant in practical settings such as:

- Portfolio risk monitoring
- Position sizing
- Volatility forecasting
- VaR / Expected Shortfall estimation
- Trading strategy risk overlays

---

## Limitations

While this project provides useful insight into volatility dynamics, several limitations should be noted:

- The analysis is based on **daily close-to-close returns**, which do not capture intraday volatility behavior.
- The models are primarily **univariate**, meaning they do not explicitly model cross-asset spillovers in a full multivariate framework.
- Structural breaks and regime shifts may affect parameter stability across long sample periods.
- Equity-only analysis limits broader generalization to multi-asset portfolios.

These limitations also create opportunities for future expansion.

---

## Future Improvements

Potential next steps include:

- Implementing **EGARCH** and **GJR-GARCH** models
- Forecasting **1-day ahead volatility**
- Comparing **realized vs forecasted volatility**
- Adding **backtesting for VaR breaches**
- Extending the analysis to **portfolio-level conditional covariance modeling**
- Incorporating **macro variables** or **market indices**
- Modeling **cross-asset volatility spillovers** with richer multivariate methods

---

## Why This Project Matters

Volatility sits at the center of modern finance.

Whether in **risk management**, **systematic investing**, **derivatives**, or **quantitative research**, understanding how volatility behaves is essential to understanding how markets behave.

This project demonstrates the application of **data science and econometric modeling** to a real financial problem:  
**measuring and interpreting dynamic market risk.**

---

## Author

**Alex Manjoro**  
MS in Data Science | Aspiring Quant Analyst | CFA Level I Candidate

If you’d like to connect or discuss the project, feel free to fork the repository or reach out.

---

## License

This project is open-source and available under the **MIT License**.
