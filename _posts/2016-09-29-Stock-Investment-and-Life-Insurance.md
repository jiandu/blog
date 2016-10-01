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
	* Buy S&P 500 Index ETF and buy an ATM put and sell an 11%-OTM call with 1-year maturity and roll the options every year
	* For simplicity, I assume 1-year interest rate of 1.5%, 1-year dividend yield of 2.46%, 1-year volatility of 15%
	* The long put-short call premium is approximated by Black-Sholes formula: annual cost is 4.35% of S&P 500 notional given the above parameters

## Investment Horizon of 10-year
1950-2016, daily backtesting, 14253 samples 

**Measure**

Final asset value at the end of investment horizon divided by initial capital

**Time Series**
{% include image.html url="images/TimeSeries10Year.png" caption="" width="800" height="500" align="right" %}

**Summary Statistics**

| Percentiles |  ETF | IUL1 | IUL2 | CoverCall |
|------------:|-----:|-----:|-----:|----------:|
|          0% | 0.74 | 0.91 | 0.85 |      0.96 |
|          1% | 0.89 | 1.01 | 0.92 |      1.05 |
|          5% | 1.07 | 1.10 | 1.00 |      1.11 |
|         10% | 1.14 | 1.15 | 1.07 |      1.16 |
|         25% | 1.34 | 1.23 | 1.23 |      1.22 |
|         50% | 1.69 | 1.32 | 1.47 |      1.29 |
|         75% | 2.17 | 1.42 | 1.81 |      1.37 |
|         90% | 2.46 | 1.52 | 2.04 |      1.46 |
|         95% | 2.82 | 1.58 | 2.16 |      1.51 |
|         99% | 3.16 | 1.66 | 2.42 |      1.58 |
|        100% | 3.30 | 1.73 | 2.93 |      1.64 |
|        Mean | 1.77 | 1.33 | 1.52 |      1.30 |
|         Vol | 0.54 | 0.14 | 0.37 |      0.12 |
|      Sharpe | 1.13 | 1.18 | 0.99 |      1.20 |

**Distributions**
{% include image.html url="images/Histogram10Year.png" caption="" width="800" height="500" align="right" %}

## Investment Horizon of 20-year
1950-2016, daily backtesting, 11737 samples 

**Time Series**
{% include image.html url="images/TimeSeries20Year.png" caption="" width="800" height="500" align="right" %}

**Summary Statistics**

| Percentiles |   ETF | IUL1 | IUL2 | CoverCall |
|-------------|------:|-----:|-----:|----------:|
|          0% |  1.60 | 1.42 | 1.15 |      1.22 |
|          1% |  1.71 | 1.61 | 1.40 |      1.33 |
|          5% |  1.85 | 1.76 | 1.65 |      1.46 |
|         10% |  1.96 | 1.87 | 1.88 |      1.58 |
|         25% |  2.30 | 2.12 | 2.49 |      1.78 |
|         50% |  3.22 | 2.40 | 3.13 |      2.03 |
|         75% |  4.74 | 2.73 | 3.85 |      2.28 |
|         90% |  7.13 | 2.97 | 4.84 |      2.53 |
|         95% |  9.05 | 3.11 | 5.65 |      2.68 |
|         99% | 10.38 | 3.39 | 6.65 |      2.93 |
|        100% | 11.20 | 3.69 | 7.84 |      3.22 |
|        Mean |  3.91 | 2.42 | 3.27 |      2.04 |
|         Vol |  2.10 | 0.42 | 1.16 |      0.36 |
|      Sharpe |  1.22 | 2.58 | 1.67 |      1.92 |

**Distributions**
{% include image.html url="images/Histogram20Year.png" caption="" width="800" height="500" align="right" %}


## Investment Horizon of 30-year
1950-2016, daily backtesting, 9210 samples 

**Time Series**
{% include image.html url="images/TimeSeries30Year.png" caption="" width="800" height="500" align="right" %}

**Summary Statistics**

| Percentiles |   ETF | IUL1 |  IUL2 | CoverCall |
|------------:|------:|-----:|------:|----------:|
|          0% |  3.92 | 2.39 |  2.96 |      1.72 |
|          1% |  4.35 | 2.74 |  3.36 |      2.02 |
|          5% |  4.65 | 3.09 |  3.70 |      2.45 |
|         10% |  5.10 | 3.34 |  3.97 |      2.73 |
|         25% |  5.74 | 3.79 |  5.03 |      3.23 |
|         50% |  8.47 | 4.50 |  7.06 |      3.84 |
|         75% | 11.27 | 5.08 |  8.77 |      4.29 |
|         90% | 13.52 | 5.43 |  9.90 |      4.64 |
|         95% | 14.46 | 5.64 | 10.60 |      4.87 |
|         99% | 15.40 | 6.03 | 11.85 |      5.28 |
|        100% | 16.32 | 6.77 | 14.22 |      6.07 |
|        Mean |  8.65 | 4.43 |  7.00 |      3.75 |
|         Vol |  3.25 | 0.81 |  2.23 |      0.74 |
|      Sharpe |  2.18 | 3.55 |  2.44 |      2.97 |

**Distributions**
{% include image.html url="images/Histogram30Year.png" caption="" width="800" height="500" align="right" %}
