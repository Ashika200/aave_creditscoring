
# Aave V2 Credit Scoring (DeFi Project)

## 🔍 Objective
Assign a credit score (0–1000) to each wallet interacting with Aave V2 based on its historical transaction behavior. Higher scores indicate trustworthy users; lower scores suggest riskier or bot-like activity.

---

## 📁 Data Source
- JSON transaction-level data from Aave V2 protocol
- Includes actions: deposit, borrow, repay, redeemUnderlying, liquidationCall

---

## 🧠 Methodology

### 🔧 Feature Engineering
For each wallet, we computed:
- Number of transactions by type (borrow, repay, liquidation, deposit)
- Total & average transaction amount
- Wallet activity duration (first to last transaction)
- Borrow-to-repay ratio
- Number of liquidations

### 🧮 Scoring Logic
A heuristic-based formula was used:
The score is then **normalized to a 0–1000 scale** using MinMaxScaler.
Credit Score =
+ 3 × (Repayments)
− 10 × (Liquidations)
+ 0.2 × (Active Days)
− 2 × (Borrow-to-Repay Ratio)
---

## ⚙️ Processing Flow
1. Load the transaction JSON
2. Group by wallet address
3. Extract features
4. Calculate raw scores
5. Normalize to credit scores (0–1000)
6. Save results

---

## 📊 Outputs
- `wallet_scores.csv`: Wallets with final credit scores
- `score_distribution.png`: Histogram of score ranges
- `analysis.md`: Breakdown and interpretation of score behaviors

---

## 📁 Project Structure
aave-credit-score/
├── Aave_Credit_Score.ipynb # Main Colab notebook with full pipeline
├── user_transactions.json # Raw transaction data (input)
├── wallet_scores.csv # Output CSV containing credit scores per wallet
├── score_distribution.png # Histogram of score ranges
├── README.md # Project overview, method, architecture
├── analysis.md # Analysis of wallet behaviors and score ranges
├── requirements.txt # Python dependencies (if running locally)

---

## 📦 Tech Stack
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn
- Google Colab

---

## 📬 Contact
 Ashika Jain  
📧 jainashika9988@gmail.com

---

## 🪪 License
MIT License
