
---

## 🧠 Objective

To assign a **credit score (0–1000)** to each user wallet by analyzing:

- Deposits
- Borrows
- Repayments
- Withdrawals (`redeemUnderlying`)
- Liquidation events

---

## ⚙️ Methodology

1. **Data Preprocessing**
   - Load transaction data from `aave_v2_data.json`
   - Parse and normalize JSON structure
   - Filter relevant actions
   - Convert timestamps and clean nulls

2. **Feature Engineering**
   - Count of each action type per wallet
   - Time range of activity (duration of engagement)
   - Ratio of repayments to borrows
   - Ratio of liquidations to total transactions

3. **Scoring Logic**
   Wallets are scored based on:
   - ✅ High activity (diverse and consistent)
   - ✅ Repayment responsibility
   - ❌ Liquidation frequency
   - ✅ Long activity duration

   A composite score is generated and normalized to a 0–1000 scale.

4. **Output**
   - Each wallet receives a final credit score
   - Results stored in `outputs/wallet_scores.csv`

---

## 🏗️ Architecture & Flow

1. **Input**: `data/aave_v2_data.json`  
2. **Script**: Run `main.py` to process and score wallets  
3. **Output**: `outputs/wallet_scores.csv` with columns:  
   - `wallet_address`, `score`

---

## 📊 Dependencies

Install via:

```bash
pip install -r requirements.txt
