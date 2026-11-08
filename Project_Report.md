# Cryptocurrency Risk Analysis Using K-Means Clustering

**Course:** CS2235 - Data Science Capstone Project  
**Program:** B.Sc. (Hons.) Data Science, Semester III  
**Institution:** School of Computer Science and Engineering, RV University, Bengaluru  
**Student Name:** Thanisha S Rao  

---

## 1. Introduction & Problem Statement
Cryptocurrencies are digital financial assets that have gained massive popularity. However, they exhibit significant differences in market behavior:
- Some cryptocurrencies (like Bitcoin and Ethereum) have high liquidity and moderate price swings.
- Stablecoins (like Tether and USD Coin) are pegged to fiat currencies and have near-zero volatility.
- Meme coins and speculative tokens (like Dogecoin, Shiba Inu, and Bonk) experience extreme, sudden price fluctuations.

### Objective
To analyze cryptocurrency market data and group cryptocurrencies into distinct risk categories based on:
1. **Price Volatility (%)**: How drastically the price moves up and down.
2. **Trading Volume (USD)**: How much liquidity and trading activity exists.

---

## 2. Machine Learning Problem Identification
A primary conceptual requirement in Data Science is choosing the right machine learning paradigm:
- **Regression:** Predicts a continuous numeric outcome (e.g., predicting Bitcoin's dollar price next week).
- **Classification:** Predicts discrete categories using pre-labeled training data (e.g., classifying an email as Spam or Not Spam).
- **Clustering (Unsupervised Learning):** Groups similar data points based on feature similarity without predefined labels.

**Why Clustering?**  
In the financial market, there are no official, predefined "ground truth" risk labels assigned to cryptocurrencies by regulators. Therefore, we cannot train a supervised classifier. Instead, we use **Unsupervised Learning (K-Means Clustering)** to find natural groupings directly from data.

---

## 3. Dataset Description
The project uses a clean dataset `crypto_data.csv` comprising 26 prominent cryptocurrencies across different categories (Store of Value, Smart Contracts, DeFi, Meme coins, and Stablecoins).

| Feature Name | Data Type | Description |
| :--- | :--- | :--- |
| `Symbol` | Categorical | Ticker symbol (e.g., BTC, ETH, SOL, DOGE) |
| `Name` | Categorical | Full name of the cryptocurrency |
| `Category` | Categorical | Functional sector (e.g., Layer 1, Meme, Stablecoin) |
| `Volatility_Percentage` | Numerical (Float) | Annualized price volatility percentage |
| `Trading_Volume_USD` | Numerical (Float) | Average daily trading volume in US Dollars |

---

## 4. Methodology & Implementation Phases

### Phase 1: Data Understanding & Exploration
- Loaded data using `pandas.read_csv()`.
- Checked data structure, shapes, and verified that there are no missing values using `df.isnull().sum()`.
- Inspected statistical distributions using `df.describe()`.

### Phase 2: Feature Selection & Scaling
- Selected the two key numerical features: `Volatility_Percentage` and `Trading_Volume_USD`.
- **StandardScaler Normalization:** Because trading volumes are in billions of dollars ($10^9$) while volatility is in percentages ($10^1$ to $10^2$), volume would artificially dominate distance calculations in Euclidean space. We applied `StandardScaler()` so each feature has $\mu = 0$ and $\sigma^2 = 1$, matching the technique from **Lab Program 9**.

### Phase 3: Determining Optimal Clusters (Elbow Method)
- Evaluated Within-Cluster Sum of Squares (Inertia) across $k = 2$ to $k = 7$.
- An "elbow" point is observed around $k = 4$, which provides a balanced and intuitive division into risk tiers.

### Phase 4: K-Means Clustering & Evaluation
- Trained `KMeans(n_clusters=4, random_state=42)`.
- Evaluated clustering quality using **Silhouette Score**:
  $$\text{Silhouette Score} = \frac{b - a}{\max(a, b)}$$
  The silhouette score validates that clusters are well-separated and cohesive.

### Phase 5: Centroid Visualization
- Generated scatter plots displaying clusters with distinct colors.
- Plotted cluster centers (**Centroids**) marked with red 'X' symbols, showing the average profile of each cluster.

### Phase 6: New Data Prediction
- Used `scaler.transform()` and `kmeans.predict()` to predict the risk cluster for new unseen cryptocurrencies (e.g., a newly launched token with specified volatility and trading volume).

---

## 5. Results & Discussion

The model successfully grouped the 26 cryptocurrencies into 4 distinct risk tiers:

| Risk Tier | Characteristics | Example Cryptocurrencies |
| :--- | :--- | :--- |
| **Tier 1: Low Risk (Stable)** | Negligible volatility (~1%), high volume | USDT, USDC |
| **Tier 2: Moderate Risk (Large Cap)** | Moderate volatility (~45-60%), very high volume | BTC, ETH, BNB |
| **Tier 3: High Risk (Mid-Cap / Altcoins)** | Higher volatility (~70-95%), moderate volume | SOL, ADA, DOT, LINK, AVAX |
| **Tier 4: Extreme Risk (Meme / Speculative)** | Extreme volatility (>100%), variable volume | DOGE, SHIB, BONK, WIF, FLOKI |

---

## 6. Conclusion
- The K-Means clustering algorithm successfully separated cryptocurrencies based on price volatility and liquidity.
- Stablecoins formed a clear low-risk cluster, whereas meme tokens separated into the extreme-risk tier.
- The pipeline is simple, interpretable, and reproducible on Google Colab and Jupyter Notebook.

---

## 7. References
1. RV University CS2235 Data Science Laboratory Manual (Programs 8 & 9: PCA and K-Means Clustering).
2. Scikit-learn Documentation: `sklearn.cluster.KMeans` and `sklearn.preprocessing.StandardScaler`.
3. McKinney, Wes. *Python for Data Analysis*, O'Reilly Media.
