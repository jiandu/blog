---
layout: post
title: Stock Index Investment and Life Insurance Investment
permalink: /_posts/
---
Compare the following strategies: 

1. Strategy 1: invest in S&P 500 Index ETF. 
	* Dividend yield gain and capital gain; dividends are immediately reinvested
	* Both dividend yield and capital gain are subject to income tax; dividend tax is deducted at distribution (assume once a year) and capital gain tax is deducted at sale of asset (end of holding period)
	* An annual dividend yield of 2.46% is applied, based on average of 1988 to 2016
	* Tax rate is assumed to be 33%
	* Use SPY's ETF cost of 0.11%
2. Strategy 2: invest in VUL (Variable Universal Life Insurance) with the cap constraint
	* Assume a $1 million notional policy and maximum allowed deposits in the first four years and no deposit afterwards
	* Four yearly installment of $27,831, $27,831, $27,831, $25,500
	* Each year's capital gain percentage is capped at 11% and floored at 0%
	* Costs include: base Cost of Insurance (follow the sample schedule), policy expense of 120 per year, premium charge of 8% in the first year and 6% from the second year on 
3. Strategy 3: invest in VUL without the cap contrainst
	* Each year's capital gain percentage is S&P 500 index return subtracted by 5%, and floored at 0%
4. Strategy 4: a strategy that tries to DIY strategy 2 
	* Buy S&P 500 Index ETF and buy a bull call spread with 1-year maturity and roll every year (long ATM call and short 11% OTM call)
	* For simplicity, I assume 1-year interest rate of 1.5%, 1-year dividend yield of 2.46%, 1-year volatility of 15%
	* The call spread premium is approximated by BS formula: annual cost is 3.41% of S&P 500 notional given the above parameters

## Investment Horizon of 10-year
1950-2016, daily backtesting, 14253 samples 

**Measure**

Final asset value at the end of investment horizon divided by initial capital

**Time Series**
{% include image.html url="images/TimeSeries10Year.png" caption="" width="800" height="500" align="right" %}

**Summary Statistics**

| Percentiles |  ETF | VUL1 | VUL2 | ETF+BullSpread |
|------------:|-----:|-----:|-----:|---------------:|
|          0% | 0.74 | 0.91 | 0.85 |           0.93 |
|          1% | 0.89 | 1.01 | 0.92 |           0.99 |
|          5% | 1.07 | 1.10 | 1.00 |           1.04 |
|         10% | 1.14 | 1.15 | 1.07 |           1.08 |
|         25% | 1.34 | 1.23 | 1.23 |           1.13 |
|         50% | 1.69 | 1.32 | 1.47 |           1.18 |
|         75% | 2.17 | 1.42 | 1.81 |           1.24 |
|         90% | 2.46 | 1.52 | 2.04 |           1.30 |
|         95% | 2.82 | 1.58 | 2.16 |           1.34 |
|         99% | 3.16 | 1.66 | 2.42 |           1.38 |
|        100% | 3.30 | 1.73 | 2.93 |           1.43 |
|        Mean | 1.77 | 1.33 | 1.52 |           1.18 |
|         Vol | 1.77 | 1.33 | 1.52 |           1.18 |
|      Sharpe | 0.34 | 0.13 | 0.24 |           0.02 |

**Distributions**
{% include image.html url="images/Histogram10Year.png" caption="" width="800" height="500" align="right" %}

## Investment Horizon of 20-year
1950-2016, daily backtesting, 11737 samples 

**Time Series**
{% include image.html url="images/TimeSeries20Year.png" caption="" width="800" height="500" align="right" %}

**Summary Statistics**

| Percentiles |   ETF | VUL1 | VUL2 | ETF+BullSpread |
|------------:|------:|-----:|-----:|---------------:|
|          0% |  1.60 | 1.42 | 1.15 |           1.02 |
|          1% |  1.71 | 1.61 | 1.40 |           1.10 |
|          5% |  1.85 | 1.76 | 1.65 |           1.17 |
|         10% |  1.96 | 1.87 | 1.88 |           1.22 |
|         25% |  2.30 | 2.12 | 2.49 |           1.34 |
|         50% |  3.22 | 2.40 | 3.13 |           1.46 |
|         75% |  4.74 | 2.73 | 3.85 |           1.61 |
|         90% |  7.13 | 2.97 | 4.84 |           1.72 |
|         95% |  9.05 | 3.11 | 5.65 |           1.78 |
|         99% | 10.38 | 3.39 | 6.65 |           1.91 |
|        100% | 11.20 | 3.69 | 7.84 |           2.04 |
|        Mean |  3.91 | 2.42 | 3.27 |           1.47 |
|         Vol |  3.91 | 2.42 | 3.27 |           1.47 |
|      Sharpe |  0.66 | 0.44 | 0.59 |           0.08 |

**Distributions**
{% include image.html url="images/Histogram20Year.png" caption="" width="800" height="500" align="right" %}


## Investment Horizon of 30-year
1950-2016, daily backtesting, 9210 samples 

**Time Series**
{% include image.html url="images/TimeSeries30Year.png" caption="" width="800" height="500" align="right" %}

**Summary Statistics**

| Percentiles |   ETF | VUL1 |  VUL2 | ETF+BullSpread |
|------------:|------:|-----:|------:|---------------:|
|          0% |  3.92 | 2.39 |  2.96 |           1.18 |
|          1% |  4.35 | 2.74 |  3.36 |           1.29 |
|          5% |  4.65 | 3.09 |  3.70 |           1.41 |
|         10% |  5.10 | 3.34 |  3.97 |           1.50 |
|         25% |  5.74 | 3.79 |  5.03 |           1.65 |
|         50% |  8.47 | 4.50 |  7.06 |           1.89 |
|         75% | 11.27 | 5.08 |  8.77 |           2.07 |
|         90% | 13.52 | 5.43 |  9.90 |           2.18 |
|         95% | 14.46 | 5.64 | 10.60 |           2.25 |
|         99% | 15.40 | 6.03 | 11.85 |           2.37 |
|        100% | 16.32 | 6.77 | 14.22 |           2.62 |
|        Mean |  8.65 | 4.43 |  7.00 |           1.86 |
|         Vol |  8.65 | 4.43 |  7.00 |           1.86 |
|      Sharpe |  0.82 | 0.65 |  0.78 |           0.16 |

**Distributions**
{% include image.html url="images/Histogram30Year.png" caption="" width="800" height="500" align="right" %}
