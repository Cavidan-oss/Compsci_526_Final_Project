
# Informed Investment from Congressional and Insider Trading

This project investigates whether publicly disclosed trades made by **U.S. congressional members** and **corporate insiders** contain exploitable information that can be used to build profitable investment strategies. Using scraped disclosure data, historical stock prices, and naïve mirroring strategies, we evaluate whether insider transactions yield above-market returns, even when executed at *report-date* prices rather than the true trade date.

This README summarizes the project motivation, datasets, exploratory analyses, and modeling framework.  
The content is based on the final milestone report. (Source: final milestone.pdf)

---

## 📌 Project Overview

Financial markets are designed to be efficient, but insiders—such as members of Congress or corporate executives—often have early access to non‑public information. Although laws like the **STOCK Act** and **SEC Form 4** require trades to be disclosed, these disclosures may still reveal delayed but valuable signals.

This project explores:

- Whether congressional and insider trades show measurable predictive value.
- Whether a naïve mirroring strategy can outperform index funds.
- How insider activity compares to a passive investing baseline.
- How future models could leverage richer features to extract predictive signals.

---

## 📊 Datasets

### **1. Congressional Trades**  ￼
Sourced from **CapitolTrades.com**, scraped using a custom parser.  
Key fields included:

- Politician name, party, ownership type  
- Ticker, transaction & report dates  
- Transaction value ranges  
- Transaction type (buy/sell)  

Challenges included coarse monetary ranges (e.g., 15k–50k) and disclosure lags (up to 45 days).


### **2. Corporate Insider Trades**
Retrieved from **OpenInsider**, based on SEC Form 4 filings.  
Included:

- Insider role/title  
- Number of shares  
- Transaction type  
- Filing vs transaction dates  

Covers insider trades from 2020–present.

### **3. Historical Stock Prices**
Collected from **Yahoo! Finance** using public API tools.  
Includes daily OHLCV fields.

Missing historical data for some tickers required filtering out incomplete stocks.


Some of the datasets used in this project are included in the `data/` directory of this repository. However, several larger files could not be uploaded due to size limitations.

To access **all datasets**, including the full raw and processed files used in our analysis, please visit the project’s DukeBox repository:

https://duke.box.com/s/cqk2gkdklttnjj2z8c21ew84iuqw96aa

---

## 🔍 Exploratory Data Analysis

### **1. Price at Trade Date vs. Report Date**
Both congressional and insider trades showed **minimal differences** between reported-date and trade-date prices, meaning report-date mirroring is still meaningful.

### **2. Naïve Insider-Mirroring Strategy**
We purchased stocks at the **report date** and sold them after:

- 1 month  
- 2 months  
- 12 months  
- 24 months  

Both datasets showed **consistent positive drift**, suggesting insiders buy stocks that later increase in value.

### **3. Comparison with Passive Index Funds**
Benchmarks used: **SPY, IVV, VOO, QQQ, VTI**

After removing sub-penny anomalies:

- Insider-mirroring **outperformed all index fund baselines** on average.
- Suggests that disclosed insider behavior still reflects privileged information.

---

## 🧠 Investment Strategy Framework

The report introduces:

### **1. Naïve Strategy**
- Buy at report date  
- Hold for fixed duration  
- Sell at end of period  
- Compute simple returns  

### **2. Naïve Risk-Adjusted Returns**
Includes variance-based and normalized metrics.

### **3. Informed Investment Strategy (Future Work)**
Will include:

- Behavioral patterns  
- Insider role weighting  
- Committee/sector context  
- Market‑regime awareness  
- Predictive modeling  

---

## 🛠 Feature Engineering

Key engineered features included:

- Transaction size midpoints  
- Lag times (trade → report)  
- Insider roles / ownership types  
- Down-sampled datasets for balanced class modeling  

---

## 🤖 Predictive Modeling Approach

The next stage involves:

- Building regression/classification models to predict drift  
- Evaluating robustness across market regimes (e.g., COVID crash)  
- Generating informed buy/sell recommendations  
- Comparing with naïve and baseline strategies  

---

## 📚 Insights and Narrative

Our findings show clear evidence that:

- Congressional and insider trades **retain predictive value**, even after delayed disclosure.
- Market information diffusion is **not instantaneous**, contradicting full efficient market assumptions.
- Publicly disclosed insider trades offer **weak but exploitable signals**.

These insights motivate more sophisticated investment models built on structural features and insider behavior patterns.

---





## 📘 References

Sources include CapitolTrades, OpenInsider, Yahoo! Finance, STOCK Act documentation, and academic literature on insider trading performance.



