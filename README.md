# Mapping Unemployment: A Spatio-Digital Data-Driven Analysis
---

## 📋 Project Overview

This project investigates whether spatio-digital indicators—environmental data, satellite imagery, mobility patterns, and freight flows—can provide real-time insights into unemployment trends that complement traditional Bureau of Labor Statistics (BLS) measures.

By combining five unconventional data sources (NDVI, VIIRS night-time lights, AQI, mobility, and FAF freight), we test whether these signals capture distinct unemployment typologies: **cyclical, structural, frictional, and seasonal**.

**Key Research Question:** Can near real-time geospatial and digital data improve unemployment nowcasting for policymakers and economists

---

## 📊 Dataset & Methodology

### Data Sources
- **Environmental:** NDVI (vegetation), VIIRS (night-time light intensity), AQI (air quality)
- **Digital/Economic:** Mobility indices, FAF freight flows
- **Labor Market:** BLS unemployment rates
- **Geography:** 13 major U.S. metros (Chicago, Boston, San Francisco, New York, Los Angeles, Atlanta, Dallas, Miami, Houston, Phoenix, Philadelphia, Washington DC, Seattle)
- **Timeframe:**
  - **5-year analysis:** Environmental (NDVI, VIIRS, AQI) + Freight (FAF) features
  - **2-year analysis:** Environmental + Freight + Mobility features (mobility data availability limited to 2 years)
### Methods Applied

1. **Principal Component Analysis (PCA)**
   - Reduced 10+ indicators into principal components
   - Captured ~85% of variance with first 2–3 components
   - Identified economic intensity vs. mobility/environmental gradients

2. **K-Means Clustering**
   - Optimal clusters: k=5–6 (silhouette score-based)
   - Grouped metros into distinct unemployment risk profiles
   - Revealed urban–rural gradient and transition bands

3. **Gaussian Mixture Models (GMM)**
   - Smooth trajectory analysis for economic shifts
   - Validated COVID-19 shock effects and recovery patterns

4. **DBSCAN**
   - Anomaly detection for outlier metro behaviors
   - Detected sharp economic disruptions

5. **Supervised Learning (Random Forest)**
   - Predictive modeling of unemployment trends
   - 5-year dataset with lag: R² = 0.687 ± 0.072 (strong performance)
   - 2-year dataset(environmental + freight + mobility): Includes mobility features; demonstrates their predictive contribution within available data window

---

## 🔍 Key Findings

### Metro Economic Profiles

**Manufacturing-Heavy:**
- **Chicago, Dallas:** High freight intensity (motor vehicles, electronics)
- **Risk Profile:** Cyclical unemployment; vulnerable to demand shocks

**Tech & Services Dominant:**
- **Boston, San Francisco:** High night-time lights, dynamic labor churn
- **Risk Profile:** Frictional unemployment; structurally resilient

**Hybrid Economies:**
- **Atlanta, Dallas:** Mix of freight and services
- **Risk Profile:** Balanced cyclical and structural risks

**Complex Outliers:**
- **Los Angeles, New York:** Multiple unemployment types coexist
- **Risk Profile:** Manufacturing decline (structural) + service volatility (frictional)

### Feature Correlations with Unemployment

Strongest correlates (Pearson r):
- **FAF Total Freight Value:** r = 0.61
- **FAF Total Tons:** r = 0.57
- **AQI (std):** r = 0.41
- **VIIRS Night-time Radiance:** r = 0.25
- **NDVI (mean):** r ≈ -0.10

### COVID-19 Validation

- DBSCAN anomalies spiked during 2020
- GMM cluster trajectories showed either return-to-baseline or structural shifts post-COVID
- Validates hypothesis: unconventional indicators capture real economic disruptions

---

## 🛠 Tech Stack

- **Python 3.8+**
- **Libraries:** pandas, scikit-learn, scipy, matplotlib, seaborn, numpy
- **Statistical Tools:** PCA, K-Means, GMM, DBSCAN, Random Forest
- **Data Sources:** NOAA, ESA, USGS, OpenStreetMap, FAF (USDOT), BLS API
