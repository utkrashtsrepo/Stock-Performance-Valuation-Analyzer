# Stock Performance & Valuation Analyzer

**Build:** November 2026

## Introduction

The Stock Performance & Valuation Analyzer is a beginner-friendly Python project designed to analyze the historical financial performance of publicly traded companies, forecast their future financial performance, and estimate their intrinsic stock value using the Discounted Cash Flow (DCF) method.

The project uses financial data obtained through the `yfinance` API and performs three key operations:

1. **Financial Performance Analysis:** Analyzes historical revenue, operating income (EBIT), revenue growth, and EBIT margins to understand a company's financial performance.
2. **Financial Forecasting:** Projects the company's revenue, EBIT, and Free Cash Flow (FCF) over the next five years using historical financial trends.
3. **DCF Valuation:** Estimates the company's intrinsic value by discounting projected future cash flows and calculating terminal value.

The project also generates visualizations to compare historical and forecasted revenue and exports financial projections to a CSV file.

The primary objective is to understand how financial data can be used to evaluate a company's performance and estimate its intrinsic value using Python.

## Features

- Fetches historical financial statements using Yahoo Finance.
- Analyzes historical revenue and operating profit.
- Calculates revenue growth and EBIT margins.
- Forecasts revenue and operating performance for five years.
- Estimates Free Cash Flow using EBIT, taxes, depreciation, and capital expenditure.
- Calculates Enterprise Value and Equity Value using the DCF method.
- Estimates intrinsic value per share.
- Visualizes historical and projected revenue trends.
- Exports forecasted financial data to CSV.

## Requirements

- Python 3.x
- Google Colab or Jupyter Notebook

Install the required libraries:

```bash
pip install yfinance pandas numpy matplotlib
```

## Usage

The project can be executed directly in Google Colab or Jupyter Notebook.

1. Open the notebook.
2. Set the stock ticker symbol.
3. Run the code.
4. Review the financial analysis, forecasts, valuation results, and charts.

Example:

```python
TICKER = "AAPL"
```

Other supported ticker examples:

```python
TICKER = "MSFT"      # Microsoft
TICKER = "KO"        # Coca-Cola
TICKER = "TCS.NS"    # Tata Consultancy Services
```

### Model Assumptions

The following assumptions are used in the model:

| Parameter | Default Value |
|---|---:|
| Forecast Period | 5 Years |
| Discount Rate (WACC) | 10% |
| Terminal Growth Rate | 3% |
| Tax Rate | 21% |

These values can be modified in the configuration section of the code.

## Methodology

### 1. Financial Performance Analysis

Historical financial statements are retrieved using the `yfinance` API.

The model analyzes:

- Revenue
- EBIT (Earnings Before Interest and Taxes)
- Revenue Growth
- EBIT Margin

**Revenue Growth**

```math
Revenue\ Growth = \frac{Current\ Revenue - Previous\ Revenue}{Previous\ Revenue}
```

**EBIT Margin**

```math
EBIT\ Margin = \frac{EBIT}{Revenue}
```

These metrics help evaluate the company's historical growth and operating profitability.

### 2. Financial Forecasting

The model uses recent historical averages to estimate future financial performance over a five-year period.

Forecasted metrics include:

- Revenue
- EBIT
- EBIAT
- Depreciation and Amortization
- Capital Expenditure
- Free Cash Flow

**Revenue Forecast**

```math
Future\ Revenue = Previous\ Revenue \times (1 + Growth\ Rate)
```

**EBIAT (Earnings Before Interest After Taxes)**

```math
EBIAT = EBIT \times (1 - Tax\ Rate)
```

**Free Cash Flow**

```math
FCF = EBIAT + D\&A - CapEx
```

The model estimates depreciation and capital expenditure using their historical proportions of revenue.

### 3. Discounted Cash Flow Valuation

Discounted Cash Flow (DCF) is a valuation method that estimates a company's intrinsic value based on the present value of its expected future cash flows.

The model uses a fixed discount rate of 10% to calculate the present value of projected cash flows.

**Present Value of Free Cash Flow**

```math
PV = \frac{FCF_t}{(1 + WACC)^t}
```

**Terminal Value – Perpetual Growth Method**

The Gordon Growth Model estimates the value of cash flows beyond the five-year forecast period.

```math
TV = \frac{FCF_n \times (1 + g)}{WACC - g}
```

Where:

- FCF = Final year Free Cash Flow
- WACC = Discount rate
- g = Terminal growth rate

**Enterprise Value**

```math
EV = PV\ of\ Forecasted\ FCF + PV\ of\ Terminal\ Value
```

**Equity Value**

```math
Equity\ Value = Enterprise\ Value - Total\ Debt + Cash
```

**Intrinsic Value Per Share**

```math
Intrinsic\ Share\ Price = \frac{Equity\ Value}{Shares\ Outstanding}
```

## Visualization

The project generates visual representations of financial performance, including:

- Historical Revenue Analysis
- Historical vs. Forecasted Revenue
- Forecasted Free Cash Flow

These visualizations help understand historical business performance and projected financial trends.

## Output

The project provides:

- Historical financial performance summary.
- Five-year financial forecast.
- Enterprise Value.
- Equity Value.
- Estimated Intrinsic Share Price.
- Current Market Price and estimated upside/downside, when market data is available.
- Revenue and Free Cash Flow visualizations.
- CSV file containing forecasted financial data.

The forecast is also exported as:

```text
AAPL_financial_forecast.csv
```

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming and calculations |
| yfinance | Fetching financial data |
| Pandas | Financial data processing and analysis |
| NumPy | Numerical calculations |
| Matplotlib | Financial data visualization |

## Limitations

- Revenue growth and EBIT margins are estimated using recent historical averages.
- WACC, tax rate, and terminal growth are based on fixed assumptions.
- Working capital changes are not included in the Free Cash Flow calculation.
- Financial statement availability and naming conventions may vary across companies.
- The valuation is sensitive to assumptions about future growth and discount rates.

## Disclaimer

This project is intended for educational and research purposes only. The estimated intrinsic value is based on simplified financial assumptions and should not be considered financial advice or a recommendation to buy or sell securities.

Always conduct independent research before making investment decisions.

## References

- [Yahoo Finance](https://finance.yahoo.com/) – Financial data source.
- [yfinance Documentation](https://ranaroussi.github.io/yfinance/) – Python library documentation.
- [Investopedia](https://www.investopedia.com/) – Financial and valuation concepts.
- [NYU Stern – Aswath Damodaran](https://pages.stern.nyu.edu/~adamodar/) – Corporate finance and valuation resources.
