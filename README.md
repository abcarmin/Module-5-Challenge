# Module-5-Challenge

For this project, I created a financial planner for members to determine if they have enough saved for emergencies. I also created a financial planner to forecast the performace of a retirement portfolio in 30 and 10 years. The tool makes an Alpaca API call via the Alpaca SDK to get historical data for the Monte Carlo simulations.

---

## Technologies

This project uses pandas programming language and utilizes Anaconda, Git Bash, Jupyter Lab, and Github. This project also makes an Alpaca API call via the Alpaca SDK.

---

## Installation Guide

These are the required libraries and dependencies:

import os
import requests
import json
import pandas as pd
from dotenv import load_dotenv
import alpaca_trade_api as tradeapi
from MCForecastTools import MCSimulation

%matplotlib inline

You must also load the environment variables from the .env file.

---

## Usage

I made an Alpaca API call to get historical data to compare the member's savings:

df_portfolio = alpaca.get_bars(
    tickers,
    timeframe,
    start = start_date,
    end = end_date
).df


I compared the total savings and the amount the member needs for the emergency fund:

if total_portfolio > emergency_fund_value:
    print('Congratulations! You have enough money in this portfolio for your emergency fund.')
elif total_portfolio == emergency_fund_value:
    print('Congratulations! You have reached your emergency fund goal.')
else:
    print(f'You are ${emergency_fund_value-total_portfolio} away from reaching your emergency fund goal.')
    
    
Using another API call(prices_df), I created a Monte Carlo simulation to create a financial planner for retirement:

MC_thirtyyear = MCSimulation(
    portfolio_data = prices_df,
    weights = [.60,.40],
    num_simulation = 500,
    num_trading_days = 252 * 30
)

---

## Contributors

Allyssa Carmin

---

## License

SMU Fintech Course