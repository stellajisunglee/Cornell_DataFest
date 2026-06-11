# Bespoke Marketplace — DataFest 2026

**Cornell MSBA DataFest 2026** | Team: Stella Lee, Alexander Warmus, Kevin Flannery

## Overview

End-to-end analysis of a fictional handmade goods marketplace ("Bespoke") exploring what drives customer satisfaction, artisan performance, and platform GMV. Built over a 72-hour competition sprint.

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
| Complaint theme extraction | BERTopic (topic modeling on free-text 1-star reviews) |
| 1-star classifier | Gradient Boosting + SHAP feature importance, stratified CV, AUC evaluation |
| Delivery attribution | Carrier vs. artisan logistics accountability framework |

## Key Findings

- **Delivery is the dominant satisfaction driver.** On-time orders average 4.2★; orders just 5–10 days late drop to 1.9★. 76% of all 1-star reviews are delivery complaints.
- **Late delivery is mostly artisan-caused.** 57% of late deliveries trace back to slow shipping by the artisan, not the carrier.
- **The "Danger Zone" is a concentrated risk.** 18% of artisans (low satisfaction, high revenue) contribute 32% of GMV while generating 49% of 1-star reviews and satisfaction has near-zero correlation with revenue (r = -0.022), meaning the platform has no natural self-correcting mechanism.
- **Three interventions proposed:** recalibrate delivery estimates using historical shipping data, introduce a verified fast-shipper badge (avg ship time < 3 days, rating > 4★), and audit carrier performance by region to address the remaining 43% of carrier-caused delays.
- **The 1-star classifier is intentionally limited.** Built on pre-transaction signals only (listing quality, tenure, price tier), it achieves AUC ~0.57 (near chance). This is itself a finding: observable artisan characteristics have little predictive power without delivery performance data, confirming that delivery behavior is the dominant driver of poor outcomes rather than anything identifiable upfront.

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
