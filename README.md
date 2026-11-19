# Stock Performance & Valuation Analyzer

## Introduction

A Python-based financial analysis project that evaluates a company's historical performance, forecasts its financials over five years, and estimates its intrinsic stock value using the Discounted Cash Flow (DCF) method.

The project retrieves financial data from Yahoo Finance using the `yfinance` library.

## Features

- Fetches historical financial statements.
- Analyzes Revenue, EBIT, Revenue Growth, and EBIT Margin.
- Forecasts Revenue, EBIT, and Free Cash Flow for five years.
- Estimates Enterprise Value and Equity Value using DCF.
- Calculates Intrinsic Share Price.
- Visualizes historical and forecasted financial performance.
- Exports forecast data to CSV.

## Technologies Used

- Python
- yfinance
- Pandas
- NumPy
- Matplotlib

## Requirements

- Python 3.x
- Google Colab or Jupyter Notebook

Install the required libraries:

```bash
pip install yfinance pandas numpy matplotlib
```

## Usage

Set the stock ticker in the configuration section:

```python
TICKER = "AAPL"
```

Examples: `MSFT`, `KO`, `TCS.NS`

Run the notebook to fetch financial data and generate the analysis, forecasts, valuation, and visualizations.

## Methodology

### 1. Financial Performance Analysis
Analyzes historical Revenue, EBIT, Revenue Growth, and EBIT Margin to understand the company's financial performance.

### 2. Financial Forecasting
Projects the following financial metrics for the next five years using historical averages and financial ratios:

- Revenue
- EBIT
- EBIAT
- Depreciation & Amortization (D&A)
- Capital Expenditure (CapEx)
- Free Cash Flow (FCF)

### 3. DCF Valuation
Estimates the company's intrinsic value by discounting projected Free Cash Flows and Terminal Value.

**Key formulas:**

FCF = EBIAT + D&A − CapEx

Terminal Value:

TV = FCF × (1 + g) / (WACC − g)

Intrinsic Share Price = Equity Value / Shares Outstanding

## Model Assumptions

The project uses the following fixed assumptions for valuation:

| Parameter | Value |
|---|---:|
| WACC | 10% |
| Terminal Growth Rate | 3% |
| Tax Rate | 21% |
| Forecast Period | 5 Years |

Revenue growth, EBIT margin, D&A, and CapEx assumptions are estimated using historical financial data.

These fixed assumptions simplify the valuation model and can affect the estimated intrinsic value.

## Disclaimer

This project is developed for educational purposes to understand financial statement analysis, forecasting, and DCF valuation. The results are based on simplified assumptions and should not be considered financial or investment advice.
