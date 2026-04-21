# WRDS + SQL + DuPont Financial Analysis

## 1. Problem & User

- **Target User**: Beginner investors learning fundamental analysis
- **Business Problem**: How can we quickly compare the profitability structure of different companies? Which driver (profitability, efficiency, or leverage) contributes most to a company's ROE?

This project uses DuPont analysis to decompose Return on Equity (ROE) into three components: profit margin, asset turnover, and equity multiplier.

## 2. Data Source

| Item | Description |
|------|-------------|
| **Platform** | WRDS (Wharton Research Data Services) |
| **Database** | Compustat (`comp.funda` table) |
| **Access Date** | 2026-04-16 |
| **Companies** | AAPL (Apple), MSFT (Microsoft), GOOGL (Google) |
| **Time Period** | 2020 - 2025 |
| **Key Variables** | `gvkey`, `tic`, `fyear`, `sale`, `ni`, `at`, `seq` |

## 3. Methods (ACC102 Course Concepts)

| Week | Concept | Implementation in Code |
|------|---------|------------------------|
| **W4** | WRDS Connection | `wrds.Connection()`, `list_libraries()`, `list_tables()`, `describe_table()` |
| **W5** | Basic SQL | `SELECT tic, fyear, sale FROM comp.funda WHERE tic = 'AAPL' LIMIT 5` |
| **W5** | `db.raw_sql()` | Execute SQL and return pandas DataFrame |
| **W5** | Export to Excel | `.to_excel()` for sharing results |
| **W6** | Parameterized SQL with f-string | Dynamic `ticker` and `start_year` variables |
| **W6** | pandas DataFrame operations | `.head()`, `.dtypes` |
| **W7** | DuPont 3-factor decomposition | `profit_margin = ni/sale`, `asset_turnover = sale/at`, `equity_multiplier = at/seq`, `ROE = profit_margin × asset_turnover × equity_multiplier` |
| **W7** | Data visualization | Matplotlib line chart for ROE trend, bar chart for multi-company comparison |

### DuPont Formula
ROE = (Net Income / Sales) × (Sales / Total Assets) × (Total Assets / Equity)
= Profit Margin × Asset Turnover × Equity Multiplier

## 4. Key Findings

1. **Apple (AAPL)** has the highest ROE among the three companies (average ~1.5 or 150%)

2. **Apple's ROE is driven by high profit margin** (~24%), not financial leverage

3. **Microsoft (MSFT)** shows lower but stable ROE (~0.35 or 35%)

4. **Google (GOOGL)** has the lowest ROE (~0.28 or 28%), indicating lower profitability compared to Apple

5. The DuPont decomposition reveals that Apple's superior ROE comes from genuine profitability (high profit margin), not from higher leverage

## 5. How to Run

### Prerequisites

- WRDS account (registered with university email)
- Duo two-factor authentication enabled
- Python 3.8+ with Jupyter Notebook

### Steps

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Launch Jupyter Notebook
jupyter notebook notebook.ipynb

# 3. Replace 'your_username' with your actual WRDS username in the connection cell
# 4. Run all cells sequentially
Expected Output Files
File	Description
aapl_sales_sample.xlsx	W5 basic query result (first 5 rows of Apple sales)
aapl_dupont_analysis.xlsx	Complete DuPont analysis for Apple (2020-2025)
roe_trend.png	Apple ROE trend line chart (2020-2025)
roe_comparison.png	ROE comparison bar chart (Apple, Microsoft, Google)
roe_comparison.xlsx	ROE comparison table for all three companies
6. Product Links

Item	Link
Demo Video	[Insert Mediasite link after recording]
GitHub Repository	[Insert your GitHub repo link]
acc102-track2-dupont-analysis/
├── README.md
├── notebook.ipynb
├── requirements.txt
├── aapl_sales_sample.xlsx
├── aapl_dupont_analysis.xlsx
├── roe_trend.png
├── roe_comparison.png
├── roe_comparison.xlsx
└── figures/                 (optional)
8. Limitations & Next Steps

Current Limitations

Only 6 years of data (2020-2025)
Limited to 3 companies (Apple, Microsoft, Google)
Does not include cash flow or valuation metrics
WRDS account required (cannot run without institutional access)
Future Improvements

Add DCF valuation model (W7 extension)
Include more companies for industry benchmark
Add time-series statistical tests
Convert to Streamlit app for interactive analysis (Track 4)
9. AI Use Disclosure

Tool	Version	Access Date	Purpose
ChatGPT	GPT-4	2026-04-15	Debug pandas code, generate README template, optimize plot labels
I have run, checked, and understood all code generated with AI assistance.

Course: ACC102 Artificial Intelligence-Driven Data Analytics
Track: 2 – GitHub Data Analysis Project
Author: [Keyao Fan]
Student ID: [2469196]
Date: 2026-04-21
