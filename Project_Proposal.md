# RV University - School of Computer Science and Engineering
## CS2235 - Data Science Capstone Project
### Title: Cryptocurrency Risk Analysis using K-Means Clustering

**Team Members:**
1. **Thanisha S** (USN: `1RUA25SCS0110`)
2. **Srujana Shreya Raju** (USN: `1RUA25SCS0105`)
3. **Rachana B** (USN: `1RUA25SCS0079`)

**Program:** B.Sc. (Hons.) Data Science, Semester III  
**Course Code:** CS2235 - Data Science  

---

## 1. Problem Statement
Cryptocurrencies are digital assets known for extreme price fluctuations and different levels of trading activity. For retail investors and beginners, it is difficult to determine which cryptocurrencies are relatively safe, moderate, or highly speculative. 

**Research Question:** How can we group different cryptocurrencies into meaningful risk categories based on their price volatility (how much their price changes) and trading volume (how much they are traded) using unsupervised machine learning?

---

## 2. Machine Learning Problem Identification
In machine learning, tasks are divided into three main paradigms:
1. **Supervised Learning - Regression:** Predicts a continuous numerical value (e.g., predicting exact future price of Bitcoin).
2. **Supervised Learning - Classification:** Predicts a predefined categorical label using labeled historical data (e.g., classifying a transaction as fraudulent or legitimate).
3. **Unsupervised Learning - Clustering:** Discovers natural groupings and hidden patterns in data without predefined labels or target outputs.

**Why Clustering for our Project?**
Cryptocurrencies do not come with pre-assigned official "risk labels" provided by financial regulatory authorities. Therefore, this problem cannot be solved using classification or regression. We use **Unsupervised Learning (K-Means Clustering)** to discover natural risk tiers directly from market data.

---

## 3. Project Workflow & Phases

### Phase 1: Problem Definition & Data Understanding
- Define objectives: Group cryptocurrencies based on price volatility and trading volume.
- Identify the dataset features: Symbol, Name, Category, Volatility Percentage, and Trading Volume.

### Phase 2: Data Preprocessing & Exploratory Data Analysis (EDA)
- Check for missing/null values (`df.isnull().sum()`).
- Statistical summary of the dataset (`df.describe()`).
- Data cleaning and inspection (`df.head()`, `df.info()`).

### Phase 3: Feature Selection & Scaling (StandardScaler)
- Select the two key numerical features: `Volatility_Percentage` and `Trading_Volume_USD`.
- Apply **StandardScaler** to normalize features to mean = 0 and variance = 1, ensuring trading volume does not dominate volatility due to magnitude differences.

### Phase 4: K-Means Clustering & Model Evaluation
- Determine the optimal number of clusters ($k$) using the **Elbow Method** (Inertia / WCSS).
- Train the **K-Means Clustering** model with the chosen $k=4$ (`KMeans(n_clusters=4, random_state=42)`).
- Evaluate cluster quality using the **Silhouette Score** (`silhouette_score`).

### Phase 5: Cluster Visualization & Centroid Analysis
- Create 2D scatter plots showing the clusters and their centroids (`plt.scatter(kmeans.cluster_centers_)`).
- Predict the risk category for unseen/new cryptocurrency data using `kmeans.predict()`.

### Phase 6: Risk Category Interpretation
- Analyze and label the 4 discovered clusters into clear student-friendly risk tiers:
  - **Cluster 0: Low Risk / Stable Assets** (Very low volatility, high volume - e.g., USDT, USDC)
  - **Cluster 1: Moderate Risk / Established Coins** (Moderate volatility, high volume - e.g., BTC, ETH)
  - **Cluster 2: High Risk / Mid-Cap Altcoins** (Higher volatility, moderate volume - e.g., SOL, ADA, LINK)
  - **Cluster 3: Extreme Risk / Speculative Coins** (Extremely high volatility, lower volume - e.g., DOGE, SHIB, BONK)

---

## 4. Expected Deliverables & GitHub Repository Structure
```
Crypto-Risk-Clustering-Beginner/
│
├── crypto_data.csv                              # Clean dataset with 26 cryptocurrencies
├── cryptocurrency_risk_clustering.ipynb        # Complete Google Colab / Jupyter Notebook (Phases 1-5)
├── Project_Report.md                           # Simple, student-friendly academic report
└── README.md                                   # Step-by-step project guide & Colab link
```

---

## 5. Technology Stack (Beginner Level)
- **Language:** Python 3
- **Libraries:**
  - `pandas` - Data loading, cleaning, and table manipulation
  - `numpy` - Numerical calculations
  - `matplotlib.pyplot` - Scatter plots and Elbow curve visualization
  - `sklearn.preprocessing.StandardScaler` - Feature normalization
  - `sklearn.cluster.KMeans` - K-Means clustering algorithm
  - `sklearn.metrics.silhouette_score` - Cluster cohesion and separation validation
