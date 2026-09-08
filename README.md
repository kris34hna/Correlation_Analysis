# Movie Correlation Analysis

 Cleaning a movies dataset and finding which factors — budget, votes, runtime — most strongly drive gross box office earnings.

---

##  Brief Summary

A data cleaning and correlation analysis project on a movies dataset using Pandas, Matplotlib, Seaborn, and SciPy — identifying that **budget and votes are the strongest predictors of gross earnings**, with Spearman correlation chosen over Pearson after verifying non-normal distributions.

---

##  Overview

This project takes a raw movies dataset, performs thorough data cleaning (handling nulls, outliers, type conversions, and feature extraction), then conducts a focused correlation analysis to determine which numeric features best explain box office gross earnings. The analysis goes beyond simply computing a heatmap — it statistically validates **which correlation method (Pearson vs Spearman) is appropriate** for each variable pair using residual plots and normality tests.

---

##  Problem Statement

The movie industry involves massive financial risk. Understanding what drives gross earnings can help studios, producers, and analysts make smarter decisions. This project aims to answer:

> *"Which factors — budget, votes, runtime — are most strongly correlated with a movie's gross box office earnings, and which correlation method is statistically appropriate for each?"*

Specific questions explored:
1. How correlated is **budget** with gross earnings?
2. How correlated are **votes** with gross earnings?
3. Is the relationship between these variables **linear or non-linear**?
4. Should we use **Pearson or Spearman** correlation — and why?

---

##  Dataset

| Detail | Info |
|--------|------|
| File | `movies.csv` |
| Domain | Movie Industry |

**Key Columns:**
| Column | Description |
|--------|-------------|
| `name` | Movie title |
| `rating` | Age rating (G, PG, R, etc.) |
| `genre` | Movie genre |
| `year` | Release year |
| `released` | Full release date string |
| `score` | IMDb score |
| `votes` | Number of audience votes |
| `director` | Director name |
| `writer` | Writer name |
| `star` | Lead actor/actress |
| `country` | Country of production |
| `budget` | Production budget |
| `gross` | Box office gross earnings |
| `company` | Production company |
| `runtime` | Movie duration (minutes) |

---

##  Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Python** | Core language |
| **Pandas / NumPy** | Data manipulation & cleaning |
| **Matplotlib / Seaborn** | Visualizations (heatmaps, boxplots, histograms, residual plots) |
| **SciPy** | Shapiro-Wilk normality test |
| **Jupyter Notebook** | Development environment |

---

##  Methods

1. **Initial Inspection** — Checked shape, data types, unique value counts, duplicates, and missing value percentages.

2. **Data Cleaning**
   - Dropped rows with nulls in critical columns (`rating`, `released`, `score`, `votes`, `writer`, `star`, `country`, `gross`, `company`, `runtime`)
   - Handled missing `budget` values by filling with **genre-level median** (genre-aware imputation) — 3 remaining nulls filled with global median
   - Converted `budget`, `gross`, `votes`, `runtime` to `int64`
   - Extracted correct year from `released` string column using regex → created `yearcorrect` column
   - Sorted dataset by `gross` in descending order

3. **Correlation Matrix (Pearson & Spearman)** — Computed both methods and visualized as heatmaps to compare results.

4. **Statistical Method Selection (Budget vs Gross)**
   - Plotted **boxplot & histogram** of `budget` to assess distribution and outliers
   - Computed **skewness** of `budget`
   - Built **residual plot** (linear regression fit) to test linearity
   - Ran **Shapiro-Wilk normality test** → result: not normally distributed → ❌ Pearson not appropriate → ✅ Spearman used

5. **Statistical Method Selection (Votes vs Gross)**
   - Same pipeline as above for `votes`
   - Shapiro-Wilk confirmed non-normal distribution → ✅ Spearman used

6. **Final Spearman Correlations** — Computed Spearman correlation for `budget` vs `gross` and `votes` vs `gross` separately and reported final coefficients.

---

##  Key Insights

-  **Budget and votes** are the two features most highly correlated with gross earnings.
-  **Budget vs Gross (Spearman): 0.55** — moderate positive correlation. As production budget increases, gross earnings tend to increase.
-  **Votes vs Gross (Spearman): 0.74** — moderate positive correlation. More audience votes (a proxy for popularity/reach) are associated with higher gross earnings.
-  Both `budget` and `votes` are **not normally distributed** (confirmed via Shapiro-Wilk test, p < 0.05) and contain **outliers** — making Pearson correlation unreliable for these variables.
-  **Residual plots** confirmed the relationship between Budget/Gross and Votes/Gross is **non-linear** — further justifying Spearman over Pearson.
-  Pearson and Spearman heatmaps gave **different correlation coefficients**, highlighting why blindly applying Pearson without checking assumptions is statistically incorrect.
-  **Practical takeaway:** Movies with higher budgets and more audience engagement (votes) tend to earn more at the box office — but the relationship is moderate, not deterministic.

---

##  Results & Conclusion

After cleaning the dataset and statistically validating the appropriate correlation method, the analysis concludes that **budget (0.55) and votes (0.74)** have the highest positive correlations with gross earnings. Both relationships are moderate — meaning budget and popularity are important but not the only factors driving box office success. Critically, the project demonstrates **why choosing the right correlation method matters**: Spearman was selected over Pearson after confirming non-normal distributions and non-linear relationships via residual plots and the Shapiro-Wilk test.

---

##  Author & Contact
| | |
|--|--|
|**Name** | KRISHNA |
|**LinkedIn** | www.linkedin.com/in/krishna-prajapati-26a106231 |
|**GitHub** | https://github.com/ |


⭐ **If you found this project helpful, consider giving it a star!**
