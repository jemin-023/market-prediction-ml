# Raw Data Directory

This folder serves as the landing zone for all **original, immutable data** used in the market prediction project. 

## 📂 Contents
- `*.csv / *.json`: Original datasets sourced from APIs (e.g., Yahoo Finance, Alpha Vantage) or manual downloads.
- **Note:** Files in this directory should never be edited manually. Any cleaning or preprocessing must be done via scripts, with the output saved to the `data/processed/` directory.

## 🛠 Data Sources
| Dataset Name | Description |
| :--- | :--- |
| Historical Prices | Daily OHLCV data for selected tickers. |
| Sentiment Data | News headlines or social media feeds. |
