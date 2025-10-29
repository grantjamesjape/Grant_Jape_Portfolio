# Grant Jape: Data Scientist Portfolio

**Data Scientist** specializing in **Predictive Modeling, Data Visualization, and ETL Pipelines** to drive **Marketing and Product Strategy**.

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
| **Programming & Modeling** | **Python** (data analysis, modeling, visualization), **R** (RStudio), JMP |
| **Visualization & BI** | **Plotly**, **Dash** (custom dashboarding), **Tableau**, Google Looker Studio, Databox |
| **Business Focus** | Regression Modeling, Revenue Forecasting, KPI Monitoring, Cross-Channel Campaign Optimization, Executive Reporting |
| **Data Warehousing & ETL** | SQL, Data Structuring, Data Collection, Custom Reporting |

---

# Featured Project: Marketing Mix Modeling (MMM) for Budget Allocation

## 🎯 Project Goal

To quantify the return on investment (ROI) for various marketing channels (e.g., social, email, paid ads) and recommend an optimal budget allocation to **maximize predicted revenue/sales conversion**. This project showcases the ability to apply **regression modeling** in Python to solve a critical business strategy problem.

## 💡 Business Context

Modern marketing involves spending across multiple channels. The challenge is that the impact of this spending is often delayed and has a decaying effect (adstock). This project provides a transparent, data-driven regression model to guide strategic budget decisions based on observed impact on sales.

## 🛠️ Methodology & Technical Breakdown

### 1. Data Collection & ETL

* **Source Data:** Aggregated weekly or monthly time-series data on **Marketing Spend per Channel** and the corresponding **Revenue/Sales Conversion**.
* **Wrangling Tool:** Python/Pandas for data cleaning, aggregation, and ensuring time-series alignment.
* **Key Challenge Addressed:** Handling any potential data gaps or outliers to create a clean, synchronized input dataset.

### 2. Feature Engineering (The Advanced Step)

To accurately model the marketing impact, two crucial marketing-specific concepts were engineered:

* **Lagged Variables:** Created features representing the spend from previous periods (e.g., *Spend\_ChannelA\_t-1*) to account for the delayed impact of campaigns.
* **Adstock (Carryover Effect):** Modeled the decaying residual effect of advertising over time using a transformation (e.g., geometrically weighted sum of past spending). This is vital because the impact of an ad today influences sales for days or weeks. 

### 3. Regression Modeling & Selection

* **Initial Model:** **Multiple Linear Regression (MLR)** in Python (using `statsmodels` or `scikit-learn`) was used as a baseline.
* **Refined Model:** Explored using **Regularized Regression** (**Lasso** or **Ridge**) to handle potential **multicollinearity** among channels and to perform feature selection. *\[Justify why you chose the final model—e.g., Lasso for its strong feature selection property and interpretability.]*
    $$Revenue \sim \beta_0 + \beta_1(ChannelA Adstock) + \beta_2(ChannelB Lag) + \dots + \epsilon$$

### 4. Model Validation & Diagnostics

* **Validation:** Assessed the model's predictive power using **R-squared** and **Adjusted R-squared**.
* **Diagnostics:** Crucial for regression. Examined **residuals** for normality and homoscedasticity. Checked for **multicollinearity** (e.g., using Variance Inflation Factor - VIF) to ensure coefficients were statistically reliable for business interpretation.

## 📊 Results and Business Recommendation

* **Key Finding (Quantifiable Impact):** Interpreted the model coefficients ($\beta$ values). For example, "The model shows that every **$1,000** spent on **Email Marketing** generates **$5,200** in revenue, making it the most efficient channel."
* **Communication:** Visualized the marginal ROI of each channel  to clearly communicate findings to leadership.
* **Recommendation:** Based on the model's coefficients, provided a recommended shift in the marketing budget—e.g., "Shift 10% of the Paid Search budget to Email and Social Media to achieve an estimated **4% increase in total revenue** without increasing total spend."

## 🚀 Next Steps (Future Work)

* **Deployment:** Containerize the model using **Docker** and expose it as a **REST API** (e.g., with Flask/FastAPI) so the marketing team can easily input new budget scenarios and receive instant revenue forecasts.
* **Advanced Modeling:** Explore non-linear relationships using models like **Random Forests** or incorporating external factors (e.g., competitor activity, seasonality, or macroeconomic indicators).

---
**Code & Live Demo:** [Link to Repo]

---

**Let's connect!**

[**LinkedIn Profile**](https://www.linkedin.com/in/grantjamesjape/) | [**Email Me**](mailto:grantjape@gmail.com)
