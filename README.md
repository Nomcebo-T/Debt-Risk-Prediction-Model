# Debt Risk Classification for South African Young Professionals
*A Machine Learning Approach Aligned with Stats SA Insights*

## 1. Project Overview

### Business Problem
Financial institutions in Johannesburg struggle to assess debt risk for young professionals (22-35) using traditional credit scoring. This project:
* Classifies individuals into 5 risk tiers: **Critical Risk**, **High Risk**, **Moderate Risk**, **Low Risk**, **Very Low Risk**
* Identifies key financial stress indicators using Stats SA-aligned simulated data
* Provides interpretable insights for lenders and policymakers

### Key Objectives
- ✅ Achieve >85% accuracy in risk classification
- ✅ Validate feature importance against SARB debt guidelines
- ✅ Highlight demographic risk patterns (age, industry, income tiers)

## 2. Dataset & Preprocessing

### Dataset Simulation (Guided by Stats SA)

| Feature | Stats SA Alignment |
|---------|-------------------|
| Age (22-35) | Focused on high-risk youth demographic |
| Salary (ZAR) | Simulated per Johannesburg income tiers (Median: R15k–R35k) |
| Rent | 30-40% of salary (Johannesburg avg.) |
| Transport | 15-20% of income (minibus taxi reliance) |
| DTI Ratio | 5-30% (SARB risk thresholds) |

### Feature Engineering

| Technique | Key Features Created | Business Rationale |
|-----------|---------------------|-------------------|
| Log Transforms | `Log_Salary`, `Log_Total_Expenses` | Handle right-skewed income data |
| Ratio Features | `Expense_to_Salary_Ratio (>50% = risky)` | Stats SA: >60% → financial distress |
| Binning | `Salary_Bin` (Low: <R10k, High: >R25k) | Align with income quartiles |
| Interaction Terms | `Salary_DTI_Interaction` | Captures debt burden relative to income |

## 3. Methodology

### Model Comparison

| Metric | XGBoost | Random Forest | Winner |
|--------|---------|--------------|--------|
| Accuracy | 87.55% | 85.00% | XGBoost |
| Precision (Macro) | 0.86 | 0.79 | XGBoost |
| Recall (High Risk) | 0.62 | 0.30 | XGBoost |
| F1 (Weighted) | 0.87 | 0.83 | XGBoost |

**Key Findings:**
* XGBoost outperformed RF by **2.5% accuracy** and **significantly improved recall for High Risk cases** (62% vs. 30%).
* RF struggled with minority classes due to class imbalance.

### Validation Strategy
* **Stratified 80-20 train-test split** (maintained class proportions)
* **5-fold cross-validation** (confirmed robustness)

## 4. Results & Insights

### Top 5 Features (XGBoost)
1. **Salary_DTI_Interaction** (24.9%) → *Validates SARB's debt-to-income focus*
2. **Debt Repayment (ZAR)** (22.3%) → Direct liquidity indicator
3. **Groceries (ZAR)** (10.2%) → Reflects 2023 food inflation (>10%)
4. **Rent (ZAR)** (9.4%) → Johannesburg's high housing costs
5. **Transport (ZAR)** (6.7%) → Commuting burden

### Demographic Risk Patterns

| High-Risk Group | Low-Risk Group |
|-----------------|----------------|
| • Age 22-28, Salary < R15k | • IT/Finance professionals |
| • DTI > 40% | • Salary > R25k |
| • Rent > 45% of income | • DTI < 20% |

**Stats SA Alignment:**
* Matches QLFS data on youth financial vulnerability
* Confirms SARB's warning on unsecured credit reliance

## 5. Business Implications

### For Lenders
* **Automate risk tiering** using `Salary_DTI_Interaction` and `Expense_to_Salary_Ratio`
* **Flag high-risk applicants** (DTI > 40% + Rent > 45% salary)

### Policy Recommendations
* Target financial literacy programs for **22-28 age group**
* Regulate unsecured credit for **low-income earners** (Stats SA: 45% youth unemployment)

## 6. Limitations & Future Work

| Challenge | Solution |
|-----------|----------|
| Simulated data | Partner with banks for anonymized data |
| Static thresholds | Inflation-adjust DTI (Stats CPI data) |
| Johannesburg-centric | Expand to Cape Town/Durban |

## 7. Conclusion
This project delivers:
- ✅ **87.5% accurate debt risk classifier** (XGBoost outperformed RF)
- ✅ **Actionable insights** aligned with SARB/Stats SA guidelines
- ✅ **Demographic-specific risk profiling** for lenders

**Next Steps:** Deploy as a Flask API for real-time scoring.


## Requirements

- Python 3.8+
- XGBoost
- Scikit-learn
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Flask (for API deployment)

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contributors

- Nomcebo Thwala

## Acknowledgments

- Stats SA for demographic and economic insights
- South African Reserve Bank (SARB) for debt guidelines

  ## Contact
  - Linkedin: www.linkedin.com/in/nomcebo-t-44b904261
  - Email: thwalanomcebo123@gmail.com
