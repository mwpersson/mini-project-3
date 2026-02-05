
# Mini Project 3: Unsupervised Discovery

## Problem Description

**Business Problem:**  
Retail businesses need to understand their customer base to optimize marketing strategies, personalize offers, and improve customer lifetime value. This project addresses the problem of identifying distinct customer segments based on purchasing behavior and income, while also detecting unusual customers for targeted interventions.

**Why Unsupervised Learning:**  
Customer segments are unknown beforehand, making unsupervised learning ideal. K-means clustering discovers natural groupings without predefined labels, while anomaly detection identifies outliers without labeled training data. This enables data-driven segmentation without requiring historical classifications.

---

## Dataset Description

**Source & Size:**  
Mall Customers dataset containing 200 customer records with 5 features. Available at [https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python)

**Features:**
- `CustomerID`: Unique identifier
- `Gender`: Male/Female
- `Age`: Customer age in years
- `Annual Income (k$)`: Annual income in thousands of dollars
- `Spending Score (1-100)`: Engagement metric (1-100 scale)

**Preprocessing:**
- Column names normalized (lowercased, spaces removed, special characters stripped)
- Gender one-hot encoded for clustering algorithms
- All features standardized using `StandardScaler` for fair distance calculations
- No missing values or duplicates detected

---

## Setup Instructions

**Install Dependencies:**
```bash
pip install -r requirements.txt
```

**Get the Data:**  
Place `Mall_Customers.csv` in the `data/` directory:
```
mini-project-3/
├── data/
│   └── Mall_Customers.csv
├── notebooks/
│   └── analysis.ipynb
└── requirements.txt
```

**Run the Notebook:**
```bash
jupyter notebook notebooks/analysis.ipynb
```

---

## Results Summary

**Optimal K Selection:**  
K = 11 was chosen because the silhouette score reaches a local maximum with strong cluster separation, while the elbow curve shows diminishing returns beyond this point. Given the dataset size of 200 customers, K = 11 balances statistical quality with interpretability and business actionability.

**Cluster Descriptions:**
- **Cluster 0:** older men, medium income, medium spending
- **Cluster 1:** younger men, below average income, above average spending
- **Cluster 2:** middle age women, low income, low spending
- **Cluster 3:** younger women, high income, high spending
- **Cluster 4:** older women, medium income, medium spending
- **Cluster 5:** middle age men, high income, low spending
- **Cluster 6:** younger women, medium income, medium spending
- **Cluster 7:** younger men, high income, high spending
- **Cluster 8:** younger women, low income, high spending
- **Cluster 9:** middle age women, high income, low spending
- **Cluster 10:** older men, low income, low spending

**Anomaly Detection:**  
Using Isolation Forest with 15% contamination, 30 anomalies were detected. Key types:
- **High-Spending Low-Income:** Annual income <25k, spending score >80
- **Low-Engagement Customers:** Spending score ≤10, potential churn risk
- **VIP Outliers:** Extremely high income (>110k) with extreme spending patterns

**Key Business Insights:**  
The analysis reveals three actionable customer archetypes. Premium customers in high-income clusters represent immediate opportunities for loyalty programs and exclusive offers. Conversely, high-engagement low-income customers, though economically constrained, show strong brand affinity and may drive growth through referrals or niche market positioning. Finally, the detected anomalies enable personalized interventions: VIP customers warrant concierge-level service, while disengaged customers require reactivation campaigns or cost-benefit reassessment. By layering clustering for segment-wide campaigns with anomaly detection for individual targeting, the business can optimize marketing spend and maximize customer lifetime value across all tiers.

## Team Contributions
- Michael: EDA, Clustering Analysis,  Dimensionality Reduction, Anomaly Detection, Analysis (Clustering), Report (Introduction, Methodology), Readme
- Sepehr: Analysis (Dimensionality Reduction, Anomaly Detection), Integrated Analysis, Report (Methodology, Results, Discussion)