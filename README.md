# 🚀 Applied Data Science Capstone — Falcon 9 Landing Prediction

This project analyzes SpaceX Falcon 9 first‑stage landing outcomes using a complete end‑to‑end data science workflow. The goal is to understand the factors influencing booster recovery and to build a predictive model capable of estimating landing success.

---

## 📁 Repository Structure

```
Applied-Data-Science-Capstone-Project/
│
├── Notebooks/                 # All Jupyter notebooks (API, scraping, EDA, Folium, ML)
│
├── Dashboard_py/              # Plotly Dash application (spacex-dash-app.py)
│
├── screenshots/               # Dashboard screenshots (renamed from "Dashboard Screenshots")
│
└── Data/                      # CSV dataset used by the Plotly dashboard
```

---

## 📊 Project Overview

This project follows the full IBM Data Science Capstone workflow:

### **Data Collection**
- SpaceX REST API  
- Wikipedia web scraping  

### **Data Wrangling**
- Cleaning, merging, feature engineering  

### **Exploratory Data Analysis (EDA)**
- SQL queries  
- Visualizations (payload, orbit, launch site patterns)  

### **Interactive Visual Analytics**
- Folium geospatial map  
- Plotly Dash dashboard  

### **Predictive Modeling**
- Logistic Regression, SVM, KNN, Decision Tree  
- Accuracy comparison + confusion matrices  
- Logistic Regression selected as final model  

---

## 📌 Notebook Index

| Notebook | Description |
|----------|-------------|
| **01-spacex-api-calls.ipynb** | Retrieves launch data from the SpaceX API |
| **02-spacex-webscraping.ipynb** | Scrapes Falcon 9 launch table from Wikipedia |
| **03-data-wrangling.ipynb** | Cleans and merges datasets |
| **04-eda-with-sql.ipynb** | SQL-based exploratory analysis |
| **05-eda-with-data-visualization.ipynb** | Visual EDA with Matplotlib/Seaborn |
| **06-interactive-map-with-folium.ipynb** | Folium map of launch sites |
| **07-predictive-analysis-machine-learning.ipynb** | Classification model development |

---

## 🌐 Dashboard Application

The interactive dashboard is built using **Plotly Dash**.

- **Dashboard Script:**  
  `Dashboard_py/spacex-dash-app.py`

- **Dashboard Screenshots:**  
  `screenshots/`

### Dashboard Features
- Launch site success pie chart  
- Payload vs. outcome scatter plot  
- Dropdown + slider interactivity  

---

## 🗺️ Folium Map Rendering Note

This project uses **Folium** for interactive geospatial mapping.  
Because Folium outputs HTML + JavaScript, GitHub cannot render the maps.

### 🔒 GitHub Limitation
GitHub strips JavaScript for security, so Folium maps appear as **blank output**.

### ✔ View the Fully Rendered Notebook
Use nbviewer to see the interactive map:

👉 **[(https://nbviewer.org/github/Maxpeligro/Applied-Data-Science-Capstone-Project/blob/main/Notebooks/06-interactive-map-with-folium.ipynb)]**

### ⚠ If you see “503 Service Unavailable”
This is caused by temporary GitHub API rate limits on nbviewer.

**Workaround:**
- Refresh after a few minutes  
- Or view the code directly in the notebook to confirm logic and coordinates  

---

## 🤖 Machine Learning Summary

- Models trained: Logistic Regression, SVM, KNN, Decision Tree  
- All models achieved **0.83 accuracy** on the test set  
- Confusion matrices were identical  
- **Logistic Regression** selected for its simplicity and generalization  

---

## 📄 Project Presentation

The full project presentation (PDF) is included in the repository:

👉 **Winning_Space_Race_with_Data_Science_Presentation.pdf**

---

## 🏁 Final Notes

This repository contains all code, data, dashboards, and notebooks required to reproduce the full IBM Data Science Capstone workflow.  
If you encounter any issues with rendering or interactivity, refer to the notes above or open the notebooks locally.