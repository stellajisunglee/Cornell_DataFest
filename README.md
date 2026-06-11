# Bespoke Marketplace — DataFest 2026

**Cornell MSBA DataFest 2026** | Team: Stella Lee, Alexander Warmus, Kevin Flannery

## Overview

End-to-end analysis of a fictional handmade goods marketplace ("Bespoke") exploring what drives customer satisfaction, artisan performance, and platform GMV. Built over a 48-hour competition sprint.

## Research Questions

- What factors most strongly predict buyer satisfaction (star ratings)?
- Which artisans are at risk of churning buyers — and how much GMV is at stake?
- How much of delivery dissatisfaction is attributable to carriers vs. artisans?
- Can we classify an artisan's probability of receiving a 1-star review?

## Methods

| Area | Techniques |
|------|-----------|
| EDA & segmentation | Pandas, Seaborn, revenue concentration analysis |
| Satisfaction drivers | OLS regression, VIF checks |
| Artisan risk profiling | "Danger Zone" 2×2 matrix (satisfaction × revenue), logistic regression |
| Complaint themes | BERTopic (topic modeling on free-text feedback) |
| 1-star classifier | Gradient Boosting + SHAP feature importance, stratified CV, AUC evaluation |
| Delivery attribution | Carrier vs. artisan logistics accountability framework |

## Repo Structure

```
.
├── bespoke.ipynb        # Main analysis notebook
└── README.md
```

> **Data files are not included in this repo** (see `.gitignore`). The notebook expects the following CSVs in the same directory at runtime:
> `marketplace_transactions.csv`, `transaction_details.csv`, `feedback.csv`, `items.csv`, `artisans.csv`, `buyers.csv`, `payments.csv`, `item_category_translation.csv`, `location_data.csv`

## Setup

```bash
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn shap nltk
jupyter notebook bespoke.ipynb
```

Python 3.9+ recommended.
