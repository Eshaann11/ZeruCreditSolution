# Zeru DeFi Wallet Credit Scoring System

This project implements a robust, interpretable machine learning-based scoring engine to assign a **credit score (0–1000)** to each DeFi wallet, based on transaction behavior from the Aave V2 protocol. Higher scores represent responsible usage; lower scores may indicate exploitative or bot-like activity.

---

## 🔍 Problem Statement

Given raw JSON records of wallet-level actions (`deposit`, `borrow`, `repay`, `redeemUnderlying`, etc.) from the Aave V2 protocol, build a scoring model to reflect behavioral reliability using transaction history only.

---

## ✅ Dataset

- Source: Aave V2 Protocol JSON logs (Polygon Network)
- Each record includes:
  - Wallet address
  - Timestamp
  - Transaction type
  - Token, USD value
  - Action-specific metadata

---

## 🧠 Methodology

### 1. **Data Normalization**
- Flattened `actionData` JSON
- Parsed timestamps
- Standardized fields like `amount`, `price`, `usd_value`

### 2. **Wallet-Level Aggregation**
Calculated the following features for each wallet:
- `total_tx`: Total number of transactions
- `total_usd`: Total USD transacted
- `mean_usd`, `std_usd`: Mean and variance of transaction value
- `unique_tokens`, `unique_actions`: Behavioral diversity
- `active_days`, `tx_per_day`: Activity consistency

### 3. **Scoring Logic**
- All features scaled using `MinMaxScaler`
- Weighted combination:
  - Emphasis on transaction count, total volume, diversity, and stability
- Final score:  
  \[
  \texttt{score} = \left( \sum w_i \cdot \text{feature}_i \right) \times 1000
  \]

---

## 📊 Output

Each wallet is assigned a `credit_score` ∈ [0, 1000] and bucketed into:
- 0–99, 100–199, ..., 900–999

Score histogram is saved as `score_distribution.png`.

---

## 📁 Files

- `ZeruCreditSolution.ipynb`: Full logic & analysis
- `wallet_scores.csv`: Final scores (wallet, score)
- `score_distribution.png`: Visual histogram
