# Indian Mutual Fund Portfolio Overlap Analyzer

## About
Millions of Indian investors hold 3-5 mutual funds thinking they're diversified, but most funds hold the same stocks. This project analyzes portfolio overlap across **45 top Indian equity mutual funds** to uncover hidden concentration risks.

## Dataset
- **Source:** Scraped from [Moneycontrol.com](https://www.moneycontrol.com) (publicly available portfolio holdings)
- **Funds Analyzed:** 45 (Top 10 by AUM in each category)
  - Large Cap: 10 funds
  - Mid Cap: 10 funds
  - Small Cap: 10 funds
  - Flexi Cap: 10 funds
  - Index Funds: 5 funds
- **Total Holdings:** 3,421 stock entries across 1,041 unique stocks
- **Data as of:** February/March 2026

## Key Findings
1. **Index funds share ~100% overlap** — holding multiple Nifty 50 funds is pointless
2. **Large cap funds overlap 54% on average** — SEBI's 80% mandate in ~100 stocks leaves little room for differentiation
3. **Small cap funds are the most unique** — only 11% average overlap with 1000+ stocks to choose from
4. **HDFC Bank & ICICI Bank appear in 28/45 funds** — massive hidden banking concentration
5. **Eternal Ltd. (Zomato) is the most widely held stock** — present in 31 out of 45 funds
6. **Parag Parikh Flexi Cap is the most unique fund** — foreign holdings ensure near-zero overlap with domestic funds
7. **Best diversification: Mid/Small Cap + Index Fund** — only 3-4% overlap
8. **Flexi Cap funds aren't really "flexi"** — 7.5x more weight in large caps vs small caps
9. **Concentration varies wildly** — HDFC Sensex needs just 6 stocks to reach 50% of portfolio, Nippon Small Cap needs 59
10. **Index funds have zero small cap exposure** — investors relying solely on index funds completely miss the small cap segment

## SQL Queries & Analysis
The project includes 19 SQL queries covering:
- Portfolio overlap between fund pairs (weighted overlap using MIN weight formula)
- Most crowded stocks and sectors across mutual funds
- Category-wise overlap comparison (Large vs Mid vs Small vs Flexi vs Index)
- Cross-category diversification analysis
- Fund concentration and diversification scoring
- Optimal 5-fund portfolio recommendation
- Hidden gem stocks with high conviction but low popularity
- Market cap distribution analysis across fund categories
- Window functions (RANK, cumulative SUM) for holdings ranking and concentration analysis

## Tech Stack
- **Python** — requests, BeautifulSoup (web scraping), pandas (data manipulation)
- **SQL (SQLite)** — JOINs, CTEs, window functions, self-joins, aggregations
- **Data Source** — Moneycontrol.com

## Project Structure
```
├── mutual_fund_overlap_analysis.ipynb  # Main analysis notebook
├── mutual_fund_overlap.db             # SQLite database
├── mutual_fund_holdings.csv           # Raw data backup
├── funds_list.json                    # Fund URLs reference
└── README.md
```

## How to Run
1. Clone this repository
2. Open `mutual_fund_overlap_analysis.ipynb` in Jupyter Notebook
3. Run all cells — the notebook scrapes fresh data, builds the database, and runs all analyses
4. Requires: `pip install requests beautifulsoup4 pandas`

## Limitations
- Data from Moneycontrol may have slight discrepancies with official AMC disclosures
- Holdings are as of a single date — overlap changes monthly with portfolio rebalancing
- Equity holdings only — debt, cash positions excluded
- "Other" market cap category includes foreign stocks and uncategorized companies

## Author
**Daksh Malhotra**
B.Tech Engineering Physics, Delhi Technological University
