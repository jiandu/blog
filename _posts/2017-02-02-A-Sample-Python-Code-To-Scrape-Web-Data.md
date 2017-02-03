---
layout: post
title: A Sample Python Code To Scrape Web Data
permalink: /_posts/
---
Below is a sample Python code that downloads the historical stock price data and scrapes company summary and statistics information for all S&P 500 companies. The data source is Yahoo! Finance. The same technique can be used to obtain information from many other websites. The code was lastly tested on 2017-02-02. 

```python
import pandas_datareader as pdr
from datetime import datetime
import os
import urllib
import json
import pandas as pd
import re
import pyperclip

htmlfile = urllib.urlopen("http://data.okfn.org/data/core/s-and-p-500-companies/r/constituents.csv")
tickers = pd.read_csv(htmlfile)

df = pd.DataFrame()
for ticker in tickers['Symbol']:
    tmp = pdr.get_data_yahoo(symbols=ticker, start=datetime(2000, 1, 1), end=datetime(2017, 1, 1))
    tmp['ticker'] = ticker
    df = df.append(tmp)

columns = ['ticker', 'prev_close', 'open', 'day_range', 'year_range', 'volume', 'avg_volume', 
                                   'market_cap', 'beta', 'PE', 'EPS', 'div_yield', 'ex_div_date', 'target']
df_summary = pd.DataFrame(columns=columns)
ticker = 'ABT'
count = 0
for ticker in tickers.loc[:len(tickers),'Symbol']:
    #summary, statistics, profiles, financials
    url_summary = "https://finance.yahoo.com/quote/" + ticker
    url_stats = "https://finance.yahoo.com/quote/" + ticker + "/key-statistics"
    url_profile = "https://finance.yahoo.com/quote/" + ticker + "/profile"
    url_fin = "https://finance.yahoo.com/quote/" + ticker + "/financials"
    htmlfile = urllib.urlopen(url_summary)
    htmltext = htmlfile.read()
    regex = 'data-test=\"PREV_CLOSE-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    #pattern = re.compile(regex)
    previous_close = re.findall(regex, htmltext)[0]
    
    regex = 'data-test=\"OPEN-value\" data-reactid=\"[0-9]+\">(.+?)</td>' 
    open_price = re.findall(regex, htmltext)[0] 
    
    regex = 'data-test=\"DAYS_RANGE-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    day_range = re.findall(regex, htmltext)[0]
    
    regex = 'data-test=\"FIFTY_TWO_WK_RANGE-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    year_range = re.findall(regex, htmltext)[0]
    
    regex = 'data-test=\"TD_VOLUME-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    volume = re.findall(regex, htmltext)[0]
    
    regex = 'data-test=\"AVERAGE_VOLUME_3MONTH-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    avg_volume = re.findall(regex, htmltext)[0]
    
    regex = 'data-test=\"MARKET_CAP-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    market_cap = re.findall(regex, htmltext)[0]
    
    regex = 'data-test=\"BETA-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    beta = re.findall(regex, htmltext)[0]
    
    regex = 'data-test=\"PE_RATIO-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    PE = re.findall(regex, htmltext)[0]
    
    regex = 'data-test=\"EPS_RATIO-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    EPS = re.findall(regex, htmltext)[0]
    
    #regex = 'data-test=\"EARNINGS_DATE-value\" data-reactid=\"417\"><span>(.+?)</span>'
    #earning_date = re.findall(regex, htmltext)
    
    regex = 'data-test=\"DIVIDEND_AND_YIELD-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    div_yield = re.findall(regex, htmltext)[0]
    
    regex = 'data-test=\"EXDIVIDEND_DATE-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    ex_div_date = re.findall(regex, htmltext)[0]
    
    regex = 'data-test=\"ONE_YEAR_TARGET_PRICE-value\" data-reactid=\"[0-9]+\">(.+?)</td>'
    target = re.findall(regex, htmltext)[0]
    df_summary.ix[ticker] = [ticker, previous_close, open_price, day_range, year_range, volume, avg_volume, 
        market_cap, beta, PE, EPS, div_yield, ex_div_date, target]
    count +=1
    print count
        
pyperclip.copy(htmltext)

```
