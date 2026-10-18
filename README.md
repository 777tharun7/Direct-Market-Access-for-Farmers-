# Direct Market Access for Farmers

A machine-learning project exploring farmer-to-vendor matching using farmer and vendor attributes. The goal is to surface relevant potential trading partners and reduce reliance on informal discovery.

## Problem
Farmers may have difficulty finding vendors whose product requirements, location, pricing, and reliability expectations align with their needs. This project explores data-driven matching to help rank candidate partners.

## Features described by the project
- Bidirectional candidate recommendations for farmers and vendors.
- Data preparation, including handling missing values, duplicates, and categorical features.
- K-Means clustering to group records using selected attributes.
- Matching attributes including product compatibility, location, vendor reliability, and price-related features.
- Sample output to illustrate the intended user experience.

## Dataset
The previous project documentation describes:
- farmers_dataset.csv — 4,265 farmer records.
- vendors_extended.csv — 4,825 vendor records.

Confirm these counts against the actual files before each release. Document the source, licence, data-generation method, and whether records are synthetic or real. Do not publish private personal data.

## Methodology
1. Inspect schemas, duplicates, missing values, and category distributions.
2. Clean records using documented rules.
3. Encode categorical variables and scale numeric variables where appropriate.
4. Cluster farmer and vendor records using the implemented K-Means configuration.
5. Generate candidate matches using product compatibility and relevant location, price, and reliability constraints.
6. Return candidate lists to the user.

**Evaluation note:** Clustering alone does not prove recommendation quality. Evaluate the final matching logic separately.

## Evaluation plan
Do not claim improved matching quality until measured. Recommended checks:
- Compare with a simple product-and-location baseline.
- Measure Precision@K / Recall@K if labelled relevant matches exist.
- Measure the percentage of recommendations satisfying product and location constraints.
- Measure the percentage of farmers and vendors receiving at least one valid candidate.
- Use NDCG@K or another ranking metric if relevance labels are available.

| Evaluation item | Result |
|---|---|
| Baseline definition | Add implemented baseline |
| Test set / validation method | Add actual method |
| Precision@K / Recall@K | Add measured result or mark unavailable |
| Valid-match rate | Add measured result |
| Coverage | Add measured result |

## Technology
The existing documentation lists Python, Pandas, NumPy, Matplotlib, and scikit-learn components including LabelEncoder, StandardScaler, and KMeans. Confirm these against the current code and dependency files.

## Reproduction
Add the actual Python version, dependency installation command, dataset placement, and commands/notebooks to run cleaning, clustering, matching, and evaluation.

## Limitations and future work
Clusters do not guarantee the best trading partner. Synthetic examples do not establish real-world economic impact. Distance, transport cost, seasonal availability, and changing market prices may improve matching if reliable data is available. Protect farmer and vendor data and explain how recommendations are generated.

## Contributors
- D. Tharun
- CH. Harsha Luke
- K. Navadeep

## Source
[View repository](https://github.com/777tharun7/Direct-Market-Access-for-Farmers-)
