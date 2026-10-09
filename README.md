Short VIX Exposure Using an ETF-Based Trading System

WorldQuant University | MSc in Financial Engineering (MScFE 690 Capstone)

Group 17843: Edgar 

NAVA (edgar.nava@grovwm.com) & Celestin NYANDWI (celestinnyandwi48@gmail.com)

Project Overview

Short volatility trading strategies utilizing VIX futures and derivative Exchange-Traded Products (ETPs) like SVXY capture structural contango roll yield and the variance risk premium during calm regimes. However, unhedged buy-and-hold inverse volatility exposure subjects investors to catastrophic tail risks, as demonstrated during the February 2018 "Volmageddon" crash (-87.91% peak-to-trough drawdown during COVID-19 for -1.0x leverage).

This repository provides an end-to-end quantitative framework and reproducible Python pipeline that:

Reconstructs standardized synthetic SVXY daily series targeting both -1.0x (ONEx) and -0.5x (HALFx) leverage objectives starting from SVXY inception (2011-10-04 to 2026-09-16), incorporating an econometric regression fix for the February 5–6, 2018 event disruption.

Analyzes empirical VIX state persistence and 15-session endpoint transition matrices across discrete volatility regimes.

Backtests a tactical regime-switching strategy—combining a 5-day / 87-day Simple Moving Average (SMA 5/87) crossover with a 15% trailing stop-loss—to systematically rotate capital between short-volatility exposure and cash under conservative transaction friction assumptions ($0.005/share fee + 0.1% slippage).
Repository Architecture
MScFE_690_Capstone_Short_VIX/
│
├── data/                                 # Standardized CSV datasets
│   ├── VIX_data.csv                      # Spot VIX daily OHLC (2004–2026)
│   ├── VVIX_data.csv                     # Volatility-of-Vol index OHLC (2007–2026)
│   ├── SVXY_data.csv                     # Raw SVXY ETF daily OHLC
│   ├── SVXY_synth-ONEx.csv               # Synthetic -1.0x daily exposure series (2011–2026)
│   └── SVXY_synth-HALFx.csv              # Synthetic -0.5x daily exposure series (2011–2026)
│
├── notebooks/                            # Sequential Jupyter Notebooks
│   ├── 00_vix_vvix_svxy_data_retrieval.ipynb  # Yahoo Finance API data pipeline
│   ├── 01_Synthetic_SVXY-ONEx.ipynb           # -1.0x SVXY reconstruction & Feb 2018 event fix
│   ├── 02_Synthetic_SVXY-HALFx.ipynb          # -0.5x SVXY reconstruction & historical scaling
│   ├── 03_VIX_Close_Study_1.ipynb             # Volatility state transition matrix & persistence
│   └── 04_Short_Vol_Timing_Strategy.ipynb     # SMA 5/87 + 15% Stop loss backtest engine
│
├── requirements.txt                      # Python dependencies
├── LICENSE                               # MIT License
└── README.md                             # Project documentation
