# Grant Jape: Data Scientist Portfolio

**Data Scientist** specializing in **Predictive Modeling, Data Visualization, and ETL Pipelines** to drive **Marketing and Product Strategy**.

[**LinkedIn Profile**](https://www.linkedin.com/in/grantjamesjape/) | [**Email Me**](mailto:grantjape@gmail.com)

---

## 🎓 Education & Background

* **International Master in Data Science and Machine Learning** \| Rome Business School (2024 – 2025)
* **Master in Statistics and Analytics** \| Azusa Pacific University (2019 – 2021) Graduated **Summa Cum Laude** \| GPA: 3.8+
* **Bachelor in Communication** \| Azusa Pacific University (2013 – 2017)

---

## 🚀 Core Expertise & Ability

I bridge the gap between complex data and actionable business decisions, leveraging a **double Masters in Data Science and Machine Learning** and **7+ years** of experience.

| Category | Tools & Languages |
| :--- | :--- |
| **Machine Learning & Modeling** | **Python** (End-to-end model training, hyperparameter tuning, and validation), R (Statistical analysis), **Scikit-Learn**, XGBoost, Neural Networks, Regression, and Clustering |
| **Visualization & BI** | **Dash & Plotly** (Custom application development), **Tableau**, Google Looker Studio, and Databox for interactive internal and client-facing decision support |
| **Data Engineering & ETL** | **Expert SQL** (CTEs, complex joins, and data structuring), automated data collection, and architecting robust DataOps pipelines for model monitoring |
| **Business Strategy** | Revenue & Time-Series Forecasting, KPI Monitoring, Cross-Channel Campaign Optimization, A/B Testing, and Executive-level Strategic Reporting ||

---

# Featured Project 1: 🩺 Medical Insurance Cost Prediction

This project analyzes and models healthcare insurance charges using demographic and lifestyle factors such as age, BMI, smoking status, and region. The goal is to understand **what drives medical insurance costs** and build a predictive model that accurately estimates charges for new customers.

---

## 🎯 **Project Objectives**

- Explore and visualize key patterns in medical insurance data.
- Identify which features (e.g., age, BMI, smoker status) most strongly influence charges.
- Build and tune several machine learning models to predict insurance costs.
- Evaluate model performance using metrics such as MAE, RMSE, and R².
- Present clean, interpretable results suitable for a data science portfolio.

---

## 🧠 **Dataset Overview**

- **File:** `data/insurance.csv`  
- **Records:** 1,338 individual policyholders  
- **Source:** Commonly used open dataset for regression modeling and EDA exercises.

| Feature | Description |
|----------|-------------|
| `age` | Age of the primary beneficiary |
| `sex` | Gender (male/female) |
| `bmi` | Body mass index — indicator of body fat |
| `children` | Number of dependents covered by insurance |
| `smoker` | Whether the individual is a smoker (yes/no) |
| `region` | Residential region in the U.S. (northeast, northwest, southeast, southwest) |
| `charges` | Individual medical insurance cost (USD) |

---

## 📊 **Approach**

1. **Exploratory Data Analysis (EDA)**  
   - Visualize distributions, correlations, and key relationships.  
   - Highlight how smoking and obesity affect charges.

2. **Feature Engineering**  
   - Create new informative variables (e.g., `is_obese`, `smoker_obese_interaction`, `age_group`).

3. **Modeling**  
   - Compare baseline models (Linear Regression, Decision Tree, Random Forest, Gradient Boosting).  
   - Tune Gradient Boosting using GridSearchCV for best performance.

4. **Evaluation & Interpretation**  
   - Compare predictions in log-transformed vs. real-dollar space.  
   - Interpret feature importances and key drivers of cost.

---

## 🧩 **Data Summary**

Descriptive statistics for the target variable (`charges`):

| Statistic | Value |
|------------|--------|
| Count | 1,338 |
| Mean | \$13,270.42 |
| Std Dev | \$12,110.01 |
| Min | \$1,121.87 |
| 25% | \$4,688.07 |
| Median | \$9,382.03 |
| 75% | \$16,717.37 |
| Max | \$63,770.43 |

👉 Full summary saved in [`data/charges_summary_stats.csv`](https://raw.githubusercontent.com/grantjamesjape/Claims_model/main/data/charges_summary_stats.csv).

---

## 📊 Exploratory Data Analysis (EDA)

The goal of EDA is to understand how demographic and lifestyle factors relate to medical insurance charges, spot patterns, and decide which transformations/features will help the model.

---

### 1) Age & BMI vs. Charges (colored by Smoker)
![Age and BMI Scatterplots](https://raw.githubusercontent.com/grantjamesjape/Claims_model/main/charts/scatterplots.png)

**What we see**
- **Smokers** (red) have **substantially higher charges** at nearly every age and BMI.
- Charges for **non-smokers** (blue) rise gently with age and BMI.
- The smoker/non-smoker gap **widens** among older and/or higher-BMI individuals.

**Takeaway:** Smoking is the strongest single driver; its impact compounds with age and BMI.

---

### 2) Charges by Smoker, Region, and Sex
![Charges by Category Boxplots](https://raw.githubusercontent.com/grantjamesjape/Claims_model/main/charts/boxplots.png)

**What we see**
- **Smoker:** Median charges are ~**3× higher** for smokers; extreme upper-tail costs are much more common.
- **Region:** Slight elevation in the **southeast** vs. other regions.
- **Sex:** Minimal difference; gender is weakly informative for charges.

**Takeaway:** Lifestyle (smoking) and regional factors matter more than sex.

---

### 3) Distribution of Charges (Original vs. Log)
![Distribution of Charges](https://raw.githubusercontent.com/grantjamesjape/Claims_model/main/charts/distributions.png)

**What we see**
- Raw charges are **right-skewed** with heavy upper tail (large claims).
- After **log transform**, the distribution is **much closer to normal**.

**Takeaway:** Modeling on `log(charges)` stabilizes variance and improves regression behavior; we convert predictions back to dollars for interpretation.

---

### 4) Feature Correlation Heatmap
![Feature Correlation Heatmap](https://raw.githubusercontent.com/grantjamesjape/Claims_model/main/charts/corr.png)

**Highlights**
- `smoker_yes` shows the **strongest positive correlation** with `log_charges` (~+0.67).
- `age` is moderately correlated (~+0.53).
- `bmi`, `sex`, and `region` exhibit weaker relationships.

**Takeaway:** Expect smoking and age to dominate model importance.

---

### 5) Grouped Descriptive Statistics (Charges by Smoker)
_Source: [`data/grouped_charges_by_smoker_T.csv`](https://raw.githubusercontent.com/grantjamesjape/Claims_model/main/data/grouped_charges_by_smoker_T.csv)_

| Statistic | Non-Smoker | Smoker |
|---|---:|---:|
| Count | 1,064 | 274 |
| Mean | \$8,434.27 | \$32,050.23 |
| Std Dev | \$5,993.78 | \$11,541.55 |
| Min | \$1,121.87 | \$12,829.46 |
| 25% | \$3,986.44 | \$20,826.24 |
| Median | \$7,345.41 | \$34,456.35 |
| 75% | \$11,362.89 | \$41,019.21 |
| Max | \$36,910.61 | \$63,770.43 |

**Takeaway:** Average smoker costs are **~4×** non-smoker costs; the variance is also much larger for smokers.

---

### Summary of EDA Findings

| Factor | Impact on Charges | Notes |
|---|---|---|
| **Smoking** | 🚀 Very high | Primary determinant; effect strengthens with age/BMI |
| **Age** | 📈 Moderate | Steady increase across lifespan |
| **BMI** | ⚖️ Moderate | Higher BMI increases risk; interacts with smoking |
| **Region** | 🌎 Low | Slight uplift in southeast |
| **Sex** | ⚪ Minimal | Weak predictor in this dataset |

---

## 🧩 Feature Engineering

After completing the initial EDA, the next step was to **enhance the predictive power** of the dataset by engineering new variables that better represent health-related risk patterns and nonlinear effects.  
These transformations allow the model to learn more meaningful relationships between **lifestyle**, **age**, and **medical cost** outcomes.

---

### 1️⃣ Creating a Binary Obesity Flag

```python
df['is_obese'] = (df['bmi'] >= 30).astype(int)
```

### 2️⃣ Adding a Smoker–Obesity Interaction Term

```python
df['smoker_obese_interaction'] = ((df['smoker'] == 'yes') & (df['is_obese'] == 1)).astype(int)
```

### 3️⃣ Deriving Age Groups (Binning)

```python
bins = [18, 30, 45, 65, 100]
labels = ['Young_Adult', 'Middle_Adult', 'Senior_Adult', 'Elderly']
df['age_group'] = pd.cut(df['age'], bins=bins, labels=labels, right=False)
```

---

# ⚙️ Modeling & Evaluation

After feature engineering, multiple regression models were trained and compared to predict medical insurance charges.  
The goal was to identify which model best balances **accuracy**, **stability**, and **interpretability**.


## 1️⃣ Data Preparation

Before training, categorical features were one-hot encoded, and the dataset was split into training and testing subsets (80/20 split).  
The target variable `charges` was log-transformed to stabilize variance and reduce skewness:

```python
df = pd.get_dummies(df, drop_first=True)

X = df.drop(["charges", "log_charges"], axis=1)
y = df['charges']
y_log = np.log(y)

X_train, X_test, y_train, y_test = train_test_split(X, y_log, test_size=0.2, random_state=42)
```

This ensured that the model focused on learning proportional relationships rather than raw monetary scale differences.

---

## 2️⃣ Model Comparison

Four supervised learning algorithms were trained and evaluated using key regression metrics:

- **Mean Absolute Error (MAE):** Average magnitude of prediction errors.  
- **Root Mean Squared Error (RMSE):** Penalizes larger errors.  
- **R² Score:** Proportion of variance in the dependent variable explained by the model.

**Models tested:**
1. Linear Regression  
2. Decision Tree Regressor  
3. Random Forest Regressor  
4. Gradient Boosting Regressor

**Performance summary:**

| Model | MAE | RMSE | R² |
|--------|------|------|------|
| Linear Regression | 0.254 | 0.401 | 0.821 |
| Decision Tree | 0.188 | 0.419 | 0.804 |
| Random Forest | 0.197 | 0.374 | 0.844 |
| Gradient Boosting | **0.184** | **0.347** | **0.866** |

**Interpretation:**  
- Linear Regression underperformed due to the nonlinear and interaction-heavy nature of the data.  
- Ensemble tree models — particularly **Gradient Boosting** — handled nonlinearities and complex feature interactions best.  
- Gradient Boosting achieved the **lowest error** and **highest R²**, making it the best-performing model overall.

---

## 3️⃣ Hyperparameter Tuning (Grid Search)

A **GridSearchCV** was performed on the Gradient Boosting model to optimize hyperparameters across a 5-fold cross-validation scheme.

```python
param_grid = {
    'n_estimators': [100, 200, 300, 500],
    'learning_rate': [0.01, 0.05, 0.1, 0.2],
    'max_depth': [3, 4, 5, 6],
    'min_samples_split': [2, 5, 10],
    'subsample': [0.8, 1.0]
}
```

**Best Parameters Found:**

```python
{
 'learning_rate': 0.01,
 'max_depth': 3,
 'min_samples_split': 10,
 'n_estimators': 500,
 'subsample': 0.8
}
```

This configuration reduced overfitting and further improved generalization.

---

## 4️⃣ Final Model Evaluation

The tuned Gradient Boosting model was retrained and tested.  
Metrics on both training and test sets confirmed the model’s robustness:

| Metric | Train | Test |
|---------|--------|-------|
| MAE | 0.182 | 0.188 |
| RMSE | 0.345 | 0.347 |
| R² | 0.857 | 0.866 |

**Interpretation:**  
The close match between training and test metrics indicates **minimal overfitting**.  
An R² of **0.866** suggests that the model explains roughly **87% of the variance** in insurance charges.

---

## 5️⃣ Actual vs. Predicted Performance
![Actual vs Predicted Charges](https://raw.githubusercontent.com/grantjamesjape/Claims_model/main/charts/fit.png)

A scatterplot of **Actual vs. Predicted** charges (in log scale) demonstrated a strong positive linear alignment —  
predictions closely follow the true values, validating the model’s consistency.

## 6️⃣ Feature Importance Analysis

Feature importance values from the final Gradient Boosting model revealed which variables contributed most to predictions.

**Top influential features:**
- `smoker_yes` — dominant predictor of higher charges  
- `age` — consistent upward impact on costs  
- `children` — moderate effect; more dependents often increase total expenses  
- `bmi` — indicates lifestyle-related health risks  

Together, these factors explain the majority of cost variation across individuals.

---

## 7️⃣ Final Results in Dollar Terms

To interpret results in their real-world monetary scale, predictions were exponentiated back to dollar values:

| Metric | Value |
|---------|-------:|
| **MAE** | $1,975.47 |
| **RMSE** | $4,418.27 |
| **R²** | 0.874 |

**Interpretation:**  
- On average, the model’s predictions are within about **$2,000** of actual charges.  
- The **RMSE of $4,400** reflects a reasonable range of expected deviation for real-world cost prediction.  
- With **R² ≈ 0.87**, the model effectively captures the majority of variability in medical expenses.

---

## 🧾 Summary

✅ Gradient Boosting outperformed all other algorithms.  
✅ Strong generalization with minimal overfitting.  
✅ Lifestyle and demographic variables — particularly **smoking**, **age**, **children**, and **BMI** — drive most of the prediction accuracy.  
✅ The final model offers an interpretable, high-performing predictor for healthcare cost estimation.

---

### 🏁 Final Note

This project successfully demonstrated how **data-driven modeling** can uncover key health cost drivers and produce reliable cost predictions.  
Such insights are valuable for both **insurance pricing strategies** and **public health planning**.


---


# 📈 Featured Project 2: Marketing Mix Modeling (MMM) for Budget Allocation on Bike Sales

## Project Overview

This project utilizes advanced econometric techniques to quantify the sales contribution and sensitivity of various marketing channels by building a robust Marketing Mix Model. The primary objective is to move beyond simple linear regression by applying **Geometric Adstock** and **Log Saturation** to provide actionable, time-aware budget allocation insights.

The final model achieved a strong fit ($\mathbf{R^2: 0.731}$) and delivered clear, data-driven recommendations.

---

## 1. Methodology & Diagnostics

### 1.1. Initial Diagnostics: Multicollinearity
The initial Exploratory Data Analysis (EDA) flagged a critical issue: perfect correlation ($r=1.00$) between **Branded Search Spend** and **Facebook Spend**. This forced a feature engineering decision to **combine** these two channels into a single feature, **`Search & Facebook`**, to ensure model stability and prevent estimation failure.

**Marketing Spend Correlation Matrix**
![Correlation Matrix of Marketing Spend Channels](https://raw.githubusercontent.com/grantjamesjape/Bike_Sales_MMM/main/charts/spend_correlation_matrix.png)

### 1.2. Feature Engineering (Advanced MMM)
To capture real-world marketing effects and improve model fidelity, all spend variables were transformed:
* **Geometric Adstock (Decay $\lambda=0.5$):** Models the carryover effect (memory) of advertising.
* **Log Saturation ($\ln(X+1)$):** Models the law of diminishing returns.

---

## 2. Final Model Performance and Fit

The final OLS model, run on the log-adstock-saturated features, yielded strong performance metrics:

| Metric | Result | Interpretation |
| :--- | :--- | :--- |
| **R-squared** | **0.731** | 73.1% of the variance in sales is explained by marketing spend features. |
| **Condition Number** | **461** | Confirms high model stability (after fixing multicollinearity). |
| **P-Value (F-stat)** | **0.000** | The model is statistically significant. |

### Model Fit Visualization

The predicted sales line closely tracks the actual sales, validating the model's ability to capture weekly trends over the full period.

**Actual vs. Predicted Sales**
![Actual vs. Predicted Sales Plot](https://raw.githubusercontent.com/grantjamesjape/Bike_Sales_MMM/main/charts/actual_vs_predicted_sales.png)

---

## 3. Key Findings and Actionable Recommendations

The most crucial output is the **Sales Sensitivity Coefficient**, which dictates which channels drive the highest incremental sales lift.

### Final Channel Sensitivity Ranking

| Channel | Coefficient (Sales Lift) | P-Value | Significance |
| :--- | :--- | :--- | :--- |
| **Nonbranded Search** | **$27,397.20** | 0.0000 | **Significant** |
| **Search & Facebook** | **$10,891.06** | 0.0000 | **Significant** |
| Radio | $1,415.73 | 0.0000 | **Significant** |
| TV | $750.99 | 0.0052 | **Significant** |
| OOH | $-749.44 | 0.0030 | **Significant** |
| Print | $-918.53 | 0.0000 | **Significant** |

### Channel Sensitivity Visualization

**Sales Sensitivity (Coefficient) by Marketing Channel**
![Channel Sensitivity Bar Chart](https://raw.githubusercontent.com/grantjamesjape/Bike_Sales_MMM/main/charts/channel_sensitivity_bar_chart.png)

### Actionable Conclusions

1.  **Prioritize Digital:** **Nonbranded Search** and the combined **Search & Facebook** are the dominant, most efficient drivers of sales. Budget allocation should maximize investment in these areas first.
2.  **Audit Traditional Media:** **OOH** and **Print** exhibit statistically significant **negative** sales coefficients. This is a critical business finding requiring immediate investigation into campaign effectiveness or budget allocation strategy.

---

**Let's connect!**

[**LinkedIn Profile**](https://www.linkedin.com/in/grantjamesjape/) | [**Email Me**](mailto:grantjape@gmail.com)
