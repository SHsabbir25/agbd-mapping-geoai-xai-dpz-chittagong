# 🌲 Explainable GeoAI Framework for Aboveground Biomass Density Mapping — DPZ, Chittagong

> Integrating GEDI L4A spaceborne lidar, Sentinel-2 multispectral imagery, Random Forest regression, and Explainable AI (SHAP + Surrogate Models) to map and interpret aboveground biomass density (AGBD) in the Development Planning Zone (DPZ) of Chittagong, Bangladesh.

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-RandomForest-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![SHAP](https://img.shields.io/badge/SHAP-Explainable%20AI-FF6F00?style=for-the-badge&logo=leaflet&logoColor=white)
![Rasterio](https://img.shields.io/badge/Rasterio-Geospatial%20Raster-4B8BBE?style=for-the-badge&logo=qgis&logoColor=white)
![GeoPandas](https://img.shields.io/badge/GeoPandas-Vector%20Data-139C5A?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C?style=for-the-badge&logo=plotly&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Plots-4C72B0?style=for-the-badge&logo=python&logoColor=white)
![Sentinel-2](https://img.shields.io/badge/Sentinel--2-Multispectral%20Imagery-1A73E8?style=for-the-badge&logo=satellite&logoColor=white)
![GEDI](https://img.shields.io/badge/GEDI%20L4A-Spaceborne%20Lidar-228B22?style=for-the-badge&logo=nasa&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)
![Google Earth Engine](https://img.shields.io/badge/Google%20Earth%20Engine-Preprocessing-4285F4?style=for-the-badge&logo=google&logoColor=white)

---

## 📌 Overview

This project develops an integrated **GeoAI and Explainable AI (XAI)** framework to model aboveground biomass density (AGBD) across the DPZ region of Chittagong, Bangladesh. The pipeline fuses **GEDI L4A** spaceborne lidar biomass estimates with **Sentinel-2** multispectral features, trains a **Random Forest** regressor, and applies **SHAP** and **surrogate decision tree models** to interpret model behavior at both local and global scales.

---

## 🛰️ Data Sources

| Source | Description |
|---|---|
| **GEDI L4A** | Monthly AGBD products (2022), quality & uncertainty filtered in GEE |
| **Sentinel-2** | Cloud-filtered growing season composite, 12 spectral bands |
| **Vegetation Indices** | NDVI, CCCI (Canopy Chlorophyll Content Index), SLAVI (Specific Leaf Area Vegetation Index) |

---

## ⚙️ Features Used
```python
FEATURES = ['B2', 'B3', 'B4', 'B5', 'B6', 'B7', 'B8', 'B11', 'B12', 'NDVI', 'CCCI', 'SLAVI']
LABEL    = ['agbd_mean']
```

---

## 🔬 Methodology

**1. GEDI Preprocessing (Google Earth Engine)**
Quality flag filtering, relative uncertainty thresholding, terrain slope masking, and upper biomass constraints applied to GEDI L4A 2022 monthly products.

**2. Sentinel-2 Feature Engineering**
Cloud-filtered imagery composited for the growing season. Spectral bands and vegetation indices spatially aligned with GEDI footprints.

**3. Random Forest Regression**
Hyperparameter tuning via GridSearchCV (n_estimators, max_depth, min_samples_split) with 5-fold cross-validation. Final model evaluated with 10-fold cross-validation RMSE.

**4. AGBD Map Generation**
Pixel-wise prediction across the full DPZ extent, exported as GeoTIFF for use in GIS platforms.

**5. Explainable AI (XAI)**
- **MDI** — Mean Decrease Impurity for embedded feature importance
- **PFI** — Permutation Feature Importance (model-agnostic)
- **SHAP** — Beeswarm and violin plots for directional feature contributions
- **Surrogate Model** — Decision Tree (max_depth=3) trained on RF predictions for global interpretability

---

## 🏙️ Planning Applications

This framework directly supports urban and regional planning in DPZ and URP contexts:

1. Green infrastructure and urban forest planning
2. Climate resilience and carbon stock assessment
3. Land use zoning and environmental impact assessment
4. Ecosystem service valuation in peri-urban and protected zones

By integrating XAI, planners can understand not only *where* biomass is high or low, but *why* — enabling evidence-based and transparent planning decisions.

---

## 📁 Repository Structure
```
agbd-mapping-geoai-xai-dpz-chittagong/
│
├── Spatial_Machine_Learning_for_Regression_Analysis_With_XAI.ipynb
├── README.md
└── requirements.txt
```

---

## 🔧 Getting Started
```bash
# Clone the repository
git clone https://github.com/SHsabbir25/agbd-mapping-geoai-xai-dpz-chittagong.git
cd agbd-mapping-geoai-xai-dpz-chittagong

# Install dependencies
pip install rasterio earthpy geopandas scikit-learn shap pandas numpy matplotlib seaborn joblib
```

Open the notebook in **Google Colab** and mount your Google Drive with the required datasets.

---

## 📄 License

MIT License
