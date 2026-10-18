<div align="center">

# Direct Market Access for Farmers

**Farmer–vendor discovery prototype using data preparation, clustering, and rule-based matching**

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![scikit--learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)

</div>

## Overview

This project explores how structured farmer and vendor data can support discovery of potential trading partners. A Streamlit interface accepts a location and product, then offers vendor or farmer candidates based on the implemented matching logic.

## Problem

Farmers and vendors may struggle to identify suitable trading partners across product and location constraints. The prototype demonstrates a data-driven workflow for narrowing possible matches; it has not yet established recommendation quality or real-world economic impact through a documented evaluation.

## Current implementation

- Loads farmer and vendor records from CSV files.
- Removes duplicate name/product records and drops rows missing location or product.
- Encodes product and location categories with scikit-learn `LabelEncoder`.
- Fits separate K-Means models for farmer and vendor feature sets.
- For vendor results, filters candidates by exact encoded location and product, then sorts by reliability score and price.
- For farmer results, uses the farmer cluster together with exact product/location filters.
- Displays up to five candidate rows in Streamlit.

## Architecture

```text
Farmer/vendor CSV files
        ↓
Data cleaning and category encoding
        ↓
Feature preparation ──→ K-Means clustering
        ↓
Location + product filtering
        ↓
Ranked vendor candidates / farmer candidates
        ↓
Streamlit results UI
```

## Tech stack

- **Language:** Python
- **UI:** Streamlit
- **Data handling:** pandas, NumPy
- **Machine learning:** scikit-learn (`LabelEncoder`, `StandardScaler`, `KMeans`)

## Run locally

The two input datasets are **not present in the current repository root**, while `app.py` expects both filenames below. Obtain or generate data you are permitted to use and place the files next to `app.py` before launching the app.

- `farmers_dataset.csv`
- `vendors_extended.csv`

Install dependencies and launch:

```bash
python -m venv .venv
# Activate the environment:
# macOS/Linux: source .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1

python -m pip install -r requirements.txt
streamlit run app.py
```

Dataset schemas should include the columns accessed by the code. Farmer records include fields such as `farmer_id`, `name`, `location`, and `product`. Vendor records additionally require `vendor_id`, `reliability_score`, and `avg_price_quintal`.

## Evaluation and limitations

No measured recommendation-quality metrics are currently documented. Before making quality claims, compare the results with a simple product/location baseline and evaluate against labelled relevant matches where available. Useful measures include Precision@K, Recall@K, NDCG@K, candidate coverage, and the share of returned matches that satisfy hard constraints.

The current approach uses integer-encoded categories as K-Means features. Such codes imply an artificial numeric order between categories, so cluster distances should be interpreted cautiously. Clustering alone does not validate the quality of the final recommendations.

## Data and privacy

Document the data source, licence, generation method, and whether records are synthetic or real. Use only data you have permission to publish, remove personal contact details, and do not commit private farmer/vendor information.

## Repository

- [Application code](app.py)
- [Exploratory notebook](Untitled7.ipynb)
