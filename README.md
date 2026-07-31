\# SMA20/SMA50 Moving-Average Crossover Backtest



\## Project Overview



This project evaluates whether a long-only SMA20/SMA50 moving-average crossover

strategy provides a better historical investment outcome than buy-and-hold.



The strategy is tested on:



\- AAPL

\- MSFT

\- NVDA



The historical sample covers January 2016 through December 2025.



\## Research Question



Does an SMA20/SMA50 crossover strategy improve return, risk-adjusted

performance, or downside protection relative to buy-and-hold after transaction

costs?



\## Strategy Rules



The trading signal is:



\\\[

\\text{Signal}\_t =

\\begin{cases}

1, \& \\text{if } SMA20\_t > SMA50\_t \\\\

0, \& \\text{otherwise}

\\end{cases}

\\]



To prevent look-ahead bias, the executable position uses the previous trading

day's signal:



\\\[

\\text{Position}\_t = \\text{Signal}\_{t-1}

\\]



The strategy is:



\- Fully invested when `Position = 1`

\- Fully in cash when `Position = 0`

\- Long-only

\- Charged a 0.1% transaction cost on every entry and exit



\## Data



Historical daily price data were downloaded from Stooq.



The available fields include:



\- Date

\- Open

\- High

\- Low

\- Close

\- Volume



The analysis is treated as a price-return backtest because the downloaded files

do not contain an explicit dividend or total-return field.



\## Methodology



The project includes:



\- Data loading and cleaning

\- Data-quality validation

\- Daily return calculations

\- SMA20 and SMA50 calculations

\- Lagged signal execution

\- Entry and exit identification

\- Transaction-cost modelling

\- Cumulative-return analysis

\- Annualized return and volatility

\- Sharpe ratio

\- Maximum drawdown

\- Market exposure

\- Buy-and-hold comparison

\- Chronological train-test evaluation

\- Performance visualizations



\## Main Findings



The SMA20/SMA50 strategy generated positive historical returns for AAPL, MSFT,

and NVDA. However, it substantially underperformed buy-and-hold over the full

sample period.



The strategy reduced market exposure and lowered volatility or drawdown in some

cases, but these risk reductions were generally insufficient to compensate for

the amount of return sacrificed.



Most of the underperformance was caused by the strategy being in cash during

important upward price movements rather than by transaction costs alone.



\## Full-Sample Results



| Asset | Net SMA Return | Gross Buy-and-Hold Return | Transactions |

|---|---:|---:|---:|

| AAPL | 289.13% | 1,044.34% | 57 |

| MSFT | 212.61% | 900.50% | 52 |

| NVDA | 4,529.72% | 23,512.02% | 48 |



\## Out-of-Sample Evaluation



The dataset was divided chronologically into:



\- Training period: 2016–2021

\- Testing period: 2022–2025



The SMA20/SMA50 parameters were kept unchanged during the testing period.



The out-of-sample analysis showed that strategy performance varied across

assets and market regimes. Strong training-period performance did not always

persist during testing.



\## Conclusion



For AAPL, MSFT, and NVDA between 2016 and 2025, the SMA20/SMA50 crossover

strategy was not superior to buy-and-hold under the assumptions used in this

project.



The strategy acted as a basic trend-following and exposure-reduction mechanism,

but it did not provide a better overall investment outcome after considering

return, risk, and transaction costs.



\## Limitations



Important limitations include:



\- Only three technology-oriented stocks were tested

\- Cash returns were assumed to be zero

\- Transaction costs were represented by a fixed 0.1% rate

\- Buy-and-hold was reported as a gross benchmark

\- Dividend treatment was not independently verified

\- Execution was based on simplified daily close-to-close returns

\- A constant 4% annual risk-free rate was used

\- Only one chronological train-test split was evaluated

\- Historical performance does not guarantee future results



## Repository Structure

```text
sma20-sma50-backtest/
│
├── README.md
├── sma20_sma50_backtest.ipynb
├── requirements.txt
├── .gitignore
│
├── data/
│   ├── aapl_us_d.csv
│   ├── msft_us_d.csv
│   └── nvda_us_d.csv
│
└── figures/
    ├── aapl_cumulative_growth.png
    ├── aapl_drawdown.png
    ├── aapl_trading_signals.png
    ├── msft_cumulative_growth.png
    ├── msft_drawdown.png
    ├── msft_trading_signals.png
    ├── nvda_cumulative_growth.png
    ├── nvda_drawdown.png
    └── nvda_trading_signals.png
```





