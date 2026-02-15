#   Cross-Asset Volatility Modeling & Risk Forecasting  
## Conditional Risk, Tail Behavior & Crisis Dynamics (2000–2024)

---

## Aim

This project analyzes the time-varying volatility and tail risk characteristics of a diversified portfolio of U.S. blue-chip equities:

- **JPM** (Financials)  
- **XOM** (Energy)  
- **GE** (Industrials)  
- **KO** (Consumer Staples)  
- **IBM** (Technology)  
- **DIS** (Consumer Discretionary)  

The study focuses on:

- Stylized facts of financial returns  
- Higher-order moments (skewness & kurtosis)  
- Volatility clustering  
- GARCH-based conditional volatility modeling  
- Crisis-period behavior (2008 Financial Crisis & 2020 COVID-19)  
- Portfolio-level risk forecasting  

---

# 1️⃣ Data & Stylized Facts

## Daily Log Returns

<img width="993" height="441" alt="image" src="https://github.com/user-attachments/assets/8cbe5668-9136-4c83-8bd9-d56964d3e1e2" />


### Interpretation

Across all six equities:

- Returns fluctuate around zero → consistent with **weak-form efficiency**
- No persistent drift in daily returns
- Clear bursts of high volatility in:
  - 2008 (Global Financial Crisis)
  - 2020 (COVID-19 shock)

### Stock-Level Observations

- **JPM**: Large return swings during 2008 reflect financial sector fragility.
- **GE**: Pronounced volatility during crisis periods, consistent with cyclical industrial exposure.
- **XOM**: Elevated volatility during oil shocks and COVID demand collapse.
- **DIS**: COVID shock particularly visible due to shutdown of theme parks and media disruption.
- **KO**: Comparatively stable; smaller magnitude shocks.
- **IBM**: Moderate volatility, less extreme than financials or energy.

### Stylized Fact Confirmed:
Returns are approximately stationary in mean but exhibit **time-varying variance**.

---

## Descriptive Statistics

<img width="657" height="307" alt="Descriptive statistics" src="https://github.com/user-attachments/assets/3f13009d-bbee-4d84-aef7-22012550332c" />


| Asset | Key Insight |
|--------|------------|
| JPM | High volatility, negative skew |
| XOM | Cyclical volatility tied to energy markets |
| GE  | Elevated variance, crisis-sensitive |
| KO  | Lower volatility, defensive |
| IBM | Moderate risk profile |
| DIS | Significant downside tail risk |

### Interpretation

- Mean returns ≈ 0 → Daily returns are small relative to volatility.
- Standard deviations vary significantly across sectors.
- All assets show **excess kurtosis (>3)** → Heavy-tailed distributions.

This confirms that **normal distribution assumptions underestimate extreme events.**

---

# 2️⃣ Higher-Order Moments

## Skewness of Log Returns

<img width="989" height="590" alt="skewness of log returns" src="https://github.com/user-attachments/assets/3aa31fd8-24b3-44f0-a302-d58572a24b14" />


### Interpretation by Stock

- **JPM, GE, DIS** → Negative skewness  
  - Greater probability of extreme downside shocks.
  - Financial and cyclical sectors show asymmetric risk.

- **KO** → Near symmetric distribution  
  - Defensive consumption reduces tail imbalance.

Negative skew implies that bad days are more extreme than good days.  
This matters for risk managers more than it does for optimists.

---

## Kurtosis of Log Returns

<img width="989" height="590" alt="kurtosis of log returns" src="https://github.com/user-attachments/assets/91cadeb4-0fa3-4900-8742-79fa3007f753" />


All assets exhibit **leptokurtosis (fat tails).**

### What “Fat Tails” Mean

- Extreme events occur more frequently than Gaussian theory predicts.
- Risk models assuming normality severely underestimate tail losses.
- Justifies use of **Student-t innovations in GARCH models**.

### Sector Interpretation

- **Financials (JPM)** and **Industrials (GE)** show the heaviest tails.
- **Energy (XOM)** reflects commodity-driven shock sensitivity.
- **KO** shows relatively thinner tails but still above Gaussian baseline.

Markets do not whisper risk — they occasionally shout it.

---

# 3️⃣ Rolling Volatility (60-Day)

<img width="990" height="441" alt="60 day rolling volatility" src="https://github.com/user-attachments/assets/dc8ec9cc-452f-4738-a1f1-cf74ba1cb4a0" />


### Observations

- Major spikes during:
  - 2008 Financial Crisis
  - March 2020 COVID crash
- Volatility clustering clearly visible.

### Stock-Level Dynamics

- **JPM**: Extreme spike in 2008 → banking system instability.
- **GE**: Sharp surge in both crises → cyclical sensitivity.
- **XOM**: Volatility surge during oil price collapse (2020).
- **DIS**: COVID volatility due to operational shutdown.
- **KO**: Smallest relative volatility spikes → defensive nature.
- **IBM**: Moderate clustering but less severe than financials.

Rolling volatility confirms that risk is **time-dependent**.

---

# 4️⃣ GARCH(1,1) Conditional Volatility

Models estimated using Student-t GARCH(1,1).

---

## JPM Conditional Volatility
<img width="977" height="451" alt="JPM conditional volatility with crisis events" src="https://github.com/user-attachments/assets/014b387a-f7a2-4d52-9972-a6d5095d2f60" />


### Interpretation

- Massive spike in 2008.
- High persistence (α + β close to 1).
- Volatility remains elevated long after initial shock.

Financial sector volatility exhibits strong memory.

---

## GE Conditional Volatility

<img width="968" height="451" alt="GE Conditional volatilty with crisis events" src="https://github.com/user-attachments/assets/8de8bbac-a6a3-45ba-a3e7-aeb28af3b4b7" />


### Interpretation

- Significant crisis amplification.
- Industrial cyclicality reflected in conditional variance.
- Elevated response to macroeconomic contractions.

GE behaves like a macro beta amplifier.

---

## KO Conditional Volatility

<img width="968" height="451" alt="KO Conditional volatility with crisis events" src="https://github.com/user-attachments/assets/dac831c5-08a8-4fde-a997-4e96da1a640d" />


### Interpretation

- Smaller volatility spikes.
- Faster reversion to baseline variance.
- Consumer staples show defensive volatility structure.

KO acts as portfolio stabilizer.

---

# 5️⃣ Cross-Asset Volatility Spillovers

Lagged spillover matrix (squared residuals):
<img width="567" height="146" alt="image" src="https://github.com/user-attachments/assets/062096e8-45ab-438d-8240-f908dbe429e4" />


- Financial and energy sectors transmit volatility.
- Defensive sectors absorb more than they transmit.

This confirms systemic interconnectedness across sectors.

---

# 6️⃣ Portfolio Risk Forecasting

## 1-Day 99% Risk Measures

- **VaR:** -1.53%  
- **Expected Shortfall:** -1.76%

### Interpretation

- 1% probability of losing ≥ 1.53% in a day.
- If breached, average loss ≈ 1.76%.

Expected Shortfall exceeding VaR confirms fat-tail exposure.

---

## Dynamic Optimized Portfolio Weights

| Asset | Weight |
|--------|--------|
| JPM | 9.5% |
| XOM | 24.1% |
| GE | 6.7% |
| KO | 35.0% |
| IBM | 9.0% |
| DIS | 15.7% |

### Interpretation

- Largest allocation to **KO** → defensive stability.
- Reduced exposure to GE → high volatility.
- Balanced exposure to cyclical and stable sectors.

Dynamic covariance allocation favors **risk-adjusted resilience**.

---

# 7️⃣ Cumulative Portfolio Returns

Cumulative returns show:

- Long-term positive drift.
- Severe drawdowns in 2008 & 2020.
- Recovery consistent with equity risk premium.

Portfolio diversification reduces catastrophic loss but does not eliminate systemic risk.

---

# 🔍 Key Investor Takeaways

- Returns are non-Gaussian and fat-tailed.
- Volatility clusters and persists.
- Financials amplify systemic shocks.
- Energy reflects commodity cycle risk.
- Consumer staples provide defensive ballast.
- Expected Shortfall is superior to VaR for tail risk.
- Dynamic volatility modeling improves risk forecasting.

---

# 🛠 Tech Stack

- Python  
- Pandas  
- NumPy  
- yfinance  
- Matplotlib / Seaborn  
- arch (GARCH modeling)  
- SciPy  

---

# 📚 Conclusion
# Conclusion

This study examined the dynamic risk characteristics of a diversified portfolio of U.S. blue-chip equities—JPM (Financials), XOM (Energy), GE (Industrials), KO (Consumer Staples), IBM (Technology), and DIS (Consumer Discretionary)—over the 2000–2024 period. The objective was to evaluate the statistical properties of returns, model conditional volatility, and assess portfolio-level tail risk during both stable and crisis regimes.

The empirical results confirm several well-documented stylized facts of financial time series. First, daily log returns are approximately stationary in mean but exhibit time-varying variance. Second, return distributions are non-normal, with statistically significant excess kurtosis and, in several cases, negative skewness. These characteristics indicate fat-tailed and asymmetric distributions, implying that extreme downside events occur more frequently than predicted by a Gaussian framework. From a risk management perspective, this finding invalidates reliance on traditional mean-variance models that assume normality.

Volatility clustering is clearly observable across all assets, particularly during the 2008 Global Financial Crisis and the 2020 COVID-19 shock. Financials (JPM) and cyclicals (GE, DIS) display pronounced volatility amplification during systemic stress, reflecting their sensitivity to macroeconomic contraction and liquidity shocks. Energy (XOM) volatility is strongly influenced by commodity price dynamics and demand disruptions. In contrast, Consumer Staples (KO) demonstrates comparatively lower volatility spikes and faster mean reversion, reinforcing its defensive profile within diversified portfolios.

The GARCH(1,1) framework with Student-t innovations effectively captures the persistence and clustering of volatility. The estimated parameters suggest high volatility persistence (α + β close to unity), consistent with long memory in conditional variance. The use of heavy-tailed error distributions materially improves model fit and more accurately reflects empirical return behavior. These results support the application of conditional volatility models for forward-looking risk estimation and stress analysis.

At the portfolio level, Value-at-Risk (VaR) and Expected Shortfall (ES) estimates confirm meaningful exposure to tail risk. The higher magnitude of Expected Shortfall relative to VaR highlights the severity of losses conditional on breach events, underscoring the importance of coherent risk measures in portfolio oversight. Dynamic covariance optimization tilts allocations toward lower-volatility assets—most notably KO—while reducing exposure to higher-beta cyclicals. This allocation structure enhances risk-adjusted stability without eliminating systematic drawdown exposure.

Cross-asset spillover analysis indicates that financial and energy sectors act as primary transmitters of volatility, reinforcing the interconnected nature of modern capital markets. Sector diversification mitigates idiosyncratic risk but does not fully insulate portfolios from systemic shocks.

Overall, the findings demonstrate that equity markets are characterized by persistent, regime-dependent volatility and heavy-tailed return distributions. Effective portfolio construction and risk management therefore require dynamic modeling frameworks that incorporate time-varying covariance structures and non-Gaussian innovations. Investors who account for these structural features are better positioned to manage drawdowns, allocate capital efficiently, and maintain resilience across economic cycles.

