📌 Project Overview
This project develops a cross-asset volatility and risk forecasting framework for a multi-asset equity portfolio using time-varying conditional volatility models.
Rather than relying on static historical risk estimates, the framework:
•	Models conditional volatility using GARCH(1,1) with Student-t innovations
•	Constructs a dynamic covariance matrix combining conditional volatilities and rolling correlations
•	Solves a conditional minimum-variance portfolio optimization
•	Produces conditional Value-at-Risk (VaR) and Expected Shortfall (ES) forecasts
•	Backtests VaR forecasts using formal statistical tests
The goal is to mirror how real-world quant risk systems respond to changing market regimes and tail risk.


**🧠 Financial Motivation****
Volatility, correlation, and tail risk are not constant over time. During market stress:
•	Volatility clusters
•	Cross-asset correlations increase
•	Tail losses become more frequent
Static covariance matrices systematically underestimate portfolio risk during such periods.
This project addresses that limitation by modeling time-varying risk explicitly and validating it statistically.

📊 Data
•	Assets: JPM, XOM, GE, KO, IBM, DIS
•	Asset class: U.S. equities (diversified across sectors)
•	Frequency: Daily
•	Period: 2000 – 2024
•	Source: Yahoo Finance (adjusted prices)

#Returns are calculated are computed as log returns

🧩 Methodology
1. Univariate Volatility Modeling
Each asset’s returns are modeled using a GARCH(1,1) process with Student-t innovations:
Student-t errors capture fat tails commonly observed in financial returns.
<img width="990" height="441" alt="image" src="https://github.com/user-attachments/assets/07887634-495f-4121-b83d-35c0531f022a" />

2. Model Diagnostics 
To validate model adequacy, the following diagnostics are applied:
•	Ljung–Box test (residuals): remaining autocorrelation
•	Ljung–Box test (squared residuals): remaining volatility clustering
•	ARCH-LM test: leftover conditional heteroskedasticity
•	Jarque–Bera test: distributional properties
These tests ensure the GARCH models are not only fitted, but econometrically sound.
<img width="523" height="216" alt="image" src="https://github.com/user-attachments/assets/b99acb18-6bc8-4c8c-a550-45b6f870e02c" />


4. Conditional Covariance Matrix
<img width="664" height="605" alt="image" src="https://github.com/user-attachments/assets/6bea0ff8-467e-4415-9fb9-9e76f8fcfca3" />


5. Portfolio Optimization
A long-only minimum-variance portfolio is solved using convex optimization:

6. Conditional Risk Forecasting
Using the conditional covariance matrix, the project computes:
•	Conditional portfolio volatility
•	1-day ahead Value-at-Risk (VaR)
•	1-day ahead Expected Shortfall (ES)
Both VaR and ES are derived under a Student-t distribution, consistent with the fitted volatility models.

7. VaR Backtesting
Forecast quality is evaluated using the Kupiec Unconditional Coverage Test, which tests whether the observed number of VaR breaches is statistically consistent with the chosen confidence level.
This step is critical: risk models must be evaluated, not just estimated.
<img width="1002" height="441" alt="image" src="https://github.com/user-attachments/assets/97fc82a6-147f-4619-872e-08c024962f6a" />

📈 Performance & Benchmarks
The conditional-risk portfolio is compared against:
•	An equal-weight benchmark
•	Rolling volatility and drawdown behavior
Key metrics reported:
•	Annualized return
•	Annualized volatility
•	Sharpe ratio
•	Maximum drawdown
•	VaR breach frequency
<img width="993" height="441" alt="image" src="https://github.com/user-attachments/assets/b79b3112-0e7e-496e-a05b-114684773b64" />


🛠️ Technologies Used
•	Python
•	arch (GARCH estimation)
•	statsmodels (statistical tests)
•	cvxpy (convex portfolio optimization)
•	yfinance (data ingestion)
•	matplotlib, pandas, numpy

🔍 Key Takeaways
•	Volatility and correlation are state-dependent
•	Conditional covariance improves tail-risk estimation
•	GARCH-based risk forecasts outperform static estimates during stress
•	VaR must be backtested to be credible
•	ES provides superior insight into extreme losses beyond VaR









