# Cryptocurrency Risk Analysis using K-Means Clustering

> **CS2235 - Data Science Capstone Project**  
> School of Computer Science and Engineering, RV University, Bengaluru  
> **Program:** B.Sc. (Hons.) Data Science — Semester III  
> 
> **Team Members:**
> - **Thanisha S** (`1RUA25SCS0110`)
> - **Srujana Shreya Raju** (`1RUA25SCS0105`)
> - **Rachana B** (`1RUA25SCS0079`)  

---

## 📌 Project Overview
This project applies **Unsupervised Machine Learning (K-Means Clustering)** to group cryptocurrencies into different risk categories based on their **price volatility** (how much their prices change) and **trading volume** (how much they are traded).

The code is designed to be simple, beginner-friendly, and follows the exact patterns taught in our university laboratory curriculum (**CS2235 Lab Program 9: K-Means Clustering**).

---

## 🚀 How to Run in Google Colab / Jupyter Notebook

### Running in Google Colab:
1. Open [Google Colab](https://colab.research.google.com/).
2. Click **Upload** and upload `cryptocurrency_risk_clustering.ipynb`.
3. In the Colab file browser (left panel), upload the dataset file `crypto_data.csv`.
4. Run each cell sequentially (**Runtime → Run all**).

### Running Locally (Jupyter Notebook):
```bash
pip install pandas numpy matplotlib scikit-learn
jupyter notebook cryptocurrency_risk_clustering.ipynb
```

---

## 📂 Repository Contents
- `crypto_data.csv`: Clean market dataset containing 26 cryptocurrencies with Volatility Percentage and Daily Trading Volume.
- `cryptocurrency_risk_clustering.ipynb`: Single, complete Google Colab / Jupyter notebook structured strictly from Phase 1 to Phase 6.
- `Project_Proposal.md`: Capstone project proposal with problem definition and methodology.
- `Project_Report.md`: Full project report detailing problem identification, implementation steps, evaluation, and results.

---

## 📊 Methodology (Phases 1 to 6)
1. **Phase 1: Problem Definition & ML Identification**: Understanding why this is an Unsupervised Clustering problem rather than Regression or Classification.
2. **Phase 2: Data Preprocessing**: Checking data shape, inspecting missing values (`df.isnull().sum()`), and summary statistics (`df.describe()`).
3. **Phase 3: Feature Selection & Scaling**: Selecting `Volatility_Percentage` and `Trading_Volume_USD`, normalized using `StandardScaler()`.
4. **Phase 4: K-Means Clustering & Elbow Method**: Finding optimal $k=4$ using inertia/WCSS plot and evaluating with `silhouette_score()`.
5. **Phase 5: Centroid Visualization**: Plotting 2D scatter plots with cluster centroids marked with red 'X'.
6. **Phase 6: Risk Category Interpretation & New Data Prediction**: Categorizing coins into 4 tiers (Low Risk, Moderate Risk, High Risk, Extreme Risk) and predicting risk for new cryptocurrency data.

---

## 📈 Discovered Risk Categories

| Tier | Category Name | Description | Key Coins |
| :---: | :--- | :--- | :--- |
| **Tier 1** | **Low Risk** | Pegged stable assets with negligible volatility (~1%) | USDT, USDC |
| **Tier 2** | **Moderate Risk** | High-liquidity, established large-cap cryptocurrencies | BTC, ETH, BNB |
| **Tier 3** | **High Risk** | Fast-growing mid-cap smart contract and DeFi platforms | SOL, ADA, DOT, LINK |
| **Tier 4** | **Extreme Risk** | Speculative meme tokens with severe price swings (>100%) | DOGE, SHIB, BONK, WIF |

---

## 👥 Team Members & Contributions

| Sl. No. | Student Name | USN | Contribution / Phase Responsibilities |
| :---: | :--- | :---: | :--- |
| 1 | **Thanisha S** | `1RUA25SCS0110` | Problem Formulation, K-Means Clustering Model (Phases 1 & 4), Report Writing |
| 2 | **Srujana Shreya Raju** | `1RUA25SCS0105` | Data Preprocessing, Cleaning & EDA (Phase 2), Colab Testing |
| 3 | **Rachana B** | `1RUA25SCS0079` | Feature Selection, StandardScaler & Visualizations (Phases 3 & 5), Documentation |
