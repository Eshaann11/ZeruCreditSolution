# Score Distribution & Wallet Behavior Analysis

### 📈 Credit Score Histogram
Credit scores were binned into deciles:

- **0–99**: Very low activity, zero diversity, short lifespan
- **100–299**: Rare usage or high volatility in value (e.g., pump/withdraw only)
- **300–499**: Irregular but not exploitative usage
- **500–699**: Average wallet — fair usage with moderate diversity
- **700–899**: Highly stable and consistent users, high tx/day and repay ratio
- **900–1000**: Ideal users — long history, consistent volume, high diversity

> ![score_distribution](score_distribution.png)

---

### 📊 Insights

- **Bot-like Wallets**: Clustered heavily in the 0–199 range, typically interacted in bursts or one-off events.
- **Reliable Wallets**: Showed high token diversity, more than 15 days of activity, and consistent `tx/day` ratios.
- **High Credit Users**:
  - Made both `deposit` and `repay` actions
  - Used multiple stablecoins (USDT, DAI, USDC)
  - Did not churn after just one interaction

---

### 🔍 Observations

- About 40% wallets fall in 0–300 bucket: typical of air-drop farmers or flash-borrowers
- Only ~10% are in 800+ range: ideal target users for premium features in DeFi lending products

---

### 📌 Conclusion

This credit scoring logic can be directly used in:
- DeFi credit underwriting
- Airdrop eligibility filters
- Sybil detection

The model is fully extensible — more behavioral flags (e.g., liquidations, rate modes) can be incorporated for richer credit estimation.
