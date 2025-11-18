# Capstone Project: Logistic Regression for Business Survival on the San Diego County Business Listing Dataset

## Table of Contents
1. [Project Overview](#project-overview)
2. [Research Question & Hypotheses](#research-question--hypotheses)
3. [Context](#context)
4. [Data](#data)
5. [Limitations](#limitations)
6. [Delimitations](#delimitations)
7. [Data Gathering and Cleaning](#data-gathering-and-cleaning)
8. [Tools and Techniques](#tools-and-techniques)
9. [Project Outcomes](#project-outcomes)
10. [References](#references)

---

## Project Overview
<details>
<summary>Click to expand</summary>

**Project Topic:** Predictive Model for Business Survival on the Business Listing Data

This project develops a predictive model to estimate the probability of business survival in San Diego County, using publicly available business listing and population datasets. The study evaluates the feasibility of constructing an accurate logistic regression model, identifies key predictors of business longevity, and provides insights for strategic business planning.

**IRB Status:** This project does not involve human subjects research and is exempt from WGU IRB review.

</details>

---

## Research Question & Hypotheses
<details>
<summary>Click to expand</summary>

**Research Question:**  
Can a logistic regression model be constructed on the San Diego County dataset?

**Hypotheses:**
- **Null Hypothesis (H₀):** A predictive logistic regression model cannot be constructed from the research dataset.
- **Alternate Hypothesis (H₁):** A predictive logistic regression model can be constructed from the research dataset with a model accuracy of 70% or higher.

</details>

---

## Context
<details>
<summary>Click to expand</summary>

Business survival is influenced by multiple factors, including geographic location, industry sector, firm age, ownership type, and local business clustering. Prior research (Reyes & Suárez, 2022) demonstrates that spatial and economic characteristics, such as proximity to major transportation routes and local business density, significantly influence firm longevity.

This project applies logistic regression modeling to identify statistically significant predictors of business survival using the San Diego County Business Listings dataset, aiming to support data-driven decisions for entrepreneurs and investors.

</details>

---

## Data
<details>
<summary>Click to expand</summary>

**Sources:**
- **San Diego Business Listings** (City of San Diego, n.d.): 159,613 businesses with information on ownership, location, industry, and operational status.
- **2020 Census Population by ZIP Code** (SANDAG, n.d.): Population data for all 113 ZIP codes in San Diego County, including household and group-quarter populations.

**Integrated Dataset:**
- **San Diego County: Active/Closed Business Listing**
- **Total Records:** 146,481 registered businesses
- **Merge Method:** ZIP code truncated to the first five digits (`zip5`) to associate each business with its ZIP code population.

**Variables:**

| Variable | Description / Purpose | Data Type | Type (IV/DV) |
|----------|----------------------|----------|---------------|
| account_status | Indicates if a business is active or inactive | Categorical | DV |
| date_account_creation | Date when the business account was created | Continuous | IV |
| ownership_type | Type of ownership (e.g., sole proprietorship, corporation) | Categorical | IV |
| naics_sector | High-level NAICS code representing the industry sector | Categorical | IV |
| naics_description | Full textual description of the NAICS sector | Categorical | IV |
| naics_code | Detailed 2–6 digit NAICS code for the specific industry | Categorical | IV |
| address_city | City of the business location | Categorical | IV |
| address_state | State of the business location (San Diego, CA) | Categorical | IV |
| zip5 | ZIP code of the business location | Categorical | IV |
| lat | Latitude coordinate for geospatial mapping | Continuous | IV |
| lng | Longitude coordinate for geospatial mapping | Continuous | IV |
| population | Number of persons in that ZIP code | Continuous | IV |

**Note:** Latitude and longitude coordinates may occasionally fall outside San Diego County. A San Diego County shapefile can be used to validate locations and restrict the dataset to businesses within county boundaries.

**Derived Variables:**
- **Business age:** Years since account creation
- **Business group:** Categorized by life cycle stage
- **Active/Closed Rate:** Proportion of active vs. closed businesses per ZIP code, NAICS sector, or city
- **Business density:** Number of businesses per capita

</details>

---

## Limitations
<details>
<summary>Click to expand</summary>

- Latitude and longitude values may be imprecise, affecting geospatial accuracy.
- Only registered businesses are included, omitting unregistered or informal businesses.
- Population data is aggregated at the ZIP code level and reflects the 2020 Census, potentially outdated.
- External factors such as revenue, employees, economic shocks, or policy changes outside San Diego County are not included, limiting generalizability.

</details>

---

## Delimitations
<details>
<summary>Click to expand</summary>

- Focus exclusively on registered businesses within San Diego County.
- Only variables relevant to logistic regression modeling are included; `naics_description` is excluded since it overlaps with `naics_code`.
- Records in sectors 22 (“Utilities”) and 92 (“Public Administration”) are removed.
- Outliers in `date_account_creation` are retained to capture long-standing businesses.

</details>

---

## Data Gathering and Cleaning
<details>
<summary>Click to expand</summary>

- Data downloaded as a CSV from Kaggle, compiled from the City of San Diego Business Listings and SANDAG 2020 Census Population datasets.
- Data cleaning includes encoding categorical variables, imputing missing values, and validating geospatial coordinates.
- Derived variables calculated for business age, life cycle group, active/closed rate, and business density.
- Data sparsity is less than 10%.

</details>

---

## Tools and Techniques
<details>
<summary>Click to expand</summary>

- **Programming Language:** Python
- **Statistical Tests:** Shapiro-Wilk, Levene (for assumption checking; not required for logistic regression)
- **Handling Imbalanced Classes:** SMOTE applied to training data
- **Modeling Approach:** Logistic Regression, Random Forest, Gradient Boosting, XGBoost, LightGBM
- **Evaluation:** Cross-validation, independent test set (20%)
- **Interpretability:** SHAP analysis for feature importance
- **Clustering:** Unsupervised segmentation to uncover meaningful data patterns
- **Visualization:** Univariate and bivariate plots, tables, interactive dashboards

**Justification:** Python offers a cost-effective, flexible, and scalable platform for end-to-end analytics compared to SAS or R.

</details>

---

## Project Outcomes
<details>
<summary>Click to expand</summary>

- Develop a logistic regression model predicting business survival based on variables such as business age, ownership type, and industry sector.
- Identify significant determinants of business longevity and support strategic business planning.
- Estimate survival probabilities and uncover high-risk or underserved areas at the ZIP code level.
- Provide actionable insights for entrepreneurs and investors to enhance long-term business sustainability.

</details>

---

## References
<details>
<summary>Click to expand</summary>

- City of San Diego. (n.d.). *San Diego Business Listings*. City of San Diego Open Data Portal.  
- San Diego Association of Governments (SANDAG). (n.d.). *2020 Census Population by ZIP Code*. SANDAG Open Data Portal.  
- Reyes, J., & Suárez, L. (2022). *The impact of location and road class on firm survival*. Journal of Business Geography.  
- Society of Actuaries. (2019). *Standard practices in multivariate statistical and predictive modeling*.  
- Nemade, S., Bharadi, P., Alegavi, S., & Marakarkandy, B. (2023). *SMOTE in predictive modeling*.  
- Wang, H., & Guedes, R. (2024). *Logistic regression for SME failure prediction*.  
- García-Vidal, J., et al. (2025). *Determinants of business closure intention*.  
- Ramirez, K. (2025). *San Diego County Business Listing Dataset*.  

</details>
